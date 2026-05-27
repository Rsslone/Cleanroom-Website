---
title: "Replicator Blacklist"
titleTemplate: "MatterOverdrive: Refitted | CleanroomMC"
description: "Prevent specific items from being replicated regardless of their matter value."
source_code_link: "https://github.com/Refitbench/MatterOverdrive/blob/master/src/main/java/matteroverdrive/compat/modules/groovyscript/ReplicatorCompat.java"
---

# Replicator Blacklist (MatterOverdrive: Refitted)

## Description

Maintains the per-item replicator blacklist. Items on this list will be
rejected by the Replicator's pattern task even if they have a non-zero matter
value; this is the recommended way to forbid replication of unbalanced or
exploit-prone items without zeroing their matter value (which would also
prevent the Matter Scanner from extracting matter from them).

## Identifier

The identifier `mods.matteroverdrive.replicator` will be used as the default on this page.

:::::::::: details All Identifiers {open id="quote"}

Any of these can be used to refer to this compat:

```groovy:no-line-numbers {1}
mods.matteroverdrive.replicator/* Used as page default */ // [!code focus]
```

::::::::::

## Adding Entries

- Adds an item to the replicator blacklist:

    ```groovy:no-line-numbers
    mods.matteroverdrive.replicator.add(String itemId)
    mods.matteroverdrive.replicator.add(Item)
    mods.matteroverdrive.replicator.add(ItemStack)
    mods.matteroverdrive.replicator.add(IIngredient)
    ```

:::::::::: details Example {open id="example"}
```groovy:no-line-numbers
mods.matteroverdrive.replicator.add('minecraft:nether_star')
mods.matteroverdrive.replicator.add(ore('gemDiamond'))
```

::::::::::
