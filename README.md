# block_constructor
A mod for minetest for generating constructions

## Types
### Cube Spawner
Simply an invisible object that gets to be at the *center* of the cube

Has a field called *name*

    name :: String

Has a field called *groups*

    groups :: [String]

Has a field called *neightbours*

    neightbours :: {(Int, Int, Int) = [String]}
        
    Example: neightbours = {(x1,y1,z1) = ["name1", "group:group1", ..], (x2,y2,z2) = ... }

### Cube
A part of a bigger construction. A Cube is spawned by Cube Spawner.
Simply a decorative element.
    
A cube will be stored as an .mts file or as a function of position in the
local coordinate system of the cube. When loading a cube from an .mts file,
blocks that start with *block_constructor:* can be replaced to create a greater
variety of cubes. Each loaded cube will be assigned its *Cube Spawner* with
appropriate *name* and *groups*. *Neightbours* is a function of *groups*.
See **Loading** for details.

## Actions
### Cube Spawner Replication
Cube spawners will replicate in certain conditions in all directions that
are set by *neightbours* field and *not occupied* by other cube spawners.

When choosing which cube spawners are to be placed, **[String]** part of the
*neightbours* field will be used. A table will be created that will contain all
cube spawners in *groups* listed in **[String]** and all cube spawners with
*names* listed in **[String]**. Then, those cube spawners will be filtered
by their own *neightbours* fields in such way so that they will meet
*neightbours* fields of already placed cube spawners. After that,
the cube spawner to be placed (if there is more than one remaining in the list)
will be determined randomly.

Conditions in which cube spawners will replicate:
* A player is near

## Included building blocks
* block_constructor:wall
* block_constructor:ceiling
* block_constructor:floor
* block_constructor:carpet
* block_constructor:lamp
* block_constructor:light{1-14}

## Miscellaneous
**block_constructor:light{1-14}** will be a set of invisible blocks of type air
with light value set to them (it will be equal to the number in the end of the name).
It can be used to illuminate some cubes with poor illumination.

## Loading

## File Structure
* **init.lua** (contains chat command for adding an arbitrary cube spawner)
* **cube_spawners.lua** (contains definitions of cube spawners and logic related to
  spawning cubes)
* **replication.lua** (contains cube spawners replication logic)
* **building_blocks.lua** (contains included building blocks)
* **add_cubes.lua** (contains tools for adding cubes ingame)
* **cubes/**
  * **cube_name.lua** (contains cube placing function and metadata (name and groups).
* **mts/**
  * **cube_name.mts** (optional)
* **groups/**
  * **group_name.lua** (contains neightbours fields for the group)
