# block_constructor
A mod for minetest for generating constructions

## Types
### Block
A node. A part of a bigger construction.

Has a field called *name*

    name :: String

Has a field called *groups*

    groups :: [String]

Has a field called *neightbours*

    neightbours :: {(Int, Int, Int) = [String]}
        
    Example: neightbours = {(x1,y1,z1) = ["name1", "group:group1", ..], (x2,y2,z2) = ... }

## Actions
### Block Replication
Blocks will replicate under certain conditions in all directions that
are set by *neightbours* field and *not occupied* by other blocks.

When choosing which blocks can be placed, **[String]** part of the
*neightbours* field will be used. A table will be created that will contain all
possible blocks with *groups* listed in **[String]** and all blocks with
*names* listed in **[String]**. Then, those cube spawners will be filtered
by their own *neightbours* fields in such way so that they will meet
*neightbours* fields of already placed blocks. After that,
the block to be placed (if there is more than one remaining in the list)
will be determined randomly.

Conditions under which blocks will replicate:
* A player is near

## Miscellaneous blocks
**block_constructor:light{1-14}** will be a set of invisible blocks of type air
with light value set to them (it will be equal to the number in the end of the name).
It can be used to fix poor illumination.

## Loading

## File Structure
* **init.lua** (contains chat command for adding an arbitrary block and light nodes)
* **block_spawn.lua** (contains logic related to spawning blocks)
* **replication.lua** (contains logic related to replicating blocks)
* **add_blocks.lua** (contains tools for adding blocks ingame)
* **blocks/**
  * **block_name.lua** (contains block placing function and metadata (name and groups)).
* **groups/**
  * **group_name.lua** (contains neightbours fields for the group)
