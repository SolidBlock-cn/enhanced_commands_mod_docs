---
title: advancements
subtitle: Tests player's advancement
---

# `advancements`: Tests player's advancement

This [entity predicate](index.md) tests player's advancement. Same as vanilla, but when specifying advancement criteria, quoted strings are allowed.

## Syntax

- `[advancements={<advancement id> = <boolean>, ...}]`
- `[advancements={<advancement id> = {<criterion> = <boolean>, ...}, ...}]`

## Data structure

- `type`: Currently `"advancements"`.
- `advancements`: Map.
    - `<advancement id>`: Boolean or map. If map, has the following fields:
        - `<criterion>`: Boolean.