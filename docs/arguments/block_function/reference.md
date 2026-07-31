---
title: reference()
subtitle: 引用方块函数
---

# `reference()`：引用方块函数

此类[方块函数](index.md)引用数据包中的方块函数 ID。

ID 为 `<namespace>:<path>` 的方块函数位于数据包中的 `data/<namespace>/enhanced_commands/block_function/<path>.json`。

!!! info
    从数据包中获取方块函数是在命令解析时就完成的，而不是在方块函数运行时进行。这与 26.3 版本之前的原版的引用战利品表谓词的操作逻辑不相同。在服务器中，当方块函数 ID 不存在时，命令无法解析。当客户端中，由于无法直接获取数据包，因此不会报出错误，但此情况下方块函数是无法运行的。

    其他的引用类型亦可参考此信息。

## 语法

- `$<ID>`
- `reference(<ID>)`

参数 `<ID>` 为数据包中的方块函数的 ID。未指定命名空间时，命名空间为 `enhanced_commands`。

## 示例

- `$white_checkerboard`（等价于 `$enhanced_commands:white_checkerboard`，也可以写成 `reference(white_checkerboard)`）

## 参见

- [`引用方块谓词`](../block_predicate/reference.md)
- [`引用物品函数`](../item_function/reference.md)
- [`引用物品谓词`](../item_predicate/reference.md)

## 数据结构

- `type`：此时为 `"reference"`。
- `value`：[带有默认命名空间的 ID](../../glossaries/id_with_default_namespace.md)。