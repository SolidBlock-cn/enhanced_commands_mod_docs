# `exhaustion`: Tests the entity's exhaustion

This [entity predicate](...md) tests the exhaustion value of the entity. Accepts float-point number ranges. Can be inverted. Similar to [`food`](../food.md), only players can be selected when this parameter is added.

## Examples

- `@a[exhaustion=0.5..]`: Selects players whose exhaustion value is at least 0.5.

## See also

See [the `/food` command](/documents/commands/food.md).

## Data structure

- `type`: Currently `"enhanced_commands:exhaustion"`.
- `exhaustion`: Floating-point number range.
- `inverted`: Boolean, optional, by default `false`.