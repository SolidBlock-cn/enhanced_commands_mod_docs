# Entity predicate: filtering entities with a syntax basically same to selectors

An **entity predicate** is an [argument type](index.md) playing the role of a condition to test whether the entity matches. In this mod, entity predicates are implemented with [entity selectors](../entity_selector.md), and use the syntax identical to entity selectors.

When `limit` option is not provided in the entity selector used by the entity predicate, it directly tests the entity. If the `limit` option exists, it selects entities at first, and then tests whether the entity belongs to the selected entities. Generally speaking, as for entity predicates, the option `limit` is not recommended.

Besides, compared to entity selectors, entity predicates can ignore the “at-variable" before it. For example, `[type=cow]` is identical to `@E[type=cow]` (the difference between `@E` and `@e` is, `@E` can select dying entities, while `@e` only selects alive entities).

See [entity selectors](../entity_selector.md) for more information.

## Syntax

The syntax of entity predicates is the same as entity selectors, but can emit "at-variables".

- `<player id>`
- `<UUID>`
- `[<option 1>=<value 1>, <option 2>=<value 2>, ...]`: unique syntax of entity predicates compared to selectors.
- `<实体选择器类型>[<option 1>=<value 1>, <option 2>=<value 2>, ...]`

For entity selector types and arguments supported, see [entity selector](../entity_selector.md).

## Examples

- `Steve`: Passes if the entity is player Steve.
- `@e`: Passes when the entity is alive.
- `@vehicle`: Passes when the entity is the entity that the command executor is riding.
- `[baby=true]`: Passes when the entity is baby.
- `[type=cow]`: Passes when the entity is cow.

## Data structure

- `type`: String, the entity predicate type. For the full list of types see below.

Each entity predicate has a type. Different types have their own fields (see the page of corresponding types). The following is the ids of all entity predicate types (all namespace `enhanced_commands`, and the namespace is emitted in the list):

- [`advancements`](advancements.md)
- [`air`](air.md)
- [`air_max`](air.md)
- [`alive`](alive.md) (special type)
- [`alternatives`](alternatives.md)
- [`baby`](baby.md)
- [`block_predicate`](block.md)
- [`block_predicates`](block.md)
- [`box`](box.md)
- [`collector`](collector.md) (special type)
- [`distance`](distance.md) (special type)
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
- [`local_world`](local_world.md) (special type)
- [`loot_table_predicate`](loot_table_predicate.md)
- [`name`](name.md)
- [`nbt`](nbt.md)
- [`owner`](owner.md)
- [`pitch`](pitch.md)
- [`player_name`](player_name.md)
- [`player_only`](player_only.md)
- [`pose`](pose.md)
- [`on_fire`](on_fire.md)
- [`region`](region.md)
- [`saturation`](saturation.md)
- [`sender_only`](sender_only.md) (special type)
- [`selector`](selector.md) (special type)
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