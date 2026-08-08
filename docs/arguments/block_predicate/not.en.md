---
title: not()
subtitle: Invert a block predicate
---

# `not()`: Invert a block predicate

The [block predicate](index.md) is used to invert a block predicate

## Syntax

- `#!js !<block predicate>`
- `#!js not(<block predicate>)` (see [compound block predicate](index.md#compound-block-predicate))

## Examples

- `#!js !dirt` or `#!js not(dirt)`: All blocks that are not dirt.
- `#!js !(dirt|grass_block)` or `#!js not(dirt|grass_block)`: All blocks that are neither dirt nor grass blocks.
    - The example above has the same effect as `#!js !dirt&!grass_block`.

## See also

- [`not()` item predicate](../item_predicate/not.md)
- [`not()` NBT predicate](../nbt_predicate/not.md)

## Data structure

- `type`: Currently `#!json "not"`.
- `predicate`: Block predicate.