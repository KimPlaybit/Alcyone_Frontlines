# Galaxy Scripting – Sound, Camera & Environment

Reference: https://mapster.talv.space/galaxy/reference

---

## Sound

### Playing sounds

```galaxy
// Play a sound by SoundLink (preferred — uses data-defined volumes)
sound lv_snd = SoundPlayForPlayer(
    SoundLink("UI_ButtonClick", -1),  // link name + index (-1 = any)
    lv_player
);

// Play at a 3D world position
sound lv_snd2 = SoundPlayAtPointForPlayer(
    SoundLink("Zerg_Hydralisk_Death1", -1),
    lv_player,
    lv_point,
    0.0,    // min distance
    30.0,   // max distance
    100.0   // volume
);

// Play attached to a unit (follows it)
sound lv_snd3 = SoundPlayOnUnit(SoundLink("Unit_Explosion", -1), lv_unit, 0.0, 30.0, 100.0);

// Wait for sound to complete (blocks trigger thread)
SoundWait(lv_snd);

// Stop a playing sound
SoundStop(lv_snd, true);    // true = fade out
SoundStopAllTriggerSounds(true, PlayerGroupAll());
```

### Sound channels

```galaxy
// mute/unmute a channel
SoundChannelMute(c_soundChannelMusic, true, false);
SoundChannelMute(c_soundChannelSFX,   false, false);

// Set volume
SoundChannelSetVolume(c_soundChannelSFX, 80.0, 0.5);  // (channel, volume, duration)

// Common channel constants
c_soundChannelMusic
c_soundChannelSFX
c_soundChannelAmbient
c_soundChannelSpeech
c_soundChannelUI
```

### Music

```galaxy
// Play/stop music
libNtve_gf_PlayMusicForPlayer(lv_player, "Sound/Music/Terran/TerranMain1.ogg", 0, true);
SoundChannelMute(c_soundChannelMusic, false, false);
```

---

## Camera

### Panning the camera

```galaxy
// Pan to a point for a player
CameraPan(lv_player, lv_point, 0.0, -1, 10.0, false);
// (player, point, distance, yaw, pitch, sync)

// Snap instantly
CameraSetTarget(lv_player, lv_point, 0.0, -1, 10.0, false);

// Smoothed pan using camera object
CameraApply(lv_player, lv_camInfo, 2.0, false);
```

### Camera info / position

```galaxy
// Get current camera position
point lv_camPos = CameraGetTarget(lv_player);
fixed lv_yaw    = CameraGetYaw(lv_player);
fixed lv_dist   = CameraGetDistance(lv_player);

// Save and restore camera state
CameraSave(lv_player);
CameraRestore(lv_player, 0.0, false);
```

### Camera shake / bounce

```galaxy
libNtve_gf_CameraShakeForPlayer(lv_player, 0.5, 2.0, 0.1);
// (player, intensity, duration, frequency)
```

---

## Environment – Fog

```galaxy
// Enable / disable fog
FogSetEnabled(true);

// Fog settings
FogSetDensity(0.3);
FogSetColor(Color(0.1, 0.1, 0.3));
FogSetFallOff(2.0);
FogSetStartHeight(0.0);
```

## Environment – Terrain / Water

```galaxy
// Terrain height at a point
fixed lv_h = WorldHeight(lv_p);

// Show/hide environment (terrain, water, sky)
EnvironmentShow(lv_player, true);

// Disable/enable no-fly zones dynamically
PathAddNoFlyZone(lv_region);
PathRemoveNoFlyZonesInRegion(lv_region);
```

---

## Leaderboard

The leaderboard is the default scoreboard panel.

```galaxy
// Create a leaderboard
LeaderboardCreate(PlayerGroupAll(), StringToText("Kills"), c_leaderboardSortNone,
    c_leaderboardValueUInt, "", Color(1.0,1.0,1.0));
int lv_board = LeaderboardLastCreated();

// Show / hide
libNtve_gf_ShowHideLeaderboard(lv_board, PlayerGroupAll(), true);

// Add a row item for each player
LeaderboardAddItem(lv_board, PlayerGroupAll(), lv_player, IntToText(lv_kills),
    Color(1.0,1.0,1.0), "", Color(1.0,1.0,1.0));

// Set value of a player's row
LeaderboardSetItemValue(lv_board, PlayerGroupAll(), lv_player, IntToText(42),
    Color(1.0,0.8,0.0));

// Sort
LeaderboardSortByValue(lv_board, c_leaderboardSortDescending, false);

// Destroy
BoardDestroy(lv_board);
```

---

## Objectives Panel

```galaxy
// Create objective
ObjectiveCreate(
    PlayerGroupAll(),
    StringToText("Destroy Enemy Base"),
    StringToText("Eliminate all enemy structures."),
    c_objectivePrimary
);
int lv_obj = ObjectiveLastCreated();

// Show/update state
ObjectiveShow(lv_obj, true, false);
ObjectiveSetState(lv_obj, c_objectiveStateCompleted);

// State constants
c_objectiveStateActive
c_objectiveStateCompleted
c_objectiveStateFailed

// Destroy
ObjectiveDestroy(lv_obj);
```

---

## Transmission (Portrait Speech)

```galaxy
// Play a scripted speech transmission
TransmissionSend(
    PlayerGroupAll(),               // who sees/hears it
    TransmissionSourceFromUnit(lv_unit),  // portrait
    StringToText("Speaker"),        // speaker name
    "",                             // sound link (or "" for none)
    StringToText("Your base is under attack!"),  // subtitle
    c_transmissionDurationAdd,      // how duration is applied
    3.0,                            // extra duration
    true                            // block until done
);
```
