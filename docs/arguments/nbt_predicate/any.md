---
title: any()
subtitle: 符合多个 NBT 谓词的任意一个即通过
---

# `any()`：符合多个 NBT 谓词的任意一个即通过

多个 [NBT 谓词](index.md)的并集，当其中一个 NBT 谓词通过时通过。

## 语法

`#!js any([NBT 谓词], ...)`

NBT 谓词的数量不限。

另一种语法是，`#!js <NBT 谓词 1>|<NBT 谓词2 >`，参见[交集、并集、取反与括号](index.md#交集并集取反与括号)。

## 示例

- `#!js any(1s, 3b, 'string')`：等价于 `#!js 1s|3b|'string'`。
- `#!js any(cat, dog)`：等价于 `#!js cat|dog`。
- `any()`：始终不通过。等效于 `!*`。

## 参见 

- [`all()`](all.md)
- [`any()` 方块谓词](../block_predicate/any.md)
- [`any()` 物品谓词](../item_predicate/any.md)

## 数据结构

- `type`：此时为 `any`。
- `values`：列表。
    - NBT 谓词。