# Hero Mechanics Agent - Proxima Frontlines

This document provides detailed mechanics, playstyles, and strategic information for all heroes in the Proxima Frontlines mod. Unlike the tooltip agent (which handles UI text), this agent explains how each hero actually works in practice.

## Table of Contents

- [Overview](#overview)
- [Hero Roles & Playstyles](#hero-roles--playstyles)
- [Protoss Heroes](#protoss-heroes)
- [Terran Heroes](#terran-heroes)
- [Zerg Heroes](#zerg-heroes)
- [General Mechanics](#general-mechanics)
- [Progression Systems](#progression-systems)
- [Common Patterns](#common-patterns)

---

## Overview

Proxima Frontlines features **18 MOBA-style heroes** split across three races:
- **6 Protoss Heroes** - High damage, shields, mobility
- **6 Terran Heroes** - Versatile, sustained damage, utility
- **6 Zerg Heroes** - Burst damage, crowd control, healing

Heroes gain XP and level from 1-10, with distinct playstyles that reward different engagement patterns.

### Critical Team Structure Restriction

⚠️ **IMPORTANT:** Heroes cannot cross race boundaries in team composition. Teams are **race-locked**:
- All 6 Protoss heroes must team together
- All 6 Terran heroes must team together
- All 6 Zerg heroes must team together

This constraint fundamentally shapes team compositions and strategic synergies. Each race must function as a cohesive unit with internal synergies, not mixed-race compositions.

### Race-Locked Team Composition Strategy

**Protoss (Shield-Focused, Defensive):**
- **Core Playstyle:** Shields, positioning control, base defense
- **Team Dynamics:** Sentry provides shield aura amplifying team durability. Mothership Core anchors base defense. Zealot + Dark Templar provide burst. Dragoon & Corsair deliver sustained DPS.
- **Composition Role Distribution:** Tank (Zealot), Ranged (Dragoon), Assassin (Dark Templar), Support (Sentry), Support (Mothership Core), Specialist (Corsair)
- **Win Condition:** Control positioning through shields and force field. Enable aggressive plays when base is secured by Mothership Core.

**Terran (Utility-Focused, Flexible):**
- **Core Playstyle:** Crowd control, sustained damage, versatile threat
- **Team Dynamics:** Goliath's CC enables Marine & Spectre burst. Firebat's area damage punishes grouped enemies. Medic heals enable aggressive positioning. Science Vessel locks down base defense.
- **Composition Role Distribution:** Tank (Firebat), Ranged (Marine), Ranged (Goliath), Assassin (Spectre), Support (Medic), Support (Science Vessel)
- **Win Condition:** Use Goliath's crowd control to set up Marine/Spectre burst windows. Medic sustain enables extended teamfights.

**Zerg (Healing-Focused, Aggressive):**
- **Core Playstyle:** Healing, area denial, burst assassination
- **Team Dynamics:** Brood Queen's healing sustains aggressive plays. Zergling + Ultralisk burst through grouped enemies. Hydralisk provides versatile dual-attack DPS. Defiler silences enemy threats. Nydalist anchors base defense.
- **Composition Role Distribution:** Tank (Ultralisk), Ranged (Hydralisk), Assassin (Zergling), Support (Brood Queen), Specialist (Defiler), Support (Nydalist)
- **Win Condition:** Use Brood Queen healing to enable melee aggression. Defiler silence prevents enemy counter-plays. Nydalist base defense allows aggressive roaming.

---

## Hero Roles & Playstyles

### Role Matrix

| Role | Heroes | Playstyle |
|------|--------|-----------|
| **Bruiser** | Zealot, Firebat, Ultralisk | Durable frontline with sustained damage, excels in extended teamfights |
| **Ranged Carry** | Dragoon, Marine, Goliath, Hydralisk | Sustained DPS from safe distance, with area damage or utility |
| **Melee Assassin** | Dark Templar, Zergling, Spectre | High burst damage, mobile hit-and-run, target isolated enemies |
| **Base Defender** | Mothership Core, Science Vessel, Nydalist | Defend base structures, area denial, positioning control |
| **Support/Healer** | Medic, Brood Queen, Sentry | Team healing, sustain, and damage mitigation |
| **Specialists** | Corsair, Defiler | Unique mechanics: splash mobility, utility control, energy-based denial |

### Early Game (Levels 1-4)

- Heroes gain initial base stats + leveling bonuses
- Focus on securing kills for XP
- Melee heroes are vulnerable without support
- Ranged heroes dominate early skirmishes

### Mid Game (Levels 5-7)

- Power spike for all heroes
- Team fights become frequent
- Positioning and ability usage crucial
- Supports amplify team carry damage significantly

### Late Game (Levels 8-10)

- Heroes approach maximum power
- Fights are decided by positioning and cooldown management
- Carries deal massive damage
- Supports provide critical team survival abilities

---

## Protoss Heroes

### Zealot Hero

**Role:** Bruiser  
**Difficulty:** Medium  
**Playstyle:** Durable frontline damage dealer with incredible staying power and extended engagement potential

#### How Zealot Works

Zealot is a **sustained melee carry** who wins extended fights through shield regeneration and high damage output. Unlike burst heroes, Zealot excels in prolonged skirmishes where shields have time to recharge.

| Aspect | Details |
|--------|---------|
| **Core Identity** | Heavy-hitting melee unit with high shield pool |
| **Strengths** | High damage scaling, excellent durability, charges through terrain |
| **Weaknesses** | Requires close range, vulnerable to crowd control, needs team peel |
| **Counter By** | Long-range burst (Dragoon, Marine), crowd control (Hydralisk) |
| **Counters** | Zealot dominates isolated melee targets (Zergling, Firebat pre-6) |

#### Ability Breakdown

1. **Charge** (`Charge2`)
   - **Mechanic:** Dashes forward with momentum, dealing damage and interrupting enemies
   - **Usage:** Initiate fights, chase fleeing targets, escape tight positions
   - **Scaling:** Better scaling with melee damage upgrades
   - **Cooldown:** Medium (allows repositioning)

2. **Whirlwind** (`VoidZealotWhirlwind`)
   - **Mechanic:** Spins attacking everything nearby, refreshes on kill
   - **Usage:** Area denial, team fight cleanup phase
   - **Scaling:** Increases damage per level
   - **Mechanic Quirk:** Kill refresh means skilled play can chain multiple spins

3. **Overcharge** (`Overcharge2`)
   - **Mechanic:** Temporarily increases damage output and shield regeneration
   - **Usage:** Secure kills during critical moments, sustain in trades
   - **Scaling:** Bonus per level
   - **Playstyle Tip:** Hold for pivotal 1v1s, don't waste on retreating enemies

4. **Shield Capacitor** (`VoidShieldCapacitor`)
   - **Mechanic:** Passive shield pool increases with each foe nearby
   - **Usage:** Automatic — encourages diving into groups
   - **Scaling:** Scales dramatically with hero leveling (-80 to -190 shields per level)
   - **Map Positioning:** More useful in teamfight-heavy maps

#### Leveling Progression

| Level Range | Damage Increase | Shield Increase | Key Powerspike |
|-------------|-----------------|-----------------|-----------------|
| **Levels 1-4** | +4 melee | +80 shields | Level 4 - Can solo melee heroes |
| **Levels 5-7** | +5 melee | +150 shields | Level 6 - Untouchable with overcharge |
| **Levels 8-10** | +6 melee | +190 shields | Level 8 - 1v2 duelist |

#### Gameplay Progression

- **Level 1-2:** Weak compared to ranged. Stick with allies, use charge for guaranteed damage.
- **Level 3-4:** Damage spike arrives. Start skirmishing in pairs, use overcharge for kills.
- **Level 5-6:** Power spike. Can pressure multiple enemies. Overcharge becomes team fight centerpiece.
- **Level 7-8:** Minor spike. Begin solo-laning effectively. Watch for burst assassins.
- **Level 9-10:** Near invincible in teamfights. Become primary engage point. Watch for focus-fire.

#### Build Recommendations

**Aggressive:** Prioritize positioning deep in enemy team. Use multiple charges per fight.

**Defensive:** Play around allies, avoid isolated 1v3s. Overcharge when your team needs durability, not kills.

**Mid-Game:** Secure kills on isolated supports (Science Vessel, Medic) to accelerate leveling.

#### Common Mistakes

- Using Charge into 5 enemies (get focus-fired)
- Overcharging defensively when team is retreating
- Fighting without nearby allies (no peel if crowd controlled)
- Ignoring enemy cooldowns before diving

#### Synergies (Race-Locked)

**Best With:** Dragoon (sustained ally DPS), Sentry (shields & utility support), Mothership Core (base defense anchor)

**Team Composition Role:** Primary frontline melee initiator for Protoss. Focuses on aggressive positioning and sustained damage output. Works well in compositions that leverage Dragoon's ranged support and base defender protection.

---

### Dragoon Hero

**Role:** Ranged Carry  
**Difficulty:** Low-Medium  
**Playstyle:** Consistent sustained damage from safe distance

#### How Dragoon Works

Dragoon is the **most reliable damage dealer** — not flashy but effective. Dragoon wins through sustained attack speed and consistent positioning, dealing steady damage while staying safe.

| Aspect | Details |
|--------|---------|
| **Core Identity** | Versatile ranged unit with good damage and utility |
| **Strengths** | Consistent DPS, strong utility, safe range, good scaling |
| **Weaknesses** | No mobility spell (pure movement), moderate early game |
| **Counter By** | Assassins (Dark Templar, Spectre), extreme burst (Goliath) |
| **Counters** | Dragoon dominates vs. other ranged heroes in sustained fights |

#### Ability Breakdown

1. **Wormhole Transit** (`ArtanisWormholeTransit`)
   - **Mechanic:** Short-range teleport for repositioning
   - **Usage:** Escape threats, reposition in fights, chase enemies
   - **Range:** Medium-range teleport
   - **Scaling:** Improves with level
   - **Playstyle Tip:** Use offensively between auto-attacks for positioning

2. **Time Bomb** (`FlagshipTimeBombTarget`)
   - **Mechanic:** Place delayed damage on target enemy
   - **Usage:** Apply sustained pressure, combo with auto-attacks for burst
   - **Duration:** Detonates after delay
   - **Scaling:** Damage improves per level
   - **Playstyle Tip:** Use on priority targets being focused

3. **Power Shield** (`FenixChampionPowerShield`)
   - **Mechanic:** Temporary damage reduction buff
   - **Usage:** Extended protection during critical engagements
   - **Duration:** Variable duration, scales with level
   - **Cooldown Management:** Save for predictable burst windows
   - **Playstyle Tip:** Use before enemy burst combos

4. **Psi Orb** (`AlarakPsiOrb`)
   - **Mechanic:** Projectile that deals damage with area effect
   - **Usage:** Deal area damage, zone enemies, setup teamfight follow-up
   - **Scaling:** Improves with attack damage
   - **Playstyle Tip:** Use on clustered groups for maximum value

#### Leveling Progression

| Level Range | Damage Increase | Ability Impact | Key Powerspike |
|-------------|-----------------|-----------------|----------------------|
| **Levels 1-4** | +7 ranged | Minor | Level 2 - Wormhole Transit utility |
| **Levels 5-7** | +8 ranged | Moderate | Level 5 - Time Bomb + Power Shield combo |
| **Levels 8-10** | +10 ranged | Major | Level 8 - Full kit sustained pressure |

#### Gameplay Progression

- **Level 1-2:** Solid early game. Farm safely from range, poke with Psi Orbs. Wormhole Transit for positioning escape.
- **Level 3-4:** Minor damage increase. Use Power Shield preemptively before burst windows. Group with teammates.
- **Level 5-6:** Power spike. Time Bomb on focused targets adds sustained pressure. Power Shield stacking becomes effective.
- **Level 7-8:** Strong mid-game. Solo-lane potential grows. Wormhole Transit escapes are critical for survival.
- **Level 9-10:** Apex damage dealer. Balance auto-attacks, Time Bombs, Psi Orbs for area damage, and Power Shield timing.

#### Build Recommendations

**Safe Farming:** Poke with Psi Orbs on groups, use Time Bomb for single-target sustained pressure. Maintain Power Shield for incoming burst.

**Aggressive Teamfights:** Lead with Wormhole Transit flanks to reposition. Apply Time Bomb to priority targets immediately. Use Power Shield reactively when enemies commit burst. Chain Psi Orbs on grouped enemies.

**Late Game:** Position where you can hit 3+ enemies. Pre-stack Power Shield before fights start. Apply Time Bomb to all high-priority threats constantly.

#### Common Mistakes

- Using Wormhole Transit into 5 enemies without ally support
- Using Power Shield too late (should be preemptive, not reactive)
- Standing still for extended periods (use Wormhole for repositioning)
- Not applying Time Bomb on focused targets (should be constant pressure)

#### Synergies (Race-Locked)

**Best With:** Zealot (complementary melee/ranged sustained damage), Mothership Core (enables safe farming), Sentry (amplifies team DPS through shields)

**Team Composition Role:** Primary ranged DPS for Protoss. Safe positioning in multi-hero teamfights. Synergizes with Zealot for extended fights and Mothership Core for base defense rotation.

---

### Dark Templar Hero (Avenger)

**Role:** Melee Assassin  
**Difficulty:** High  
**Playstyle:** Mobile melee burst assassin with invisibility and hit-and-run mechanics

#### How Dark Templar Works

Dark Templar is the **glass cannon assassin** — extreme burst damage potential offset by fragility. DT wins through surprise and burst timing rather than sustained engagement.

| Aspect | Details |
|--------|---------|
| **Core Identity** | Invisible burst assassin with shadow mechanics |
| **Strengths** | Highest burst damage, invisibility for ganks, escape tools |
| **Weaknesses** | Dies quickly if caught, no sustained DPS, cooldown reliant |
| **Counter By** | Search/detection (Medic, SCV wards), ranged carries in open |
| **Counters** | Dark Templar demolishes isolated fragile heroes (Medic, Spectre) |

#### Ability Breakdown

1. **Blink** (`ZeratulBlink`)
   - **Mechanic:** Short-range dash that applies invulnerability frames
   - **Usage:** Final initiate tool, escape from danger, dodge incoming damage
   - **Range:** Medium (through walls works)
   - **Playstyle Tip:** Use offensively to commit to burst, defensively to escape

2. **Cloak** (`CloakOnSpectre2`)
   - **Mechanic:** Become undetectable, drains energy while active
   - **Usage:** Setup for ganks, repositioning out of vision, escape
   - **Energy Drain:** Consistent cost (see tooltip for exact value)
   - **Mechanic:** Invisible units can still be targeted if revealed or predicted

3. **Shadow Fury** (`VoidDarkTemplarShadowFury`)
   - **Mechanic:** Melee attack that applies bonus damage and applies effect
   - **Usage:** Core burst damage, primary damage output ability
   - **Scaling:** Improves significantly with melee damage
   - **Playstyle Impact:** Should be followed with immediate auto-attacks

4. **Deep Shadows** (`VoidDarkTemplarDeepShadowBlink2`)
   - **Mechanic:** Enter shadow form — gain movement speed and undetectability
   - **Usage:** Aggressive repositioning in fights, setup for burst, escape
   - **Duration:** 5 seconds
   - **Playstyle Tip:** Time entry/exit for maximum burst amplification

5. **Damage Reduction** (`DamageReduction`)
   - **Mechanic:** Brief window of 100% damage immunity
   - **Usage:** I-frame defensive tool, dodge ultimates
   - **Duration:** 1.6 seconds
   - **Playstyle Tip:** Use when you see enemies committing to you

#### Leveling Progression

| Level Range | Damage Increase | Shield Increase | Key Powerspike |
|-------------|-----------------|-----------------|-----------------|
| **Levels 1-4** | +6 melee | +40 shields | Level 2 - One-shot potential on weak heroes |
| **Levels 5-7** | +8 melee | +110 shields | Level 5 - Delete support heroes |
| **Levels 8-10** | +10 melee | +150 shields | Level 8 - Can burst tanks |

#### Gameplay Progression

- **Level 1-2:** Strong 1v1 assassin. Lurk in fog, surprise isolated enemies.
- **Level 3-4:** Increasing burst. Can combo Shadow Fury + autos for kills.
- **Level 5-6:** Power spike. Watch enemies stay grouped up in fear.
- **Level 7-8:** Lethal. Can target-swap to different victims per fight.
- **Level 9-10:** Apex assassin. Proper positioning = guaranteed kills.

#### Build Recommendations

**Aggressive:** Hunt isolated heroes. Use cloak to position aggressively. Blink in, Shadow Fury, blink out.

**Defensive:** Use invisibility for vision control. Entry/exit fights unpredictably. Save Damage Reduction for enemy ults.

**Late Game:** Identify lowest-health/easiest enemy each fight. You don't need to kill—kill the target, leave.

#### Common Mistakes

- Using Blink into 5 enemies (get focus-fired)
- Cloaking when enemy has detection (wastes energy)
- Shadow Fury without follow-up auto-attacks
- Staying in fights too long (be hit-and-run focused)
- Giving away position before optimal burst window

#### Synergies (Race-Locked)

**Best With:** Mothership Core (detection & base defense), Sentry (crowd control support), Zealot (melee initiation coordination)

**Team Composition Role:** Primary burst assassin for Protoss. Excels when Mothership Core provides base defense allowing Dark Templar aggressive roaming. Benefits from Sentry's crowd control setup opportunities.

---

### Mothership Core Hero

**Role:** Base Defender  
**Difficulty:** Medium  
**Playstyle:** Flying base defender providing defensive structures, team utility and positioning control

#### How Mothership Core Works

Mothership Core is the **primary Protoss base defender** — flying unit providing defensive utilities, team protection, and positioning control. MSC wins through strategic ability usage and maintaining strong base presence.

| Aspect | Details |
|--------|---------|
| **Core Identity** | Flying base defender with protective and positioning mechanics |
| **Strengths** | Mobility, protective utilities, positioning control, decent scaling |
| **Weaknesses** | Low damage, vulnerable to burst, reliant on smart placement |
| **Counter By** | Assassins (targets fragile unit), concentrated burst (Dragoon focus) |
| **Counters** | Mothership Core denies aggressive base pushes through protective abilities |

#### Ability Breakdown

1. **Photon Overcharge** (Passive/Active)
   - **Mechanic:** Boost ally shields and attack power
   - **Usage:** Amplify carry damage in fights
   - **Scaling:** Improves per level
   - **Playstyle Tip:** Use before fights, not mid-combo

2. **Mass Recall**
   - **Mechanic:** Team-wide repositioning/safety valve
   - **Usage:** Save teammates from death, regroup team, escape wipes
   - **Range:** Large area
   - **Playstyle Impact:** Single ability that can swing games

3. **Time Warp** / **Temporal Field**
   - **Mechanic:** Temporal effect that alters ally/enemy time
   - **Usage:** Slow enemies chasing, speed up allies escaping
   - **Scaling:** Improves duration per level
   - **Playstyle Tip:** Use on key targets being focused

4. **Teleport** (`MothershipCoreTeleport`)
   - **Mechanic:** Mobile repositioning tool for the Mothership Core
   - **Usage:** Escape ganks on the core, reposition defensively, enable base rotation
   - **Range:** Medium range repositioning
   - **Scaling:** Improves per level
   - **Playstyle Tip:** Use When threatened or repositioning between objectives

5. **Photon Cannon** (`PhaseCannon`)
   - **Mechanic:** Deploy defensive cannon structure at location
   - **Usage:** Establish area denial, provide defensive firepower, protect positioning
   - **Range:** Medium placement range
   - **Scaling:** Cannon damage improves per level
   - **Playstyle Tip:** Place at base entrances or choke points for defense

6. **Purify Nexus** (`MothershipCorePurifyNexus`)
   - **Mechanic:** Cleanse negative effects and restore shields to nearby structures/allies
   - **Usage:** Remove debuffs from teammates, restore structure integrity
   - **Range:** Medium area effect
   - **Scaling:** Cleanse power improves per level
   - **Playstyle Tip:** Use preemptively on structures under attack

#### Leveling Progression

| Level Range | Damage Increase | Utility | Key Powerspike |
|-------------|-----------------|---------|-----------------|
| **Levels 1-4** | +4 ranged | Minor | Level 2 - Photon Cannon placement |
| **Levels 5-7** | +5 ranged | Moderate | Level 5 - Time Warp + Purify Nexus combo |
| **Levels 8-10** | +6 ranged | Major | Level 8 - Full defensive toolkit |

#### Gameplay Progression

- **Level 1-2:** Support mode. Place Photon Cannons at base. Use Photon Overcharge sparingly.
- **Level 3-4:** Purify Nexus becomes relevant for structure cleanse. Position carefully for safety.
- **Level 5-6:** Power spike. Time Warp duration increases. Purify Nexus is game-saving against debuffs.
- **Level 7-8:** Strong base defender. Teleport escape becomes reliable. Mass Recall saves critical moments.
- **Level 9-10:** Apex defender. Full kit mattering. Proper Teleport + Purify timing denies pushes.

#### Build Recommendations

**Base Protection:** Position near base structures. Deploy Photon Cannons at entrances. Use Purify Nexus preemptively on towers under attack.

**Defensive Repositioning:** Use Teleport to escape ganks on core. Position where you can Purify compromised structures quickly.

**Team Protection:** Use Mass Recall when entire team getting wiped. Time Warp on chasing enemies. Photon Overcharge before teamfights.

**Emergency Defense:** Monitor base constantly. Teleport to threatened structures. Purify removes debuffs immediately. Mass Recall is last-resort save.

#### Common Mistakes

- Using Mass Recall too early (save for actual wipe scenarios)
- Positioning within range of assassins without Teleport ready
- Overcharging when no fight is happening (waste of buff)
- Not Purifying structures proactively (should cleanse before they reach low HP)
- Teleporting predictably (enemies can read patterns)

#### Synergies (Race-Locked)

**Best With:** Zealot (sustains in extended fights), Dark Templar (aggressive ganking enabler), Dragoon (safe farming support)

**Team Composition Role:** Primary base defender and support for Protoss. Mothership Core is essential anchor for defensive play. Coordinates with Zealot/Dark Templar for aggressive phases.

---

### Sentry Hero (Energizer)

**Role:** Support/Utility  
**Difficulty:** Medium-High  
**Playstyle:** Smart cooldown disruption and team protection

#### How Sentry Works

Sentry is the **utility support** — instead of healing, Sentry disables and protects through clever ability usage. Forces enemies to play around Sentry's tools.

| Aspect | Details |
|--------|---------|
| **Core Identity** | Utility-focused support with cooldown disruption |
| **Strengths** | Crowd control, team shields, position control, scaling |
| **Weaknesses** | Low health, not mobile, reliant on timing |
| **Counter By** | Sustained damage, positioning disruption |
| **Counters** | Sentry negates ability-reliant heroes (Mothership Core, Defiler) |

#### Ability Breakdown

1. **guardian Shield** (Passive Aura)
   - **Mechanic:** Nearby allies gain shield regeneration
   - **Usage:** Automatic team defense, stacks with shields
   - **Scaling:** Improves significantly per level
   - **Playstyle Impact:** Encourages teamfight clustering

2. **Force Field**
   - **Mechanic:** projectile wall that blocks movement and damage
   - **Usage:** Block important ability casts, protect allies, trap enemies
   - **Range:** Medium
   - **Playstyle Tip:** Time casts to block enemy initiations

3. **Psionic Protection**
   - **Mechanic:** Speed boost + damage reduction for targets
   - **Usage:** Save allies during focus-fire, enable escapes
   - **Cooldown:** Manage carefully per target
   - **Playstyle Tip:** Use offensively to let carries overextend

#### Leveling Progression

| Level Range | Damage Increase | Shield Increase | Key Powerspike |
|-------------|-----------------|-----------------|-----------------|
| **Levels 1-4** | +4 ranged | +40 shields | Level 2 - Shield regen becomes relevant |
| **Levels 5-7** | +5 ranged | +120 shields | Level 5 - Aura becomes dominating |
| **Levels 8-10** | +5 ranged | +150 shields | Level 8 - Carries nearly unkillable |

#### Gameplay Progression

- **Level 1-2:** Weak early. Stay grouped, Shield Regen barely helps.
- **Level 3-4:** Minor shield improvements. Block important casts.
- **Level 5-6:** Power spike. Shield Regen becomes significant. Teamfight presence.
- **Level 7-8:** Strong support. Your aura denies enemy damage.
- **Level 9-10:** Extreme teamfight presence. Almost unkillable allies.

#### Build Recommendations

**Aggressive:** Position inside allied groups. Use Force Field offensively to block enemy combos.

**Defensive:** Protect high-priority carries. Use Psionic Protection preemptively before burst.

**Late Game:** Be within range of your entire team. Your aura matters more than anything else.

#### Common Mistakes

- Using Psionic Protection poorly (use on incoming burst, not random allies)
- Separating from team (aura range is limited)
- Force Field too early (enemies dodge)
- Letting yourself get burst (critical target)

#### Synergies (Race-Locked)

**Best With:** Zealot (shield aura amplifies melee presence), Dragoon (enables safe positioning), Dark Templar (supports burst windows)

**Team Composition Role:** Utility support for Protoss. Guardian Shield aura amplifies team durability. Best utilized with melee-heavy Protoss compositions leveraging Zealot + Dark Templar burst.

---

### Corsair Hero

**Role:** Ranged Carry  
**Difficulty:** Low-Medium  
**Playstyle:** Fast, mobile ranged attacker with strong area damage and positioning flexibility

#### How Corsair Works

Corsair is the **mobile ranged carry** — emphasizes speed and positioning over raw sustained DPS. Corsair excels at hit-and-run attacks and dealing splash damage to grouped enemies while maintaining mobility.

| Aspect | Details |
|--------|---------|
| **Core Identity** | Mobile ranged unit with splash damage and movement |
| **Strengths** | Area damage, mobility, positioning flexibility, good early game |
| **Weaknesses** | Lower raw damage than other ranged carries, requires positioning finesse |
| **Counter By** | Sustained burst (Dragoon), crowd control (locks down mobile unit) |
| **Counters** | Corsair dominates vs. grouped enemies through splash |

#### Ability Breakdown

1. **Disrupt ionWeb** (`CorsairMPDisruptionWeb`)
   - **Mechanic:** Projectile that applies slowing web to enemies
   - **Usage:** Slow enemy team, reduce kiting potential, setup kills
   - **Area Effect:** Hits all enemies in radius
   - **Scaling:** Slow strength improves per level
   - **Playstyle Tip:** Use on grouped enemies to enable teamfight advantage

2. **Corsair Attack** (Auto-attack special)
   - **Mechanic:** Ranged splash attack hitting nearby enemies
   - **Usage:** Automatic—deal area damage while attacking
   - **Scaling:** Splash damage increases per level
   - **Playstyle Tip:** Position where multiple enemies nearby for max splash

3. **Force Field** (`ForceField2`)
   - **Mechanic:** Projectile wall that blocks movement and damage
   - **Usage:** Block important ability casts, protect allies, trap enemies
   - **Range:** Medium placement
   - **Playstyle Tip:** Time placements to block enemy initiations

4. **Psionic Shockwave** (`PsionicShockwave`)
   - **Mechanic:** Area burst damage around location
   - **Usage:** Team fight area damage, burst grouped enemies
   - **Scaling:** Damage improves per level
   - **Playstyle Tip:** Use in center of fights for maximum value

5. **Mothership Stasis** (`MothershipStasis`)
   - **Mechanic:** Temporarily slow or control area effect
   - **Usage:** Area denial, protect positioning, enable escapes
   - **Duration:** Variable, scales with level
   - **Playstyle Tip:** Use reactively to prevent enemy bursts

6. **Interceptor Boost** (Speed buff)
   - **Mechanic:** Temporary movement speed increase
   - **Usage:** Chase enemies, reposition in fights, escape ganks
   - **Duration:** Variable
   - **Playstyle Impact:** Turns from safe distance to aggressive hunting

#### Leveling Progression

| Level Range | Ranged Damage | Splash Damage | Ability Impact | Key Powerspike |
|-------------|---------------|----------------|---------|-----------------|
| **Levels 1-4** | +3 ranged | +3 splash | Minor | Level 2 - Disruption Web utility |
| **Levels 5-7** | +4 ranged | +4 splash | Moderate | Level 5 - Psionic Shockwave burst |
| **Levels 8-10** | +5 ranged | +5 splash | Major | Level 8 - Full utility kit mattering |

#### Gameplay Progression

- **Level 1-2:** Strong early damage through splash. Use Disruption Web to slow grouped enemies.
- **Level 3-4:** Mobility allows aggressive positioning. Interceptor Boost enables hit-and-run tactics.
- **Level 5-6:** Power spike. Psionic Shockwave adds burst damage. Force Field enables area control.
- **Level 7-8:** Strong mid-game. Can solo groups through splash. Mothership Stasis provides area denial.
- **Level 9-10:** Peak versatility. Position aggressively, use all utilities. Force Field chains with Shockwave.

#### Build Recommendations

**Aggressive Splash Damage:** Position where 3+ enemies grouped. Auto-attack heavily in groups. Use Psionic Shockwave on clusters.

**Kite & Control:** Use Interceptor Boost to maintain range while attacking. Use Disruption Web to slow backline, Force Field to block enemy advances. Chain with Mothership Stasis for persistent area denial.

**Late Game:** Position where splash hits entire enemy team. Lead with Disruption Web to group enemies, follow with Psionic Shockwave. Interceptor Boost for constant repositioning.

#### Common Mistakes

- Using Interceptor Boost defensively (should be offensive for aggressive positioning)
- Poor splash positioning (should maximize enemy hit count)
- Overextending without Force Field backup (no escape)
- Not timing Psionic Shockwave with enemy groups (should hit 3+ targets)

#### Synergies (Race-Locked)

**Best With:** Sentry (crowd control setup), Zealot (melee grouping for splash), Dragoon (ranged support positioning)

**Team Composition Role:** Mobile ranged specialist for Protoss. Excels in grouped teamfights with Zealot. Corsair's splash and mobility enable hit-and-run tactics with Sentry support.

---

## Terran Heroes

### Marine Hero

**Role:** Ranged Carry  
**Difficulty:** Low  
**Playstyle:** Reliable sustained DPS with good utility

#### How Marine Works

Marine is the **most accessible ranged carry** — straightforward gameplay with high skill ceiling for positioning and ability timing. Marines dominate through consistent, reliable damage.

| Aspect | Details |
|--------|---------|
| **Core Identity** | Standard ranged unit with attack speed and utility |
| **Strengths** | Consistent DPS, attack speed scaling, good early game |
| **Weaknesses** | No mobility tool, moderate durability, vulnerable to burst |
| **Counter By** | Assassins (no escape), long-range burst (Dragoon) |
| **Counters** | Marine beats other melee heroes through sustained fire |

#### Ability Breakdown

1. **Stimpack** (`Stim2`)
   - **Mechanic:** Temporary attack speed and movement speed boost
   - **Usage:** Burst DPS phase, kite away from threats, position aggressively
   - **Trade-off:** Reduces healing received during buff
   - **Duration:** 10 seconds
   - **Playstyle Tip:** Use after enemy cooldowns blow, not at fight start

2. **Toss Grenade** (`TossGrenade2`)
   - **Mechanic:** Projectile that applies area damage
   - **Usage:** Damage grouped enemies, apply area denial
   - **Scaling:** Improves with ranged damage
   - **Playstyle Tip:** Use on clustered targets for maximum value

3. **Radar** (`Radar`)
   - **Mechanic:** Deploy sensor revealing nearby enemies
   - **Usage:** Vision control, detect hidden units, map awareness
   - **Range:** Large detection radius
   - **Scaling:** Detection range improves per level
   - **Playstyle Tip:** Place in key locations for team map control

4. **Voodoo Shield** (`VoodooShield`)
   - **Mechanic:** Grant temporary shield buff
   - **Usage:** Block burst damage, protect self or allies
   - **Duration:** 10 seconds
   - **Cooldown Management:** Use reactively to avoid burst windows

#### Leveling Progression

| Level Range | Damage Increase | Life Increase | Ability Impact | Key Powerspike |
|-------------|-----------------|---------------|---------|---------------|
| **Levels 1-4** | +7 ranged | +30 life | Minor | Level 2 - Radar vision control |
| **Levels 5-7** | +9 ranged | +90 life | Moderate | Level 5 - Stimpack burst becomes relevant |
| **Levels 8-10** | +11 ranged | +120 life | Major | Level 8 - Full utility kit with grenades |

#### Gameplay Progression

- **Level 1-2:** Good early game. Farm safely, place Radar for vision. Use post-kill Stimpack for chase.
- **Level 3-4:** Solid early. Minor damage increase. Radar coverage expanding.
- **Level 5-6:** Power spike. Stimpack + Grenade combo becomes effective. Voodoo Shield timing matters.
- **Level 7-8:** Strong mid-game. Nearly Dragoon's DPS through sustained fire. Radar denies enemy ganks.
- **Level 9-10:** Peak damage. Stimpack becomes devastating with high base damage. Radar coverage critical.

#### Build Recommendations

**Aggressive Stimpack:** Use Stim timing carefully—after enemy cooldowns blow. Grenades on grouped targets. Hold Voodoo for reactionary burst defense.

**Defensive Vision Control:** Place Radar in key choke points and jungle areas. Maintain map awareness to prevent surprise ganks.

**Duo Sustain:** Position where Firebat/Goliath engage. Use Grenades to support area damage. Voodoo on focused allies, not just self.

**Late Game:** Position aggressively where Stimpack + autos can constantly hit enemies. Grenades on groups. Use Radar to maintain vision advantage throughout fights.

#### Common Mistakes

- Using Stimpack too early in fight (should use after enemy cooldowns blow)
- Placing Radar poorly (should cover jungle, base, key chokes)
- Standing still while shooting (easy target for assassins)
- Saving Voodoo only for self (can protect allies from burst)
- Not using Grenades on grouped targets (waste of ability potential)

#### Synergies (Race-Locked)

**Best With:** Firebat (area damage focus), Goliath (crowd control combo), Medic (healing sustain)

**Team Composition Role:** Primary ranged carry for Terran. Sustained DPS enabler. Works with Firebat for grouped fights and benefits from Medic's healing.

---

### Firebat Hero

**Role:** Bruiser  
**Difficulty:** Medium  
**Playstyle:** Durable area damage bruiser who excels in clustered teamfights and sustained presence

#### How Firebat Works

Firebat is the **area damage melee** — unlike Zealot's single-target focus, Firebat deals splash damage hitting groups. Firebat excels when fighting multiple enemies simultaneously.

| Aspect | Details |
|--------|---------|
| **Core Identity** | Melee unit with area fire damage |
| **Strengths** | Area damage, avatar form amplification, teamfight dominance |
| **Weaknesses** | Requires close range, weak against isolated targets, positioning dependent |
| **Counter By** | Kiting (avoid clustered fights), burst (Zealot, Dark Templar) |
| **Counters** | Firebat dominates when enemies group |

#### Ability Breakdown

1. **Lightning Dash** (`ArtanisLightningDash`)
   - **Mechanic:** Dash with AOE damage and stun on impact
   - **Usage:** Initiate fights, interrupt enemy combos, close gap
   - **Scaling:** Damage improves per level
   - **Playstyle Tip:** Lead with dash into groups

2. **Place Turret** (`DutchPlaceTurret`)
   - **Mechanic:** Deploy defensive structure
   - **Usage:** Area denial, turret damage, zone control
   - **Placement:** Flexible positioning
   - **Playstyle Tip:** Place in teamfight chokepoints

3. **Stimpack** (`SuperStimpackNova`)
   - **Mechanic:** Instant combat buff providing attack/move speed and damage
   - **Usage:** Burst phase damage, initiate fights, chase enemies
   - **Duration:** Temporary boost
   - **Scaling:** Improves per level
   - **Playstyle Tip:** Use after initiating to maximize damage output

4. **Avatar** (`Avatar`)
   - **Mechanic:** Transform into powered-up form for duration
   - **Duration:** 10 seconds
   - **Benefits:** +300 life, 80% damage reduction, area damage aura
   - **Usage:** Turn from losing fight to winning, secure kills
   - **Playstyle Impact:** Single ability that changes fights dramatically

#### Leveling Progression

| Level Range | Damage Increase | Life Increase | Ability Impact | Key Powerspike |
|-------------|-----------------|---------------|---------|------|
| **Levels 1-4** | +3/+3 splash | +80 life | Minor | Level 2 - Lightning Dash initiation |
| **Levels 5-7** | +4/+4 splash | +50 life | Moderate | Level 5 - Stimpack burst combo |
| **Levels 8-10** | +6/+6 splash | +180 life | Major | Level 8 - Avatar transformation dominates |

#### Gameplay Progression

- **Level 1-2:** Weak early melee. Use Lightning Dash to initiate, Stimpack for burst.
- **Level 3-4:** Area damage becoming relevant. Place Turrets in key chokepoints.
- **Level 5-6:** Power spike. Stimpack + Dash combo becomes devastating on grouped enemies.
- **Level 7-8:** Strong mid-game. Avatar duration enables extended teamfight presence.
- **Level 9-10:** Peak teamfight damage. Proper Avatar + Stimpack timing wins games.

#### Build Recommendations

**Aggressive Dash-Stim:** Lead with Lightning Dash into groups. Immediately Stimpack for damage surge. Auto-attack through splash.

**Turret Positioning:** Place multiple Turrets in expected enemy paths. Use Avatar when enemies forced into Turret zones.

**Avatar Timing:** Save Avatar for when 2+ enemies grouped. Dash in, Avatar (gain damage reduction + aura), Stimpack, cleanup splash damage.

**Late Game:** Position to hit 3+ enemies with splash. Chain Lightning Dash into groups, activate Stimpack for burst phase, Avatar when focused.

#### Common Mistakes

- Avatar on single target (wastes transformation and aura)
- Using Stimpack before Dash initiation (should combo together)
- Placing Turrets randomly (should control chokepoints strategically)
- Dashing too far without Avatar (dies to focus-fire without damage reduction)
- Forgetting Avatar provides area aura (allies benefit from damage reduction)

#### Synergies (Race-Locked)

**Best With:** Goliath (crowd control crowd control combo), Spectre (burst assassination focus), Medic (sustain enabler)

**Team Composition Role:** Primary melee bruiser for Terran. Area damage forces enemy grouping. Pairs well with Goliath's CC and benefits from Medic's healing.

---

### Goliath Hero

**Role:** Ranged Carry / Off-tank  
**Difficulty:** Medium  
**Playstyle:** Sustained ranged damage with crowd control and utility

#### How Goliath Works

Goliath is the **versatile off-tank ranged dealer** — strong sustained damage, excellent crowd control, and surprising durability. Goliath excels when playing around cooldowns and enabling allies.

| Aspect | Details |
|--------|---------|
| **Core Identity** | Ranged unit with missiles and levitation |
| **Strengths** | Crowd control, dual damage types, utility, good scaling |
| **Weaknesses** | Lower pure damage than Dragoon/Marine, reliant on cooldowns |
| **Counter By** | Excessive mobility (can't stick with kiting), burst |
| **Counters** | Goliath locks down mobile heroes |

#### Ability Breakdown

1. **Missile Pods** (`LokiMissilePods`)
   - **Mechanic:** Launch explosive missiles at enemies
   - **Usage:** Sustained ranged damage, area damage
   - **Scaling:** Improves with level
   - **Playstyle Tip:** Use for consistent pressure

2. **Psionic Lift** (`PsionicLift`)
   - **Mechanic:** Lift target into air, disabling actions temporarily
   - **Duration:** 2.7 seconds lift effect
   - **Usage:** Lock down priority targets, interrupt combos
   - **Scaling:** Duration and effects improve per level
   - **Playstyle Tip:** Use on highest-threat enemy to temporarily remove them

3. **Psionic Shockwave** (`ZHybridPsionicShockwave`)
   - **Mechanic:** Area explosive burst dealing damage
   - **Usage:** Group damage, area denial, burst phase
   - **Scaling:** Improves per level
   - **Playstyle Impact:** Gives Goliath two damage modes

4. **Stimpack** (`StimpackHero2`)
   - **Mechanic:** Temporary attack and movement speed boost
   - **Usage:** Burst DPS phase, kiting from threats, aggressive positioning
   - **Duration:** 10 seconds boost
   - **Scaling:** Bonus per level
   - **Playstyle Tip:** Use after enemy cooldowns blow, not at fight start

#### Leveling Progression

| Level Range | Ranged Damage | CC Effect | Ability Impact | Key Powerspike |
|-------------|---------------|-----------|---------|------------------|
| **Levels 1-4** | +6 ranged | Minor | Minor | Level 2 - Psionic Lift viable |
| **Levels 5-7** | +7 ranged | Moderate | Moderate | Level 5 - CC duration matters |
| **Levels 8-10** | +8 ranged | Major | Major | Level 8 - Full utility kit |

#### Gameplay Progression

- **Level 1-2:** Early game strength. Psionic Lift provides CC setup. Missile Pods for baseline damage.
- **Level 3-4:** Minor scaling. Psionic Lift duration increases. Psionic Shockwave adds area damage.
- **Level 5-6:** Power spike. Control enemy engagement with Psionic Lift CC. Stimpack burst becomes relevant.
- **Level 7-8:** Strong mid-game. Psionic Lift becomes reliable crowd control lockdown.
- **Level 9-10:** Peak utility and damage. Nearly permanent crowd control with Stimpack burst phases.

#### Build Recommendations

**CC-Focused:** Lead with Psionic Lift on highest-threat targets. Team focuses while enemies lifted. Use Psionic Shockwave for area damage follow-up.

**Damage-Focused:** Use Missile Pods for sustained pressure. Psionic Lift to position enemies favorably. Stimpack between Psionic Lift casts for burst phases.

**Utility-Tank:** Position between team and enemies. Psionic Lift disrupts enemy engagement. Psionic Shockwave denies grouped pushes.

**Late Game:** Identify priority targets for Psionic Lift. CC them before they engage your team. Use Stimpack + Missile Pods to clean up fights.

#### Common Mistakes

- Using Psionic Lift on wrong target (should focus highest-threat enemy)
- Not focusing lifted targets (wastes lift duration and lock potential)
- Using Stimpack too early (save for after Psionic Lift wears off)
- Repositioning unpredictably (enemies can predict lift patterns)

#### Synergies (Race-Locked)

**Best With:** Marine (sustained DPS pairing), Firebat (grouped damage focus), Medic (sustain enabler)

**Team Composition Role:** Utility off-tank for Terran. CC-focused playstyle enables Marine and Spectre burst. Coordinates with Medic for team sustain.

---

### Medic Hero

**Role:** Support / Healer  
**Difficulty:** Medium  
**Playstyle:** Mobile support healer providing sustained team healing and status removal

#### How Medic Works

Medic is the **Terran support healer** — focuses on keeping teammates alive through healing and utility. Medic excels at enabling fragile carries through sustained healing and protective spells.

| Aspect | Details |
|--------|---------|
| **Core Identity** | Mobile support unit with healing and cleanse mechanics |
| **Strengths** | Strong healing output, cleanse/status removal, team sustain, decent mobility |
| **Weaknesses** | Low damage, vulnerable to burst, reliant on positioning near allies |
| **Counter By** | Assassins (fragile target), silences/CC (prevents healing) |
| **Counters** | Medic enables vulnerable carries to survive burst through heals |

#### Ability Breakdown

1. **Nano Repair** (`NanoRepair`)
   - **Mechanic:** Restore health to nearby allies over time
   - **Usage:** Sustain team through fights, prevent kills, enable aggressive play
   - **Scaling:** Healing rate improves per level
   - **Playstyle Tip:** Prioritize wounded carries, keep multiple teammates topped up

2. **Caduceus Reactor** (Passive aura)
   - **Mechanic:** Nearby allies gain passive health regeneration
   - **Usage:** Automatic team sustain outside of fights
   - **Scaling:** Regen rate improves per level
   - **Playstyle Impact:** Encourages team grouping and positioning

3. **Flash Bang Grenades** (`NovaGadgetFlashBangGrenades`)
   - **Mechanic:** Throw grenades that stun and damage enemies
   - **Usage:** Apply crowd control, protect teammates, interrupt abilities
   - **Area Effect:** Damages/stuns all in radius
   - **Scaling:** Stun duration and damage improve per level
   - **Playstyle Tip:** Use defensively to save focused allies

4. **Observer Squad Sight** (`ObserverSquadSight`)
   - **Mechanic:** Deploy vision unit or gain shared sight temporarily
   - **Usage:** Extend team vision range, detect hidden enemies
   - **Duration:** Persistent or temporary sight
   - **Scaling:** Sight range improves per level
   - **Playstyle Tip:** Place for map control and early threat detection

5. **Astral Wind** (`ArtanisAstralWind`)
   - **Mechanic:** Grant temporary speed or protective buff to allies
   - **Usage:** Enable positioning, escape threats, protect burst targets
   - **Duration:** Variable buff duration
   - **Scaling:** Buff strength improves per level
   - **Playstyle Impact:** Turns losing fights into winnable engagements

#### Leveling Progression

| Level Range | Healing Output | Utility | Key Powerspike |
|-------------|-----------------|---------|---------|
| **Levels 1-4** | +40 HP/sec | Minor | Level 2 - Observer Squad Sight vision |
| **Levels 5-7** | +110 HP/sec | Moderate | Level 5 - Flash Bang Grenades CC |
| **Levels 8-10** | +140 HP/sec | Major | Level 8 - Astral Wind enables aggression |

#### Gameplay Progression

- **Level 1-2:** Weak early. Stay near teammates, provide Nano Repair. Place Observer Squads for map control.
- **Level 3-4:** Minor healing increase. Flash Bang Grenades provide defensive CC. Caduceus Reactor helps sustain.
- **Level 5-6:** Power spike. Healing becomes reliable sustain. Astral Wind enables allied aggression.
- **Level 7-8:** Strong support. Multiple heals per fight, observer sight coverage. Flash Bang frequently available.
- **Level 9-10:** Elite healer. Constant healing + Astral Wind buffs make carries unkillable. Observer coverage denies enemy ganks.

#### Build Recommendations

**Aggressive Healing:** Position near carries in extended fights. Use Nano Repair proactively before damage. Use Astral Wind to enable allied diving.

**Defensive Crowd Control:** Use Flash Bang Grenades to interrupt enemy burst rotations. Place Observer Squads in jungle to detect ganks early.

**Aura Positioning:** Keep team grouped so Caduceus Reactor affects as many as possible. Position centrally for maximum vision coverage.

**Late Game:** Position where you can see entire team and provide Nano Repair to multiple heroes. Use Astral Wind preemptively before enemy bursts. Observer coverage critical for map security.

#### Common Mistakes

- Using Nano Repair on already safe heroes (waste of healing)
- Poor positioning without team nearby (get caught out by assassins)
- Not placing Observer Squads strategically (should cover jungle and base)
- Using Flash Bang too early (save for enemy burst windows)
- Forgetting Astral Wind can enable aggressive plays (use reactively when team needs to commit)

#### Synergies (Race-Locked)

**Best With:** Marine (sustained DPS support), Firebat (burst combo), Science Vessel (base defense anchor)

**Team Composition Role:** Primary support healer for Terran. Enables aggressive play by sustaining bruisers. Works best with healing-reliant compositions featuring Marine and Firebat.

---

### Spectre Hero (Nova variant)

**Role:** Melee Assassin (Ranged)  
**Difficulty:** High  
**Playstyle:** Cloaked ranged burst assassin with hit-and-run mechanics

#### How Spectre Works

Spectre is the **ranged assassin** — burst damage from range with cloaking for escape and repositioning. Spectre excels at surprising enemies and securing isolated kills.

| Aspect | Details |
|--------|---------|
| **Core Identity** | Invisible ranged burst unit |
| **Strengths** | Long range burst, cloaking, energy-efficient escapes |
| **Weaknesses** | Dies quickly if caught, detection counters, reliant on positioning |
| **Counter By** | Grouped enemies (can't pick isolated targets), detection |
| **Counters** | Spectre eliminates isolated supports and carries |

#### Ability Breakdown

1. **Pinpoint Targeting** (Passive)
   - **Mechanic:** Ranged attacks apply bonus damage
   - **Usage:** Automatic passive, sets up burst potential
   - **Scaling:** Improves with level
   - **Playstyle Impact:** Passive makes even auto-attacks hit hard

2. **Cloaking Field** (`SpectreHeroCloak`)
   - **Mechanic:** Become invisible, drain energy while active
   - **Usage:** Setup ganks, escape after kills, repositioning
   - **Energy Cost:** Consistent drain (check tooltip)
   - **Playstyle Tip:** Cloak for positioning, not for extended periods

3. **Nuke Calldown** (`SpectreNuke`)
   - **Mechanic:** Call down devastating orbital strike
   - **Usage:** Burst damage on location, execute grouped enemies
   - **Scaling:** Damage improves per level
   - **Playstyle Impact:** High-risk high-reward ultimate ability

4. **Ultrasonic Pulse** (`UltrasonicPulse`)
   - **Mechanic:** Apply area stun/disruption to enemies
   - **Usage:** Area control, interrupt fights, setup kills
   - **Radius:** Medium area effect
   - **Scaling:** improves per level
   - **Playstyle Tip:** Use mid-fight to disrupt enemy coordination

5. **Hold Fire** (`SpectreHoldFire`)
   - **Mechanic:** Prevent automatic attacks, hold position
   - **Usage:** Precision positioning, avoid triggering cloak loss
   - **Playstyle Impact:** Control over auto-attacks for stealth

6. **Weapons Free** (`SpectreWeaponsFree`)
   - **Mechanic:** Release weapons lock and resume attacking
   - **Usage:** Resume combat after Hold Fire
   - **Playstyle Impact:** Toggle control for positioning

7. **Obliterate** (`Obliterate`)
   - **Mechanic:** Single-target execution ability
   - **Usage:** Finish low-health targets, burst priority enemies
   - **Scaling:** Damage improves per level
   - **Playstyle Tip:** Use on isolated targets for maximum impact

#### Leveling Progression

| Level Range | Ranged Damage | Ability Impact | Key Powerspike |
|-------------|---------------|---------|----------|
| **Levels 1-4** | +5 ranged | Minor | Level 2 - Cloaking gank potential |
| **Levels 5-7** | +8 ranged | Moderate | Level 5 - Nuke + Obliterate burst |
| **Levels 8-10** | +10 ranged | Major | Level 8 - Execute isolated targets |

#### Gameplay Progression

- **Level 1-2:** Weak early melee. Cloak for positioning, apply auto-attack burst, escape.
- **Level 3-4:** Increasing burst potential. Target weak/isolated heroes. Use Hold Fire to avoid triggering cloak.
- **Level 5-6:** Power spike. Nuke Calldown one-shots isolated supports. Obliterate finishes low-health targets.
- **Level 7-8:** Deadly assassin. Ultrasonic Pulse disrupts enemy coordination. Can chain kills together.
- **Level 9-10:** Instant kill specialist. Hold Fire + Weapons Free control enables perfect bursts. Proper positioning = guaranteed kills.

#### Build Recommendations

**Aggressive Ganking:** Hunt isolated heroes with cloak. Lead with Nuke Calldown or Ultrasonic Pulse. Auto-attack burst, Obliterate to finish. Escape immediately.

**Precision Positioning:** Use Hold Fire to prevent auto-attacks from revealing cloak. Reposition, use Weapons Free to burst. Escape after.

**Area Disruption:** Use Ultrasonic Pulse in mid-fight to disrupt enemy coordination and setup kills on vulnerable targets.

**Late Game:** Scout enemy positions using cloak. Identify isolated targets. Nuke Calldown for burst, Obliterate to finish. Chain kills on separated enemies.

#### Common Mistakes

- Auto-attacking from obvious positions (reveals cloak location)
- Staying in fights after burst (should leave immediately)
- Cloaking without a repositioning plan (wasting energy)
- Not using Hold Fire before critical bursts (unintended auto-attacks ruin stealth)
- Overcommitting to kills when team can't follow up (dies to counter-engagement)

#### Synergies (Race-Locked)

**Best With:** Marine (burst combo pairing), Goliath (crowd control setup), Medic (healing support)

**Team Composition Role:** Primary ranged assassin for Terran. Mobile burst trader. Synergizes with Goliath's CC and Medic's healing for safe aggressive plays.

---

### Science Vessel (Base Defender)

**Role:** Base Defender  
**Difficulty:** Medium  
**Playstyle:** Supporting base defense through repair, utility spells, and area denial

#### How Science Vessel Works

Science Vessel is the **Terran base defender** — focuses on protecting structures and teammates through repair beams and support utilities. SV excels at enabling defensive play and keeping allied presence alive during base attacks.

| Aspect | Details |
|--------|---------|
| **Core Identity** | Support vessel with repair and utility abilities |
| **Strengths** | Structure repair, team sustain, defensive positioning, good range |
| **Weaknesses** | Low damage output, vulnerable to focused fire, slow movement |
| **Counter By** | Assassins (fragile target), mobility-based burst |
| **Counters** | Science Vessel denies structure destruction through repairs |

#### Ability Breakdown

1. **Repair Beam** (Primary tool)
   - **Mechanic:** Restore health to allies or structures over time
   - **Usage:** Keep structures alive during attacks, heal injured allies
   - **Scaling:** Improves repair rate per level
   - **Playstyle Tip:** Prioritize structures when being attacked

2. **Repair Drone Hangar** (`ScienceVesselRepairDroneHanger`)
   - **Mechanic:** Deploy repair drones to continuously repair friendly structures
   - **Usage:** Keep multiple structures alive simultaneously, autonomous healing
   - **Scaling:** Drone quality and quantity improve per level
   - **Playstyle Tip:** Position hangars near critical structures

3. **Emergency Thrusters** (`ScienceVesselEmergencyThrusters`)
   - **Mechanic:** Temporary movement speed boost for repositioning
   - **Usage:** Reposition under fire, escape threats, respond to multiple attacks
   - **Duration:** Temporary boost
   - **Playstyle Impact:** Enables rapid base response

4. **EMP Shockwave** (`Irradiate`)
   - **Mechanic:** Area effect that damages and disrupts enemy energy/shields
   - **Usage:** Disable enemy casters, apply area pressure, damage grouped enemies
   - **Scaling:** Improves with level
   - **Playstyle Impact:** Weakens enemy spell casting near base

5. **Turret Lab** (`TurretLab`)
   - **Mechanic:** Deploy defensive turret structure
   - **Usage:** Static defense, area denial, automatic damage on approaching enemies
   - **Placement:** Flexible positioning
   - **Playstyle Tip:** Place in choke points and base entrances

6. **Defensive Positioning**
   - **Mechanic:** Maintain position near critical structures
   - **Usage:** Always have repair beam ready for emergencies
   - **Playstyle Tip:** Position where you can reach multiple structures

#### Leveling Progression

| Level Range | Repair Rate | Utility | Key Powerspike |
|-------------|---------|---------|---------|
| **Levels 1-4** | +50 HP/sec | Minor | Level 2 - Turret Lab placement |
| **Levels 5-7** | +110 HP/sec | Moderate | Level 5 - Repair Drone Hangar drones |
| **Levels 8-10** | +130 HP/sec | Major | Level 8 - Full defensive suite |

#### Gameplay Progression

- **Level 1-2:** Early support. Keep main structures alive with Repair Beam. Deploy Turret Lab in chokepoints.
- **Level 3-4:** Repair rate increasing. Place Turret Labs strategically. Emergency Thrusters enable rapid repositioning.
- **Level 5-6:** Power spike. Repair Drone Hangar provides autonomous structure healing. EMP Shockwave disrupts enemy casters.
- **Level 7-8:** Strong defender. Multiple repair sources sustain base. Turrets deter pushes. Emergency Thrusters rapid-response capability.
- **Level 9-10:** Nearly impossible raid victim. Constant repair from multiple sources. EMP Shockwave weakens enemy burst. Turret coverage denies entry.

#### Build Recommendations

**Structure Protection:** Deploy Repair Drone Hangars near critical structures for autonomous healing. Use Repair Beam for emergency top-ups. Place Turret Labs at base entrances and chokes.

**Threat Response:** Position centrally where you can reach compromised structures quickly. Emergency Thrusters for rapid repositioning to threats. EMP Shockwave to weaken enemy casters.

**Area Denial:** Turret Lab coverage makes base nearly impenetrable. Combine with Repair Drone drones for layered defense. EMP burst to prevent enemy casting near base.

**Base Coordination:** Monitor structure health constantly. Preemptively deploy Repair Drone Hangars before expected pushes. Use Emergency Thrusters to respond to multi-directional attacks.

#### Common Mistakes

- Abandoning base to roam (defense is priority job)
- Overextending away from repairable structures
- Not placing Repair Drone Hangars proactively (should anticipate damage)
- Turret Lab placement randomly (should control chokepoints strategically)
- Forgetting EMP Shockwave weakens enemy spell-casting (should use reactively on caster-heavy teams)

#### Synergies (Race-Locked)

**Best With:** Firebat (area damage focus), Marine (sustained DPS), Medic (healing anchor)

**Team Composition Role:** Primary base defender for Terran. Science Vessel enables aggressive phases by securing base. Coordinates with Firebat for area control and Medic for team sustain.

---

## Zerg Heroes

### Zergling Hero

**Role:** Melee Assassin  
**Difficulty:** Low  
**Playstyle:** Mobile melee burst assassin who excels through rapid engagements and repositioning resets

#### How Zergling Works

Zergling is the **mobile melee carry** — high movement speed allows aggressive positioning and rapid repositioning. Zergling excels through constant engagement and re-engagement with resets.

| Aspect | Details |
|--------|---------|
| **Core Identity** | Fast melee unit with chase and mobility |
| **Strengths** | Movement speed, good early game, evasion/repositioning |
| **Weaknesses** | Lower raw damage than Zealot, fragile to burst, reliant on proper spacing |
| **Counter By** | Crowd control (negates mobility), ranged burst (kited from range) |
| **Counters** | Zergling dominates other mobile melee through superior stats |

#### Ability Breakdown

1. **Raptor Charge** (`HotSRaptorCharge`)
   - **Mechanic:** Mobile dash toward target with damage
   - **Usage:** Close gaps, chase fleeing enemies, repositioning
   - **Scaling:** Damage per level
   - **Playstyle Tip:** Use multiple times per fight to chain engagements

2. **Morph to Baneling** (`Baneling`)
   - **Mechanic:** Transform into area damage form for duration
   - **Duration:** 8 seconds
   - **Benefits:** Increases splash damage significantly
   - **Usage:** Area damage phase in teamfights, cleanup multiple weak targets
   - **Playstyle Impact:** Provides temporary transformation for flexibility

3. **Poison Nova** (`PoisonNova`)
   - **Mechanic:** Apply slowing cloud to enemies nearby
   - **Usage:** Area denial, reduce enemy repositioning in fights
   - **Scaling:** Slow strength per level
   - **Playstyle Tip:** Use to trap enemies in kill zones

4. **Zergling Mine** (`ZerglingMine`)
   - **Mechanic:** Place explosive trap that detonates on enemy contact
   - **Usage:** Area denial, burst damage on grouped enemies
   - **Scaling:** Damage improves per level
   - **Playstyle Tip:** Place in expected enemy paths and chokes

#### Leveling Progression

| Level Range | Damage | Speed | Ability Impact | Key Powerspike |
|-------------|--------|-------|---------|----------|
| **Levels 1-4** | +5 melee | +1% move | Minor | Level 2 - Raptor Charge combos |
| **Levels 5-7** | +7 melee | +2% move | Moderate | Level 5 - Baneling transform + mines |
| **Levels 8-10** | +8 melee | +3% move | Major | Level 8 - Unchase-able with mines |

#### Gameplay Progression

- **Level 1-2:** Acceptable early. Raptor Charge combo, fight, exit. Place mines in expected paths.
- **Level 3-4:** Movement speed helps kiting and repositioning. Chase low-health targets. Mine placement strategy.
- **Level 5-6:** Power spike. Baneling transform + Poison Nova area denial. Mines for area control.
- **Level 7-8:** Strong chaser. Place mines ahead of chases. Enemy teams split trying to avoid mines.
- **Level 9-10:** Apex mobile assassin. Chain Raptor Charges around mines. Baneling splash through grouped enemies.

#### Build Recommendations

**Aggressive Chasing:** Use Raptor Charge multiple times per fight for repositioning. Place Zergling Mines in choke points and expected escape routes. Never let enemies escape.

**Area Control:** Place mines defensively near base and chokes. Offensively place mines in enemy territory to deny positioning.

**Transform Timing:** Save Baneling transform for teamfight clusters. Activate, auto-attack splashing. Position mines to block enemy escape.

**Late Game:** Plant mines ahead of engagements to control enemy movement. Lead with Raptor Charge + Poison Nova for area denial. Activate Baneling in center of grouped enemies.

#### Common Mistakes

- Using Raptor Charge into focused enemies (overextend without exit plan)
- Not placing Zergling Mines strategically (should control chokes and paths)
- Using Baneling transform on single targets (should be for grouped enemies)
- Forgetting Poison Nova locks enemies (use to trap in mine fields)

- Using Raptor Charge into 5 enemies (get focus-fired)
- Transforming 1v1 (you want pure melee in duels)
- Overextending beyond team backup
- Poison Nova poorly timed (should lock enemies for team)

#### Synergies (Race-Locked)

**Best With:** Defiler (burst assassination focus), Ultralisk (melee grouping), Brood Queen (healing support)

**Team Composition Role:** Primary melee assassin for Zerg. Mobile burst trader. Synergizes with Defiler's crowd control and Brood Queen's healing.

---

### Hydralisk Hero

**Role:** Ranged Carry / Versatile  
**Difficulty:** Medium  
**Playstyle:** Dual-attack ranged carry with crowd control and movement support

#### How Hydralisk Works

Hydralisk is the **versatile ranged dealer** — dual attack system (ranged + melee) provides flexibility. Hydralisk excels when enemies are grouped and crowd control is needed.

| Aspect | Details |
|--------|---------|
| **Core Identity** | Dual attack ranged unit with crowd control |
| **Strengths** | Dual damage types, crowd control, movement support, good scaling |
| **Weaknesses** | Moderate sustained damage compared to pure ranged, reliant on positioning |
| **Counter By** | Burst (vulnerable isolated), positioning disruption |
| **Counters** | Hydralisk locks down mobile targets |

#### Ability Breakdown

1. **Impale** (Melee attack special)
   - **Mechanic:** Apply piercing melee attack with focus damage
   - **Usage:** Anti-armor through grouped enemies, apply cleave
   - **Scaling:** Improves with level
   - **Playstyle Tip:** Use when enemies grouped

2. **Hydralisk Frenzy** (`HydraliskFrenzy`)
   - **Mechanic:** Self-buff increasing attack speed and movement speed
   - **Duration:** Variable
   - **Usage:** Team fight or chase phase, burst damage window
   - **Scaling:** Improves per level
   - **Playstyle Tip:** Use mid-fight for momentum shifts

3. **Stunning Blast** (Crowd control ability)
   - **Mechanic:** Apply stun to target area
   - **Duration:** 2 seconds
   - **Usage:** Interrupt enemy abilities, setup kills, create escape opportunities
   - **Playstyle Tip:** Target high-threat enemies being focused

4. **Ensnare** (Crowd control ability)
   - **Mechanic:** Apply slowing effect to target
   - **Duration:** 2 seconds  
   - **Usage:** Reduce enemy damage output through slower movement, enable chasing
   - **Playstyle Tip:** Use on mobile threats or retreating enemies

5. **Noxious Creep** (`NoxiousCreep`)
   - **Mechanic:** Create area of poisoned ground damage and slowing
   - **Usage:** Area denial, zone control, reduce enemy teamfight presence
   - **Duration:** Persistent area effect
   - **Scaling:** Damage and slow improve per level
   - **Playstyle Tip:** Place in chokes where enemies must pass through

#### Leveling Progression

| Level Range | Ranged | Melee | CC Impact | Key Powerspike |
|-------------|--------|-------|---------|----------|
| **Levels 1-4** | +5 ranged | +2 melee | Minor | Level 2 - Dual attacks + CC |
| **Levels 5-7** | +6 ranged | +3 melee | Moderate | Level 5 - Noxious Creep area denial |
| **Levels 8-10** | +7 ranged | +3 melee | Major | Level 8 - Full CC utility kit |

#### Gameplay Progression

- **Level 1-2:** Decent early through dual attacks and Stunning Blast CC.
- **Level 3-4:** Minor scaling. Ensnare duration increases. Impale cleave matters.
- **Level 5-6:** Power spike. Noxious Creep creates area denial zones. Frenzy burst timing.
- **Level 7-8:** Strong mid-game. Crowd control becomes reliable. Creep placement strategy matters.
- **Level 9-10:** Apex versatile carry. All CC skills maxed. Full area denial coverage.

#### Build Recommendations

**CC-Focused:** Use Stunning Blast on priority targets, Ensnare on high-threat enemies. Place Noxious Creep in chokes to deny positioning. Team focuses CCd targets.

**Damage-Focused:** Use Hydralisk Frenzy during fight start for momentum. Auto-attack with dual damage system. Use Noxious Creep for utility area denial.

**Area Denial:** Place Noxious Creep preemptively in expected fight locations. Use Ensnare + Creep to trap enemies. Stunning Blast interrupts attempts to leave zones.

**Late Game:** Position to apply both melee and ranged attacks on grouped enemies. Place Creep strategically. CC threats, damage on groups.

#### Common Mistakes

- Using all CC on same target (should spread CC among threats)
- Not placing Noxious Creep strategically (should control chokes proactively)
- Impale positioning too far (melee component needs range)
- Forgetting Frenzy positioning (should use after engaged, not before)

#### Synergies (Race-Locked)

**Best With:** Zergling (melee burst focus), Brood Queen (healing sustain), Defiler (crowd control setup)

**Team Composition Role:** Primary ranged carry for Zerg. Dual attack flexibility enables team composition options. Works with Zergling for burst and Brood Queen for sustain.

---

### Brood Queen Hero

**Role:** Support / Sustain  
**Difficulty:** Medium  
**Playstyle:** Team healing and area denial support with energy emphasis

#### How Brood Queen Works

Brood Queen is the **Zerg support specialist** — exceptionally strong team healing and area denial through spawn mechanics. BQ excels when healing multiple teammates through sustained damage.

| Aspect | Details |
|--------|---------|
| **Core Identity** | Support unit with healing and spawn mechanics |
| **Strengths** | Best healing in game, spawn army, area denial, team sustain |
| **Weaknesses** | Low damage, fragile, mana-reliant, positioning dependent |
| **Counter By** | Assassins (fragile target), burst (can't heal through it), mana drain |
| **Counters** | Brood Queen enables fragile carries through constant healing |

#### Ability Breakdown

1. **Burst Heal** (`QueenBurstHeal2`)
   - **Mechanic:** Applied healing over time (HoT)
   - **Duration:** 2.5 seconds
   - **Healing:** 10 life per tick (0.5s intervals) = 50 total
   - **Usage:** Heal allies during fights, sustained recovery
   - **Scaling:** Improves per level
   - **Playstyle Tip:** Use before burst damage expected

2. **Primal Gas Cloud** (`PrimalGasCloud`)
   - **Mechanic:** Area denial cloud that slows enemies
   - **Duration:** Variable
   - **Effect:** -20% movement and attack speed
   - **Usage:** Area denial in chokepoints, protect positioning
   - **Playstyle Tip:** Place where enemies must pass through

3. **Spawn Broodlings** (`QueenMPSpawnBroodlings`)
   - **Mechanic:** Create allied units for assault or defense
   - **Usage:** Army presence, extra damage/pressure
   - **Scaling:** Improves with level
   - **Playstyle Impact:** Adds presence without constant spawning cost

4. **Ensnare** (`QueenMPEnsnare`)
   - **Mechanic:** Apply immobilizing effect to target enemy
   - **Duration:** Duration scales with level
   - **Usage:** Lock down high-priority targets, prevent escapes
   - **Scaling:** Duration and potency improve per level
   - **Playstyle Tip:** Use on threats targeting your carries

5. **Building Construct** (`QueenBuild`)
   - **Mechanic:** Rapidly construct nearby Zerg structures
   - **Usage:** Accelerate base development, rebuild destroyed structures
   - **Scaling:** Build speed improves per level
   - **Playstyle Impact:** Enables defensive rebuilding

#### Leveling Progression

| Level Range | Healing | Utility | Key Powerspike |
|-------------|---------|---------|---------|
| **Levels 1-4** | +25 HP/sec | Minor | Level 2 - Burst Heal matters |
| **Levels 5-7** | +70 HP/sec | Moderate | Level 5 - Ensnare + Gas Cloud combo |
| **Levels 8-10** | +150 HP/sec | Major | Level 8 - Full healing + CC suite |

#### Gameplay Progression

- **Level 1-2:** Weak early support. Positioning matters. Use Burst Heal preemptively.
- **Level 3-4:** Mild healing scaling. Place Gas Cloud defensively. Ensnare basics matter.
- **Level 5-6:** Power spike. Team healing keeps multiple allies alive. Ensnare duration increases.
- **Level 7-8:** Strong support. Sustained healing enables extended fights. Building Construct enables base rebuilding.
- **Level 9-10:** Apex healer. Nearly unkillable carries with healing + Gas Cloud protection + Ensnare CC.

#### Build Recommendations

**Aggressive Healing:** Dive into teamfights when multiple allies wounded. Burst Heal multiple targets. Use Ensnare on threats.

**Defensive Positioning:** Position behind main grouping. Place Gas Cloud on approaches. Use Building Construct to repair base while fighting.

**CC Combo:** Use Ensnare on highest-threat enemy. Team focuses while locked. Place Gas Cloud to prevent escape routes.

**Late Game:** Anticipate burst damage on carries. Pre-heal before enemy combos. Gas Cloud blocks chases. Ensnare the threat. Building Construct keeps base alive.

#### Common Mistakes

- Using healing when no damage incoming (mana waste)
- Standing isolated from team (no one to heal, fragile target)
- Not using Ensnare on priority threats (biggest danger to carries)
- Gas Cloud placement randomly (should control chokepoints strategically)
- Forgetting Building Construct (should repair while safe, not mid-fight)

#### Synergies (Race-Locked)

**Best With:** Zergling (burst assassination), Hydralisk (sustained DPS), Nydalist (base defense anchor)

**Team Composition Role:** Primary support healer for Zerg. Enables aggressive play through sustained healing. Works with melee-heavy Zerg compositions leveraging Zergling + Ultralisk burst.

---

### Ultralisk Hero (Torrasque variant)

**Role:** Bruiser  
**Difficulty:** Medium  
**Playstyle:** Durable frontline bruiser with area damage and late-game air attack capability

#### How Ultralisk Works

Ultralisk is the **tanky melee carry** — highest durability of melee heroes with area damage and late-game air attack. Ultralisk excels through sustained presence and area denial in fights.

| Aspect | Details |
|--------|---------|
| **Core Identity** | Durable melee unit with area damage and scaling |
| **Strengths** | High health pool, splash damage, air attacks at level 6+, scaling |
| **Weaknesses** | Reliant on groups for area damage, vulnerable to kiting, positioning dependent |
| **Counter By** | Ranged kiting (avoid group fights), separation from allies |
| **Counters** | Ultralisk dominates grouped enemy melee |

#### Ability Breakdown

1. **Monarch Blades** (`MonarchBlades2`)
   - **Mechanic:** Temporary movement speed and attack power buff
   - **Usage:** Chase phase, teamfight momentum, area damage amplification
   - **When Unlocked:** Levels 1+
   - **Scaling:** Improves per level
   - **Playstyle Tip:** Use when surrounded by enemies for maximum splash impact

2. **Frenzied Form** (`Frenzied2`)
   - **Mechanic:** Self-buff increasing damage output
   - **When Unlocked:** Levels 1+, gains air attack at level 6+
   - **Air Attack:** Allows attack flying units (Mothership Core, Science Vessel)
   - **Usage:** Teamfight dominance, enable attacking flying heroes
   - **Playstyle Impact:** Level 6+ massive power spike (can finally hit flying targets)

3. **Burrow Charge** (If applicable)
   - **Mechanic:** Mobile charge through terrain
   - **Usage:** Repositioning, interrupt enemy abilities
   - **Scaling:** Improves per level
   - **Playstyle Tip:** Use for surprise engages

#### Leveling Progression

| Level Range | Melee | Splash | Life | Key Powerspike |
|-------------|-------|--------|------|-----------------|
| **Levels 1-4** | +5 melee | +2 splash | +80 HP | Level 2 - Area damage matters |
| **Levels 5-7** | +7 melee | +3 splash | +110 HP | Level 5 - Health scaling |
| **Levels 6** | (no bonus) | (no bonus) | (same) | **AIR ATTACK UNLOCKED** |
| **Levels 8-10** | +8 melee | +3 splash | +200 HP | Level 8 - Can duel anyone |

#### Gameplay Progression

- **Level 1-2:** Acceptable early through area damage.
- **Level 3-4:** Increasing durability. Area damage more relevant.
- **Level 5-6:** Power spike. Health scaling & air attacks become available.
- **Level 7-8:** Strong mid-game. Nearly unkillable unit.
- **Level 9-10:** Apex damage and durability. Proper grouping = wins.

#### Build Recommendations

**Aggressive Grouping:** Execute Monarch Blades in center of enemy team. Area damage everyone.

**Sustained Presence:** Keep melee groups together. Tank damage through health pool. Area damage applies automatically.

**Late Game:** Position such that you're hitting entire enemy team. Splash damage and air attacks eliminate flying units.

#### Common Mistakes

- Fighting solo (area damage needs groups)
- Using Monarch Blades poorly timed (use when surrounded)
- Overextending past shield/support
- Forgetting air attack at level 6+

#### Synergies (Race-Locked)

**Best With:** Zergling (melee grouping for splash), Hydralisk (sustained DPS support), Brood Queen (healing sustain)

**Team Composition Role:** Primary bruiser for Zerg. Area damage forces enemy grouping. Pairs well with Zergling for melee focus and benefits from Brood Queen's healing.

---

### Defiler Hero

**Role:** Support / Caster  
**Difficulty:** High  
**Playstyle:** Energy-focused control caster with burst damage, crowd control and area denial

#### How Defiler Works

Defiler is the **energy-focused assassin caster** — relies on energy management and ability timing rather than auto-attacks. Defiler excels through burst ability combos and crowd control application.

| Aspect | Details |
|--------|---------|
| **Core Identity** | Energy-based caster with burst and deny mechanics |
| **Strengths** | High burst damage, crowd control, area denial, energy scaling |
| **Weaknesses** | Energy reliant, vulnerable without abilities, positioning critical |
| **Counter By** | Mana drain (negates abilities), ranged burst, positioning lockdown |
| **Counters** | Defiler silences and denies ability-reliant heroes |

#### Ability Breakdown

1. **MP Plague** (`DefilerMPPlague`)
   - **Mechanic:** Damage over time that drains enemy energy (mana)
   - **Duration:** 10 seconds
   - **Period:** 0.5 seconds per tick
   - **Effect:** -100% energy regeneration while active
   - **Usage:** Silence enemy heroes (prevents ability casting), apply DoT
   - **Scaling:** Damage improves per level
   - **Playstyle Tip:** Target ability-reliant enemies (supports, casters)

2. **Consume** (`DefilerMPConsume`)
   - **Mechanic:** Drain enemy unit to regain energy and health
   - **Usage:** Sustain energy for ability spam, remove threatening units
   - **Target:** Can target ally or enemy units for different effects
   - **Scaling:** Energy/health restore improves per level
   - **Playstyle Tip:** Use on low-health allies proactively or enemy units reactively

3. **Dark Swarm** (`DefilerMPDarkSwarm`)
   - **Mechanic:** Area of effect that provides damage reduction
   - **Duration:** Varies
   - **Reduction:** 40% damage reduction in swarm area
   - **Usage:** Team heal/protect through mitigation, reposition in swarm safety
   - **Playstyle Tip:** Place where allies damaged, move group into swarm

4. **Insect Infestation** (`InfestorConsumption`)
   - **Mechanic:** Control or damage enemy unit
   - **Usage:** Disable high-priority threats temporarily, apply burst damage
   - **Duration:** Variable control duration
   - **Scaling:** Improves per level
   - **Playstyle Tip:** Use on priority targets being focused

5. **Leech** (`Leech`)
   - **Mechanic:** Applied silence to target hero
   - **Duration:** Variable
   - **Effect:** Prevents ability casting
   - **Usage:** Disable priority threats, prevent ults
   - **Playstyle Tip:** Target hero about to use important ability

6. **Frenzy**
   - **Mechanic:** Self-buff increasing energy generation and damage
   - **Usage:** Enable ability spam in fights, burst phase
   - **Scaling:** Improves per level
   - **Playstyle Tip:** Use when maximum ability usage needed

#### Leveling Progression

| Level Range | Spell Damage | Energy | CC Impact | Key Powerspike |
|-------------|--------------|--------|---------|----------|
| **Levels 1-4** | +4 ranged | +20 energy | Minor | Level 2 - MP Plague combo |
| **Levels 5-7** | +5 ranged | +30 energy | Moderate | Level 5 - Silence + CC spam |
| **Levels 8-10** | +7 ranged | +40 energy | Major | Level 8 - Delete heroes with combo |

#### Gameplay Progression

- **Level 1-2:** Decent early through crowd control. MP Plague silences key abilities.
- **Level 3-4:** Increasing burst potential. Consume sustains energy. Leech prevents enemy ults.
- **Level 5-6:** Power spike. Energy allows ability spam. Insect Infestation + Leech disable threats.
- **Level 7-8:** Strong mid-game. Silence becomes constant. Dark Swarm + Frenzy protect team plays.
- **Level 9-10:** Apex caster. Proper positioning + energy management = burst combo kills.

#### Build Recommendations

**Energy Spam Combo:** Maximize energy through Consume. Use MP Plague + Leech spam on priority targets. Frenzy for extended ability sequences.

**Area Denial:** Dark Swarm protect team positioning and retreat routes. Plague on threats to prevent ability casting.

**CC Control:** Leech on ult-about-to-be-cast. Insect Infestation on high-priority targets being focused. Consume for energy sustain.

**Late Game:** Identify priority targets. MP Plague to silence. Insect Infestation to control. Leech ult prevention. Dark Swarm team protection. Frenzy for burst phase.

#### Common Mistakes

- Using abilities on non-priority targets (wastes energy)
- Overextending for silence without team backup
- Dark Swarm placement poorly (should protect team retreat routes)
- Not managing energy (should use Consume proactively)
- Forgetting Frenzy enables extended ability sequences

#### Synergies (Race-Locked)

**Best With:** Zergling (burst assassination setup), Hydralisk (crowd control combo), Brood Queen (healing anchor)

**Team Composition Role:** Unique caster specialist for Zerg. Energy-focused control enables burst plays. Synergizes with Zergling's mobility and Hydralisk's CC.

---

### Nydalist (Base Defender)

**Role:** Base Defender  
**Difficulty:** Medium-High  
**Playstyle:** Zerg base defender specializing in spawn mechanics and area denial

#### How Nydalist Works

Nydalist is the **Zerg base defender** — controls base defense through spawning mechanics and area denial. Nydalist excels at overwhelming attacking forces with spawned units and denying base encroachment.

| Aspect | Details |
|--------|---------|
| **Core Identity** | Base defender with spawn army generation |
| **Strengths** | Spawns allied units, area denial, scaling defense force |
| **Weaknesses** | Reliant on spawned units for damage, vulnerable if caught out |
| **Counter By** | Area of effect damage (kills spawns), mobile burst (kills Nydalist) |
| **Counters** | Nydalist denies base pushes through spawned army |

#### Ability Breakdown

1. **Spawn Mechanics** (Primary tool)
   - **Mechanic:** Generate allied units to defend base
   - **Usage:** Overwhelm attacking forces with numbers
   - **Scaling:** Spawned unit quality improves per level
   - **Playstyle Tip:** Spawn before enemy push arrives

2. **Nydus Canal** (Mobility)
   - **Mechanic:** Create warp points for rapid base positioning
   - **Usage:** Respond to multiple attacks simultaneously
   - **Scaling:** Number of active canals improves per level
   - **Playstyle Tip:** Place canals at key defensive positions

3. **Dig** (`Dig`)
   - **Mechanic:** Tunnel into terrain for concealment
   - **Usage:** Hide near spawn locations, surprise attackers, reposition
   - **Duration:** Variable
   - **Playstyle Tip:** Dig before enemyarrival for defensive surprise

4. **Spawn Hydralisk Charge** (`UseChargeSpawnHydralisk`)
   - **Mechanic:** Spawn charged Hydralisk unit with special abilities
   - **Usage:** Generate elite garrison unit for base defense
   - **Scaling:** Unit quality improves per level
   - **Playstyle Tip:** Use for critical defensive moments

5. **Empower Building** (`EmpowerZergBuilding`)
   - **Mechanic:** Buff nearby structures with enhanced defense
   - **Usage:** Strengthen structures under attack, increase defense output
   - **Scaling:** Buff strength improves per level
   - **Playstyle Tip:** Preemptively boost structures before raids

6. **Static Presence**
   - **Mechanic:** Position near spawning locations
   - **Usage:** Maintain constant threat near base
   - **Playstyle Impact:** Discourages direct base attacks

#### Leveling Progression

| Level Range | Spawn Quality | Unit Count | Ability Impact | Key Powerspike |
|-------------|---------------|-----------|---------|----------|
| **Levels 1-4** | Basic units | 2-3 units | Minor | Level 2 - Dig + spawns |
| **Levels 5-7** | Improved stats | 3-4 units | Moderate | Level 5 - Spawn Hydralisk Charge |
| **Levels 8-10** | Elite units | 4-5 units | Major | Level 8 - Unstoppable base defense |

#### Gameplay Progression

- **Level 1-2:** Early defense. Basic spawns come online. Use Dig for positioning near spawns.
- **Level 3-4:** Spawns becoming tougher. Defend light pressure. Empower Building increases structure defense.
- **Level 5-6:** Power spike. Spawn Hydralisk Charge units are elite. Nydus Canals enable rapid response.
- **Level 7-8:** Strong defender. Multiple spawn rotations. Dig for tactical repositioning. Empower Building on critical structures.
- **Level 9-10:** Unstoppable base defense. Army continuously replenishes. All utilities (Dig, Canals, Empower) mattering.

#### Build Recommendations

**Defensive Focus:** Keep base defended. Spawn preemptively before expected attacks. Place Nydus Canals at key defensive points for rapid repositioning.

**Structure Protection:** Empower Building on critical towers/hatcheries before raids. Use Dig to hide near spawn points. Spawn Hydralisk Charge for elite defensive units.

**Area Denial:** Position Nydus Canals to cover multiple base entrances. Use Dig to surprise attackers. Spawn units to overwhelm invaders.

**Base Coordination:** Monitor base constantly. Pre-spawn before attacks arrive. Empower structures preemptively. Use Canals to position near threats.

#### Common Mistakes

- Spawning reactively (units don't arrive in time, die immediately)
- Abandoning base to assist team (spawning needs your presence)
- Placing Nydus Canals poorly (should connect key threat points)
- Not Empowering structures preemptively (should boost before push arrives)
- Forgetting Dig provides surprise positioning value near base

#### Synergies (Race-Locked)

**Best With:** Ultralisk (melee grouping focus), Hydralisk (sustained DPS support), Brood Queen (healing sustain)

**Team Composition Role:** Primary base defender for Zerg. Nydalist enables aggressive phases by securing base. Coordinates with Ultralisk for area control and Brood Queen for team sustain.

---

## General Mechanics

### Experience & Leveling

- Heroes start at level 1
- Gain XP from: killing enemy heroes, destroying structures, killing minions
- Level 10 is maximum
- Stat progression is **permanent per level** — no resets

### Crowd Control Priority

When multiple enemies use CC, targets are controlled in priority order:
1. Stun > Slow > Other effects
2. First CC application wins
3. Overlapping CC extends duration

### Ability Cooldowns

Most hero abilities have cooldowns. Managing cooldown windows is key to winning fights:
- **Short cooldown** (3-5s): Can spam throughout fight
- **Medium cooldown** (8-15s): Use tactically per fight phase
- **Long cooldown** (20s+): Save for pivotal moments

### Energy/Mana Systems

- **Protoss heroes** use shields (don't typically have energy costs)
- **Terran heroes** use life/armor (most pure damage cost)
- **Zerg heroes** use energy (Defiler, Brood Queen especially; reliant on management)

Heroes with energy need careful resource management:
- Low energy = can't cast abilities
- Energy regenerates slowly
- Some abilities drain energy (Spectre cloaking, etc.)

### Positioning

**Core Principle:** Positioning determines fight outcomes more than stats

- **Backline:** Ranged carries, supports (safe from melee)
- **Midline:** Utility heroes, off-tanks (between groups)
- **Frontline:** Melee carries, tanks (absorb damage, initiate)

Heroes out of position die quickly regardless of stats.

---

## Progression Systems

### Hero Progression (Veterancy)

Heroes use race-specific leveling behaviors:
- **Protoss** (`ProtossLevels`): Shield-focused scaling
- **Terran** (`TerranLevels`): Life + attack speed scaling
- **Zerg** (`ZergLevels`): Life + movement speed scaling

Each tier increases different stats:
- **Early (1-4):** Base damage increases
- **Mid (5-7):** Secondary stat increases (shields, attack speed, etc.)
- **Late (8-10):** Minor damage + significant survival improvements

### Equipment/Builds

While not explicitly detailed here, consider hero synergies and positioning recommendations as "builds":
- **Aggressive:** Position deep, use abilities to secure kills
- **Defensive:** Position safe, enable allies through utility
- **Supportive:** Prioritize team survival > personal damage

---

## Common Patterns

### The Bruiser Pattern

Bruisers (Zealot, Firebat, Ultralisk) are durable melee frontliners:
1. High health/shield pool — designed to absorb damage
2. Sustained damage output — win extended fights, not burst
3. Excel in grouped teamfights — area damage or high durability benefits groups
4. **Playstyle:** Lead engagements, stay in fights, enable carries to output damage safely
5. **Win condition:** Enemy team focuses fire / wasted cooldowns on bruiser while carries DPS

### The Melee Assassin Pattern

Melee assassins (Dark Templar, Zergling, Spectre) are mobile burst specialists:
1. Lower durability than bruisers — can't tank extended fire
2. High burst damage — delete isolated targets quickly
3. Mobile escapes — hit-and-run engagement model
4. **Playstyle:** Hunt isolated targets, burst them down, escape before backup arrives
5. **Win condition:** Secure isolated kills, create 4v5 situations through target elimination

### The Ranged Carry Pattern

Ranged heroes (Dragoon, Marine, Goliath, Hydralisk) share patterns:
1. Strong early game safety through range
2. Consistent sustained damage output
3. Less reliant on perfect positioning than melee
4. Vulnerable to assassins without team peel

### The Support Pattern

Support heroes (Sentry, Brood Queen, Defiler) share patterns:
1. Low personal damage (not priority targets)
2. Enable carries through utility/healing/crowd control
3. Critical at all game phases (scaling utilities)
4. Become stronger with team coordination

### The Base Defender Pattern

Base defenders (Mothership Core, Science Vessel, Nydalist) specialize in defensive structures and positioning:
1. Focused on protecting base and structures from attacks
2. Prioritize defensive positioning and staying near critical assets
3. Provide utilities that discourage base encroachment (repairs, spawns, denial)
4. **Playstyle:** Monitor base, respond to threats, maintain presence at key defensive points
5. **Win condition:** Deny enemy ability to push/destroy base through sustained defensive utilities
6. Less effective in roaming/ganking roles — their power is location-dependent

### The Assassin Pattern

Assassins (melee and ranged variants like Dark Templar, Spectre, Defiler) share patterns:
1. High burst damage potential
2. Limited sustained damage
3. Need perfect positioning/timing
4. Die quickly if caught unprepared
5. Specialize in eliminating isolated or vulnerable targets

---

## Related Documentation

- [tooltip-agent.md](tooltip-agent.md) - Ability text and dynamic value references
- [AGENTS.md](AGENTS.md) - Overview of all agent types in mod
- [HARDCODED_VALUE_FIXES.md](HARDCODED_VALUE_FIXES.md) - Fixed data value references

---

## References

- Proxima Frontlines Discord: https://discord.gg/abBfe66wey
- SC2 Editor Guides: https://s2editor-guides.readthedocs.io/
- SC2Mapster: https://sc2mapster.github.io/mkdocs/

