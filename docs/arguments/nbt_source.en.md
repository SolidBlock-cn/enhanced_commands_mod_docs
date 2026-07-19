title: NBT source
subtitle: specifying from where to get NBT

# NBT source: specifying from where to get NBT

**NBT source** is an [argument type](index.md), specifying from where to get NBT data. Note that NBT source is a whole NBT, which usually is only a compound. When running the command actually, it is usually needed to specify the path and the [concentration type](nbt_concentration_type.md)。

## Syntax

- `block <region>`: The NBT data of all block entities from a specified region (which can be a single position). If none of the block in the region is a block entity, it will fail.
- `entity <entity selector>`: The NBT data of specified entities. The selector can specify multiple entities.
- `literal <NBT function>`: Directly specifying NBT data. The NBT function when being used, takes null as a parameter.
- `storage <id>`: The NBT data from a specified storage. Same as vanilla `/data ... storage <id>`.

For the usage of parameters, see [region](region/index.md), [entity selector](entity_selector.md) and [NBT function](nbt_function/index.md).

## Examples

- `block 5 1 4`
- `block sphere(5)`
- `entity @e[type=cow,limit=1]`
- `entity @p[c=-5]`
- `storage namespace:id`

## See also

- [NBT target](nbt_target.md)
- [`/nbt` command](../commands/nbt.md)