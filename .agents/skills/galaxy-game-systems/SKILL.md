# Galaxy Scripting – Game Systems

Reference: https://mapster.talv.space/galaxy/reference

---

## Bank System (Save / Load Player Data)

Banks persist data between sessions per player. One bank = one named file tied to one player slot.

```galaxy
// Open (create if missing)
BankLoad("ProximaFrontlines", lv_player);
bank lv_bank = BankLastCreated();

// Wait for async load to complete (needed if called at game start)
BankWait(lv_bank);

// Check section/key existence
bool lv_has = BankKeyExists(lv_bank, "Stats", "TotalKills");

// Read values
int   lv_kills   = BankValueGetAsInt(lv_bank, "Stats", "TotalKills");
bool  lv_flag    = BankValueGetAsFlag(lv_bank, "Flags", "CompletedTutorial");
fixed lv_score   = BankValueGetAsFixed(lv_bank, "Stats", "BestScore");
text  lv_name    = BankValueGetAsText(lv_bank, "Profile", "Name");

// Write values
BankValueSetFromInt(lv_bank, "Stats", "TotalKills", lv_kills + 1);
BankValueSetFromFlag(lv_bank, "Flags", "CompletedTutorial", true);
BankValueSetFromFixed(lv_bank, "Stats", "BestScore", 9999.0);

// Save to disk
BankSave(lv_bank);

// Remove section
BankSectionRemove(lv_bank, "OldData");

// Remove a key
BankKeyRemove(lv_bank, "Stats", "OldKey");
```

### Proxima Frontlines bank init pattern

```galaxy
void lib5A1C9904_gf_InitBank(int lp_player) {
    BankLoad("ProximaFrontlines", lp_player);
    lib5A1C9904_gv_playerBank[lp_player] = BankLastCreated();
    BankWait(lib5A1C9904_gv_playerBank[lp_player]);

    if (!BankKeyExists(lib5A1C9904_gv_playerBank[lp_player], "Stats", "Kills")) {
        BankValueSetFromInt(lib5A1C9904_gv_playerBank[lp_player], "Stats", "Kills", 0);
        BankSave(lib5A1C9904_gv_playerBank[lp_player]);
    }
}
```

---

## Spawner / Wave System

Proxima Frontlines uses a custom spawner system built on top of `UnitCreate` and a trigger loop.

### Spawner structs (from _h.galaxy)

```galaxy
struct gs_Spawner {
    point spawnPoint;
    string unitType;
    int player;
}

struct gs_CreatedSpawner {
    unit spawner;
    point[11] movePoints;    // waypoints after spawn
    int lastIndexPoint;
    int amountOfUnits;
    string waveUnitType;
}
```

### Adding a spawner

```galaxy
int lib5A1C9904_gf_AddSpawner(
    point lp_spawnPoint,
    string lp_unitType,
    string lp_waveType,
    int lp_amount,
    int lp_player
) {
    // stores in gv_spawners array, increments counter, returns index
}

void lib5A1C9904_gf_AddNewWavePoint(point lp_wavePoint, int lp_spawnerIndex) {
    // appends to gv_createdSpawners[lp_spawnerIndex].movePoints
}
```

### Creating all spawners

```galaxy
void lib5A1C9904_gf_CreateSpawners() {
    int lv_i = 1;
    for (; lv_i <= lib5A1C9904_gv_spawnerCount ; lv_i += 1) {
        UnitCreate(1,
            lib5A1C9904_gv_spawners[lv_i].unitType,
            c_unitCreateIgnorePlacement,
            lib5A1C9904_gv_spawners[lv_i].player,
            lib5A1C9904_gv_spawners[lv_i].spawnPoint,
            270.0
        );
        lib5A1C9904_gv_createdSpawners[lv_i].spawner = UnitLastCreated();
        UnitSetState(lib5A1C9904_gv_createdSpawners[lv_i].spawner,
            c_unitStateInvulnerable, true);
    }
}
```

### Enabling/disabling spawns

```galaxy
TriggerEnable(lib5A1C9904_gt_SpawnUnits, true);   // start spawning
TriggerEnable(lib5A1C9904_gt_SpawnUnits, false);  // pause spawning
```

---

## Jungle / Camp Respawn System

```galaxy
struct gs_UnitsToSpawn {
    string unitType;
    int count;
}

struct gs_Spawn {
    point spawnPoint;
    gs_UnitsToSpawn[5] units;
    int respawnTime;     // seconds until respawn
    int spawnTime;       // countdown (modified at runtime)
    trigger deathCallbackTrigger;
}

// Register a jungle camp
void lib5A1C9904_gf_AddJungleSpawn(
    point lp_spawnPoint,
    string lp_unitType1, int lp_count1,
    int lp_respawnSeconds
) {
    // stores in gv_jungleSpawns[] array
}

// Respawn callback — attached as TriggerAddEventUnitDied
bool lib5A1C9904_gf_JungleDeath_Func(bool testConds, bool runActions) {
    // record death time, start respawn timer
    Wait(lib5A1C9904_gv_jungleSpawns[lv_idx].respawnTime * 1.0, c_timeGame);
    // recreate units at spawn point
    lib5A1C9904_gf_Respawn(lv_idx);
    return true;
}
```

---

## Resource Rewards (Jungle Unit Kills)

```galaxy
struct gs_JG_PricePerUnit {
    string unitType;
    int minerals;
    int gas;
}

// Register a reward
void lib5A1C9904_gf_AddUnitJunglePrice(
    string lp_unitType,
    int lp_minerals,
    int lp_gas
) {
    // stores in gv_junglePrices[] by index
}

// Distribute reward on kill
void lib5A1C9904_gf_GiveResource(unit lp_killedUnit, int lp_killerPlayer) {
    int lv_i = 1;
    for (; lv_i <= lib5A1C9904_gv_junglePricesCount ; lv_i += 1) {
        if (UnitGetType(lp_killedUnit) == lib5A1C9904_gv_junglePrices[lv_i].unitType) {
            PlayerModifyPropertyInt(lp_killerPlayer, c_playerPropMinerals,
                c_playerPropOperAdd, lib5A1C9904_gv_junglePrices[lv_i].minerals);
            PlayerModifyPropertyInt(lp_killerPlayer, c_playerPropVespene,
                c_playerPropOperAdd, lib5A1C9904_gv_junglePrices[lv_i].gas);
            return;
        }
    }
}
```

---

## Tech Tree Upgrades

```galaxy
// Add an upgrade level to a player's tech tree
TechTreeUpgradeAddLevel(lv_player, "UpgradeName", 1);   // +1 level
TechTreeUpgradeAddLevel(lv_player, "UpgradeName", -1);  // -1 level (downgrade)

// Set level to a specific value
TechTreeUpgradeSetLevel(lv_player, "UpgradeName", 3);

// Get current level
int lv_lvl = TechTreeUpgradeGetLevel(lv_player, "UpgradeName");

// Query event for upgrade changes
TriggerAddEventUpgradeLevelChanged(myTrigger, c_playerAny);
// Inside handler:
string lv_upgrade = EventUpgradeName();
int    lv_delta   = EventUpgradeLevelDelta();

// Production restrictions
TechTreeRestrictionsEnable(lv_player, "Marine", false);   // allow
TechTreeRestrictionsEnable(lv_player, "Marine", true);    // restrict
```

---

## Melee Init (RTS Player Setup)

Initializes the default melee economy and unit placement for an AI/RTS player:

```galaxy
// Place starting units at startPoint for the given player and race
MeleeInitUnitsForPlayer(lv_player, PlayerRace(lv_player), lv_startPoint);

// Give standard starting resources
MeleeInitResourcesForPlayer(lv_player, PlayerRace(lv_player));

// Optionally set upgrade levels for the RTS player
libNtve_gf_SetUpgradeLevelForPlayer(lv_player, "UpgradeName", 1);
```

---

## Scoreboard (Custom Dialog Labels)

```galaxy
// Arrays declared in _h.galaxy (indexed by player number)
dialogcontrol lib5A1C9904_gv_scoreboard_kills[17];
dialogcontrol lib5A1C9904_gv_scoreboard_deaths[17];
dialogcontrol lib5A1C9904_gv_scoreboard_minerals[17];
int           lib5A1C9904_gv_playerKills[17];
int           lib5A1C9904_gv_playerDeaths[17];

// Update function
void lib5A1C9904_gf_UpdateScoreboard(
    int lp_player, int lp_kills, int lp_deaths, int lp_minerals
) {
    lib5A1C9904_gv_playerKills[lp_player] = lp_kills;
    libNtve_gf_SetDialogItemText(
        lib5A1C9904_gv_scoreboard_kills[lp_player],
        IntToText(lp_kills),
        PlayerGroupAll()
    );
    libNtve_gf_SetDialogItemText(
        lib5A1C9904_gv_scoreboard_deaths[lp_player],
        IntToText(lp_deaths),
        PlayerGroupAll()
    );
}
```

---

## Death & Revive System

```galaxy
bool lib5A1C9904_gt_HeroDied_Func(bool testConds, bool runActions) {
    unit  lv_dead   = EventUnit();
    int   lv_player = UnitGetOwner(lv_dead);
    int   lv_revive = 10;   // seconds

    // Display death message
    lib5A1C9904_gf_DisplayDeathMessage(lv_dead, EventKillingUnit(), lv_revive);

    // Wait then revive
    Wait(lv_revive * 1.0, c_timeGame);

    // Check if all team mates are dead
    if (libNtve_gf_UnitGroupIsDead(lib5A1C9904_gv_soldierPlayers1)) {
        // Team wipe — game over
        return true;
    }

    // Respawn at base
    UnitCreate(1, UnitGetType(lv_dead), c_unitCreateIgnorePlacement,
        lv_player, lib5A1C9904_gf_GetSpawnPointTeam1(), 270.0);
    return true;
}
```

---

## Heal Spots

```galaxy
// Find the closest healing structure for a unit (Zerg vs non-Zerg)
point lib5A1C9904_gf_FindHealspot(unit lp_unit) {
    int   lv_player = UnitGetOwner(lp_unit);
    point lv_pos    = UnitGetPosition(lp_unit);

    if (lib5A1C9904_gf_IsZerg(lv_player)) {
        // Return position of allied town hall (hatchery)
        return UnitGetPosition(lib5A1C9904_gv_healStructureZerg[lv_player]);
    } else {
        // Return position of nearest heal unit from the heal units group
        return UnitGetPosition(
            UnitGroupClosestToPoint(lib5A1C9904_gv_healUnitsRTS1, lv_pos)
        );
    }
}
```

---

## Game Attributes (Mode Detection)

```galaxy
// Read lobby options (set at game creation)
string lv_attr = GameAttributeGameValue("attrId");

// Pattern used in lib5A1C9904:
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

## Game Time

```galaxy
fixed lv_elapsed  = GameGetMissionTime();   // seconds since map start
fixed lv_timeGame = TimerGetElapsed(lv_timer);

// Async delay in a trigger function
Wait(5.0, c_timeGame);     // 5 game seconds
Wait(1.0, c_timeReal);     // 1 real second
```
