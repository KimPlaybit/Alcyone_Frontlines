# Galaxy Scripting – Language Fundamentals

Galaxy is the scripting language used in StarCraft II map/mod development. It is a statically-typed, C-like language compiled by the SC2 editor.

---

## File Structure & Includes

Code is split across multiple `.galaxy` files using `include`. The entry point is `MapScript.galaxy`, which hands off to a `scripts/main.galaxy` coordinator:

```galaxy
// MapScript.galaxy (editor-managed — do not add logic here)
include "TriggerLibs/NativeLib"
include "TriggerLibs/LibertyLib"
void InitLibs() { libNtve_InitLib(); libLbty_InitLib(); }
include "scripts/main"
void InitCustomScript() { main(); }
void InitMap() { InitLibs(); InitCustomScript(); }
```

```galaxy
// scripts/main.galaxy — coordinator, lists all includes and defines main()
include "scripts/Enums"
include "scripts/GlobalVariables"
include "scripts/Header"
include "scripts/Utilities"
// ... all other files ...
include "scripts/MapInit"

void main() {
    TriggerAddEventMapInit(TriggerCreate("MapInit_Main"));
}
```

- Paths in `include` are **relative to the map root**, no `.galaxy` extension.
- Order matters: a file can only use types/functions declared in earlier includes.
- `Header.galaxy` holds forward declarations so files can call functions defined later in the include chain.
- See `galaxy-code-organization` skill for the full file-splitting pattern.

### Campaign map pattern (WoL / HotS / LotV story missions)
Campaign maps include three engine libraries — NativeLib + LibertyLib + CampaignLib:
```galaxy
include "TriggerLibs/NativeLib"
include "TriggerLibs/LibertyLib"
include "TriggerLibs/CampaignLib"

void InitLibs() {
    libNtve_InitLib();
    libLbty_InitLib();
    libCamp_InitLib();
}
```
This gives access to `libNtve_*` (native helpers), `libLbty_*` (Liberty/WoL helpers), and `libCamp_*` (campaign-specific API: transmissions, objectives, story state, drop pods, etc.).

### Library mod pattern (alternate)
When working inside an `.SC2Mod` library, files use a split header/impl pattern with a hash prefix:
```galaxy
include "TriggerLibs/NativeLib"
include "Lib5A1C9904_h"  // header: structs, globals, forward decls
```

### Test map / simple map pattern (alternate)
Some small maps use a no-path include with just the library name:
```galaxy
include "LibHASH"   // no path, no extension — editor resolves from linked dependencies
```

---

## Naming Conventions

### Standalone map / SC2Map (primary — SSF pattern)

| Kind | Convention | Example |
|---|---|---|
| Global variable | `gv_SystemName_Variable` | `gv_PlayerStats`, `gv_ActivePG` |
| Global const (game-wide config) | `gv_MaxX` | `gv_MaxAmountPlayers`, `gv_GameTimeMax` |
| Named constant / enum | `c_Category_Name` | `c_Part_Terran`, `c_BossFightState_Alive` |
| Function | `SystemName_Action` | `Player_AddExp`, `MapInit_ActivePlayers` |
| Static trigger param | `SystemName_Param_Name` | `Utility_DelayedTextTagDestroyer_ParamTextTag` |
| Local variable | no prefix (short name) | `tmpInt`, `hero`, `playerID` |
| Struct field | no prefix | `activeFlag`, `heroUnit`, `bankfile` |

### Library mod / SC2Mod (alternate — editor-generated)

| Kind | Prefix | Example |
|---|---|---|
| Global variable | `libHASH_gv_` | `lib5A1C9904_gv_soldiers` |
| Global function | `libHASH_gf_` | `lib5A1C9904_gf_IsZerg` |
| Trigger variable | `libHASH_gt_` | `lib5A1C9904_gt_SpawnJungle` |
| Struct type | `libHASH_gs_` | `lib5A1C9904_gs_Spawn` |
| Local parameter | `lp_` | `lp_startPosition1` |
| Local variable | `lv_` | `lv_raceName` |

---

## Primitive Types

```galaxy
int     lv_count = 0;          // integer
bool    lv_flag = true;        // boolean
string  lv_name = "";          // text string (ASCII)
text    lv_display;            // localized text (UI)
fixed   lv_amount = 3.5;       // fixed-point number (like float)
```

### Engine Handle Types

```galaxy
unit        lv_hero;           // reference to a unit on the map
unitgroup   lv_soldiers;       // a collection of units
playergroup lv_team;           // a collection of player slots
trigger     lv_spawnTrigger;   // a trigger object
bank        lv_bank;           // a saved bank file
point       lv_pos;            // a 2D map coordinate
color       lv_col;            // RGBA color
```

---

## Constants

```galaxy
// In a header file:
const int lib5A1C9904_gv_heroDialogWidth = 1200;
const int lib5A1C9904_gv_buttonSizePickY = 50;

// Built-in engine constants use the c_ prefix:
c_timeGame          // time constant for Wait()
c_playerAny         // wildcard player slot
c_invalidDialogControlId
c_invalidDialogId
c_anchorTopLeft
c_stringAnywhere
c_stringNoCase
c_unitCountAll
c_gameOverVictory
c_gameOverDefeat
c_playerPropMinerals
c_playerPropVespene
c_playerPropOperSetTo
c_unitPropEnergy
c_unitPropCurrent
c_allianceIdSeekHelp
c_allianceIdChat
c_targetFilterMissile
c_targetFilterDead
c_targetFilterHidden
```

---

## Structs

Structs are declared in header files. Fields are accessed with `.`.

```galaxy
// Declaration:
struct lib5A1C9904_gs_Spawner {
    point  lv_point;
    string lv_unitType;
    int    lv_player;
};

struct lib5A1C9904_gs_Spawn {
    point                          lv_point;
    lib5A1C9904_gs_UnitsToSpawn[5] lv_unitSpawn;  // fixed-size array field
    int                            lv_respawnTime;
    int                            lv_spawnTime;
    trigger                        lv_deathCallbackTrigger;
};

// Usage:
lib5A1C9904_gv_spawners[lv_index].lv_unitType = "Marine";
lib5A1C9904_gv_createdSpawners[lv_index].lv_lastIndexPoint += 1;
```

Passing structs by reference uses `structref<T>`:

```galaxy
void lib5A1C9904_gf_AddJungleSpawn (structref<lib5A1C9904_gs_Spawn> lp_toSpawn) {
    lib5A1C9904_gv_jungleToSpawn[lib5A1C9904_gv_lastIndexOfSpawn].lv_point = lp_toSpawn.lv_point;
}
```

---

## Arrays

Fixed-size arrays are declared with `[size]`. 0-based indexing is typical.

```galaxy
// Declaration (in GlobalVariables.galaxy):
PlayerStruct[gv_MaxAmountPlayers + 1] gv_PlayerStats;   // indexed 1..gv_MaxAmountPlayers
int[gv_MaxAmountParts] gv_PartWins;                     // sized by const

// Multi-dimensional array (part x difficulty x playerCount):
int[gv_MaxAmountParts][gv_MaxAmountDifficulties][gv_MaxAmountPlayers] speedrunsTime;

// Initialization loop:
int tmpInt = 0;
for (; tmpInt < gv_MaxAmountPlayers; tmpInt += 1) {
    gv_ActivePG = PlayerGroupEmpty();
}
```

---

## Control Flow

```galaxy
// if / else if / else
if ((lib5A1C9904_gf_IsSurvival() == true)) {
    // ...
}
else if ((lv_raceCheck == true)) {
    // ...
}
else {
    // ...
}

// for loop (Galaxy compiler pattern – uses auto variables):
const int auto4853DB8A_ai = 1;
int auto4853DB8A_ae = lib5A1C9904_gv_spawnerLastIndex;
lv_index = 0;
for ( ; ( (auto4853DB8A_ai >= 0 && lv_index <= auto4853DB8A_ae)
         || (auto4853DB8A_ai < 0 && lv_index >= auto4853DB8A_ae) )
      ; lv_index += auto4853DB8A_ai ) {
    // body
}

// while (PlayerGroup iteration pattern):
lv_loopedPlayer = -1;
while (true) {
    lv_loopedPlayer = PlayerGroupNextPlayer(autoGroup, lv_loopedPlayer);
    if (lv_loopedPlayer < 0) { break; }
    // body
}

// switch-style (auto val):
int auto4221B408_val = lv_race;
if (auto4221B408_val == 1) { PlayerSetRace(lp_player, "Terr"); }
else if (auto4221B408_val == 2) { PlayerSetRace(lp_player, "Zerg"); }
else if (auto4221B408_val == 3) { PlayerSetRace(lp_player, "Prot"); }
```

---

## String Operations

```galaxy
StringContains(haystack, needle, c_stringAnywhere, c_stringNoCase)  // → bool
StringEqual(a, b, c_stringNoCase)                                   // → bool
IntToString(lv_count)                                               // → string
FixedToText(lv_fixed, c_fixedPrecisionAny)                          // → text
TextToString(lv_text)                                               // → string
StringExternal("Param/Value/lib_5A1C9904_KeyName")                  // → text (localized)
```

Concatenation uses `+`:

```galaxy
string lv_key = lp_key + IntToString(lv_index);
text lv_msg = lv__KilledTextBuilder + StringExternal("Param/Value/lib_5A1C9904_956C1A6F") + lv__KillerTextBuilder;
```

---

## Color

```galaxy
color lv_allyColor  = Color(28*100/255, 167*100/255, 234*100/255);
color lv_enemyColor = Color(100.00, 0.00, 0.00);
color lv_transparent = ColorWithAlpha(0, 0, 0, 0);
color lv_playerColor = libNtve_gf_ConvertPlayerColorToColor(PlayerGetColorIndex(lp_player, false));
```

---

## Map Initialization Pattern (SSF)

The bootstrap chain: `MapScript.galaxy` → `main()` → map-init trigger → init functions:

```galaxy
// scripts/main.galaxy
void main() {
    TriggerAddEventMapInit(TriggerCreate("MapInit_Main"));
}

// scripts/MapInit.galaxy
bool MapInit_Main(bool testCond, bool runActions) {
    MapInit_ActivePlayers();   // alliances, playergroups
    SSFCustomUI_Init();        // UI
    PartTerran_TriggerCreate(); // register part triggers
    // ... other init calls
    return true;
}
```

### Library mod init pattern (alternate)

Libraries use an idempotent `InitLib` function:
```galaxy
bool lib5A1C9904_InitLib_completed = false;
void lib5A1C9904_InitLib() {
    if (lib5A1C9904_InitLib_completed) { return; }
    lib5A1C9904_InitLib_completed = true;
    lib5A1C9904_InitVariables();
    lib5A1C9904_InitTriggers();
}
```
