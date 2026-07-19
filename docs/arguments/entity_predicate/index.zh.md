# 实体谓词：使用和选择器基本相同的语法筛选实体

**实体谓词**（entity predicate）是可用于判断实体是否符合的条件的[参数类型](index.md)。在本模组中，实体谓词是通过[实体选择器](../entity_selector.md)实现的，并且使用和实体选择器相似的语法。

当实体谓词所使用的实体选择器没有 `limit` 选项时，会直接对实体进行判断。如果有 `limit` 选项，则会先选择出相应的实体，然后再判断实体是否属于被选择出来的实体。通常来说，对于实体谓词，一般不建议使用 `limit` 选项。

此外，与实体选择器相比，实体谓词可以忽略前面的“at-变量”，例如 `[type=cow]` 等价于 `@E[type=cow]`（`@E` 与 `@e` 的区别在于，`@E` 能够选择死亡的实体，而 `@e` 只选择存活的实体）。

更多信息请见[实体选择器](../entity_selector.md)。

## 语法

实体谓词的语法和实体选择器一致，但可以省略“at-变量”。

- `<玩家 id>`
- `<UUID>`
- `[<选项 1>=<值 1>, <选项 2>=<值 2>, ...]`：实体谓词相比实体选择器独有的语法。
- `<实体选择器类型>[<选项 1>=<值 1>, <选项 2>=<值 2>, ...]`

关于支持的实体选择器类型和参数，请见[实体选择器](../entity_selector.md)。

## 示例

- `Steve`：当实体为玩家 Steve 时通过。
- `@e`：当实体存活时通过。
- `@vehicle`：当实体为命令执行者骑乘的实体时通过。
- `[baby=true]`：当实体为幼年实体时通过。
- `[type=cow]`：当实体为牛时通过。

## 数据结构

- `type`：字符串，实体谓词的类型。具体可见的类型见下。

每个实体谓词都有一个类型，不同的类型会支持一些各自的字段（见对应具体实体选择器类型的页面）。以下为目前的所有实体选择器类型的 id（均以 `enhanced_commands` 为命名空间，这里省略命名空间）：

- [`advancements`](advancements.md)
- [`air`](air.md)
- [`air_max`](air.md)
- [`alive`](alive.md)（特殊类型）
- [`alternatives`](alternatives.md)
- [`baby`](baby.md)
- [`block_predicate`](block.md)
- [`block_predicates`](block.md)
- [`box`](box.md)
- [`collector`](collector.md)（特殊类型）
- [`distance`](distance.md)（特殊类型）
- [`effect`](effect.md)
- [`effects`](effect.md)
- [`empty`](empty.md)
- [`exhaustion`](exhaustion.md)
- [`fire`](fire.md)
- [`food`](food.md)
- [`game_mode`](game_mode.md)
- [`health`](health.md)
- [`health_max`](health.md)
- [`level`](level.md)
- [`local_world`](local_world.md)（特殊类型）
- [`loot_table_predicate`](loot_table_predicate.md)
- [`name`](name.md)
- [`nbt`](nbt.md)
- [`owner`](owner.md)
- [`pitch`](pitch.md)
- [`player_name`](player_name.md)
- [`player_only`](player_only.md)
- [`pose`](pose.md)
- [`on_fire`](on_fire.md)
- [`region`](region/index.md)
- [`saturation`](saturation.md)
- [`sender_only`](sender_only.md)（特殊类型）
- [`selector`](selector.md)（特殊类型）
- [`sneaking`](sneaking.md)
- [`sprinting`](sprinting.md)
- [`sub_predicate`](sub_predicate.md)
- [`swimming`](swimming.md)
- [`tag`](tag.md)
- [`team`](team.md)
- [`type`](type.md)
- [`types`](type.md)
- [`type_tag`](type.md)
- [`unknown`](unknown.md)
- [`uuid`](uuid.md)
- [`yaw`](yaw.md)

特殊类型是指无法通过实体选择器参数直接指定，而是由原版的实体选择器参数间接指定或者由实体选择器类型指定的。