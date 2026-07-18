This mod adds a series of **commands**.

## Region commands

- [`/activeregion`](activeregion.md) or `/ar` and `//activeregion` and `//ar`: Manage the player's active region.
- [`/regionselection`](regionselection.md) or `/rs`: Manage the player's region selection type.

## Block commands

These commands are used to operate on blocks (sometimes including entities) within a range.

- [`/convertblock`](convertblock.md): Convert the block to a specific entity (such as display entity, falling block).
- [`/convertblocks`](convertblocks.md) and `//convertblocks`: Convert the blocks within a range to specific entities.
- [`/draw`](draw.md): Draw a curve in the world.
- [`/mirror`](mirror.md) and `//mirror`: Mirror (flip) the blocks and entities within a range.
- [`/moveblocks`](moveblocks.md) and `//moveblocks`: Move the blocks and entities within a range.
- [`/outline`](outline.md): Fill the blocks on the outline of a region. It can also fill the inner part within the outline meanwhile.
- [`/postprocess`](postprocess.md) and `//postprocess`: Postprocess on blocks, such as fixing connection issues related to fences and walls.
- [`/replaceblocks`](replace.md) and `//replaceblocks`: Replace blocks within a region that match the specified predicate.
- [`/rotateblocks`](rotateblocks.md) and `//rotateblocks`: Rotate blocks and entities within a region.
- [`/setblocks`](setblocks.md), `//setblocks` and `/s`, `//s`: Set the blocks within a region.
- [`/stackblocks`](stackblocks.md) and `//stackblocks`: Duplicate the region in one direction.
- [`/wall`](wall.md): Fill the walls in a region. It can also fill the inner part within the wall meanwhile.

## Entity commands

- [`/air`](air.md): Modify the entity's air value.
- [`/food`](food.md): Modify the entity's food value, saturation and exhaustion.
- [`/health`](health.md): Modify the entity's health value.
- [`/pile`](pile.md): Pile entities by riding.
- [`/tame`](tame.md): Tame or cancel taming the entity.
- [`/tprel`](tprel.md) Teleporting entities, and the coordinates and rotations are calculated based on each entity to be transported.
- [`/velocity`](velocity.md): Modify entity's speed.

## Test commands

- [`/testarg`](testarg.md): Test on argument types.
- `/testfor`: Can get and test some content in the world. At present, the following subcommands are supported:
    - [`/testfor block`](testfor/block.md): Get a single block, or test [block predicate](/documents/arguments/block_predicate.md).
    - [`/testfor blockinfo`](testfor/blockinfo.md): Get or test the information of a single block, such as hardness and light.
    - [`/testfor blocks`](testfor/blocks.md): Get information of multiple blocks, and test [block predicates](/documents/arguments/block_predicate.md).
    - [`/testfor entity`](testfor/entity.md): Get the information of entities selected by an [entity selector](/documents/arguments/entity_selector.md), or use an [entity predicate](/documents/arguments/entity_predicate.md) to test the entities.
    - [`/testfor biome`](testfor/biome.md): Get the information of the specified position, and test.

## Independent `/execute` subcommands

The subcommands of `/execute` are separated to single commands (former grammar is still normally available). For example, `/execute as @e at @s run summon creeper` can be written as `/as @e at @s summon creeper`.

Separated subcommands of `/execute` include:

- Condition subcommands: `/if` and `/unless`
    - Vanilla: `block`, `biome`, `loaded`, `dimension`, `score`, `blocks`, `entity`, `predicate`, `function`, `items`, `data` etc.
    - [`blockinfo`](if_and_unless/blockinfo.md): Execute the command when the block info match or does not match the specified condition.
    - [`rand`](if_and_unless/rand.md): Execute or do not execute the command on a specified probability.
- Attribution subcommands:
    - `/as`, `/at`, `/positioned`, `/rotateblocksd`, `/facing`, `/align`, `/anchored`, `/in`, `/summon` etc.
    - [`/inregion`](inregion.md) (added in the mod): Execute commands in each block coordinates within a range.
    - [`/silenced`](silenced.md) (added in the mod): Execute commands without leaving any feedback in the chat or console.
    - [`/for`](for.md) (added in the mod)
- Storage subcommands:
    - `/store`

## Simplified `/gamemode` commands

Commands of several game modes are all simplified.

- `/gmc [players]` is equivalent to `/gamemode creative [players]`
- `/gms [players]` is equivalent to `/gamemode survival [players]`
- `/gma [players]` is equivalent to `/gamemode adventure [players]`
- `/gmsp [players]` is equivalent to `/gamemode spectator [players]`

## Debug commands

- [`debug:deop`](debug_deop.md): Force to repeal admission permission from players, even if the executor does not have permissions.
- [`debug:op`](debug_op.md): Force to give players admission permission, even if the executor does not have permissions.
- [`debug:permissionlevel`](debug_permissionlevel.md): View the current permission level, or simulate the specified permission level to execute commands.

## Other commands:

- [`/history`](history.md): Manage operation history.
- [`/moon`](moon.md): Query and set moon phase. `/jadeplate` is an alise to this command.
- [`/nbt`](nbt.md): Query and set NBT data.
- [`/rand`](rand.md): Generate random number.
- [`/tasks`](tasks.md): Manage tasks in the current server.
- [`/undo` 和 `/redo`](undo_and_redo.md): Undo and redo.
