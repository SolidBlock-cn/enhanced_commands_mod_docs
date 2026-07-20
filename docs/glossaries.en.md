# Glossaries

This page contains some phrase conventions of Enhanced Commands mod.

## Data structure

The data structure in this mod refer to the codec of mod contents, which means the pattern where they are serialized or deserialized (or encoded and decoded) between JSON or NBT.

For example, if a content has the following data structure:

- `name`: String.
- `age`: Integer.
- `member`: Boolean, optional, false by default.

it means this content is a map when serialized. After serializing to NBT it may become `{name: Example, age: 25, member: true}`, and after serializing to JSON it may become `#!json {"name": "Example", "age": 25, "member": true}`.

Sometimes, when describing a data structure, what is specified may not be basic types but other types, which means it follows the data structure of this type. For example, if a field is described as follows:

- `can_use_on`: Block predicate.

the value of field `can_use_on` follows the data structure of block predicates.

## ID with default namespace

In the data structure of this mod, some IDs when converting between strings, use namespaces different from `minecraft`. Without special explanation, the "ID with default namespace" has the default namespace `enhanced_commands`. When converting strings to IDs, those without namespaces specified use the default namespace. If "simply" is specified, when the ID is represented as a string, when the namespace of the ID is just the default one, the namespace will be emitted.

## Tag or direct list

A special data type of Minecraft (`#!java HolderSet`), which can specify an inline list of a series of entries, or specify with a data-pack tag (the format is a string with hash and tag ID).

For example, if there is a field like follows:

- `available_items`: Tag or direct list of items.

it means the value of field `available_items` can be either a direct list (`#!json ["diamond", "iron_ingot", "emerald"]`), or a tag (such as`#!json "#stairs"`).