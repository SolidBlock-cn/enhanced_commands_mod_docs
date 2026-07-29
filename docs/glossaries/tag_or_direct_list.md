# 标签或直接列表

Minecraft 中的一种特殊数据类型（`#!java HolderSet`），可以内联指定一系列的项的列表，也可以通过数据包中的标签指定（格式为字符串，带有井号以及标签 ID）。

例如，如果有下面这样的字段：

- `available_items`：物品的标签或直接列表。

则表示这个 `available_items` 的值可能是直接列表（例如 `#!json ["diamond", "iron_ingot", "emerald"]`），也可能是一个标签（例如 `#!json "#stairs"`）。