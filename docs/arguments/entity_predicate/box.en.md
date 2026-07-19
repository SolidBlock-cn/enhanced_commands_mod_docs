# `box`

This [entity predicate](index.md) is used to limit the range to search for entities. This entity predicate exist only technically, because some vanilla entity selector options (such as `distance`, `dx`, `dy`, `dz`) restrict the range of entity search.

This entity predicate cannot be specified through entity selector arguments, please use [the `region` option](../region/index.md) instead.

## Data structure

- `type`: Currently `"enhanced_commands:box`.
- None of the other fields are supported.