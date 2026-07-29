# Data structure

The data structure in this mod refer to the codec of mod contents, which means the pattern where they are serialized or deserialized (or encoded and decoded) between JSON or NBT.

For example, if a content has the following data structure:

- `name`: String.
- `age`: Integer.
- `member`: Boolean, optional, false by default.

it means this content is a map when serialized. After serializing to NBT it may become `#!snbt {name: Example, age: 25, member: true}`, and after serializing to JSON it may become `#!json {"name": "Example", "age": 25, "member": true}`.

Sometimes, when describing a data structure, what is specified may not be basic types but other types, which means it follows the data structure of this type. For example, if a field is described as follows:

- `can_use_on`: Block predicate.

the value of field `can_use_on` follows the data structure of block predicates.