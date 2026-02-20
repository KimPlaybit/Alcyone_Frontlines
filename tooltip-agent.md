# Agents - Proxima Frontlines SC2 Mod

This document describes the specialized agents configured to help with development of the Proxima Frontlines mod.

## Table of Contents

- [Overview](#overview)
- [Hero Tooltip Agent](#hero-tooltip-agent)
- [Hero Leveling System](#hero-leveling-system)
- [Dynamic Value Reference Syntax](#dynamic-value-reference-syntax)
- [Hero Ability Mappings](#hero-ability-mappings)
- [Files Reference](#files-reference)

---

## Overview

Proxima Frontlines is a SC2 + MOBA hybrid mod featuring:
- **2 RTS Players** controlling standard StarCraft II armies
- **10 Hero/Soldier Players** playing MOBA-style heroes

Heroes gain XP and level from 1-10, with stats scaling through behavior attributes.

---

## Hero Tooltip Agent

### Purpose
Fixes and maintains tooltip text for all hero characters (`CUnitHero`) in the mod. Ensures ability descriptions use proper dynamic value references for accurate in-game display, including level-based scaling.

### Workflow

1. **Find Hero Unit**: Locate `CUnitHero` in `UnitData.xml`
2. **Extract Abilities**: Parse `CardLayouts > LayoutButtons > Face` attribute
3. **Identify Level Behaviors**: Find `{HeroName}1to4`, `{HeroName}5to7`, `{HeroName}8to10` in `BehaviorData.xml`
4. **Map Button to Tooltip**: Match `Face` value to `Button/Tooltip/{Face}` in `GameStrings.txt`
5. **Validate Values**: Ensure tooltips use `<d ref="..."/>` for dynamic values including level scaling
6. **Update**: Modify `GameStrings.txt` with corrected tooltip text

---

## Hero Leveling System

Heroes use `CBehaviorAttribute` entries for level-based stat scaling. Each hero has 3 tiers:

| Tier | Levels | Behavior Suffix | XP Required |
|------|--------|-----------------|-------------|
| Early | 1-4 | `{Hero}1to4` | 50-200 |
| Mid | 5-7 | `{Hero}5to7` | 400-1200 |
| Late | 8-10 | `{Hero}8to10` | 1600-2400 |

### Level Behavior Reference by Hero

#### Protoss Heroes

| Hero | Behavior ID | Damage Type | Dmg 1-4 | Dmg 5-7 | Dmg 8-10 | Shield/Life Bonus |
|------|-------------|-------------|---------|---------|----------|-------------------|
| **Zealot** | `Zealot1to4` | Melee | +4 | +5 | +6 | +80/+150/+190 shields |
| | `Zealot5to7` | | | | | |
| | `Zealot8to10` | | | | | |
| **Dragoon** | `Dragoon1to4` | Ranged | +7 | +8 | +10 | +40/+100/+75 shields |
| | `Dragoon5to7` | | | | | |
| | `Dragoon8to10` | | | | | |
| **Corsair** | `Corsair1to4` | Splash | +3 | +4 | +5 | +30/+100/+140 shields |
| | `Corsair5to7` | | | | | |
| | `Corsair8to10` | | | | | +15/+20/+30 energy |
| **Dark Templar** | `DarkTemplar1to4` | Melee | +6 | +8 | +10 | +40/+110/+150 shields |
| | `DarkTemplar5to7` | | | | | |
| | `DarkTemplar8to10` | | | | | |
| **Mothership Core** | `MothershipCore1to4` | Ranged | +4 | +5 | +6 | +60/+45/+150 shields |
| | `MothershipCore5to7` | | | | | +120 life (5-7) |
| | `MothershipCore8to10` | | | | | |
| **Sentry/Energizer** | `Sentry1to4` | Ranged | +4 | +5 | +5 | +40/+120/+150 shields |
| | `Sentry5to7` | | | | | |
| | `Sentry8to10` | | | | | |

#### Terran Heroes

| Hero | Behavior ID | Damage Type | Dmg 1-4 | Dmg 5-7 | Dmg 8-10 | Life Bonus |
|------|-------------|-------------|---------|---------|----------|------------|
| **Marine** | `Marine1to4` | Ranged | +7 | +9 | +11 | +30/+90/+120 |
| | `Marine5to7` | | | | | +5%/+10%/+10% atk spd |
| | `Marine8to10` | | | | | |
| **Firebat** | `Firebat1to4` | Ranged+Splash | +3/+3 | +4/+4 | +6/+6 | +80/+50/+180 |
| | `FirebatAttackSpeed` | | | | | |
| | `Firebat8to10` | | | | | |
| **Goliath** | `Goliath1to4` | Ranged+NoProc | +6/+2 | +7/+3 | +8/+4 | +40/+110/+150 |
| | `Goliath5to7` | | | | | +2%/+3% atk spd |
| | `Goliath8to10` | | | | | |
| **Spectre** | `Spectre1to4` | Ranged | +5 | +8 | +10 | +20/+110/+130 |
| | `Spectre5to7` | | | | | +20/+25/+30 energy |
| | `Spectre8to10` | | | | | +3% XP mult |
| **Medic** | `Medic1to4` | — | — | — | — | +40/+110/+140 |
| | `Medic5to7` | | | | | +1 sight (1-4, 5-7) |
| | `Medic8to10` | | | | | |
| **Science Vessel** | `ScienceVessel1to4` | — | — | — | — | +50/+110/+130 |
| | `ScienceVessel5to7` | | | | | +10/+20/+50 energy |
| | `ScienceVessel8to10` | | | | | |

#### Zerg Heroes

| Hero | Behavior ID | Damage Type | Dmg 1-4 | Dmg 5-7 | Dmg 8-10 | Life Bonus |
|------|-------------|-------------|---------|---------|----------|------------|
| **Zergling** | `Zergling1to4` | Melee | +5 | +7 | +8 | +50/+100/+180 |
| | `Zergling5to7` | | | | | +1%/+2%/+3% move spd |
| | `Zergling8to10` | | | | | |
| **Hydralisk** | `Hydralisk1to4` | Melee+Ranged | +2/+5 | +3/+6 | +3/+7 | +40/+110/+150 |
| | `Hydralisk5to7` | | | | | +1% move spd |
| | `Hydralisk5to72` | | | | | |
| **Ultralisk** | `Ultralisk1to4` | Melee+Splash | +5/+2 | +7/+3 | +8/+3 | +80/+110/+200 |
| | `Ultralisk5to7` | | | | | +1 sight |
| | `Ultralisk8to10` | | | | | Air attack at lvl 6+ |
| **Defiler** | `Defiler1to4` | Ranged | +4 | +5 | +7 | +40/+110/+150 |
| | `Defiler5to7` | | | | | +20/+30/+40 energy |
| | `Defiler8to10` | | | | | +2% energy regen |
| **Brood Queen** | `Queen1to4` | — | — | — | — | +25/+70/+150 |
| | `Queen1to42` | | | | | +50/+40/+50 energy |
| | `Queen1to422` | | | | | +0.2/+0.5/+1 sight |

### Veterancy Systems

Heroes use race-specific veterancy behaviors:
- `ProtossLevels` - Applies Protoss level scaling
- `TerranLevels` - Applies Terran level scaling  
- `ZergLevels` - Applies Zerg level scaling

XP thresholds: 50 → 100 → 200 → 400 → 800 → 1200 → 1600 → 2000 → 2400

---

## Dynamic Value Reference Syntax

### ⚠️ CRITICAL REQUIREMENT: NO HARDCODED VALUES

**All tooltips MUST use dynamic value references (`<d ref="..."/>`) instead of hardcoded numbers.** Hardcoded values become out-of-sync when data changes and create maintenance nightmares.

**Exceptions (only when no dynamic reference exists):**
- Descriptive text only (e.g., "reduces damage taken")
- Placeholder text where effect data cannot be found
- UI descriptors that don't change (e.g., "nearby units", "target area")

**When adding a tooltip:**
1. Search the game data files (BehaviorData.xml, EffectData.xml, UpgradeData.xml, AbilData.xml)
2. Find the Effect, Behavior, or Upgrade reference
3. Use the correct `<d ref="..."/>` syntax
4. If the value cannot be found, add a comment in the agent file noting the missing reference
5. NEVER hardcode ability numbers

### Effect References
```
<d ref="Effect,{EffectID},Amount"/>
<d ref="Effect,{EffectID},VitalArray[0].Change"/>      <!-- Life change -->
<d ref="Effect,{EffectID},VitalArray[1].Change"/>      <!-- Shield change -->
<d ref="Effect,{EffectID},PeriodicPeriodArray[0]"/>
```

### Periodic Effects

Many abilities apply effects over time using Initial, Periodic, and Final effects. Understanding these is crucial for accurate tooltips:

#### Effect Types
- **Initial Effect**: Applied once when the ability is cast or behavior starts
- **Periodic Effect**: Applied repeatedly at a specified interval (period) while the behavior is active
- **Final Effect**: Applied once when the behavior expires or is removed

#### Common Patterns

**Heal Over Time (HoT)**
```xml
<!-- Behavior with 2.5s duration -->
<CBehaviorBuff id="QueenBurstHeal">
    <Duration value="2.5"/>
    <!-- Periodic effect heals every 0.5s -->
</CBehaviorBuff>

<!-- Effect that heals 10 life per tick -->
<CEffectModifyUnit id="QueenBurstHeal">
    <VitalArray index="Life">
        <Change value="10"/>
    </VitalArray>
</CEffectModifyUnit>
```

**Tooltip Formula:**
```
Total Heal = <d ref="Effect,QueenBurstHeal,VitalArray[0].Change * Behavior,QueenBurstHeal,Duration / 0.5"/>
Per Tick = <d ref="Effect,QueenBurstHeal,VitalArray[0].Change"/>

Example: "Heals for 50 life over 2.5 seconds (10 per tick)"
Where: 10 life/tick × (2.5s / 0.5s period) = 50 total life
```

**Damage Over Time (DoT)**
```
Total Damage = <d ref="Effect,{PeriodicEffect},Amount * Behavior,{BehaviorID},Duration / Behavior,{BehaviorID},Period"/>
DPS = <d ref="Effect,{PeriodicEffect},Amount / Behavior,{BehaviorID},Period"/>
```

#### Referencing Periodic Values
```
<d ref="Behavior,{BehaviorID},Period"/>                    <!-- Time between ticks -->
<d ref="Behavior,{BehaviorID},Duration"/>                  <!-- Total duration -->
<d ref="Effect,{EffectID},Amount"/>                        <!-- Damage/heal per tick -->
<d ref="Behavior,{BehaviorID},PeriodicPeriodArray[0]"/>   <!-- Alternative period ref -->
```

#### Examples

**Irradiate (DoT with period)**
```
Duration: 10s
Period: 0.5s
Damage per tick: Scales with level (+1/+2/+3 from upgrades)
Total damage = damage_per_tick × (10s / 0.5s) = damage_per_tick × 20 ticks
```

**DefilerMPPlague**
```
Tooltip: Inflicting <d ref="Effect,DefilerMPPlagueDamage,Amount*Behavior,DefilerMPPlague,Duration/Behavior,DefilerMPPlague,Period"/> damage over <d ref="Behavior,DefilerMPPlague,Duration"/> seconds.
```

### Behavior References
```
<d ref="Behavior,{BehaviorID},Duration"/>
<d ref="Behavior,{BehaviorID},Period"/>
<d ref="Behavior,{BehaviorID},Modification.AttackSpeedMultiplier"/>
<d ref="Behavior,{BehaviorID},Modification.MoveSpeedMultiplier"/>
<d ref="Behavior,{BehaviorID},Modification.VitalMaxArray[Life]"/>
<d ref="Behavior,{BehaviorID},Modification.VitalMaxArray[Shields]"/>
<d ref="Behavior,{BehaviorID},Modification.VitalMaxArray[Energy]"/>
<d ref="Behavior,{BehaviorID},Modification.VitalRegenArray[Life]"/>
<d ref="Behavior,{BehaviorID},Modification.DamageDealtUnscaled[Melee]"/>
<d ref="Behavior,{BehaviorID},Modification.DamageDealtUnscaled[Ranged]"/>
<d ref="Behavior,{BehaviorID},Modification.DamageDealtUnscaled[Splash]"/>
<d ref="Behavior,{BehaviorID},Modification.LifeArmorBonus"/>
<d ref="Behavior,{BehaviorID},DamageResponse.ModifyFraction"/>
```

### Level Scaling Examples

To show damage that scales with level, reference the behavior attributes:

```
<!-- Show base + level scaling -->
Base damage plus <d ref="Behavior,DarkTemplar1to4,Modification.DamageDealtUnscaled[Melee]"/> at levels 1-4, 
<d ref="Behavior,DarkTemplar5to7,Modification.DamageDealtUnscaled[Melee]"/> at levels 5-7, or 
<d ref="Behavior,DarkTemplar8to10,Modification.DamageDealtUnscaled[Melee]"/> at levels 8-10.

<!-- Show shield bonus -->
Grants <d ref="Behavior,Zealot1to4,Modification.VitalMaxArray[Shields]"/> bonus shields (levels 1-4).
```

### Buff Duration & Effects

| Behavior | Duration | Key Stats |
|----------|----------|-----------|
| `FirebatAvatar` | 10s | +300 life, 80% damage reduction, periodic AoE |
| `FenixChampionPowerShield` | 5s | — |
| `FenixChampionPowerShield2` | — | 70% damage reduction |
| `DragoonFrenzy` | 15s | +80% atk speed, +50% crit, +15 splash |
| `HydraliskFrenzy` | — | +5% move, +100% atk speed, +10% damage |
| `Stimpack3` | 10s | +50% move/atk speed, 40% heal reduction |
| `GravitonBeamUrun` | 2.7s | Lift effect |
| `GravitonBeamUrunHeight` | 3s | +3.75 height |
| `HeroDarkTemplarDeepShadows` | 5s | +50% move, undetectable |
| `Irradiate` | 10s | 0.5s period, DoT |
| `DefilerMPPlague` | 10s | 0.5s period, -100% energy regen |
| `DefilerMPDarkSwarm` | — | 40% damage reduction, +life regen |
| `EmpowerZergBuilding` | 10s | +150 shields, +15 armor, +10 life regen |
| `StunningBlast` | 2s | Stun |
| `Ensnare` | 2s | Slow |
| `VileAcidSlowEffectsLevel12` | 3s | -25% move/atk speed |
| `PoisonGas` | 0.45s | -20% move speed |
| `FlashBangGrenade` | 2s | Blind |
| `VoodooShield` | 10s | +50 shields |
| `DamageReduction` | 1.6s | 100% damage immunity |
| `FenixWhirlwind` | 6s | +30% move speed |
| `QueenBurstHeal` | 2.5s | Heal over time |

### Calculations
```
<d ref="Effect,{EffectID},Amount * Behavior,{BehaviorID},Duration"/>
<d ref="(1 - Behavior,{BehaviorID},Modification.MoveSpeedMultiplier) * 100"/>
<d ref="(Behavior,{BehaviorID},Modification.AttackSpeedMultiplier - 1) * 100"/>
<d ref="(1 - Behavior,{BehaviorID},DamageResponse.ModifyFraction) * 100"/>
```

### Time & Text Formatting

#### Color Guidelines

Use specific colors for different value types to improve readability:

**Damage Values** - Bright Red Bold
```
<s val="HeaderRed"><d ref="Effect,{EffectID},Amount"/></s>
<c val="ff0000"><d ref="..."/></c>                      <!-- Bright red (alternative) -->
```

**Healing Values** - Green
```
<c val="00ff00"><d ref="Effect,QueenBurstHeal,VitalArray[0].Change"/></c>
```

**Time/Duration** - White Bold
```
<s val="HeaderWhite"><d ref="Behavior,{BehaviorID},Duration"/></s>
```

**Energy Costs/Values** - Purple
```
<c val="f078ff"><d ref="..."/></c>
```

**Shields** - Cyan
```
<c val="00ffff"><d ref="Behavior,{BehaviorID},Modification.VitalMaxArray[Shields]"/></c>
```

**Life/Health** - Green
```
<c val="00ff00"><d ref="Behavior,{BehaviorID},Modification.VitalMaxArray[Life]"/></c>
```

**General Highlights** - Yellow
```
<c val="ffff8a">Text</c>
```

#### Style Tags

**Bold Headers**
```
<s val="HeaderRed">Text</s>       <!-- Red bold - WORKS -->
```

**⚠️ KNOWN ISSUE:** `<s val="HeaderWhite">` does **NOT** work in-game. Use `<c val="#ColorAttackInfo">` instead for highlighted text.

#### Formatting Tokens
```
<d time="10"/>                    <!-- Formatted time value -->
<n/>                              <!-- New line -->
```

#### Complete Examples

**Damage Ability**
```
Deals <s val="HeaderRed"><d ref="Effect,TossGrenadeDamage,Amount"/></s> damage in a small radius.
```

**Heal Over Time**
```
Heals a unit or structure for <c val="00ff00"><d ref="Effect,QueenBurstHeal,VitalArray[0].Change * Behavior,QueenBurstHeal,Duration / 0.5"/></c> life over <c val="#ColorAttackInfo"><d ref="Behavior,QueenBurstHeal,Duration"/></c> seconds (<c val="00ff00"><d ref="Effect,QueenBurstHeal,VitalArray[0].Change"/></c> per tick).
```

**Shield Ability**
```
Grants <c val="00ffff"><d ref="Behavior,VoodooShield,Modification.VitalMaxArray[Shields]"/></c> shields for <c val="#ColorAttackInfo"><d ref="Behavior,VoodooShield,Duration"/></c> seconds.
```

**Energy Cost**
```
<c val="f078ff">Drains <d ref="-1 * (Behavior,SpectreCloaking,Modification.VitalRegenArray[2] + Unit,Spectre,EnergyRegenRate)" precision="1"/> energy per second.</c>
```

**Structured Buff/Debuff with Information Table**

For complex abilities with multiple effects, use a structured format with:
1. Cost/Resource line
2. Duration line
3. Bullet point effects (using `- ` prefix)
4. Descriptive flavor text

```
Costs <c val="#ColorAttackInfo"><d ref="Abil,StimpackHero,Cost[0].VitalFraction[Life] * 100"/>%</c> Max Health<n/>For <c val="#ColorAttackInfo"><d ref="Behavior,Stimpack3,Duration"/> Seconds</c><n/>- Increases Attack Speed by <c val="#ColorAttackInfo"><d ref="(Behavior,Stimpack3,Modification.AttackSpeedMultiplier -1) * 100"/>%</c><n/>- Movement Speed by <c val="#ColorAttackInfo"><d ref="(Behavior,Stimpack3,Modification.MoveSpeedMultiplier - 1) * 100"/>%</c><n/>- Reduced Healing Received by <c val="#ColorAttackInfo"><d ref="(1 - Behavior,Stimpack3,Modification.HealTakenMultiplier) * 100"/>%</c><n/><n/>Injects Hero with powerful stimulants that greatly increases combat capability inform of Attack Speed and Movement Speed bonus for the cost of some Health and reduced Healing Intake
```

**Structured Format Guidelines:**
- **First line**: Cost or activation requirement with `#ColorAttackInfo`
- **Second line**: Duration with `#ColorAttackInfo` and `Seconds` capitalized
- **Bullet effects**: Use `- ` prefix for each stat modification with `#ColorAttackInfo`
- **Spacing**: `<n/>` between each line, double `<n/><n/>` before flavor text
- **Flavor text**: Plain text description at the end
- **Color**: Use `#ColorAttackInfo` for all numeric values (works with game's color scheme)

**Adapting to New Color Scheme:**

When using the structured format, adapt colors based on value type:

```
<!-- Damage ability with table format -->
For <s val="HeaderWhite"><d ref="Behavior,{BehaviorID},Duration"/> Seconds</s><n/>- Deals <s val="HeaderRed"><d ref="Effect,{EffectID},Amount"/></s> damage per second<n/>- Reduces movement speed by <c val="#ColorAttackInfo"><d ref="..."/>%</c><n/><n/>Description text.

<!-- Heal ability with table format -->
Heals over <s val="HeaderWhite"><d ref="Behavior,{BehaviorID},Duration"/> Seconds</s><n/>- Restores <c val="00ff00"><d ref="..."/></c> life per tick<n/>- Total healing: <c val="00ff00"><d ref="..."/></c><n/><n/>Description text.

<!-- Shield ability with table format -->
For <s val="HeaderWhite"><d ref="Behavior,{BehaviorID},Duration"/> Seconds</s><n/>- Grants <c val="00ffff"><d ref="..."/></c> shields<n/>- Absorbs incoming damage<n/><n/>Description text.
```

---

## Hero Ability Mappings

### Protoss Heroes

#### ZealotHero
| Button Face | Tooltip Key | Status | Notes |
|-------------|-------------|--------|-------|
| `Charge2` | `Button/Tooltip/Charge2` | ⚠️ | Needs dynamic refs |
| `VoidZealotWhirlwind` | `Button/Tooltip/VoidZealotWhirlwind` | ⚠️ | Missing - uses `FenixWhirlwind` (6s, +30% move) |
| `Overcharge2` | `Button/Tooltip/Overcharge2` | ✅ | Has scaling info |
| `VoidShieldCapacitor` | `Button/Tooltip/VoidShieldCapacitor` | ✅ | Static |

**Level Scaling:**
```
Levels 1-4: +<d ref="Behavior,Zealot1to4,Modification.DamageDealtUnscaled[Melee]"/> melee damage, +<d ref="Behavior,Zealot1to4,Modification.VitalMaxArray[Shields]"/> shields
Levels 5-7: +<d ref="Behavior,Zealot5to7,Modification.DamageDealtUnscaled[Melee]"/> melee damage, +<d ref="Behavior,Zealot5to7,Modification.VitalMaxArray[Shields]"/> shields
Levels 8-10: +<d ref="Behavior,Zealot8to10,Modification.DamageDealtUnscaled[Melee]"/> melee damage, +<d ref="Behavior,Zealot8to10,Modification.VitalMaxArray[Shields]"/> shields
```

#### DragoonHero
| Button Face | Tooltip Key | Status | Notes |
|-------------|-------------|--------|-------|
| `VoidImmortalStasisHeal` | `Button/Tooltip/VoidImmortalStasisHeal` | ⚠️ | Uses `FlagshipTimeBomb` (-20% move, -5% atk) |
| `FenixChampionPowerShield2` | `Button/Tooltip/FenixChampionPowerShield2` | ✅ | 5s duration, 70% reduction |
| `MothershipCoreTeleport` | `Button/Tooltip/MothershipCoreTeleport` | ✅ | Static |
| `AlarakPsiOrb` | `Button/Tooltip/AlarakPsiOrb` | ⚠️ | Hardcoded 30 dps, 50 explosion |
| `DragoonFrenzy` | `Button/Tooltip/DragoonFrenzy` | ✅ | Uses duration ref |

**Level Scaling:**
```
Levels 1-4: +<d ref="Behavior,Dragoon1to4,Modification.DamageDealtUnscaled[Ranged]"/> ranged damage, +<d ref="Behavior,Dragoon1to4,Modification.VitalMaxArray[Shields]"/> shields
Levels 5-7: +<d ref="Behavior,Dragoon5to7,Modification.DamageDealtUnscaled[Ranged]"/> ranged damage, +<d ref="Behavior,Dragoon5to7,Modification.VitalMaxArray[Shields]"/> shields
Levels 8-10: +<d ref="Behavior,Dragoon8to10,Modification.DamageDealtUnscaled[Ranged]"/> ranged damage, +<d ref="Behavior,Dragoon8to10,Modification.VitalMaxArray[Shields]"/> shields
```

#### AvengerHero (Dark Templar)
| Button Face | Tooltip Key | Status | Notes |
|-------------|-------------|--------|-------|
| `ZeratulBlink` | `Button/Tooltip/ZeratulBlink` | ✅ | Static |
| `CloakOnSpectre2` | `Button/Tooltip/CloakOnSpectre2` | ✅ | Dynamic energy drain |
| `VoidDarkTemplarShadowFury` | `Button/Tooltip/VoidDarkTemplarShadowFury` | ✅ | Uses effect ref |
| `VoidDarkTemplarDeepShadowBlink2` | `Button/Tooltip/VoidDarkTemplarDeepShadowBlink2` | ⚠️ | Uses `HeroDarkTemplarDeepShadows` (5s, +50% move) |
| `DamageReduction` | `Button/Tooltip/DamageReduction` | ⚠️ | 1.6s, 100% immunity |

**Level Scaling:**
```
Levels 1-4: +<d ref="Behavior,DarkTemplar1to4,Modification.DamageDealtUnscaled[Melee]"/> melee damage, +<d ref="Behavior,DarkTemplar1to4,Modification.VitalMaxArray[Shields]"/> shields
Levels 5-7: +<d ref="Behavior,DarkTemplar5to7,Modification.DamageDealtUnscaled[Melee]"/> melee damage, +<d ref="Behavior,DarkTemplar5to7,Modification.VitalMaxArray[Shields]"/> shields
Levels 8-10: +<d ref="Behavior,DarkTemplar8to10,Modification.DamageDealtUnscaled[Melee]"/> melee damage, +<d ref="Behavior,DarkTemplar8to10,Modification.VitalMaxArray[Shields]"/> shields
```

---

### Terran Heroes

#### FirebatHero
| Button Face | Tooltip Key | Status | Notes |
|-------------|-------------|--------|-------|
| `ArtanisLightningDash` | `Button/Tooltip/ArtanisLightningDash` | ⚠️ | Hardcoded 60 dmg, 2s stun |
| `DutchPlaceTurret` | `Button/Tooltip/DutchPlaceTurret` | ⚠️ | Missing |
| `Avatar` | `Button/Tooltip/Avatar` | ⚠️ | Use `FirebatAvatar`: 10s, +300 life, 80% reduction |

**Correct Avatar Tooltip:**
```
Button/Tooltip/Avatar=Enhances the firebat's suit for <d ref="Behavior,FirebatAvatar,Duration"/> seconds. Gains <d ref="Behavior,FirebatAvatar,Modification.VitalMaxArray[Life]"/> extra health and reduces damage taken by <d ref="(1 - Behavior,FirebatAvatar,DamageResponse.ModifyFraction) * 100"/>%. Deals periodic fire damage to nearby enemies.
```

**Level Scaling:**
```
Levels 1-4: +<d ref="Behavior,Firebat1to4,Modification.DamageDealtUnscaled[Ranged]"/> ranged/splash damage, +<d ref="Behavior,Firebat1to4,Modification.VitalMaxArray[Life]"/> life
Levels 5-7: +<d ref="Behavior,FirebatAttackSpeed,Modification.DamageDealtUnscaled[Ranged]"/> ranged/splash damage, +<d ref="Behavior,FirebatAttackSpeed,Modification.VitalMaxArray[Life]"/> life
Levels 8-10: +<d ref="Behavior,Firebat8to10,Modification.DamageDealtUnscaled[Ranged]"/> ranged/splash damage, +<d ref="Behavior,Firebat8to10,Modification.VitalMaxArray[Life]"/> life
```

#### MarineHero
| Button Face | Tooltip Key | Status | Notes |
|-------------|-------------|--------|-------|
| `Stim2` | `Button/Tooltip/Stim2` | ⚠️ | Use `Stimpack3`: 10s, +50% move/atk, 40% heal reduction |
| `TossGrenade2` | `Button/Tooltip/TossGrenade2` | ✅ | Uses effect ref |
| `VoodooShield` | `Button/Tooltip/VoodooShield` | ⚠️ | Use `VoodooShield`: 10s, +50 shields |

**Correct Stim Tooltip:**
```
Button/Tooltip/Stim2=Increases movement and attack speed by <d ref="(Behavior,Stimpack3,Modification.MoveSpeedMultiplier - 1) * 100"/>% for <d ref="Behavior,Stimpack3,Duration"/> seconds. Reduces healing received by <d ref="(1 - Behavior,Stimpack3,Modification.HealTakenMultiplier) * 100"/>%.
```

**Level Scaling:**
```
Levels 1-4: +<d ref="Behavior,Marine1to4,Modification.DamageDealtUnscaled[Ranged]"/> ranged damage, +<d ref="Behavior,Marine1to4,Modification.VitalMaxArray[Life]"/> life
Levels 5-7: +<d ref="Behavior,Marine5to7,Modification.DamageDealtUnscaled[Ranged]"/> ranged damage, +<d ref="Behavior,Marine5to7,Modification.VitalMaxArray[Life]"/> life
Levels 8-10: +<d ref="Behavior,Marine8to10,Modification.DamageDealtUnscaled[Ranged]"/> ranged damage, +<d ref="Behavior,Marine8to10,Modification.VitalMaxArray[Life]"/> life
```

#### GoliathHero
| Button Face | Tooltip Key | Status | Notes |
|-------------|-------------|--------|-------|
| `GravitonBeamUrun` | `Button/Tooltip/GravitonBeamUrun` | ⚠️ | Use `GravitonBeamUrun`: 2.7s, `GravitonBeamUrunHeight`: 3s |
| `GravitonOvercharge` | `Button/Tooltip/GravitonOvercharge` | ⚠️ | Hardcoded 3s |
| `WidowMineBioSplash2` | `Button/Tooltip/WidowMineBioSplash2` | ⚠️ | Hardcoded values |

**Level Scaling:**
```
Levels 1-4: +<d ref="Behavior,Goliath1to4,Modification.DamageDealtUnscaled[Ranged]"/> ranged, +<d ref="Behavior,Goliath1to4,Modification.DamageDealtUnscaled[NoProc]"/> rocket damage, +<d ref="Behavior,Goliath1to4,Modification.VitalMaxArray[Life]"/> life
Levels 5-7: +<d ref="Behavior,Goliath5to7,Modification.DamageDealtUnscaled[Ranged]"/> ranged, +<d ref="Behavior,Goliath5to7,Modification.DamageDealtUnscaled[NoProc]"/> rocket damage, +<d ref="Behavior,Goliath5to7,Modification.VitalMaxArray[Life]"/> life, +<d ref="(Behavior,Goliath5to7,Modification.AttackSpeedMultiplier - 1) * 100"/>% attack speed
Levels 8-10: +<d ref="Behavior,Goliath8to10,Modification.DamageDealtUnscaled[Ranged]"/> ranged, +<d ref="Behavior,Goliath8to10,Modification.DamageDealtUnscaled[NoProc]"/> rocket damage, +<d ref="Behavior,Goliath8to10,Modification.VitalMaxArray[Life]"/> life, +<d ref="(Behavior,Goliath8to10,Modification.AttackSpeedMultiplier - 1) * 100"/>% attack speed
```

---

### Zerg Heroes

#### ZerglingHero
| Button Face | Tooltip Key | Status | Notes |
|-------------|-------------|--------|-------|
| `HotSRaptorCharge` | `Button/Tooltip/HotSRaptorCharge` | ⚠️ | Missing |
| `MorphtoBanelingHero` | `Button/Tooltip/MorphtoBanelingHero` | ⚠️ | Uses `TimedLifeBaneling`: 8s duration |
| `PoisonNova` | `Button/Tooltip/PoisonNova` | ⚠️ | Uses `VileAcidSlowEffectsLevel12`: 3s, -25% move/atk |

**Level Scaling:**
```
Levels 1-4: +<d ref="Behavior,Zergling1to4,Modification.DamageDealtUnscaled[Melee]"/> melee damage, +<d ref="Behavior,Zergling1to4,Modification.VitalMaxArray[Life]"/> life, +<d ref="(Behavior,Zergling1to4,Modification.MoveSpeedMultiplier - 1) * 100"/>% move speed
Levels 5-7: +<d ref="Behavior,Zergling5to7,Modification.DamageDealtUnscaled[Melee]"/> melee damage, +<d ref="Behavior,Zergling5to7,Modification.VitalMaxArray[Life]"/> life, +<d ref="(Behavior,Zergling5to7,Modification.MoveSpeedMultiplier - 1) * 100"/>% move speed
Levels 8-10: +<d ref="Behavior,Zergling8to10,Modification.DamageDealtUnscaled[Melee]"/> melee damage, +<d ref="Behavior,Zergling8to10,Modification.VitalMaxArray[Life]"/> life, +<d ref="(Behavior,Zergling8to10,Modification.MoveSpeedMultiplier - 1) * 100"/>% move speed
```

#### HydraliskHero
| Button Face | Tooltip Key | Status | Notes |
|-------------|-------------|--------|-------|
| `Impale` | `Button/Tooltip/Impale` | ✅ | Uses effect ref |
| `HydraliskFrenzy` | `Button/Tooltip/HydraliskFrenzy` | ⚠️ | Use `HydraliskFrenzy`: +5% move, +100% atk speed |
| `StunningBlast` | `Button/Tooltip/StunningBlast` | ⚠️ | Use `StunningBlast`: 2s stun |
| `Ensnare` | `Button/Tooltip/Ensnare` | ⚠️ | Use `Ensnare`: 2s slow |

**Correct Frenzy Tooltip:**
```
Button/Tooltip/HydraliskFrenzy=Enters a frenzy, increasing movement speed by <d ref="(Behavior,HydraliskFrenzy,Modification.MoveSpeedMultiplier - 1) * 100"/>% and attack speed by <d ref="(Behavior,HydraliskFrenzy,Modification.AttackSpeedMultiplier - 1) * 100"/>%.
```

**Level Scaling:**
```
Levels 1-4: +<d ref="Behavior,Hydralisk1to4,Modification.DamageDealtUnscaled[Ranged]"/> ranged, +<d ref="Behavior,Hydralisk1to4,Modification.DamageDealtUnscaled[Melee]"/> melee damage, +<d ref="Behavior,Hydralisk1to4,Modification.VitalMaxArray[Life]"/> life
Levels 5-7: +<d ref="Behavior,Hydralisk5to7,Modification.DamageDealtUnscaled[Ranged]"/> ranged, +<d ref="Behavior,Hydralisk5to7,Modification.DamageDealtUnscaled[Melee]"/> melee damage, +<d ref="Behavior,Hydralisk5to7,Modification.VitalMaxArray[Life]"/> life
Levels 8-10: +<d ref="Behavior,Hydralisk5to72,Modification.DamageDealtUnscaled[Ranged]"/> ranged, +<d ref="Behavior,Hydralisk5to72,Modification.DamageDealtUnscaled[Melee]"/> melee damage, +<d ref="Behavior,Hydralisk5to72,Modification.VitalMaxArray[Life]"/> life
```

#### DefilerHero
| Button Face | Tooltip Key | Status | Notes |
|-------------|-------------|--------|-------|
| `DefilerMPPlague` | `Button/Tooltip/DefilerMPPlague` | ✅ | 10s, 0.5s period, -100% energy regen |
| `DefilerMPDarkSwarm` | `Button/Tooltip/DefilerMPDarkSwarm` | ⚠️ | 40% damage reduction |
| `Leech` | `Button/Tooltip/Leech` | ⚠️ | Uses `Leech`: Silence |

**Level Scaling:**
```
Levels 1-4: +<d ref="Behavior,Defiler1to4,Modification.DamageDealtUnscaled[Ranged]"/> ranged damage, +<d ref="Behavior,Defiler1to4,Modification.VitalMaxArray[Life]"/> life, +<d ref="Behavior,Defiler1to4,Modification.VitalMaxArray[Energy]"/> energy
Levels 5-7: +<d ref="Behavior,Defiler5to7,Modification.DamageDealtUnscaled[Ranged]"/> ranged damage, +<d ref="Behavior,Defiler5to7,Modification.VitalMaxArray[Life]"/> life, +<d ref="Behavior,Defiler5to7,Modification.VitalMaxArray[Energy]"/> energy
Levels 8-10: +<d ref="Behavior,Defiler8to10,Modification.DamageDealtUnscaled[Ranged]"/> ranged damage, +<d ref="Behavior,Defiler8to10,Modification.VitalMaxArray[Life]"/> life, +<d ref="Behavior,Defiler8to10,Modification.VitalMaxArray[Energy]"/> energy
```

#### BroodQueenHero
| Button Face | Tooltip Key | Status | Notes |
|-------------|-------------|--------|-------|
| `QueenBurstHeal2` | `Button/Tooltip/QueenBurstHeal2` | ⚠️ | Use `QueenBurstHeal`: 2.5s |
| `PrimalGasCloud` | `Button/Tooltip/PrimalGasCloud` | ⚠️ | Use `PoisonGas`: 0.45s, -20% move |

**Level Scaling:**
```
Levels 1-4: +<d ref="Behavior,Queen1to4,Modification.VitalMaxArray[Life]"/> life, +<d ref="Behavior,Queen1to4,Modification.VitalMaxArray[Energy]"/> energy
Levels 5-7: +<d ref="Behavior,Queen1to42,Modification.VitalMaxArray[Life]"/> life, +<d ref="Behavior,Queen1to42,Modification.VitalMaxArray[Energy]"/> energy
Levels 8-10: +<d ref="Behavior,Queen1to422,Modification.VitalMaxArray[Life]"/> life, +<d ref="Behavior,Queen1to422,Modification.VitalMaxArray[Energy]"/> energy
```

#### UltraliskHero (HotSTorrasque2)
| Button Face | Tooltip Key | Status | Notes |
|-------------|-------------|--------|-------|
| `MonarchBlades2` | `Button/Tooltip/MonarchBlades2` | ⚠️ | Uses `NydusWhirlwind`: 10s, +30% move |
| `Frenzied2` | `Button/Tooltip/Frenzied2` | ✅ | Level 6+ gains air attack via `UltraliskAirAttack` |

**Level Scaling:**
```
Levels 1-4: +<d ref="Behavior,Ultralisk1to4,Modification.DamageDealtUnscaled[Melee]"/> melee, +<d ref="Behavior,Ultralisk1to4,Modification.DamageDealtUnscaled[Splash]"/> splash damage, +<d ref="Behavior,Ultralisk1to4,Modification.VitalMaxArray[Life]"/> life
Levels 5-7: +<d ref="Behavior,Ultralisk5to7,Modification.DamageDealtUnscaled[Melee]"/> melee, +<d ref="Behavior,Ultralisk5to7,Modification.DamageDealtUnscaled[Splash]"/> splash damage, +<d ref="Behavior,Ultralisk5to7,Modification.VitalMaxArray[Life]"/> life
Levels 8-10: +<d ref="Behavior,Ultralisk8to10,Modification.DamageDealtUnscaled[Melee]"/> melee, +<d ref="Behavior,Ultralisk8to10,Modification.DamageDealtUnscaled[Splash]"/> splash damage, +<d ref="Behavior,Ultralisk8to10,Modification.VitalMaxArray[Life]"/> life
```

---

## Recent Hardcoded Value Fixes

The following tooltips have been converted to use dynamic references instead of hardcoded values:

### Completed Conversions

| Tooltip | Fixed Values | Dynamic Reference |
|---------|--------------|-------------------|
| `BurrowChargeCampaign` | "2 seconds" | `<d ref="Behavior,UltraliskBurrowChargeStun,Duration"/>` |
| `GuardianShield3` | "+9 shields per second" | `<d ref="Effect,VoidSentryShieldRepairDouble2,RechargeVitalRate"/>` |
| `GuardianShield3` | "-2 attack damage" | `<d ref="Behavior,GuardianShield2,DamageResponse.ModifyAmount"/>` |
| `ArtanisLightningDash` | "60 damage" → 5 | `<d ref="Effect,ArtanisLightningDashDamage,Amount"/>` |

### Partially Fixed (TODO)

| Tooltip | Remaining Hardcoded | Status |
|---------|-------------------|--------|
| `GuardianShield3` | "+100 shields" | Need to find initial shield grant effect |
| `ArtanisLightningDash` | "2 seconds" stun | Need to find stun behavior effect |
| `CommanderTraitNovaDefensiveDrone` | "10 damage per deflection" | Need to find reflection damage effect |
| `AlarakPsiOrb` | Multiple values | Not yet investigated |

### Data File Findings

**Effect Examples Found:**
- `ArtanisLightningDashDamage`: Amount = 5
- `VoidSentryShieldRepairDouble2`: RechargeVitalRate = 9 (shields/sec)
- `UltraliskBurrowChargeStun`: Duration = 1.5 (was hardcoded as 2)
- `GuardianShield2`: DamageResponse.ModifyAmount = -2

### Investigation Notes

When searching for dynamic references:
1. Check `AbilData.xml` for ability definitions and their Effect arrays
2. Navigate to `EffectData.xml` to find CEffect entries matching the effect name
3. For behaviors, look in `BehaviorData.xml` for CBehavior entries
4. For initial actions, check CEffectSet and CEffectEnumArea for chained effects
5. Amount/Duration/Rate values are typically in the CEffect* definitions

---

## Files Reference

| File | Location | Purpose |
|------|----------|---------|
| `UnitData.xml` | `Base.SC2Data/GameData/` | Hero definitions, `CardLayouts > LayoutButtons` |
| `BehaviorData.xml` | `Base.SC2Data/GameData/` | Level scaling behaviors (`{Hero}1to4`, etc.) |
| `GameStrings.txt` | `enUS.SC2Data/LocalizedData/` | All `Button/Tooltip/{Face}` entries |
| `EffectData.xml` | `Base.SC2Data/GameData/` | Effect IDs for damage refs |
| `AbilData.xml` | `Base.SC2Data/GameData/` | Ability configurations |

---

## Legend

| Status | Meaning |
|--------|---------|
| ✅ | Tooltip uses dynamic references correctly |
| ⚠️ | Tooltip has hardcoded values or missing refs |
| ❌ | Tooltip is missing entirely |

---

## References

- [SC2 Editor Guides](https://s2editor-guides.readthedocs.io/)
- [SC2Mapster Data Reference](https://sc2mapster.github.io/mkdocs/)
- [Proxima Frontlines Discord](https://discord.gg/abBfe66wey)