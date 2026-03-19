# Galaxy Scripting – UI & Dialogs

Reference: https://mapster.talv.space/galaxy/reference

---

## Dialogs

Dialogs are overlay panels. Each contains controls (buttons, labels, images, etc.).

### Creating a dialog

```galaxy
dialog lv_dlg = DialogCreate(
    1200,              // width  (pixels)
    600,               // height (pixels)
    c_anchorCenter,    // anchor position on screen
    0,                 // x offset from anchor
    0,                 // y offset from anchor
    false              // modal (blocks input to game underneath)
);
// Or capture:
lib5A1C9904_gv_heroDialog = DialogLastCreated();
```

### Showing / hiding

```galaxy
DialogSetVisible(lv_dlg, PlayerGroupAll(), true);   // show to all
DialogSetVisible(lv_dlg, PlayerGroupSingle(3), false); // hide for player 3
```

### Anchor constants

```galaxy
c_anchorTopLeft
c_anchorTop
c_anchorTopRight
c_anchorLeft
c_anchorCenter
c_anchorRight
c_anchorBottomLeft
c_anchorBottom
c_anchorBottomRight
```

---

## Dialog Controls

### Button

```galaxy
libNtve_gf_CreateDialogItemButton(
    lv_dlg,          // parent dialog
    200, 50,         // width, height
    c_anchorTopLeft, // anchor within dialog
    10, 10,          // x, y offset from anchor
    StringToText(""),         // tooltip
    StringToText("Click Me"), // label
    ""               // style (empty = default)
);
dialogcontrol lv_btn = DialogControlLastCreated();
```

### Label

```galaxy
libNtve_gf_CreateDialogItemLabel(
    lv_dlg,
    300, 40,
    c_anchorTopLeft,
    10, 60,
    StringToText("Score: 0"),  // initial text
    ColorWithAlpha(255, 255, 255, 255), // white
    false,           // word wrap
    0                // wrap width (0 = no limit)
);
dialogcontrol lv_label = DialogControlLastCreated();
```

### Image

```galaxy
libNtve_gf_CreateDialogItemImage(
    lv_dlg,
    100, 100,
    c_anchorTopLeft,
    10, 110,
    StringToText(""),   // tooltip
    "Assets\\Textures\\UI_Protoss_Something.dds",
    c_triggeredImageTypeNormal,
    false,   // tiled
    ColorWithAlpha(255, 255, 255, 255)
);
dialogcontrol lv_img = DialogControlLastCreated();
```

### Portrait / unit image

```galaxy
libNtve_gf_CreateDialogItemPortrait(
    lv_dlg, 150, 150, c_anchorTopLeft, 10, 10,
    StringToText(""), -1,
    null, // unit (null for no unit)
    true  // use unit model
);
```

---

## Updating Controls

```galaxy
// Change text
libNtve_gf_SetDialogItemText(lv_label, StringToText("Score: 42"), PlayerGroupAll());

// Change image
libNtve_gf_SetDialogItemImage(lv_img, "Assets\\Textures\\NewImage.dds", PlayerGroupAll());

// Enable / disable
DialogControlSetEnabled(lv_btn, PlayerGroupAll(), true);
DialogControlSetEnabled(lv_btn, PlayerGroupSingle(lv_player), false);

// Guard against an uninitialized control (c_invalidDialogControlId == 0)
if (lv_label != c_invalidDialogControlId) {
    libNtve_gf_SetDialogItemText(lv_label, StringToText("..."), PlayerGroupAll());
}
```

---

## Dialog Events

### Register click handler on ALL controls in a dialog

```galaxy
TriggerAddEventDialogControl(
    myTrigger,
    c_playerAny,
    c_invalidDialogControlId,        // 0 = any control in dialog
    c_triggerControlEventTypeClick
);
```

### Register click handler on a specific button

```galaxy
TriggerAddEventDialogControl(
    myTrigger,
    c_playerAny,
    lv_btn,
    c_triggerControlEventTypeClick
);
```

### Reading the event inside the handler

```galaxy
bool MyClickHandler_Func(bool testConds, bool runActions) {
    dialogcontrol lv_clicked = EventDialogControl();
    int           lv_player  = EventPlayer();
    
    if (lv_clicked == lib5A1C9904_gv_lockInButton) {
        // handle lock-in ...
    }
    return true;
}
```

---

## Hero Selection Dialog Pattern

Pattern from lib5A1C9904 (1200×600 modal dialog, 3-panel layout):

```galaxy
// Constants from _h.galaxy
// gv_heroDialogWidth  = 1200
// gv_heroDialogHeight = 600
// gv_leftPanelWidth   = 300
// gv_middlePanelX     = 300
// gv_rightPanelX      = 700

void lib5A1C9904_gf_CreateHeroDialog(int lp_team) {
    dialog lv_dlg;
    dialogcontrol lv_slots[10];
    dialogcontrol lv_infoName;
    dialogcontrol lv_lockIn;
    int lv_i = 1;

    DialogCreate(1200, 600, c_anchorCenter, 0, 0, true);
    lv_dlg = DialogLastCreated();

    // Left panel — hero slot buttons
    for (; lv_i <= lib5A1C9904_gv_heroCount ; lv_i += 1) {
        libNtve_gf_CreateDialogItemButton(lv_dlg, 280, 50,
            c_anchorTopLeft, 10, 10 + ((lv_i - 1) * 60),
            StringToText(""), lib5A1C9904_gv_heroNames[lv_i], "");
        lv_slots[lv_i] = DialogControlLastCreated();
    }

    // Right panel — Lock In button
    libNtve_gf_CreateDialogItemButton(lv_dlg, 200, 60,
        c_anchorTopRight, -10, -70, StringToText(""), StringToText("Lock In"), "");
    lv_lockIn = DialogControlLastCreated();

    DialogSetVisible(lv_dlg, PlayerGroupAll(), true);
}
```

---

## Per-Level Upgrade Dialog Pattern

```galaxy
// Nydus and Hero each have level 2/5/7/10 upgrade dialogs
// Stored in arrays: gv_heroUpgradeDialog[4], gv_nydusUpgradeDialog[4]
// Level thresholds:  2, 5, 7, 10

bool lib5A1C9904_gt_HeroLevelUp_Func(bool testConds, bool runActions) {
    unit  lv_unit  = EventUnit();
    int   lv_level = UnitXPGetCurrentLevel(lv_unit);
    int   lv_player = UnitGetOwner(lv_unit);

    if (lv_level == 2) {
        DialogSetVisible(lib5A1C9904_gv_heroUpgradeDialog[1],
            PlayerGroupSingle(lv_player), true);
    } else if (lv_level == 5) {
        DialogSetVisible(lib5A1C9904_gv_heroUpgradeDialog[2],
            PlayerGroupSingle(lv_player), true);
    }
    return true;
}
```

---

## Messages & Feedback

### Display message in HUD area

```galaxy
UIDisplayMessage(PlayerGroupAll(), c_messageAreaChat,     StringToText("GG!"));
UIDisplayMessage(PlayerGroupAll(), c_messageAreaSubtitle, StringToText("Round 1 – Fight!"));
UIDisplayMessage(
    PlayerGroupSingle(lv_player),
    c_messageAreaChat,
    StringToText("Not enough minerals!")
);

// Area constants
c_messageAreaChat         // bottom-left chat area
c_messageAreaSubtitle     // center subtitle
c_messageAreaDefault
c_messageAreaObjective
c_messageAreaWarning
```

### Error message with sound

```galaxy
libNtve_gf_UIErrorMessage(
    PlayerGroupSingle(lv_player),
    StringToText("Cannot afford this upgrade!"),
    SoundLink("UI_GenericError", -1)
);
```

---

## Localized Text

```galaxy
// Read from GameStrings.txt (keyed by path)
text lv_heroName = StringExternal("Param/Value/lib5A1C9904_HeroName_Zealot");

// Combine text values
text lv_msg = lv_prefix + StringToText(" ") + IntToText(lv_score) + StringToText(" points!");

// Colorize text
text lv_colored = TextWithColor(lv_heroName, ColorWithAlpha(255, 100, 100, 255));
```

---

## UI Alerts & Minimap

```galaxy
// Toggle built-in alert types
UISetAlertTypeVisible(PlayerGroupAll(), "AlertWorkerAttacked", false);

// Minimap ping
PingCreate(PlayerGroupAll(), lv_point, 10.0, ColorWithAlpha(255, 0, 0, 255), "");
```

---

## Scoreboard / Stats Panel

Pattern from lib5A1C9904 — per-player dialog labels updated on events:

```galaxy
// Declare arrays in _h.galaxy
dialogcontrol lib5A1C9904_gv_scoreKillsLabel[17];   // indexed by player
dialogcontrol lib5A1C9904_gv_scoreDeathsLabel[17];
// ... etc.

void lib5A1C9904_gf_UpdateScoreboard(int lp_player, int lp_kills, int lp_deaths) {
    libNtve_gf_SetDialogItemText(
        lib5A1C9904_gv_scoreKillsLabel[lp_player],
        IntToText(lp_kills),
        PlayerGroupAll()
    );
    libNtve_gf_SetDialogItemText(
        lib5A1C9904_gv_scoreDeathsLabel[lp_player],
        IntToText(lp_deaths),
        PlayerGroupAll()
    );
}
```
