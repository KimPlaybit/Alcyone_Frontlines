# Galaxy Scripting – Units & Unit Groups

Reference: https://mapster.talv.space/galaxy/reference

---

## Creating Units

```galaxy
// Basic create
UnitCreate(1, "Marine", c_unitCreateIgnorePlacement, 1, lv_point, 270.0);
unit lv_marine = UnitLastCreated();

// Via library helpers (common variants)
libNtve_gf_CreateUnitsAtPoint2(1, "Marine", 1, lv_point);
libNtve_gf_UnitCreateFacingPoint(1, "Marine", 0, 1, lv_point, lv_facingPoint);

// UnitCreate flags
c_unitCreateIgnorePlacement    // ignore placement rules (most common)
c_unitCreateUsePreferences     // use placement preferences
```

---

## Testing Units

```galaxy
bool lv_alive   = UnitIsAlive(lv_unit);
bool lv_valid   = UnitIsValid(lv_unit);
bool lv_dead    = !UnitIsAlive(lv_unit);
bool lv_type    = (UnitGetType(lv_unit) == "Marine");
int  lv_owner   = UnitGetOwner(lv_unit);
```

---

## Destroying / Removing Units

```galaxy
UnitKill(lv_unit);          // kill (triggers death events)
UnitRemove(lv_unit);        // remove instantly (no events)
```

---

## Unit Position & Facing

```galaxy
point lv_pos = UnitGetPosition(lv_unit);
UnitSetPosition(lv_unit, lv_newPos, false);          // false = no smooth move
UnitSetFacing(lv_unit, 90.0, 0.0);                   // angle in degrees, duration 0
fixed lv_facing = UnitGetFacing(lv_unit);
```

---

## Unit Properties

```galaxy
// Reading
fixed lv_life    = UnitGetPropertyFixed(lv_unit, c_unitPropLife, true);       // true = current
fixed lv_maxLife = UnitGetPropertyFixed(lv_unit, c_unitPropLife, false);      // false = max
fixed lv_energy  = UnitGetPropertyFixed(lv_unit, c_unitPropEnergy, true);
fixed lv_shield  = UnitGetPropertyFixed(lv_unit, c_unitPropShields, true);

// Writing
UnitSetPropertyFixed(lv_unit, c_unitPropLife,     75.0);
UnitSetPropertyFixed(lv_unit, c_unitPropShields, 100.0);

// Property constants
c_unitPropLife           // current HP
c_unitPropLifeMax        // max HP
c_unitPropShields        // current shields
c_unitPropShieldsMax     // max shields
c_unitPropEnergy         // current energy
c_unitPropEnergyMax      // max energy
c_unitPropKills          // kill count
c_unitPropMoveSpeed      // movement speed
c_unitPropArmorLevel     // armor rating
c_unitPropCurrent        // attack damage (general current)
```

---

## Scale, Appearance

```galaxy
UnitSetScale(lv_unit, 1.5, 1.5, 1.5);      // x, y, z scale multipliers
```

---

## Behaviors

Behaviors are the primary mechanism for applying upgrades, buffs, and debuffs:

```galaxy
// Add a behavior (with stack count)
UnitBehaviorAdd(lv_unit, "PowerOverwhelming", lv_unit, 1);
UnitBehaviorAdd(lv_unit, "ArmorPlatesAura",   lv_unit, 1);

// Remove a behavior
UnitBehaviorRemove(lv_unit, "PowerOverwhelming", 1);

// Set behavior count
UnitBehaviorSetCount(lv_unit, "ShieldBoost", lv_unit, 2);

// Query
int  lv_count   = UnitBehaviorCount(lv_unit, "PowerOverwhelming");
bool lv_hasBhvr = UnitHasBehavior(lv_unit, "PowerOverwhelming");
```

---

## Abilities

```galaxy
// Reset cooldown of an ability
UnitAbilityReset(lv_unit, "Ability_Name", true);

// Check if unit can use ability
bool lv_can = UnitAbilityEnabled(lv_unit, "Ability_Name");

// Set ability enabled
UnitAbilityEnable(lv_unit, "Ability_Name", true);

// Order a unit to use ability at a point
UnitOrder(lv_unit, OrderTargetingPoint(AbilityCommand("Ability_Name", 0), lv_point));
```

---

## XP / Level System

```galaxy
// Add XP
UnitXPAddXP(lv_unit, 200.0);

// Query XP
fixed lv_xp    = UnitXPGetCurrentXP(lv_unit);
int   lv_level = UnitXPGetCurrentLevel(lv_unit);
int   lv_level2 = UnitLevel(lv_unit);   // same result, shorter

// Event: listen for level-up
TriggerAddEventUnitGainLevel(myTrigger, null);   // null = any unit
// Inside handler:
unit lv_leveledUnit = EventUnit();
int  lv_newLevel    = UnitXPGetCurrentLevel(lv_leveledUnit);
```

---

## Unit Groups

### Creating a unit group

```galaxy
// Empty group
unitgroup lv_group = UnitGroupEmpty();

// Filtered group from the game world
unitgroup lv_enemies = UnitGroup(
    null,                       // null = any unit type (or "Marine" for specific)
    1,                          // player
    RegionEntire(),             // region to search in
    UnitFilter(0, 0, (1 << c_targetFilterDead), 0),   // exclude dead
    0                           // max units, 0 = unlimited
);
```

### UnitFilter

```galaxy
// UnitFilter(requiresMask, excludeMask, requiresType, excludeType)
UnitFilter(0, 0, 0, 0)                              // no filter
UnitFilter(0, 0, (1 << c_targetFilterDead), 0)      // exclude dead
UnitFilter((1 << c_targetFilterEnemy), 0, 0, 0)     // require enemy

// Common filter constants
c_targetFilterDead
c_targetFilterAlly
c_targetFilterEnemy
c_targetFilterSelf
c_targetFilterGround
c_targetFilterAir
c_targetFilterStructure
c_targetFilterWorker
c_targetFilterHero
```

### Modifying a group

```galaxy
UnitGroupAdd(lv_group, lv_unit);
UnitGroupRemove(lv_group, lv_unit);
UnitGroupAddUnitGroup(lv_group, lv_otherGroup);
UnitGroupClear(lv_group);
```

### Querying a group

```galaxy
int  lv_count  = UnitGroupCount(lv_group, c_unitCountAll);
bool lv_has    = UnitGroupHasUnit(lv_group, lv_unit);
unit lv_first  = UnitGroupUnit(lv_group, 1);        // 1-based index
unit lv_random = UnitGroupRandomUnit(lv_group, c_unitCountAll);
unit lv_close  = UnitGroupClosestToPoint(lv_group, lv_point);
bool lv_dead   = libNtve_gf_UnitGroupIsDead(lv_group);
point lv_center = UnitGroupCenterOfGroup(lv_group);

// Filter by player
unitgroup lv_filtered = UnitGroupFilterPlayer(lv_group, 2);

// Convert single unit to group
unitgroup lv_single = libNtve_gf_ConvertUnitToUnitGroup(lv_unit);

// Unit count constants
c_unitCountAll
c_unitCountAlive
c_unitCountDead
```

### Iterating a unit group (from-end pattern)

The editor generates iteration from the end to safely handle removal during loops:

```galaxy
int lv_u = UnitGroupCount(lv_group, c_unitCountAll);
unit lv_cur;
for (; lv_u > 0 ; lv_u -= 1) {
    lv_cur = UnitGroupUnitFromEnd(lv_group, lv_u);
    if (lv_cur == null) { continue; }
    // act on lv_cur ...
}
```

---

## Unit Orders

```galaxy
// Move to point
UnitOrder(lv_unit, OrderTargetingPoint(AbilityCommand("Move", 0), lv_point));

// Attack-move to point
UnitOrder(lv_unit, OrderTargetingPoint(AbilityCommand("Attack", 0), lv_point));

// Stop
UnitOrder(lv_unit, Order(AbilityCommand("Stop", 0)));

// Hold position
UnitOrder(lv_unit, Order(AbilityCommand("HoldPosition", 0)));

// Queue orders
UnitOrderAdd(lv_unit, OrderTargetingPoint(AbilityCommand("Move", 0), lv_pt2), false);

// Queued group orders
UnitGroupOrder(lv_group, OrderTargetingPoint(AbilityCommand("Move", 0), lv_point), false);
```

---

## Unit Utility Functions

```galaxy
// Find nearest unit
unit lv_near = UnitNearestUnit(lv_point, lv_group);

// Default facing from one position to another
fixed lv_angle = AngleBetweenPoints(lv_from, lv_to);

// Give unit to a different player
UnitSetOwner(lv_unit, lv_newPlayer, true);   // true = change color

// Unit state flags
UnitSetState(lv_unit, c_unitStateInvulnerable, true);
UnitSetState(lv_unit, c_unitStateHidden,       true);

// Common state constants
c_unitStateInvulnerable
c_unitStateHidden
c_unitStatePaused
c_unitStateIsHallucination
```
