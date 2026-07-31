---
title: reference()
subtitle: 引用方块谓词
---

# `reference()`：引用方块谓词

此[方块谓词](index.md)引用数据包中的方块谓词 ID。

ID 为 `<namespace>:<path>` 的方块谓词位于数据包中的 `data/<namespace>/enhanced_commands/block_predicate/<path>.json`。

!!! info
    从数据包中获取方块谓词是在命令解析时就完成的，而不是在方块谓词运行时进行。参见[引用方块函数](../block_function/reference.md)中的相关说明。

## 语法

- `$<ID>`
- `reference(<ID>)`

参数 `<ID>` 为数据包中的方块谓词的 ID。未指定命名空间时，命名空间为 `enhanced_commands`。

## 示例

- `$air_grid`（等价于 `$enhanced_commands:air_grid`）

## 参见

- [`引用方块函数`](../block_function/reference.md)
- [`引用物品函数`](../item_function/reference.md)
- [`引用物品谓词`](../item_predicate/reference.md)

## 数据结构

- `type`：此时为 `"reference"`。
- `value`：[带有默认命名空间的 ID](../../glossaries/id_with_default_namespace.md)。