---
title: not()
subtitle: Invert an item predicate
---

# `not()`: Invert an item predicate

Tbe [item predicate](index.md) is used to invert an item predicate.

## Syntax

- `#!js !<item predicate>`
- `#!js not(<item predicate>)`

## Examples

- `#!js !diamond`: All items except diamonds.
- `#!hs ![enchantments]`: All items not enchanted.

## Examples

- [`not()` block predicate](../block_predicate/not.md)
- [`not()` NBT predicate](../nbt_predicate/not.md)

## Data structure

- `type`: Currently `#!json "not"`.
- `predicate`: Item predicate.