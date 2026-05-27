---
title: "Android Biotic Stats"
titleTemplate: "MatterOverdrive: Refitted | CleanroomMC"
description: "Tweak Android biotic stats: xp cost, required items, enable/disable."
source_code_link: "https://github.com/Refitbench/MatterOverdrive/blob/master/src/main/java/matteroverdrive/compat/modules/groovyscript/AndroidCompat.java"
---

# Android Biotic Stats

## Description

Controls Matter Overdrive's Android biotic stat tree. Existing
stats can be enabled, disabled, re-priced, or have their unlock requirements
changed.

:::::::::: details Note {open id="note"}
Only stats that extend `matteroverdrive.data.biostats.AbstractBioticStat`
can be mutated through this compat. Mods adding
fully custom `IBioticStat` implementations may not be patchable here.
::::::::::

## Identifier

The identifier `mods.matteroverdrive.android` will be used as the default on this page.

:::::::::: details All Identifiers {open id="quote"}

Any of these can be used to refer to this compat:

```groovy:no-line-numbers {1}
mods.matteroverdrive.android/* Used as page default */ // [!code focus]
```

::::::::::

## Tweaking Stats

- Sets the xp cost to unlock or level up the given stat:

    ```groovy:no-line-numbers
    mods.matteroverdrive.android.setXp(IBioticStat, int xp)
    ```

- Forces the stat enabled or disabled, overriding config-based rules:

    ```groovy:no-line-numbers
    mods.matteroverdrive.android.enable(IBioticStat)
    mods.matteroverdrive.android.disable(IBioticStat)
    ```

- Adds or clears the required items list for a stat:

    ```groovy:no-line-numbers
    mods.matteroverdrive.android.addRequiredItem(IBioticStat, ItemStack)
    mods.matteroverdrive.android.clearRequiredItems(IBioticStat)
    ```

:::::::::: details Example {open id="example"}
```groovy:no-line-numbers
def shield = androidStat('shield')
mods.matteroverdrive.android.setXp(shield, 50)
mods.matteroverdrive.android.clearRequiredItems(shield)
mods.matteroverdrive.android.addRequiredItem(shield, item('minecraft:iron_ingot') * 8)
mods.matteroverdrive.android.disable(androidStat('cloak'))
```

::::::::::

## Unregistering Stats

- Removes a stat from the registry. This will gray out the ability, and pass through dependants of the stat, if you want the full chain to be removed, unregister all stats individually.

    ```groovy:no-line-numbers
    mods.matteroverdrive.android.unregister(String unlocalizedName)
    ```

:::::::::: details Example {open id="example"}
```groovy:no-line-numbers
mods.matteroverdrive.android.unregister('cloak')
```

::::::::::

## Object Mapper

The `androidStat` bracket handler resolves an unlocalized name to its
`IBioticStat`:

```groovy:no-line-numbers
androidStat('shield')
androidStat('nightvision')
```

### All Built-in Stat Names

| Name | Description |
|---|---|
| `teleport` | Short-range teleport |
| `nanobots` | Nanobot healing |
| `nano_armor` | Nano-scale armor plating |
| `floatation` | Water/lava flotation |
| `speed` | Movement speed boost |
| `high_jump` | Increased jump height |
| `inertial_dampers` | Fall damage reduction |
| `equalizer` | Spacetime equalizer ability |
| `shield` | Energy shield |
| `auto_shield` | Automatic shield activation |
| `cloak` | Optical cloaking |
| `attack` | Melee damage boost |
| `flash_cooling` | Flash cooling / fire immunity |
| `shockwave` | Melee shockwave burst |
| `nightvision` | Night vision |
| `minimap` | Minimap overlay |
| `step_assist` | Step-up assist |
| `zero_calories` | Zero caloric consumption |
| `oxygen` | Underwater oxygen supply |
| `wireless_charger` | Wireless energy charging |
| `item_magnet` | Item attraction magnet |
| `air_dash` | Mid-air dash |
| `tan_temperature` | Temperature regulation *(Requires Tough As Nails or Simple Difficulty)* |

:::::::::: details Note {open id="note"}
`tan_temperature` is always registered, however it only has an effect when [Tough As Nails](https://www.curseforge.com/minecraft/mc-mods/tough-as-nails)
or [Simple Difficulty](https://www.curseforge.com/minecraft/mc-mods/simple-difficulty) is installed.
::::::::::
