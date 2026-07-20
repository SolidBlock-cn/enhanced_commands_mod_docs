# 命令

本模组加入了一系列增强的**命令**。

## 区域命令

- [`/activeregion`](activeregion.md) 或 `/ar` 以及 `//activeregion` 和 `//ar`：管理玩家的活动区域。
- [`/regionselection`](regionselection.md) 或 `/rs`：管理玩家的区域选择的类型。

## 方块命令

这些命令用于对一个区域内的方块（有时包括实体）进行操作。

- [`/convertblock`](convertblock.md)：将方块转换为特定的实体（如展示实体、下落的方块）。
- [`/convertblocks`](convertblocks.md) 和 `//convertblocks`：将区域内的方块转换为特定的实体。
- [`/draw`](draw.md)：在世界内绘制一条曲线。
- [`/mirror`](mirror.md) 和 `//mirror`：镜像（翻转）区域内的方块和实体。
- [`/moveblocks`](moveblocks.md) 和 `//moveblocks`：移动区域内的方块和实体。
- [`/outline`](outline.md)：填充区域边缘位置的方块，可以一并填充区域边缘以内的方块。
- [`/postprocess`](postprocess.md) 和 `//postprocess`：对方块进行后处理，例如修复栅栏与墙的连接问题。
- [`/replaceblocks`](replace.md) 和 `//replaceblocks`：替换区域内的符合指定谓词的方块。
- [`/rotateblocks`](rotateblocks.md) 和 `//rotateblocks`：旋转区域内的方块和实体。
- [`/setblocks`](setblocks.md)、`//setblocks` 和 `/s`、`//s`：设置区域内的方块。
- [`/stackblocks`](stackblocks.md) 和 `//stackblocks`：向一个方向多次复制区域。
- [`/wall`](wall.md)：填充区域内的四周（墙面）的方块，可以一并填充区域四周以内的方块。

## 实体命令

- [`/air`](air.md)：修改实体的空气值。
- [`/food`](food.md)：修改玩家的饱食度、饱和度和消耗度。
- [`/health`](health.md)：修改实体的生命值。
- [`/pile`](pile.md)：通过骑乘的方式堆叠实体。
- [`/tame`](tame.md)：驯养或取消驯养实体。
- [`/tprel`](tprel.md)：传送实体，其中坐标和旋转均是以被传送实体为基础计算的。
- [`/velocity`](velocity.md)：修改实体的速度。

## 测试命令

- [`/testarg`](testarg.md)：对特定类型的参数进行测试。
- `/testfor`：可获取并测试世界内的一些内容。目前支持以下子命令：
    - [`/testfor block`](testfor/block.md)：获取单个方块，或测试[方块谓词](../arguments/block_predicate/index.md)。
    - [`/testfor blockinfo`](testfor/blockinfo.md)：获取或测试单个方块的信息，例如硬度、光照等信息。
    - [`/testfor blocks`](testfor/blocks.md)：获取多个方块的信息，并测试[方块谓词](../arguments/block_predicate/index.md)。
    - [`/testfor entity`](testfor/entity.md)：获取使用[实体选择器](../arguments/entity_selector.md)选择到的实体的信息，或使用[实体谓词](../arguments/entity_predicate/index.md)测试这些实体。
    - [`/testfor biome`](testfor/biome.md)：获取指定位置的生物群系，并进行测试。

## 独立的 `/execute` 子命令

`/execute` 的各个子命令已经独立为单独的命令（原先的语法依然可以正常使用）。如 `/execute as @e at @s run summon creeper` 可以写成 `/as @e at @s summon creeper`。

`/execute` 的各个已经独立的子命令共包括：

- 条件子命令：`/if` 和 `/unless`
    - 原版：`block`、`biome`、`loaded`、`dimension`、`score`、`blocks`、`entity`、`predicate`、`function`、`items`、`data` 等
    - [`blockinfo`](if_and_unless/blockinfo.md)：当方块信息符合或不符合指定条件时执行命令。
    - [`rand`](if_and_unless/rand.md)：在特定的概率下执行或不执行命令。
- 修饰子命令：
    - `/as`、`/at`、`/positioned`、`/rotateblocksd`、`/facing`、`/align`、`/anchored`、`/in`、`/summon` 等
    - [`/inregion`](inregion.md)（本模组添加）：在一个区域内的所有方块坐标中分别执行命令。
    - [`/silenced`](silenced.md)（本模组添加）：执行命令，但是不会在聊天或者控制台产生任何反馈。
    - [`/for`](for.md)（本模组添加）
- 存储子命令：
    - `/store`

## 简化的 `/gamemode` 命令

各个游戏模式的命令均添加了简化的版本。

- `/gmc [玩家]` 相当于 `/gamemode creative [玩家]`
- `/gms [玩家]` 相当于 `/gamemode survival [玩家]`
- `/gma [玩家]` 相当于 `/gamemode adventure [玩家]`
- `/gmsp [玩家]` 相当于 `/gamemode spectator [玩家]`

## 调试命令

- [`debug:deop`](debug_deop.md)：强制清除玩家管理员权限，即使自己没有管理员权限。
- [`debug:op`](debug_op.md)：强制赋予玩家管理员权限，即使自己没有管理员权限。
- [`debug:permissionlevel`](debug_permissionlevel.md)：查看当前的权限等级，或者模拟指定的权限等级执行命令。

## 其他命令

- [`/history`](history.md)：管理操作历史记录。
- [`/moon`](moon.md)：查询和设置月相。`/jadeplate` 是此命令的别称。
- [`/nbt`](nbt.md)：查看和设置 NBT 数据。
- [`/rand`](rand.md)：生成随机数。
- [`/tasks`](tasks.md)：管理当前服务器中的任务。
- [`/undo` 和 `/redo`](undo_and_redo.md)：撤销和重做。
