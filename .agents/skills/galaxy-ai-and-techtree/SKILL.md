# Galaxy Scripting – AI & Tech Tree

Reference: https://mapster.talv.space/galaxy/reference

---

## Melee AI Initialization

For RTS players that use the standard SC2 melee AI:

```galaxy
// Place starting units (workers + command center/hatchery/nexus)
MeleeInitUnitsForPlayer(lv_player, "Terr", lv_startPoint);
MeleeInitUnitsForPlayer(lv_player, "Zerg", lv_startPoint);
MeleeInitUnitsForPlayer(lv_player, "Prot", lv_startPoint);

// Give starting resources (minerals/gas)
MeleeInitResourcesForPlayer(lv_player, PlayerRace(lv_player));

// Start the AI
AIStart(lv_player, "AI\\Terran.SC2AIData", false, false, false, false);

// Variant that applies to all computer players
MeleeInitAI();
```

---

## AI Build/Train/Research (Script-Level)

```galaxy
// Queue a building
AIBuild(lv_player, "CommandCenter", lv_town, 1, true);
AITrain(lv_player, "Marine", lv_town, 1, true);
AIResearch(lv_player, "MarineRange", lv_town);

// Stock control (maintain a count of a unit type)
AISetStock(lv_player, "Marine", 8);
AISetStockEx(lv_player, "Tank", 4, c_townAny, true, true);

// Clear queues
AIClearBuildQueue(lv_player);
AIClearTrainQueue(lv_player);
```

---

## AI Waves

Waves are AI attack or patrol groups.

```galaxy
// Get a wave
wave lv_wave = AIWaveGet(lv_player, c_waveTypeAttack, 0);

// Get units in a wave
unitgroup lv_waveUnits = AIWaveGetUnits(lv_wave);

// Wave target helpers
wavetarget lv_tgt = AIWaveTargetGatherMelee(lv_player, lv_gatherPoint);
wavetarget lv_tgt2 = AIWaveTargetMeleeDefend(lv_player, lv_defPoint);

// Turn waves on/off
libNtve_gf_CAIWavesEnable(lv_player, true);
libNtve_gf_CAIWaveEnable(lv_player, lv_wave, false);
```

---

## Tech Tree – Upgrades

```galaxy
// Add a level to an upgrade for a player
TechTreeUpgradeAddLevel(lv_player, "MarineRange", 1);
TechTreeUpgradeAddLevel(lv_player, "MarineRange", -1);  // remove a level

// Set to specific level
TechTreeUpgradeSetLevel(lv_player, "MarineRange", 2);

// Read current level
int lv_lvl = TechTreeUpgradeGetLevel(lv_player, "MarineRange");

// Event when an upgrade changes
TriggerAddEventUpgradeLevelChanged(myTrigger, c_playerAny);
// Inside handler:
string lv_upgrade = EventUpgradeName();
int    lv_delta   = EventUpgradeLevelDelta();  // +1 or -1
int    lv_player  = EventPlayer();
```

---

## Tech Tree – Unit Counts

```galaxy
// How many of a unit type does player have?
int lv_count = TechTreeUnitCount(lv_player, "Marine", c_techCountBoth);

// Count constants
c_techCountAny   // counting training + alive
c_techCountBoth  // both alive and in training
c_techCountMade  // how many have ever been trained
c_techCountLost  // how many have been killed
```

---

## Tech Tree – Restrictions

```galaxy
// Stop a player from training/building something
TechTreeRestrictionsEnable(lv_player, "Banshee", true);  // restrict
TechTreeRestrictionsEnable(lv_player, "Banshee", false); // allow

// Check if restricted
bool lv_restr = TechTreeRestrictionsEnabled(lv_player, "Banshee");

// Requirements (prerequisite check)
TechTreeRequirementsEnable(lv_player, false); // disable all requirements checks
```

---

## Tech Tree – Production

```galaxy
// Set production cap (max simultaneous training of a type)
TechTreeProductionCapSet(lv_player, "Marine", 5);

// Reset
TechTreeProductionCapSet(lv_player, "Marine", c_techTreeProductionCapUnlimited);
```

---

## Proxima Frontlines: Wave Upgrade Pattern

The map applies upgrades per wave to scale enemy difficulty:

```galaxy
void lib5A1C9904_gf_AddUpdateForWaves(int lp_player, string lp_upgrade) {
    // tracks which upgrades to add each wave
    TechTreeUpgradeAddLevel(lp_player, lp_upgrade, 1);
}

void lib5A1C9904_gf_RemoveUpdateForWaves(int lp_player, string lp_upgrade) {
    TechTreeUpgradeAddLevel(lp_player, lp_upgrade, -1);
}

// Called at start of each new wave:
void lib5A1C9904_gf_ApplyWaveUpgrades(int lp_waveNumber) {
    if (lp_waveNumber == 3) {
        lib5A1C9904_gf_AddUpdateForWaves(
            lib5A1C9904_gv_rTSPlayer1, "InflictedDamageIncrease");
    }
}
```

---

## AI Towns (Advanced)

```galaxy
// Get number of mineral/gas spots in a town
int lv_minerals = AIGetMineralNumSpots(lv_player, lv_town);
int lv_gas      = AIGetRawGasNumSpots(lv_player, lv_town);

// Get a town's gathering/defense locations
point lv_gather  = AIGetGatherLocation(lv_player, lv_town);
point lv_defense = AIGetGatherDefLocation(lv_player, lv_town);

// Set default economy behavior
AIDefaultEconomy(lv_player);
AIDefaultExpansion(lv_player);
```

---

## AI Evaluation

```galaxy
// Compare relative strengths
int lv_ratio = AIEvalRatio(lv_player1, lv_player2);
int lv_wRatio = AIWaveEvalRatio(lv_wave, lv_targetPlayer);

// Get best attack target
point lv_target = AIGetBestTarget(lv_player, lv_town, c_aiAttackWaveGround);
```
