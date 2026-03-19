# Galaxy Scripting – Language Fundamentals

Galaxy is the scripting language used in StarCraft II map/mod development. It is a statically-typed, C-like language compiled by the SC2 editor.

---

## File Structure & Includes

Every library uses a split header / implementation pattern:

```galaxy
// In the implementation file (.galaxy):
include "TriggerLibs/NativeLib"   // built-in engine library
include "Lib5A1C9904_h"           // own header (structs, variable declarations, function forward-decls)
include "Lib5A1C9904_SoldierSelectionTeam1.galaxy"  // sub-module include
```

```galaxy
// In the header file (_h.galaxy):
include "TriggerLibs/natives"     // low-level natives
```

- Headers (`_h.galaxy`) contain: `const`, `struct`, global variable declarations, and forward declarations of all functions and triggers.
- Implementation files (`.galaxy`) contain: function bodies, trigger `_Func` / `_Init` implementations, and library init.
- Sub-modules can be split into separate `.galaxy` files and included.

---

## Naming Conventions

All identifiers are prefixed with the library hash to avoid conflicts:

| Kind | Prefix | Example |
|---|---|---|
| Global variable | `libHASH_gv_` | `lib5A1C9904_gv_soldiers` |
| Global function | `libHASH_gf_` | `lib5A1C9904_gf_IsZerg` |
| Trigger variable | `libHASH_gt_` | `lib5A1C9904_gt_SpawnJungle` |
| Struct type | `libHASH_gs_` | `lib5A1C9904_gs_Spawn` |
| Local parameter | `lp_` | `lp_startPosition1` |
| Local variable | `lv_` | `lv_raceName` |
| Auto/compiler var | `auto` prefix | `auto4853DB8A_ae` |
| Const inside function | `c_` prefix (built-in) | `c_timeGame`, `c_playerAny` |

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

Fixed-size arrays are declared with `[size]`. 1-based or 0-based depending on context.

```galaxy
// Declaration (in header):
lib5A1C9904_gs_Spawner[10]   lib5A1C9904_gv_spawners;
int[17]                      lib5A1C9904_gv_playerKills;
unitgroup[100]               lib5A1C9904_gv_jungleUnitGroups;

// Initialization loop:
for (init_i = 0; init_i <= 99; init_i += 1) {
    lib5A1C9904_gv_jungleUnitGroups[init_i] = UnitGroupEmpty();
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

## Library Initialization Pattern

Every library must expose an `InitLib` function that is idempotent:

```galaxy
bool lib5A1C9904_InitLib_completed = false;

void lib5A1C9904_InitLib () {
    if (lib5A1C9904_InitLib_completed) {
        return;
    }
    lib5A1C9904_InitLib_completed = true;

    lib5A1C9904_InitLibraries();   // initialize dependencies
    lib5A1C9904_InitVariables();   // set default values for globals
    lib5A1C9904_InitTriggers();    // register all triggers
}
```

`InitVariables` uses its own completion guard:

```galaxy
bool lib5A1C9904_InitVariables_completed = false;

void lib5A1C9904_InitVariables () {
    if (lib5A1C9904_InitVariables_completed) { return; }
    lib5A1C9904_InitVariables_completed = true;
    // set defaults...
}
```
