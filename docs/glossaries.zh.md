# 术语表

本页包含增强命令模组中常用的一些词汇约定。

## 数据结构（<span id="data-structure">Data structure</span>）

本模组的数据结构，指的模组中的内容的 codec，即与 JSON 或 NBT 之间序列化或反序列化（或称编码和解码）的模式。

例如，某个内容的数据结构为：

- `name`：字符串。
- `age`：整数。
- `member`：布尔值，可选，默认为 false。

则表示该内容在序列化后是一个映射，它转化成 NBT 后可能是 `{name: Example, age: 25, member: true}`，序列化为 JSON 后可能是 `#!json {"name": "Example", "age": 25, "member": true}`。

有时，在描述数据结构时，可能不是指定基本的类型，而是一个其他的类型，则说明遵循该类型的数据结构，例如，如果某个字段像这样描述：

- `can_use_on`：方块谓词。

则表示这个 `can_use_on` 字段的值遵循方块谓词的数据结构。

## 带有默认命名空间的 ID（<span id="id-with-default-namespace">ID with default namespace</span>）

在本模组的数据结构中，有些 ID 在与字符串转化时，会使用不同于 `minecraft` 的默认命名空间。在没有特别说明的情况下，本模组说的带有默认命名空间的 ID 均以 `enhanced_commands` 为默认命名空间，在将字符串转化为 ID 时，没有指定命名空间的使用默认命名空间。如果指明了“简化”，则在将 ID 转化为字符串呈现时，当这个 ID 的命名空间恰好为默认命名空间时，会省略默认命名空间。

对于没有特别说明的 ID，则是指原版的 ID，即以 `minecraft` 为默认命名空间，且在将 ID 转化为字符串时，始终显示命名空间。

## 标签或直接列表（<span id="tag-or-direct-list">Tag or direct list</span>）

Minecraft 中的一种特殊数据类型（`#!java HolderSet`），可以内联指定一系列的项的列表，也可以通过数据包中的标签指定（格式为字符串，带有井号以及标签 ID）。

例如，如果有下面这样的字段：

- `available_items`：物品的标签或直接列表。

则表示这个 `available_items` 的值可能是直接列表（例如 `#!json ["diamond", "iron_ingot", "emerald"]`），也可能是一个标签（例如 `#!json "#stairs"`）。