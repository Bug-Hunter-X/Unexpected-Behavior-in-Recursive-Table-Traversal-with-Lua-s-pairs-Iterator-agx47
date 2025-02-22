# Lua Recursive Table Traversal Bug

This repository demonstrates a potential issue with Lua's `pairs` iterator when used in recursive table traversal.  The bug arises from the unpredictable iteration order of `pairs` if the table is modified during iteration.  The provided code recursively traverses a nested table, but the output may vary inconsistently between Lua versions or runtime conditions.

## Bug Description
The `foo` function recursively iterates over a table using `pairs`. If the table structure is modified during iteration, `pairs`'s order is not guaranteed, leading to unexpected results.

## Solution
The solution is to create a copy of the table before iterating, ensuring that the original table remains unchanged, and the iterator won't see changes in-flight.

## How to reproduce
1. Save the code in `bug.lua`.
2. Run the Lua script (e.g., using `lua bug.lua`).
3. Observe the inconsistency of the output in different Lua implementations or runs.