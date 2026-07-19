# `from()` function: importing NBT data from the specified source

The [NBT function](index.md) can be used to import NBT data from a specified [NBT source](../arguments/nbt_source.md). It is possible to specify the path of NBT data to be import, and the concentration type of the data. If the NBT source has multiple NBTs, such as a [region](../../region/index.md) containing multiple block entities, or an [entity selector](../../entity_selector.md) that finds multiple entity, the concentration type must be specified, or errors will be thrown.

## Syntax

- `from(<NBT source>, [NBT path], [NBT concentration type])`

## 参数

### `<NBT source>`

The [NBT source](../arguments/nbt_source.md).

### `[NBT path]`

NBT path, the format is the same as vanilla. It specifies the path in which to import and return data. If the path is not specified, the whole data of the source will be returned.

### `[NBT concentration type]`

[NBT concentration type](../../nbt_concentration_type.md). When applying the function, if the NBT source is found to have multiple NBTs, such as a [region](../../region/index.md) containing multiple block entities, or an [entity selector](../../entity_selector.md) that finds multiple entities, while the concentration is not specified, exceptions will be thrown.

## Examples

- `from(entity @s, Health)`: Return the `Health` value in the NBT of the command executor, which is the health value in floating-point numbers.
