---
title: Tag or direct list
---

# Tag or direct list

A special data type of Minecraft (`#!java HolderSet`), which can specify an inline list of a series of entries, or specify with a data-pack tag (the format is a string with hash and tag ID).

For example, if there is a field like follows:

- `available_items`: Tag or direct list of items.

it means the value of field `available_items` can be either a direct list (`#!json ["diamond", "iron_ingot", "emerald"]`), or a tag (such as`#!json "#stairs"`).