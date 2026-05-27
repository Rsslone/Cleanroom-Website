---
title: "Inscriber"
titleTemplate: "MatterOverdrive: Refitted | CleanroomMC"
description: "Add or remove recipes for the Inscriber: two item inputs, one item output, plus energy and time costs."
source_code_link: "https://github.com/Refitbench/MatterOverdrive/blob/master/src/main/java/matteroverdrive/compat/modules/groovyscript/InscriberCompat.java"
---

# Inscriber (MatterOverdrive: Refitted)

## Description

Add or remove inscriber recipes.

## Identifier

The identifier `mods.matteroverdrive.inscriber` will be used as the default on this page.

:::::::::: details All Identifiers {open id="quote"}

Any of these can be used to refer to this compat:

```groovy:no-line-numbers {1}
mods.matteroverdrive.inscriber/* Used as page default */ // [!code focus]
```

::::::::::

## Adding Recipes

### Recipe Builder

Just like other recipe types, the Inscriber uses a recipe builder.

Don't know what a builder is? Check [the builder info page](../../getting_started/builder.md) out.

:::::::::: details Recipe Builder {open id="abstract"}

---

- Create the Recipe Builder.

    ```groovy:no-line-numbers
    mods.matteroverdrive.inscriber.recipeBuilder()
    ```

---

- `IngredientList<IIngredient>`. Sets the item inputs of the recipe. Requires
  exactly 2. The first is treated as the primary input, the second as the
  secondary input.

    ```groovy:no-line-numbers
    input(IIngredient)
    input(IIngredient...)
    input(Collection<IIngredient>)
    ```

- `ItemStackList`. Sets the item outputs of the recipe. Requires exactly 1.

    ```groovy:no-line-numbers
    output(ItemStack)
    ```

- `int`. Sets the FE cost. Must be greater than 0. (Default `1000`).

    ```groovy:no-line-numbers
    energy(int)
    ```

- `int`. Sets the processing time in ticks. Must be greater than 0. (Default `60`).

    ```groovy:no-line-numbers
    time(int)
    ```

---

- First validates the builder, returning `null` and outputting errors to the log file if the validation failed, then registers the builder and returns the registered object. (returns `null` or `matteroverdrive.data.recipes.InscriberRecipe`).

    ```groovy:no-line-numbers
    register()
    ```

---

::::::::: details Example {open id="example"}
```groovy:no-line-numbers
mods.matteroverdrive.inscriber.recipeBuilder()
    .input(item('minecraft:redstone'))
    .input(item('minecraft:gold_ingot'))
    .output(item('matteroverdrive:circuit_basic'))
    .energy(1000)
    .time(80)
    .register()
```

:::::::::

::::::::::

## Removing Recipes

- Removes any Inscriber recipe whose output matches the given stack:

    ```groovy:no-line-numbers
    mods.matteroverdrive.inscriber.removeByOutput(ItemStack)
    ```

- Removes any Inscriber recipe whose primary and secondary input pair match
  the given stacks (order matters):

    ```groovy:no-line-numbers
    mods.matteroverdrive.inscriber.removeByInputs(ItemStack main, ItemStack sec)
    ```

- Removes all registered Inscriber recipes:

    ```groovy:no-line-numbers
    mods.matteroverdrive.inscriber.removeAll()
    ```

:::::::::: details Example {open id="example"}
```groovy:no-line-numbers
mods.matteroverdrive.inscriber.removeByOutput(item('matteroverdrive:circuit_basic'))
mods.matteroverdrive.inscriber.removeByInputs(item('minecraft:redstone'), item('minecraft:gold_ingot'))
mods.matteroverdrive.inscriber.removeAll()
```

::::::::::

## Getting the value of recipes

- Iterates through every entry in the registry, with the ability to call
  remove on any element to remove it:

    ```groovy:no-line-numbers
    mods.matteroverdrive.inscriber.streamRecipes()
    ```
