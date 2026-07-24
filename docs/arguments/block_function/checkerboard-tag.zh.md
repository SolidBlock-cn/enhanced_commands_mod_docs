title: checkerboard-tag()
subtitle: 根据方块标签画棋盘格

# `checkerboard-tag()`：根据方块标签画棋盘格

此[方块函数](index.md)类似于 [`checkerboard()`](checkerboard.md)，但是以拥有方块标签的各个方块作为棋盘格图案。

如果方块标签是空的，该方块函数不会生效。

## 语法

- `#!mcfunction checkerboard-tag(#<方块标签 id>)`
- `#!mcfunction checkerboard-tag(#<方块标签 id>; [参数])`

方块标签必须存在。参数的用法同 [`checkerboard() 的参数`](checkerboard.md)。

## 示例

- `#!mcfunction checkerboard-tag(#planks)`：由不同的木板方块组成的棋盘格。
- `#!mcfunction checkerboard-tag(#wool; scale = 2)`：由不同的羊毛方块组成的棋盘格，棋盘大小为 2×2×2 的正方体。

## 数据格式

- `id`：此时为 `checkerboard-tag`。
- `tag`：方块的[标签或直接列表](../../glossaries.md#tag-or-direct-list)。
- `floor`：三维向量（双精度浮点数，下同），可选，默认值为 `[0d, 0d, 0d]`。
- `scale`：三维向量（双精度浮点数，下同），可选，默认值为 `[1d, 1d, 1d]`。
- `offset`：三维向量（双精度浮点数，下同），可选，默认值为 `[0d, 0d, 0d]`。

??? example "示例：`checkerboard-tag(#planks)`"
    ```json
    {
      "tag": "#minecraft:planks",
      "type": "checkerboard-tag"
    }
    ```

??? example "示例：`checkerboard-tag(#wool; scale = 2)`"
    ```json
    {
      "tag": "#minecraft:wool",
      "scale": [
        2.0,
        2.0,
        2.0
      ],
      "type": "checkerboard-tag"
    }
    ```
