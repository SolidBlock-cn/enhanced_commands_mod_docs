---
title: reference()
subtitle: 引用物品函数
---

# `reference()`：引用物品函数

此类[物品函数](index.md)引用数据包中的物品函数 ID。

ID 为 `<namespace>:<path>` 的物品函数位于数据包中的 `data/<namespace>/enhanced_commands/item_function/<path>.json`。

!!! info
    从数据包中获取物品函数是在命令解析时就完成的，而不是在物品函数运行时进行。参见[引用方块函数](../block_function/reference.md)中的相关说明。

## 语法

- `$<ID>`
- `reference(<ID>)`

参数 `<ID>` 为数据包中的物品函数的 ID。未指定命名空间时，命名空间为 `enhanced_commands`。

## 参见

- [`引用方块函数`](../block_function/reference.md)
- [`引用方块谓词`](../block_predicate/reference.md)
- [`引用物品谓词`](../item_predicate/reference.md)

## 数据结构

- `type`：此时为 `"reference"`。
- `value`：[带有默认命名空间的 ID](../../glossaries/id_with_default_namespace.md)。