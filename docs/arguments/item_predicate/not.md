---
title: not()
subtitle: 反转一个物品谓词
---

# `not()`：反转一个物品谓词

此[物品谓词](index.md)用于反转一个物品谓词。

## 语法

- `#!js !<物品谓词>`
- `#!js not(<物品谓词>)`

## 示例

- `#!js !diamond`：所有不是钻石的物品。
- `#!hs ![enchantments]`：所有未附魔的物品。

## 示例

- [`not()` 方块谓词](../block_predicate/not.md)
- [`not()` NBT 谓词](../nbt_predicate/not.md)

## 数据结构

- `type`：此时为 `#!json "not"`。
- `predicate`：物品谓词。