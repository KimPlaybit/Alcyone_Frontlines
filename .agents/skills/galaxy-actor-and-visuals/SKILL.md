# Galaxy Scripting – Actors & Visual Effects

Reference: https://mapster.talv.space/galaxy/reference

---

## What is an Actor?

An **Actor** is the visual/audio representation of something in-game — a model, an attachment, a beam effect, etc. Actors are separate from the simulation (units, regions) and communicate via **messages**.

Most visual scripting goes through `ActorSend` (send a message to an actor) or by spawning actors directly with `ActorCreate`.

---

## Actor Types and Handles

```galaxy
actor lv_a;            // model/effect actor
actorscope lv_scope;   // actor scope (groups related actors)
```

---

## Creating Actors

```galaxy
// Spawn a named actor (defined in data) at a point
lv_a = ActorCreate("MyEffectActor", lv_point, 0.0, lv_host);

// Attach model to unit at attach point (returns an actor handle)
lv_a = libNtve_gf_AttachModelToUnit(
    "Assets\\Units\\Zerg\\Hydralisk\\Hydralisk.m3",
    lv_unit,
    "Chest",    // attach point
    true        // inherit visibility from unit
);

// Attach an existing named actor (from data) to a unit at an attach point
libNtve_gf_AttachActorToUnit(lv_unit, "TalkIcon",         "Ref_Origin");
libNtve_gf_AttachActorToUnit(lv_unit, "BriefingUnitSelectRed", "Ref_Center");
// (unit, actorName, attachPoint)

// Get the last actor created by any actor operation
actor lv_last = libNtve_gf_ActorLastCreated();

// Get the last created actor scope
actorscope lv_scope2 = libNtve_gf_ActorScopeLastCreated();
ActorScopeKill(lv_scope2);   // destroy all actors in the scope

// Attach model to another actor
lv_a = libNtve_gf_AttachModelToActor2(
    "Assets\\Effects\\SomeEffect.m3",
    lv_hostActor,
    "Origin"
);

// Create actor at point (simple)
lv_a = libNtve_gf_CreateActorAtPoint("SomeActorName", lv_point);

// Scope
lv_scope = ActorScopeCreate("ScopeId", lv_hostActor);
lv_scope = libNtve_gf_ActorScopeLastCreated();
```

---

## Sending Actor Messages

Messages control everything about an actor — animations, tints, scale, visibility, etc.

```galaxy
// Send a constructed message string to an actor
ActorSend(lv_a, "SetTintColor {1,0,0,1}");
ActorSend(lv_a, "SetScale 0.800000");   // scale by string

// Using library message constructors:
ActorSend(lv_a, libNtve_gf_SetTintColor(1.0, 0.0, 0.0, 1.0));
ActorSend(lv_a, libNtve_gf_SetScale("1.5 1.5 1.5"));
ActorSend(lv_a, libNtve_gf_SetVisibility("Hide"));
ActorSend(lv_a, libNtve_gf_SetVisibility("Show"));

// Destroy actor
ActorSend(lv_a, "Destroy");

// Team color
ActorSend(lv_a, libNtve_gf_SetTeamColor(lv_player));

// Send to a unit's main actor
ActorSendTo(ActorFrom(lv_unit), libNtve_gf_SetTintColor(1.0, 0.5, 0.5, 1.0));

// Send actor message to a unit (shortcut — targets the unit’s own actor)
libNtve_gf_SendActorMessageToUnit(lv_unit, "AnimGroupApply Stand,Victory");
libNtve_gf_SendActorMessageToUnit(lv_unit, "StatusSet MarinePortrait 7");
```

### Common message constructors

| Message | Constructor | Effect |
|---|---|---|
| Set tint | `libNtve_gf_SetTintColor(r,g,b,a)` | Color tint |
| Set scale | `libNtve_gf_SetScale("x y z")` | Scale model |
| Set visibility | `libNtve_gf_SetVisibility("Show"/"Hide")` | Show/hide |
| Set bearings | `libNtve_gf_SetBearings(x,y,z,fx,fy,fz)` | Position+facing |
| Signal | `libNtve_gf_Signal("EventName")` | Trigger data event |
| Play animation | `MakeMsgAnimPlay("Walk Stand Birth Death",flags,blend,0,0)` | Animation |

---

## Animations

```galaxy
// Play animation by name
libNtve_gf_PlayAnimation(lv_unit, "Attack", c_animFlagPlayForever, 0.0, true);

// Clear animation
libNtve_gf_ClearAnimation(lv_unit);

// Using actor messages with bracket animations:
ActorSend(lv_a, MakeMsgAnimBracketStart("Walk", "Stand", "", "", c_animFlagPlayForever, 0, 0.0));
ActorSend(lv_a, MakeMsgAnimBracketStop("Walk", 0.0));

// Turn on animation properties (global motion blur, etc.)
libNtve_gf_TurnAnimationPropertiesOn(lv_unit, "Charred", 1.0);
libNtve_gf_TurnAnimationPropertiesOff(lv_unit, "Charred");

// On doodads in region — full signature (very common in campaign maps)
libNtve_gf_PlayAnimationOnDoodadsInRegion(
    lv_region,
    "DoodadType",          // doodad type name (empty = all doodads)
    c_animNameDefault,     // animation track
    "Stand Work",          // animation name
    c_animFlagPlayForever, // flag
    c_animTimeDefault      // duration
);
libNtve_gf_KillDoodadsInRegion(lv_region);

// Wait for an animation length
AnimLengthQueryByName(lv_unit, "Attack", false, false);
AnimLengthQueryWait(AnimLengthQueryLastCreated());
fixed lv_len = AnimLengthSync(AnimLengthQueryLastCreated());
```

---

## Actor Texture / Appearance

```galaxy
// Swap out a texture group
ActorSend(lv_a, libNtve_gf_TextureGroupApply("ZergPlayerColor"));
ActorSend(lv_a, libNtve_gf_TextureGroupRemove("ZergPlayerColor"));

// Swap model
ActorSend(lv_a, libNtve_gf_ModelSwap("NewModelName"));

// Desaturate
libNtve_gf_SetDialogItemDesaturated(lv_control, PlayerGroupAll(), true);
```

---

## Cinematic Fade

```galaxy
// Fade to black (and back)
CinematicFade(true, 1.5, c_fadeStyeLinear, Color(0.0, 0.0, 0.0), 1.0, PlayerGroupAll());
// (fadeIn, duration, style, color, alpha, players)

CinematicFade(false, 1.0, c_fadeStyeLinear, Color(0.0, 0.0, 0.0), 1.0, PlayerGroupAll());

// Full cinematic mode (hides UI, letterbox)
libNtve_gf_CinematicMode(PlayerGroupAll(), true, 0.0);
```

---

## Doodads

```galaxy
// Show/hide doodads by region
libNtve_gf_ShowHideDoodadsInRegion(lv_region, true, PlayerGroupAll());

// Remove death models from a region (cleanup)
libNtve_gf_RemoveDeathModelsinRegion(lv_region);
libNtve_gf_RemoveDeathModelsinRegionImmediately(lv_region);
```

---

## Portrait

```galaxy
// Get the game portrait (bottom-left)
portrait lv_p = PortraitGetGame();

// Set portrait to a unit
PortraitSetUnit(lv_p, lv_unit, 0.0, "", false);

// Play anim in portrait
libNtve_gf_PortraitSetAnim(lv_p, "Talk");
```
