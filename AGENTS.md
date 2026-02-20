# Agents

This document describes the various agents (units, heroes, and special entities) used in the Proxima Frontlines mod. Each agent is defined in the mod's GameData XML files and may have unique models, actors, sounds, and abilities.

## Table of Contents

- [Overview](#overview)
- [AI Development Agents](#ai-development-agents)
- [Protoss Agents](#protoss-agents)
- [Terran Agents](#terran-agents)
- [Zerg Agents](#zerg-agents)
- [Neutral & Special Agents](#neutral--special-agents)
- [File Structure](#file-structure)
- [Adding New Agents](#adding-new-agents)

---

## Overview

Proxima Frontlines is a SC2 + MOBA hybrid mod featuring:
- **2 RTS Players** controlling standard StarCraft II armies
- **10 Hero/Soldier Players** playing MOBA-style heroes

Agents in this mod are defined across multiple data files within the `Base.SC2Data/GameData/` directory.

---

## AI Development Agents

These are specialized AI assistants configured to help with specific development tasks.

### Tooltip Agent

**File:** [tooltip-agent.md](tooltip-agent.md)

**Purpose:** Fixes and maintains tooltip text for all hero characters (`CUnitHero`) in the mod. Ensures ability descriptions use proper dynamic value references for accurate in-game display.

**Capabilities:**
- Locates hero units via `CUnitHero` entries in `UnitData.xml`
- Extracts abilities from `CardLayouts > LayoutButtons > Face` attributes
- Maps buttons to tooltips in `GameStrings.txt`
- Understands level scaling behaviors (`{Hero}1to4`, `{Hero}5to7`, `{Hero}8to10`)
- Generates correct `<d ref="..."/>` dynamic value syntax

**Key Features:**
- Hero leveling system documentation (levels 1-10, 3 tiers)
- Dynamic value reference syntax guide
- Complete hero ability mappings with tooltip status
- Behavior reference tables for buffs and effects

**Usage:** Reference this agent when fixing or updating hero ability tooltips to ensure values are dynamically linked to game data.

---

## Protoss Agents

| Agent | Model ID | Description |
|-------|----------|-------------|
| Void Pylon Spawner | `VoidPylonSpawner` | Missile FX using Tempest Plasma Missile |
| Artanis Lightning Dash | `ArtanisLightningDashImpact`, `ArtanisLightningDashIn` | Dash ability effects |
| Mothership Core Hero | `MothershipCoreHero` | Mobile flying caster with Photon Overcharge, Mass Recall, Time Warp |
| Avatar | `Avatar` | One-shot spell FX using Fenix Whirlwind Impact |
| Reversal Field | `ReversalFieldModel` | Persistent spell FX using Temporal Field |
| Sentry Purifier | `SentryPurifier2` | Purifier variant with morph capabilities |
| Dark Templar Deep Shadow | `VoidDarkTemplarDeepShadowBlinkIn2`, `VoidDarkTemplarDeepShadowBlinkOut2` | Blink effects |

**Related Files:**
- [Base.SC2Data/GameData/ModelData.xml](ProximaFrontlines.SC2Mod/Base.SC2Data/GameData/ModelData.xml)
- [Base.SC2Data/GameData/ActorData.xml](ProximaFrontlines.SC2Mod/Base.SC2Data/GameData/ActorData.xml)

---

## Terran Agents

| Agent | Model ID | Description |
|-------|----------|-------------|
| Firebat | `Firebat2`, `Firebat3` | Heavy infantry with flamethrower attacks |
| Firebat Attack | `FirebatAttackLaunch2`, `FirebatAttackLaunch3` | Attack launch effects |
| Firebat Bunker Attack | `FirebatBunkerAttackLaunch2`, `FirebatBunkerAttackLaunch3` | Bunker attack variants |
| Firebat Death | `FirebatDeath2`, `FirebatDeath3` | Death animations |
| Firebat Portrait | `FirebatPortrait2`, `FirebatPortrait3` | Unit portraits |
| Toss Grenade | `TossGrenadeWeapon`, `TossGrenadeWeapon2` | Grenade projectile |
| Toss Grenade Impact | `TossGrenadeImpact2` | Explosion effect |
| HERC Hero | `HERC2` | Grapple-equipped infantry unit |
| Goliath Hero | `GoliathHero` | Heavy fire support with Graviton Overcharge |
| Science Vessel | — | Support unit with Repair Drones |
| Lab Turret | `LabTurret2` | Defensive structure |

**Related Files:**
- [Base.SC2Data/GameData/ModelData.xml](ProximaFrontlines.SC2Mod/Base.SC2Data/GameData/ModelData.xml)
- [Base.SC2Data/GameData/ActorData.xml](ProximaFrontlines.SC2Mod/Base.SC2Data/GameData/ActorData.xml)
- [Base.SC2Data/GameData/SoundData.xml](ProximaFrontlines.SC2Mod/Base.SC2Data/GameData/SoundData.xml)

---

## Zerg Agents

| Agent | Model ID | Description |
|-------|----------|-------------|
| Hydralisk Impale | `HydraliskImpaleAttackImpactExplode` | Impact explosion effect |
| Empower Zerg Building | `EmpowerZergBuilding` | Wild Mutation Buff effect |
| Nydus Canal | `NydusCanalPlacement2` | Placement model for Nydus |
| Zergling Death Explosion | `ZerglingDeathExplosion` | Baneling-style death effect |
| Death Void Shadow | `DeathVoidShadowMedium2`, `DeathVoidShadowMedium3` | Void unit death effects |
| Zerg Small Unit Death | `ZergSmallUnitDeathLow2`, `ZergSmallUnitDeathLow3` | Low-quality death effects |

**Related Files:**
- [Base.SC2Data/GameData/ModelData.xml](ProximaFrontlines.SC2Mod/Base.SC2Data/GameData/ModelData.xml)

---

## Neutral & Special Agents

| Agent | Model ID | Description |
|-------|----------|-------------|
| Invisible Unit | `Invisible2`, `Invisible3` | Hidden/invisible units |
| Range Effect | `RangeEffect` | Visual range indicator |
| Goliath Turret Mode | `GoliathTurretMode` | Turret activation effect |
| Stunning Blast Impact | `StunningBlastImpact` | Stun ability impact |
| Spawn MiniMap | `SpawnMiniMap` | Minimap spawn indicator |

---

## File Structure

```
ProximaFrontlines.SC2Mod/
├── Base.SC2Data/
│   ├── GameData/
│   │   ├── ActorData.xml      # Actor definitions and animations
│   │   ├── BehaviorData.xml   # Buff/behavior definitions (level scaling)
│   │   ├── ModelData.xml      # Model references and scaling
│   │   ├── SoundData.xml      # Sound effects and voice lines
│   │   ├── AbilData.xml       # Ability definitions
│   │   ├── UnitData.xml       # Unit stats and properties (CUnitHero)
│   │   ├── WeaponData.xml     # Weapon configurations
│   │   └── EffectData.xml     # Effect definitions
│   └── Lib5A1C9904.galaxy     # Galaxy script functions
├── enUS.SC2Data/
│   └── LocalizedData/
│       └── GameStrings.txt    # Localized text strings (tooltips)
└── DocumentInfo               # Mod metadata and dependencies
```

---

## Adding New Agents

### 1. Define the Model
Add a `<CModel>` entry in [Base.SC2Data/GameData/ModelData.xml](ProximaFrontlines.SC2Mod/Base.SC2Data/GameData/ModelData.xml):

```xml
<CModel id="MyNewAgent" parent="Unit" Race="Terran">
    <Model value="Assets\Units\Path\To\Model.m3"/>
    <Occlusion value="Show"/>
</CModel>
```

### 2. Create the Actor
Add a `<CActorUnit>` entry in [Base.SC2Data/GameData/ActorData.xml](ProximaFrontlines.SC2Mod/Base.SC2Data/GameData/ActorData.xml):

```xml
<CActorUnit id="MyNewAgent" parent="GenericUnitStandard" unitName="MyNewAgent">
    <Model value="MyNewAgent"/>
    <!-- Animation and event handlers -->
</CActorUnit>
```

### 3. Add Sounds (Optional)
Add `<CSound>` entries in [Base.SC2Data/GameData/SoundData.xml](ProximaFrontlines.SC2Mod/Base.SC2Data/GameData/SoundData.xml):

```xml
<CSound id="MyNewAgent_Attack" parent="Combat">
    <AssetArray File="Assets\Sounds\Path\To\Sound.wav"/>
</CSound>
```

### 4. Add Localized Strings
Add tooltip and name strings in [enUS.SC2Data/LocalizedData/GameStrings.txt](ProximaFrontlines.SC2Mod/enUS.SC2Data/LocalizedData/GameStrings.txt):

```
Button/Name/MyNewAgent=My New Agent
Button/Tooltip/MyNewAgent=Description of the agent's abilities.
```

For dynamic values in tooltips, use the `<d ref="..."/>` syntax. See [tooltip-agent.md](tooltip-agent.md) for full documentation.

---

## References

- [SC2 Editor Guides](https://s2editor-guides.readthedocs.io/)
- [SC2Mapster Setup Guide](https://sc2mapster.github.io/mkdocs/setup/)
- [Proxima Frontlines Discord](https://discord.gg/abBfe66wey)

---