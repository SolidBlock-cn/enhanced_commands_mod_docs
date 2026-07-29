---
title: 数据结构
subtitle: Data structure
---

# 数据结构

本模组的数据结构，指的模组中的内容的 codec，即与 JSON 或 NBT 之间序列化或反序列化（或称编码和解码）的模式。

例如，某个内容的数据结构为：

- `name`：字符串。
- `age`：整数。
- `member`：布尔值，可选，默认为 false。

则表示该内容在序列化后是一个映射，它转化成 NBT 后可能是 `#!snbt {name: Example, age: 25, member: true}`，序列化为 JSON 后可能是 `#!json {"name": "Example", "age": 25, "member": true}`。

有时，在描述数据结构时，可能不是指定基本的类型，而是一个其他的类型，则说明遵循该类型的数据结构，例如，如果某个字段像这样描述：

- `can_use_on`：方块谓词。

则表示这个 `can_use_on` 字段的值遵循方块谓词的数据结构。