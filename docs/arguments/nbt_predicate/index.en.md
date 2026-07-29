---
title: NBT predicate
---

# NBT predicate

**NBT predicate** is a condition used to test whether an NBT matches. Any NBT value either matches or does not match an NBT predicate.

Use [`#!js /testarg nbt_predicate <NBT predicate> match <NBT>`](../../commands/testarg.md) to test whether a specified NBT matches the specified predicate.

## Simple value

NBT predicates can directly test any NBT value. In the NBT predicate, except list and compound, directly expressing a value means such kind of simple predicate.

- `#!snbt 3s`: Passes when the NBT value is a short integer 3. For example, `3s` matches this predicate, `4s` and `2d` and other types such as `"string"` and `[]` do not match.
- `#snbt "str"`: Passes when the NBT value is a string `"str"`.

The NBT predicate of a simple value can be prefixed with "`:`". For example, `3s` is equivalent to `:3s`.

Before "`:`", "`!`" can be prepended, which is "`!:`", negates the predicate. For example, `#!js !: 3s` means it passes when the NBT value is not a short value 3.

Examples:

| predicate    | NBT to be tested | whether matches    |
|-------|----------|---------|
| `3s`  | `3s`     | `true`  |
| `3s`  | `3`      | `false` |
| `3s`  | `5`      | `false` |
| `str` | `str`    | `true`  |
| `str` | `STR`    | `false` |

!!! note
    Same as the parsing strategy of vanilla NBT value, text not in quotation marks that can be parsed as numbers will be parsed as numbers. Text not in quotation marks `true` of `false` will be parsed as byte value `1b` and `0b`. In other situations, the text will be parsed as strings, for example `abs` is equivalent to `#!js "abc"`. If the text not in quotation marks contain characters that cannot be outside of quotation marks, the parsing fails. For example, `happy ghast` is not a valid NBT value (because it contains spaces), and of course it cannot be used as an NBT predicate. Quotation marks are required to represent this string, which is `#!js "happy ghast"`.

## Any value

`*` can match any NBT value. `:*` and `=*` are equivalent.

| predicate  | NBT to be tested | whether matches   |
|-----|----------|--------|
| `*` | `123`    | `true` |
| `*` | `abc`    | `true` |
| `*` | `[]`     | `true` |

## Equal and comparison

Using `=` (equal sign) followed by a number value to test whether an NBT is equal to some value (in number values), regardless of its data type. This type of predicate only applies to any number-type nbt, and other NBT types cannot match this predicate.

- `= 3s`: Passes when it's equal to 3 in number values. For example, `3s`, `3` and `3d` match this predicate, and `4s` and `5` and other types not.
- `= 8.5`: Passes when it's equal to 8.5. For example, `8.5` and `8.5f` match this predicate, and `9`, `10s` and other types of values not.

If the equal sign is followed by a string or array, it is equivalent to simple predicates. For example, `= t` is equivalent to `: t` and `t`; `#!js = [i;1,2,3]` is equivalent to `#!js : [i;1,2,3]` and `#!js [i;1,2,3]`.

"`=`" can be followed by "`!`", which is "`!=`", meaning inverting the predicate. For example, `!= 3s` passes when the NBT does not equal to 3 in number values or the NBT is not of number types.

When followed by numbers or string, besides using equal signs, comparison symbols can also be used, including `>`, `<`, `>=`, `<=`.

Equal sign (`=`) and inequality sign (`!=`) can be followed by numbers or compound tags, lists or contents of other types, but after the comparison symbol, only numbers and strings can follow.

| predicate      | NBT to be tested | whether matches    |
|---------|----------|---------|
| `=3s`   | `3`      | `true`  |
| `=3.0`  | `3s`     | `true`  |
| `!=2`   | `2`      | `false` |
| `!=2`   | `2s`     | `false` |
| `>3s`   | `9`      | `true`  |
| `>=3s`  | `3`      | `true`  |
| `>=abc` | `def`    | `true`  |
| `>=[]`  | invalid       |         |

## Regular expressions

Regular expressions can be used to test strings. NBT values of other types cannot match this type of predicate.

- `~ "^abc"`: Passes when the NBT is a string and is prefixed by `abc`. `abc`, `abcd`, `abcAABB` match this predicate, and `bcd`, `ab`, `2`, `[]` cannot match this predicate.
- `~ "[Cc]at"`: Passes when the NBT is a string and match this regular expression. `cat` and `Cat` match this predicate.

Adding "`!`" before "`~`", which "`!~`", means a predicate that passes when the string does not match this regular expression.

In specific situations, quotation marks can be omitted, some characters (including `$`, `^`, `*`) are allowed not to be quoted, but if it contains characters like spaces or brackets, quotation marks are required. If the regular expression is invalid, the parsing fails.

| predicate          | NBT to be tested                     | whether matches    |
|-------------|-----------------------------------|---------|
| `~ ^abc`    | `abc`<br/> `abcd` <br/> `abcAABB` | `true`  |
| `~ ^abc`    | `bcd` <br/>`ab`<br/>`2`<br/>`[]`  | `false` |
| `~ "[Cc]at"` | `cat`<br/>`Cat`                   | `true`  |
| `~ "[Cc]at"` | `dog`<br/>`123`                   | `false` |
| `!~ ^abc`   | `abc`<br/> `abcd` <br/> `abcAABB` | `false` |
| `!~ ^abc`    | `bcd` <br/>`ab`<br/>`2`<br/>`[]`  | `true`  |

!!! info
    This syntax is fully identical to [`regex()`](regex.md).

## Compound tag

There are two types of matching for compound tags: accurate matching and inaccurate matching. This type of predicate only matches compound tags, and other types of NBT values do not match this predicate.

The syntax of a compound-tag predicate is similar to that of a compound tag, which is also a pair of curly braces and key-value pairs, but all the values are NBT predicates, and symbols other than colons may be used. If the curly braces is prefixed by an equal sign, it means accurate matching. In accurate matching mode, the NBT compound tag to be tested cannot contain any fields that are not specified, or the matching fails.

- `{a: 1}`: Passes when the NBT value is a compound tag and the value of field `a` is 1. Other tags in the compound tag do not affect. For example, `{a: 1}` and `{a: 1, b: 2}` both match this predicate.
- `= {a: 1}`: Passes when the NBT value is a compound tag and the value of field `a` is 1 and there are no other fields. For example, `{a: 1}` matches this predicate, but `{a: 1, b: 2}` does not.

| predicate         | NBT to be tested                              | whether matches    |
|------------|---------------------------------------|---------|
| `{a: 1}`   | `{a: 1}`<br/>`{a: 1, b: 2}`           | `true`  |
| `{a: 1}`   | `{b: 2}`<br/>`123`                    | `false` |
| `= {a: 1}` | `{a: 1}`<br/>                         | `true`  |
| `= {a: 1}` | `{a: 1, b: 2}`<br/>`{b: 2}`<br/>`123` | `false` |

Different predicates can be used for the content of compound tags. For example:

- `{a > 1}`: Passes when the `a` in the compound tag is greater than 1 in number values.
- `{a ~ "s$"}`: Passes when the `a` in the compound tag matches this regular expression.
- `{a = {x: y}}`: Passes when the value of `a` in the compound tag is a compound tag, and its `x` value is `y`, and there are no other fields.
- `{a !: b}`: Passes when the value of `a` in the compound tag exists and its value is not a string value `b`.
- `{a: *}`: Passes when the value of `a` in the compound tag exists.

| predicate             | NBT to be tested                                        | whether matches    |
|----------------|-------------------------------------------------|---------|
| `{a > 5}`      | `{a: 5}`<br/>`{a: 9b}`                          | `true`  |
| `{a > 5}`      | `{}`<br/>`{a: -1}`<br/>`{a: "str"}`             | `false` |
| `{a ~ "s$"}`   | `{a: floats}`<br/>`{a: values, b: other_value}` | `true`  |
| `{a ~ "s$"}`   | `{}`<br/>`{a: 1}`<br/>`{a: play}`               | `false` |
| `{a = {x: y}}` | `{a: {x: y}, b: other_value}`                   | `true`  |
| `{a = {x: y}}` | `{a: {x: y, z: w}}`                             | `false` |
| `{a !: b}`     | `{a: 3}`<br/>`{a: 123}`                         | `true`  |
| `{a !: b}`     | `{a: b}`<br/>`{}`<br/>`123`                     | `false` |
| `{a: *}`       | `{a: 1, b: 2}`<br/>`{a: [1, 2]}`<br/>`{a: ""}`  | `true`  |
| `{a: *}`       | `{b: 5}`                                        | `false` |

If negation is used in the compound tag, it still requires the field to exist to pass:

- `{a != *}`: Passes when the value of field `a` in the compound tag exists and is not any value. This predicate is valid, but no NBT values can match in theory.
- `{a != 3}`: Passes when the value of field `a` in the compound tag exists and is not a number value or does not equal to 3 in number values.

| predicate         | NBT to be tested                   | whether matches    |
|------------|----------------------------|---------|
| `{a != *}` | `{a: 5}`<br/>`{}`          | `false` |
| `{a != 3}` | `{a: floats}`<br/>`{a: 5}` | `true`  |
| `{a != 3}` | `{}`<br/>`{a: 3}`          | `false` |

In non-accurate matches, keys can be specified as star symbols, which means it passes when there is any field whose value matches this specified predicate:

- `{*: a}`: Passes when there is a field in the compound tag whose value is string `a`.
- `{* > 3}`: Passes when there is a field in the compound tag whose value is a number value and is greater than 3 in number values. For example, `{a: 5}` and `{b: 8}` both match this predicate.
- `{*: *}`: Passes when there is at least one value in the compound tag, which means any non-empty compound tags match this predicate.
- `= {*: b}`: Invalid NBT predicate, because predicates of accurate matching cannot use star symbols as keys.
- `{"*": a}`: As quotation mark is used, this NBT predicate as parsed as what passes when the value of the field whose name is a star symbol is `a`.

Currently, duplicate keys are not allowed in the accurate matching NBT predicate.

## List

The matching of lists is classified as accurate matching and inaccurate matching. The syntax of list predicates is similar to the that of lists, which is a square bracket wrapping NBT predicates targeting on elements separated with commas. Accurate matching is used when an equal sign be prepended before the list. NBT values other than lists cannot match this NBT predicate.

In accurate matching, the predicate passes only when the length and all elements of the list match, while in non-accurate matching, it passes as long as the predicates in the expected list can all find elements matching this predicate in the list to be tested:

- `#!js [1, 2, 3]`: Passes when the NBT value is a list, and the list contain the three values, regardless of the order. This predicate is equivalent to `[:1, :2, :3]`.
- `#!js =[1, 2, 3]`: Passes when the NBT value is a list, and the list has and only has three elements, and the three elements are 1, 2 and 3, without changing the order. As an equal sign is prepended before the list, elements inside it use equal-sign matching by default. This predicate is identical to  `= [=1, =2, =3]`.
- `#!js []`: Passes when the NBT value is a list, regardless of its contents.
- `#!js =[]`: Passes only when the list is empty.

| predicate           | NBT to be tested                          | whether matches    |
|--------------|-----------------------------------|---------|
| `[1, 2, 3]`  | `[3, 1, 2]`<br/>`[1, 3, 3, 2, 5]` | `false` |
| `[1, 2, 3]`  | `[1, 2]`<br/>`{key: value}`       | `false` |
| `=[1, 2, 3]` | `[1, 2, 3]`<br/>`[1, 2s, 3b]`     | `true`  |
| `=[1, 2, 3]` | `[3, 2, 1]`<br/>`[1, 2, 3, 4]`    | `false` |
| `[]`         | `[]`<br/>`[1, 2, 3]`              | `true`  |
| `=[]`        | `[1, 2, 3]`                       | `false` |

In the list predicate of non-accurate matching, one element may be matched by multiple predicates:

- `[>3, <5]`: Passes when the list contains an element greater than 3, and contains an element lower than 5. `[4]` and `[1, 8]` both match this predicate.
- `[3, 3]`: Passes when any element of the list is integer 3. `[3]` matches this predicate.

In non-accurate matching lists, indexes can be specified for list elements, meaning the element at the index must exist and match this predicate. Indexes can be negative values, meaning counting from last to first:

- `[a, 1: b]`: Passes when the list contains an element `a`, and the value of its 2nd element is `b`.
- `[0: a, -1: b]`: Passes when the 1st element in the list is `a` and the last element is `b`.
- `[5: *]`: Passes when the 6th element in the list exists.
- `= [5: *]`: Invalid, because the accurate matching list does not support specifying element indexes.

## Intersection, union, negation and parentheses

You can use symbol "`|`" to concatenate multiple NBT predicates to make unions, and the whole predicate passes when one of the predicates passes. You can also use symbol "`&`" to concatenate multiple NBT predicates to make intersections, and the whole predicate passes when all NBT predicates pass. Prepending "`!`" before an NBT predicate to negate. Besides, you can also wrap an NBT predicate with a pair of parentheses.

Without parentheses, the priority order of parsing: negation (`!`), intersection (`&`), union (`|`). `a|!b&c` is equivalent to `a|((!b)&c)`.

| predicate           | NBT to be tested          | whether matches    |
|--------------|-------------------|---------|
| `gray\|grey` | `gray`<br/>`grey` | `true`  |
| `gray&grey`  | `gray`<br/>`grey` | `false` |
| `gray&grey`  | `gray`<br/>`grey` | `false` |
| `(>3)&(<5)`  | `4`               | `true`  |
| `(>3)&(<5)`  | `3`、`9`           | `false` |

!!! note
    Without being wrapped in parentheses, spaces cannot be added around `|` and `&`, otherwise the content after the space will be parsed as the next command argument. However, spaces are allowed when wrapped in parentheses. For example:

    - ✔️The command is valid: `/testarg nbt_predicate a|b`
    - ❌The command is invalid: `/testarg nbt_predicate a | b`
    - ✔️The command is valid: `/testarg nbt_predicate (a | b)`

!!! info
    The syntax of intersection and union is identical to function grammars [`all()`](all.md) and [`any()`](any.md).

## Function grammar

NBT predicates support a series of function grammars. Before function grammars, "`=`" and "`:`" can be prepended like regular values, the two are the same. For example: `: all()` and `= all()` are equivalent to `all()`, and`{x: all()}` and `{x = all()}` are equivalent.

Currently, the following function grammars of NBT predicate are supported by this mod:

- [`any()`](any.md): Passes when any one NBT predicate passes.
- [`all()`](all.md): Passes when all NBT predicates pass.
- [`regex()`](regex.md): Passes when the regular expression matches.

## Data structure

- `type`: String, the [ID with default namespaces](../../glossaries/id_with_default_namespace.md) of the NBT predicate type. For predicates that can be represented as function grammars, the data structures are shown in separate pages.
- *(when `type` is `comparison`:)*
- `comparator`: String, the name of the symbol, identical to what the symbol itself looks like, such as `"="` and `">"`.
- `value`: NBT element.
- *(when `type` is `constant`:)*
- `value`: Boolean value. Regardless of the NBT to be tested, this boolean value will always be returned.
- *(when `type` is `equals_compound`:)*
- `values`: Map.
    - The key is the corresponding key in the NBT compound tag predicate, and the value is an NBT predicate.
- *(when `type` is `equals_list`:)*
- `values`: The list of NBT predicates.
- *(when `type` is `match_compound`:)*
- `entries`: Map or list. Map is used when all entries have keys specified and there are no duplicate keys, otherwise please represent it in a list. When storing, if all entries have keys specified and there are no duplicate keys, it will be stored in the form of the map, otherwise stored as a list.
    - *(if map)*
    - `<key>`: NBT predicate.
    - *(if list)*
    - An entry of the list, map.
        - `key`: Key. If not specified, it means any key, such as the "`*`" in `{*: a}`.
        - `value`: NBT predicate.
- *(when `type` is `match_list`:)*
- `values`: List of NBT predicates.
- `positional_values`: List.
    - An element. Map.
        - `index`: Integer.
        - `value`: NBT predicate.
- *(when `type` is `match_primitive`:)*
- `value`: NBT predicate.
- *(when `type` is `negating`:)*
- `value`: NBT predicate.
- *(when `type` is `range`:)*
- `range_number_type`: String.
- *(when `type` is `regex`:)*
- `pattern`: String, representing the regular expression.
- *(for other `type` values, please refer to separate pages of NBT predicates.)*
