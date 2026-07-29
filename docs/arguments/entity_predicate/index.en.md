---
title: Entity predicate
subtitle: filtering entities using a syntax basically the same as selectors
---

# Entity predicate: filtering entities using a syntax basically the same as selectors

An **entity predicate** is an [argument type](index.md) representing condition used to test whether the entity matches. In this mod, entity predicates are implemented with [entity selectors](../entity_selector.md), and use the same syntax as entity selectors.

When `limit` option is not provided in the entity selector used by the entity predicate, it directly tests the entity. If the `limit` option exists, it selects entities at first, and then tests whether the entity belongs to the selected entities. Generally speaking, as for entity predicates, the option `limit` is not recommended.

Besides, compared to entity selectors, entity predicates can omit the preceding “at-variable”. For example, `[type=cow]` is identical to `@E[type=cow]` (the difference between `@E` and `@e` is, `@E` can select dying entities, while `@e` only selects alive entities).

See [entity selectors](../entity_selector.md) for more information.

## Syntax

The syntax of entity predicates is the same as entity selectors, but can emit "at-variables".

- `<player id>`
- `<UUID>`
- `[<option 1>=<value 1>, <option 2>=<value 2>, ...]`: unique syntax of entity predicates compared to selectors.
- `<entity selector type>[<option 1>=<value 1>, <option 2>=<value 2>, ...]`

For entity selector types and arguments supported, see [entity selector](../entity_selector.md).

## Examples

- `Steve`: Passes if the entity is the player Steve.
- `@e`: Passes when the entity is alive.
- `@vehicle`: Passes when the entity is the entity that the command executor is riding.
- `[baby=true]`: Passes when the entity is a baby.
- `[type=cow]`: Passes when the entity is a cow.

## Data structure

- `type`: String, the entity predicate type, [ID with default namespace](../../glossaries/id_with_default_namespace.md). For the full list of types see below.

Each entity predicate has a type. Different types have their own fields (see the page of corresponding types). The following is the ids of all entity predicate types (all namespace `enhanced_commands`, and the namespace is emitted in the list):

- [`advancements`](advancements.md)
- [`air`](air.md)
- [`air_max`](air.md)
- [`alive`](special/alive.md) (special type)
- [`alternatives`](alternatives.md)
- [`baby`](baby.md)
- [`block_predicate`](block.md)
- [`block_predicates`](block.md)
- [`box`](box.md)
- [`collector`](special/collector.md) (special type)
- [`distance`](special/distance.md) (special type)
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
- [`local_world`](special/local_world.md) (special type)
- [`loot_table_predicate`](predicate.md)
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
- [`sender_only`](special/sender_only.md) (special type)
- [`selector`](special/selector.md) (special type)
- [`sneaking`](sneaking.md)
- [`sprinting`](sprinting.md)
- [`sub_predicate`](is_and_not.md)
- [`swimming`](swimming.md)
- [`tag`](tag.md)
- [`team`](team.md)
- [`type`](type.md)
- [`types`](type.md)
- [`type_tag`](type.md)
- [`unknown`](unknown.md)
- [`uuid`](uuid.md)
- [`yaw`](yaw.md)

“Special type” means that it cannot be directly specified by entity selector arguments, but is specified by vanilla entity selector arguments or by the entity selector type itself.