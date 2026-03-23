# Galaxy Scripting – Debug, Data Table & Catalog

Reference: https://mapster.talv.space/galaxy/reference

---

## Debug Output

```galaxy
// Print to the in-game debug window (F7 to open in test mode)
TriggerDebugOutput(c_triggerDebugOutputCode, StringToText("my value: " + IntToString(lv_n)), true);

// Enable/disable debug output globally
TriggerDebugOutputEnable(c_triggerDebugOutputCode, true);

// Open or close the debug window for a player
TriggerDebugWindowOpen(lv_player, true);

// Convenience debug functions (Template / unclassified)
DebugString(lv_player, "lv_unit type: " + UnitGetType(lv_unit));
DebugInt(lv_player, "lv_i", lv_i);
DebugFixed(lv_player, "lv_dist", lv_dist);
DebugUnit(lv_player, lv_unit);
DebugPoint(lv_player, lv_point);

// Debug message type constants
c_triggerDebugOutputCode      // code path output
c_triggerDebugOutputError     // error highlighting
c_triggerDebugOutputMessage   // general message
```

---

## Data Table (Global Key-Value Store)

The Data Table stores arbitrary values by `string` name, accessible from any trigger. It survives the scope of individual functions.

### Global (map-wide) data table

```galaxy
// Save values
DataTableSetInt("myKey", 42);
DataTableSetFixed("position_x", 16.5);
DataTableSetBool("isPhase2", true);
DataTableSetUnit("heroUnit", lv_hero);
DataTableSetString("lastEvent", "SpawnWave");
DataTableSetPoint("spawnPt", lv_point);
DataTableSetUnitGroup("activeGroup", lv_group);
DataTableSetTimer("countdownTimer", lv_timer);
DataTableSetRegion("baseRegion", lv_region);
DataTableSetSound("ambience", lv_sound);
DataTableSetDialog("scoreDialog", lv_dialog);

// Load values
int    lv_n   = DataTableGetInt("myKey");
fixed  lv_x   = DataTableGetFixed("position_x");
bool   lv_b   = DataTableGetBool("isPhase2");
unit   lv_u   = DataTableGetUnit("heroUnit");
string lv_s   = DataTableGetString("lastEvent");
point  lv_p   = DataTableGetPoint("spawnPt");

// Check existence
bool lv_has = DataTableValueExists(c_dataTableScopeGlobal, "myKey");

// Remove
DataTableValueRemove(c_dataTableScopeGlobal, "myKey");

// Scope constants
c_dataTableScopeGlobal   // map-wide
c_dataTableScopeLocal    // trigger-local
```

### Instance Data Tables

Instance tables let you create multiple independent tables (like a dictionary per unit):

```galaxy
DataTableInstanceCreate();
int lv_dt = DataTableInstanceLastCreated();

DataTableInstanceSetInt(lv_dt, "kills", 0);
DataTableInstanceSetUnit(lv_dt, "owner", lv_unit);

int  lv_k = DataTableInstanceGetInt(lv_dt, "kills");
unit lv_o = DataTableInstanceGetUnit(lv_dt, "owner");

DataTableInstanceClear(lv_dt);
```

---

## Catalog (Runtime Data Field Access)

The Catalog lets you read and modify game data fields at runtime — damage, range, cost, etc. — from within triggers.

### Reading catalog values

```galaxy
// Get the string value of a data field
string lv_val = CatalogFieldValueGet(
    c_gameCatalogUnit,           // which catalog
    "Marine",                    // entry name
    "LifeMax",                   // field name
    lv_player                    // player context
);

// Get as integer or fixed
int   lv_int  = CatalogFieldValueGetAsInt(c_gameCatalogUnit, "Marine", "LifeMax", lv_player);
fixed lv_real = libNtve_gf_CatalogFieldValueGetAsReal(c_gameCatalogWeapon, "C-14Rifle", "Range", lv_player);

// Catalog constants
c_gameCatalogUnit
c_gameCatalogWeapon
c_gameCatalogAbil
c_gameCatalogEffect
c_gameCatalogBehavior
c_gameCatalogUpgrade
c_gameCatalogModel
c_gameCatalogSound
c_gameCatalogActor
```

### Writing catalog values

```galaxy
// Set a field for a player (overrides for that player)
bool lv_ok = CatalogFieldValueSet(
    c_gameCatalogWeapon, "C-14Rifle", "Range",
    lv_player, "8"               // value as string
);

// Modify relative to current value
CatalogFieldValueModify(
    c_gameCatalogUnit, "Marine", "LifeMax",
    lv_player, c_upgradeOperAdd, "25"    // add 25 HP
);

// Set as real
libNtve_gf_CatalogFieldValueSetAsReal(
    c_gameCatalogWeapon, "C-14Rifle", "Range",
    lv_player, 9.0
);
```

### Array fields

```galaxy
// Field array element — for fields like Weapons[0].Range
int lv_count = CatalogFieldValueCount(c_gameCatalogUnit, "Marine", "Weapons", lv_player);
string lv_wpn = CatalogFieldValueGet(c_gameCatalogUnit, "Marine", "Weapons[0]", lv_player);
```

### Catalog references

```galaxy
// Read a link reference (e.g., which weapon a unit uses)
string lv_ref = CatalogReferenceGet(c_gameCatalogUnit, "Marine", "Weapons[0]", lv_player);

// get as int
int lv_ri = CatalogReferenceGetAsInt(c_gameCatalogUnit, "Marine", "Weapons[0]", lv_player);
```

---

## User Data

User data allows embedding custom typed values directly in game data entries (configured in the editor's data module).

```galaxy
// Load a user data value by category and field
string lv_val = UserDataGetString("MyCategory", lv_entryName, "MyField", 0, lv_player);
int    lv_i   = UserDataGetInt("MyCategory", lv_entryName, "MyField", 0, lv_player);
fixed  lv_f   = UserDataGetFixed("MyCategory", lv_entryName, "MyField", 0, lv_player);
text   lv_t   = UserDataGetText("MyCategory", lv_entryName, "MyField", 0, lv_player);
color  lv_c   = UserDataGetColor("MyCategory", lv_entryName, "MyField", 0, lv_player);
```

---

## Preloading Assets

Preload before they're needed to avoid hitches:

```galaxy
PreloadAsset("Assets\\Textures\\MyHero.dds");
PreloadModel("Assets\\Units\\Hero\\Hero.m3");
PreloadImage("Assets\\UI\\HeroPortrait.dds");
PreloadLayout("Assets\\UI\\MyDialog.SC2Layout");

// Preload model animations — native function (NOT a libNtve helper):
ModelAnimationLoad("Assets\\Units\\Hero\\Hero.m3",  "Assets\\Units\\Hero\\Hero_Attack.m3a");
ModelAnimationLoadOverriding("Assets\\Units\\Hero\\Hero.m3", "Assets\\Override\\Hero_Walk.m3a");
ModelAnimationUnload("Assets\\Units\\Hero\\Hero.m3", "Assets\\Units\\Hero\\Hero_Attack.m3a");
// (modelPath, animPath) — animPath is the .m3a animation file
```
