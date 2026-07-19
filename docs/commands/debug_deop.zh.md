# `/debug:deop`

此[命令](index.md)用于调试，可以剥夺指定玩家的管理员权限，而无需命令的执行者拥有权限。

!!! danger "危险"
    此命令可以被任何玩家执行（包括非管理员）。除非你是在调试或测试，请使用命令  `/enhanced_commands:config commands enable_debug_commands false` 以禁用调试命令（在非开发环境中默认被禁用）。

## 语法

- `/debug:deop [目标]`

## 参数

### `[目标]`

[实体选择器](../arguments/entity_selector.md)。只能包含玩家。如果不使用实体选择器，可以直接指定不在线的玩家的名称。

## 参见

- [`/debug:op`](debug_op.md)