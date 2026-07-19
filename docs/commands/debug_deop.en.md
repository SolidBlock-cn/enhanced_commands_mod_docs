# `/debug:deop`

The [command](index.md) is used to debug, and can repeal the specified players of administrator permission, without requiring the executor of the command having the permission.

!!! danger
    The command can be executed by any player (including non-operators). Unless you are debugging or testing, please use command `/enhanced_commands:config commands enable_debug_commands false` to disable debug commands (which is disabled by default if not in the development environment).

## Syntax

- `/debug:deop [targets]`

## Parameters

### `[targets]`

[Entity selector](../arguments/entity_selector.md). Only contains players. If the entity selector is not used, it can directly reference the name of a player not online.

## See also

- [`/debug:op`](debug_op.md)