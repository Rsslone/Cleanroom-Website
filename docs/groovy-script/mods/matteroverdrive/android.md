---
title: "Android Biotic Stats"
titleTemplate: "MatterOverdrive: Refitted | CleanroomMC"
description: "Tweak Android biotic stat parameters such as XP cost, required items, and enabled state."
source_code_link: "https://github.com/Refitbench/MatterOverdrive/blob/v1.4.3/src/main/java/matteroverdrive/compat/modules/groovyscript/Android.java"
---

# Android Biotic Stats (MatterOverdrive: Refitted)

## Description

Tweak Android biotic stat parameters such as XP cost, required items, and enabled state.

:::::::::: details Info {open id="info"}
Use the `androidStat(name)` bracket handler to obtain an IBioticStat.
::::::::::

:::::::::: details Tip {open id="tip"}
Use the command `/android list` to print all registered biotic stat names to chat.
::::::::::

## Identifier

The identifier `mods.matteroverdrive.android` will be used as the default on this page.

:::::::::: details All Identifiers {open id="quote"}

Any of these can be used to refer to this compat:

```groovy:no-line-numbers {1}
mods.matteroverdrive.android/* Used as page default */ // [!code focus]
mods.matteroverdrive.Android
```

::::::::::

## Editing Values

- Set the XP cost in levels required for the given biotic stat:

    ```groovy:no-line-numbers
    mods.matteroverdrive.android.setXp(IBioticStat, int)
    ```

- Force the given biotic stat to be enabled, overriding config-based rules:

    ```groovy:no-line-numbers
    mods.matteroverdrive.android.enable(IBioticStat)
    ```

- Force the given biotic stat to be disabled, overriding config-based rules:

    ```groovy:no-line-numbers
    mods.matteroverdrive.android.disable(IBioticStat)
    ```

:::::::::: details Example {open id="example"}
```groovy:no-line-numbers
mods.matteroverdrive.android.setXp(androidStat('shield'), 25)
```

::::::::::

## Adding Entries

- Add an item that must be present in the player's inventory to install the given biotic stat:

    ```groovy:no-line-numbers
    mods.matteroverdrive.android.addRequiredItem(IBioticStat, ItemStack)
    ```

:::::::::: details Example {open id="example"}
```groovy:no-line-numbers
mods.matteroverdrive.android.addRequiredItem(androidStat('shield'), item('minecraft:iron_ingot') * 5)
```

::::::::::

## Removing Entries

- Unregister a biotic stat entirely, preventing it from appearing or functioning:

    ```groovy:no-line-numbers
    mods.matteroverdrive.android.unregister(IBioticStat)
    ```

- Remove all required installation items from the given biotic stat:

    ```groovy:no-line-numbers
    mods.matteroverdrive.android.clearRequiredItems(IBioticStat)
    ```

:::::::::: details Example {open id="example"}
```groovy:no-line-numbers
mods.matteroverdrive.android.unregister(androidStat('cloak'))
```

::::::::::

## Getting the value of entries

- Returns a sorted list of all currently registered biotic stat unlocalized names:

    ```groovy:no-line-numbers
    mods.matteroverdrive.android.getStatNames()
    ```
