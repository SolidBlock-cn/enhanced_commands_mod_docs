---
title: all()
subtitle: 当所有 NBT 谓词通过时通过
---

多个 [NBT 谓词](index.md)的并集。当多个 NBT 谓词均通过时，这个 NBT 谓词才通过。如果没有提供 NBT 谓词则始终通过。

## 语法

`#!js all([NBT 谓词], ...)`

NBT 谓词的数量不限。

另一种语法是，`#!js <NBT 谓词 1>|<NBT 谓词2 >`，参见[交集、并集、取反与括号](index.md#交集并集取反与括号)。

## 示例

- `#!js all(>8, <5)`：当 NBT 值为数值，且大于 8 且小于 5 时通过，等价于 `>8&<5`。
- `#!js all(~light, ~concrete)`：当 NBT 值为字符串，且包括“light”和“concrete”时通过，等价于 `~light&~concrete`。
- `#!js all()`：始终通过。

## 参见

- [`any()`](any.md)
- [`all()` 方块谓词](../block_predicate/all.md)
- [`all()` 物品谓词](../item_predicate/all.md)

## 数据结构

- `type`：此时为 `all`。
- `values`：列表。
    - NBT 谓词。