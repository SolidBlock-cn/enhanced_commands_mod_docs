# Block Function

The **block function** is an [argument type](index.md) used to modify a block (including block entity) at a certain position in the world.

## Basic usage

Block functions can use block ID and can also specify block state properties and NBT, like vanilla. Generally speaking, original blocks are directly ignored in these cases. For example:

- `minecraft:stone`: Stone.
- `minecraft:redstone_lamp[lit=true]`: Lit redstone lamp.
- `minecraft:repeating_command_block{Auto: true}`: Repeating command block that runs automatically.

## Compound block function

Multiple block functions can be compounded to produce a more complex block function.

- `<block function 1>*<block function 2>`: Two or more block functions are applied in order. The result of the first function acts as the parameter for the second function.
- `<block function 1>|<block function 2>`: Two or more block functions are selected randomly. One of the two block functions will be randomly chosen to apply.

The order of the two block functions above is, first `*` then `|`. For example, `a|b*c` is identical to `a|(b*c)`.

These two syntaxes cannot be space-separated, but if they are in a parentheses, space is allowed. For example, `a | b` is invalid, but `(a | b)` and `dry(a | b)` are valid.

For example (all the examples below omitted namespace):

- `stone|dirt|grass_block`: Randomly select stone, dirt and grass block.
- `black_wool|white|wool`: Randomly select black wool and white wool.

## Full list

### Non-function-like syntax

- [Simple block function: `block id`](simple.md): Simply use the block of the specified ID.
- [Tag block function: `#tag id`](tag.md): Randomly choose a block from the block tag.
- [Properties block function: `[proeprty=value]`](property_names.md): Modify the properties of the current block.
- [NBT block function: `{}`](nbt.md): Modify the block's NBT data.
- [Properties NBT combination: `block id[...]{...}`](property_nbt_combination.md): Set the id or tag, block state properties and NBT of blocks, which is similar to vanilla usage.
- [Random block function: `*`](random.md): Randomly choose a block and random select a block state.
- [Original block function: `~`](use_original.md): Use the block before the whole function evaluation.
- [Reference block function: `$`](reference.md): Reference a block function defined in the data pack.

### Function-like syntax

- [`checkerboard(<block function> [weight] ...)`](checkerboard.md): Checkerboard pattern.
- [`checkerboard-tag(<block function> [weight] ...)`](checkerboard-tag.md): Checkerboard pattern whose content is the blocks with a block tag.
- [`dry([block function])`](dry.md): Remove water from the current block, or apply the block function and then remove water.
- [`filter(<block function 1>, <block predicate>, [block function 2])`](filter.md): Calculate the result of block function 1 first, and if the result of block function 1 matchest the block predicate, then it is applied directly, or block function 2 will be calculated, or do nothing.
- [`idcontain(<regex>)`](idcontain.md): Randomly pick a block whose ID matches the specified regular expression.
- [`idreplace(<regex>)`](idreplace.md): Replace the block ID. If the replaced block ID still exists, it will be applied.
- [`if(<block predicate>, <block function 1>, [block function 2])`](if.md): Test which the former block match the block predicate, and if so, use block function 1, or use block function 2 to do nothing.
- [`ifs(<block predicate 1>, <block function 1a>, [block function 1b]; ...)`](ifs.md): Test multiple block predicates.
- [`mirror(<方向>)`](mirror.md): Mirror the current block.
- [`noise(<block function> [weight], ...; ...)`](noise.md): Noise.
- [`overlay([block function], ...)`](overlay.md): Apply multiple block functions in order.
- [`pick(<block function>, ...)`](pick.md): Randomly choose a block function.
- [`postprocess<direction> ...`](postprocess.md): Postprocess blocks, such as solving connection issues of fences and walls.
- [`random()`](random.md): Randomly chose a block state. Similar to the random block function above, but supports specifying the seed.
- [`rotate(<方向>)`](rotate.md): Rotate the current block.
- [`stonecut([block function])`](stonecut.md): Apply stonecutting on the current block or the result of the specified block function. If there are multiple stonecut results, select one stonecut result randomly.

## Data structure

- `type`: String. ID of the block function type.
- Fields that the type may have.

There are following types of block functions (the namespace `enhanced_commands` are all omitted in the list):

- [`simple`](simple.md)
- [`property_names`](property_names.md)
- [`nbt`](nbt.md)
- [`properties_nbt_combination`](property_nbt_combination.md)
- [`empty`](empty.md)
- [`random`](random.md)
- [`tag`](tag.md)
- [`use_original`](use_original.md)
- [`checkerboard`](checkerboard.md)
- [`checkerbard-tag`](checkerboard-tag.md)
- [`conditional`](if.md)
- [`conditions`](ifs.md)
- [`dry`](dry.md)
- [`filter`](filter.md)
- [`id_contain`](idcontain.md)
- [`id_replace`](idreplace.md)
- [`mirror`](mirror.md)
- [`noise`](noise.md)
- [`overlay`](overlay.md)
- [`pick`](pick.md)
- [`post_process`](postprocess.md)
- [`reference`](reference.md)
- [`rotate`](rotate.md)
- [`stonecut`](stonecut.md)