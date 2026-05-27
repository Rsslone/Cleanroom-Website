---
title: "Matter Registry"
titleTemplate: "MatterOverdrive: Refitted | CleanroomMC"
description: "Add, remove, or replace the matter value of items and ore-dictionary entries used by the Matter Scanner and Replicator."
source_code_link: "https://github.com/Refitbench/MatterOverdrive/blob/master/src/main/java/matteroverdrive/compat/modules/groovyscript/MatterCompat.java"
---

# Matter Registry (MatterOverdrive: Refitted)

## Description

Controls the matter value assigned to each item and ore-dictionary entry, plus
the per-mod matter calculation blacklist. Matter values determine how much
"matter" the Decomposer extracts from an item and how much it costs to
replicate.

## Identifier

The identifier `mods.matteroverdrive.matter` will be used as the default on this page.

:::::::::: details All Identifiers {open id="quote"}

Any of these can be used to refer to this compat:

```groovy:no-line-numbers {1}
mods.matteroverdrive.matter/* Used as page default */ // [!code focus]
```

::::::::::

## Adding Entries

- Sets the matter value of an item (overwriting any existing value):

    ```groovy:no-line-numbers
    mods.matteroverdrive.matter.add(String itemId, int matter)
    mods.matteroverdrive.matter.add(Item item, int matter)
    mods.matteroverdrive.matter.add(Item item, IMatterEntryHandler handler)
    ```

- Sets the matter value of an ore-dictionary entry:

    ```groovy:no-line-numbers
    mods.matteroverdrive.matter.addOre(String oreName, int matter)
    mods.matteroverdrive.matter.addOre(String oreName, IMatterEntryHandler handler)
    ```

:::::::::: details Example {open id="example"}
```groovy:no-line-numbers
mods.matteroverdrive.matter.add('minecraft:gold_ingot', 256)
mods.matteroverdrive.matter.addOre('oreCopper', 32)
```

::::::::::

## Removing Entries

- Removes the matter value for an item or ore-dictionary entry:

    ```groovy:no-line-numbers
    mods.matteroverdrive.matter.remove(String itemId)
    mods.matteroverdrive.matter.remove(Item item)
    mods.matteroverdrive.matter.removeOre(String oreName)
    ```

:::::::::: details Example {open id="example"}
```groovy:no-line-numbers
mods.matteroverdrive.matter.remove('minecraft:apple')
mods.matteroverdrive.matter.removeOre('oreTin')
```

::::::::::

## Mod Blacklist

The mod blacklist prevents Matter Overdrive from auto-calculating matter
values for items belonging to the listed mods. Explicit `add()` calls still
work regardless of blacklist status.

- Adds a mod to the matter calculation blacklist:

    ```groovy:no-line-numbers
    mods.matteroverdrive.matter.blacklistMod(String modId)
    ```

:::::::::: details Example {open id="example"}
```groovy:no-line-numbers
mods.matteroverdrive.matter.blacklistMod('thaumcraft')
```

::::::::::

## Object Mapper

The `matter` bracket handler resolves an item id to its existing
`MatterEntryItem`:

```groovy:no-line-numbers
matter('minecraft:gold_ingot')
```
