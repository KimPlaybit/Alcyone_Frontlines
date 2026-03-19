# Galaxy Scripting – Players & Alliances

Reference: https://mapster.talv.space/galaxy/reference

---

## Player Slots in Proxima Frontlines

```galaxy
// Library-specific globals (declare in _h.galaxy)
int  lib5A1C9904_gv_rTSPlayer1;          // Team 1 RTS player (1-based slot)
int  lib5A1C9904_gv_rTSPlayer2;          // Team 2 RTS player
playergroup lib5A1C9904_gv_soldierPlayers1;  // All soldier players on team 1
playergroup lib5A1C9904_gv_soldierPlayers2;  // All soldier players on team 2
```

---

## Player Groups

### Creating / populating

```galaxy
playergroup lv_pg = PlayerGroupEmpty();     // empty group
PlayerGroupAdd(lv_pg, 3);                   // add player 3
PlayerGroupAdd(lv_pg, 4);

playergroup lv_all    = PlayerGroupAll();    // all players (observers too)
playergroup lv_active = PlayerGroupActive();// only active (connected, playing) players
playergroup lv_single = PlayerGroupSingle(lv_player);// single-player group

// From lobby — all players assigned to a team
playergroup lv_team1 = GameAttributePlayersForTeam(1);
```

### Querying

```galaxy
bool lv_has   = PlayerGroupHasPlayer(lv_pg, 2);
int  lv_count = PlayerGroupCount(lv_pg);
```

### Iterating

```galaxy
playergroup lv_group = lib5A1C9904_gv_soldierPlayers1;
int lv_player = -1;
while (true) {
    lv_player = PlayerGroupNextPlayer(lv_group, lv_player); // start at -1
    if (lv_player < 0) { break; }
    // act on lv_player ...
}
```

---

## Player Info

```galaxy
string lv_name   = PlayerName(lv_player);
string lv_race   = PlayerRace(lv_player);            // "Terr", "Zerg", "Prot", "random"
int    lv_color  = PlayerGetColorIndex(lv_player, false);
color  lv_c      = libNtve_gf_ConvertPlayerColorToColor(lv_player);

// Slot state
int lv_status = PlayerStatus(lv_player);  // c_playerStatusActive, c_playerStatusLeft, etc.
bool lv_active = (lv_status == c_playerStatusActive);

// Slot type
PlayerType(lv_player);  // c_playerTypeUser, c_playerTypeComputer, c_playerTypeHuman
```

---

## Race Helpers (project pattern)

```galaxy
bool lib5A1C9904_gf_IsTerran(int lp_player) {
    return StringContains(PlayerRace(lp_player), "Terr", c_stringAnywhere, c_stringNoCase);
}
bool lib5A1C9904_gf_IsZerg(int lp_player) {
    return StringContains(PlayerRace(lp_player), "Zerg", c_stringAnywhere, c_stringNoCase);
}
bool lib5A1C9904_gf_IsProtoss(int lp_player) {
    return StringContains(PlayerRace(lp_player), "Prot", c_stringAnywhere, c_stringNoCase);
}
```

---

## Setting Race

```galaxy
PlayerSetRace(lv_player, "Terr");   // "Terr", "Zerg", "Prot"
```

---

## Alliance Settings

### Using the library helper (recommended)

```galaxy
// Ally with full shared vision
libNtve_gf_SetAlliance(1, 2, libNtve_ge_AllianceSetting_AllyWithSharedVision);

// Enemy
libNtve_gf_SetAlliance(1, 3, libNtve_ge_AllianceSetting_Enemy);

// Neutral with shared vision
libNtve_gf_SetAlliance(1, 2, libNtve_ge_AllianceSetting_NeutralWithSharedVision);

// Neutral (no vision)
libNtve_gf_SetAlliance(1, 2, libNtve_ge_AllianceSetting_Neutral);

// Other presets
libNtve_ge_AllianceSetting_Passive
libNtve_ge_AllianceSetting_AllyWithAlliedVictory
```

### Low-level alliance control

```galaxy
// Set a specific alliance channel
PlayerSetAlliance(lv_player, c_allianceIdTrade,     lv_other, true);
PlayerSetAlliance(lv_player, c_allianceIdControl,   lv_other, true);
PlayerSetAlliance(lv_player, c_allianceIdSeekHelp,  lv_other, false);
PlayerSetAlliance(lv_player, c_allianceIdPassive,   lv_other, false);
PlayerSetAlliance(lv_player, c_allianceIdSharedVision, lv_other, true);

// Query an alliance channel
bool lv_allied = PlayerGetAlliance(lv_player, c_allianceIdChat, lv_other);

// Common alliance ID constants
c_allianceIdTrade
c_allianceIdControl
c_allianceIdSeekHelp
c_allianceIdPassive
c_allianceIdPushToTalk
c_allianceIdSharedVision
c_allianceIdChat
```

### Enemy/ally relationship check

```galaxy
// libNtve helper
bool lv_isEnemy = libNtve_gf_PlayerIsEnemy(
    lv_me, lv_target,
    libNtve_ge_PlayerRelation_Enemy  // or _Ally or _Neutral
);
```

---

## Player Resources

```galaxy
// Read
int lv_minerals = PlayerGetPropertyInt(lv_player, c_playerPropMinerals);
int lv_gas      = PlayerGetPropertyInt(lv_player, c_playerPropVespene);
int lv_supply   = PlayerGetPropertyInt(lv_player, c_playerPropSuppliesUsed);

// Write (absolute set)
PlayerModifyPropertyInt(lv_player, c_playerPropMinerals, c_playerPropOperSetTo, 500);

// Write (add/subtract)
PlayerModifyPropertyInt(lv_player, c_playerPropMinerals, c_playerPropOperAdd, 100);
PlayerModifyPropertyInt(lv_player, c_playerPropVespene,  c_playerPropOperSubtract, 25);

// Common property constants
c_playerPropMinerals
c_playerPropVespene
c_playerPropSuppliesUsed
c_playerPropSuppliesMade
c_playerPropSuppliesLimit
c_playerPropKills
c_playerPropDeaths
```

---

## Camera Control

```galaxy
// Pan camera to point
CameraPan(lv_player, lv_point, 0.0, -1, 10.0, false);
// (player, point, distance, yaw, pitch, sync)

// Snap camera instantly
CameraSetTarget(lv_player, lv_point, 0.0, -1, 10.0, false);
```

---

## Game Attributes (Lobby Options)

Used to read lobby-configured game settings:

```galaxy
// Returns the string value of the attribute for this player/game
string lv_val = GameAttributeGameValue("1");   // attribute id "1"

// Project mode detection pattern (from lib5A1C9904):
bool lib5A1C9904_gf_GetWaveStatus() {
    return (GameAttributeGameValue("1") == "0001");
}
bool lib5A1C9904_gf_WithRTSPlayer() {
    return (GameAttributeGameValue("4") == "0001");
}
bool lib5A1C9904_gf_IsSurvival() {
    return (GameAttributeGameValue("3") == "0001");
}
```

---

## Game Over

```galaxy
// For a specific player
GameOver(lv_player, c_gameOverVictory, true, true);  // (player, result, showScore, restart)
GameOver(lv_player, c_gameOverDefeat,  true, true);

// For a playergroup
libNtve_gf_EndGameForPlayerGroup(lv_group, c_gameOverVictory, true, true);

// Constants
c_gameOverVictory
c_gameOverDefeat
c_gameOverLeave
c_gameOverTie
```

---

## Player Color

```galaxy
// Get color index
int lv_idx = PlayerGetColorIndex(lv_player, false);

// Convert to color value
color lv_color = libNtve_gf_ConvertPlayerColorToColor(lv_player);

// Use in text
text lv_colored = TextWithColor(StringToText(PlayerName(lv_player)), lv_color);
```

---

## Setup Pattern (from lib5A1C9904)

```galaxy
// Typical alliance init for 2-team game
void lib5A1C9904_gf_SetupAlliances() {
    int lv_p1 = -1;
    int lv_p2 = -1;

    // All team 1 members ally each other
    while (true) {
        lv_p1 = PlayerGroupNextPlayer(lib5A1C9904_gv_soldierPlayers1, lv_p1);
        if (lv_p1 < 0) { break; }
        lv_p2 = -1;
        while (true) {
            lv_p2 = PlayerGroupNextPlayer(lib5A1C9904_gv_soldierPlayers1, lv_p2);
            if (lv_p2 < 0) { break; }
            if (lv_p1 == lv_p2) { continue; }
            libNtve_gf_SetAlliance(lv_p1, lv_p2, libNtve_ge_AllianceSetting_AllyWithSharedVision);
        }
    }
}
```
