---
title: not()
subtitle: 反转一个方块谓词
---

# `not()`：反转一个方块谓词

此[方块谓词](index.md)用于否定一个方块谓词。

## 语法

- `#!js !<方块谓词>`
- `#!js not(<方块谓词>)`（参见[复合方块谓词](index.md#复合方块谓词)）

## 示例

- `#!js !dirt` 或 `#!js not(dirt)`：所有不是泥土的方块。
- `#!js !(dirt|grass_block)` 或 `#!js not(dirt|grass_block)`：所有既不是泥土、也不是草方块的方块。
    - 上述示例等效于 `#!js !dirt&!grass_block`。

## 参见

- [`not()` 物品谓词](../item_predicate/not.md)
- [`not()` NBT 谓词](../nbt_predicate/not.md)

## 数据结构

- `type`：此时为 `#!json "not"`。
- `predicate`：方块谓词。