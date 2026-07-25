---
title: regex()
subtitle: 通过正则表达式匹配 NBT
---

# `regex()`：通过正则表达式匹配 NBT

此 [NBT 谓词](index.md)用于检测 NBT 是否符合指定的正则表达式。对于非字符串类型的 NBT 值，此谓词始终始终不通过。

## 语法

- `#!js ~ <正则表达式>`
- `#!js pattern(<正则表达式>)`

上面两种方法等价。对于正则表达式而言，部分字符，如 `$`、`^`、`*`，可以不加引号，但是如果涉及空格、括号等字符，则必须加引号。如果正则表达式错误，会解析错误。

## 示例

- `#!js pattern('^minecraft:')` 或 `#!js ~'^minecraft:'`：当 NBT 值为字符串，且以 `minecraft:` 开头时通过。
- `#!js pattern('^\[.*?\]$')` 或 `#!js ~ '^\[.*?\]$'`：当 NBT 值为字符串，且以“`[`”开头、以“`]`”结尾时通过。
- `#!js pattern('[Ss][Oo][Ll][Ii][Dd]')` 或 `#!js ~ '[Ss][Oo][Ll][Ii][Dd]'`：当 NBT 值为字符串，且含有单词“solid”（不区分大小写）时通过。
- `#!js pattern([Ss][Oo][Ll][Ii][Dd])` 或 `#!js ~ [Ss][Oo][Ll][Ii][Dd]`：无效的 NBT 谓词，因为这种情况下必须要有引号。

## 数据结构

- `type`：此时为 `pattern`。
- `pattern`：字符串，正则表达式。