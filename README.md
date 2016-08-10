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
    local coordinate system of the cube.

## Actions
### Cube Spawner Replication
Cube spawners will replicate at certain time intervals in all directions that
are set by *neightbours* field and *not occupied* by other cube spawners.

When choosing which cube spawners are to be placed, **[String]** part of the
*neightbours* field will be used. A table will be created that will contain all
cube spawners in *groups* listed in **[String]** and all cube spawners with
*names* listed in **[String]**. Then, those cube spawners will be filtered
by their own *neightbours* fields in such way so that they will meet
*neightbours* fields of already placed cube spawners. After that,
the cube spawner to be placed (if there is more than one remaining in the list)
will be determined randomly.


## Included building blocks
*   block_constructor:wall
*   block_constructor:ceiling
*   block_constructor:floor
*   block_constructor:carpet
*   block_constructor:lamp
*   block_constructor:light{1-14}

## Miscellaneous
**block_constructor:light{1-14}** will be a set of invisible blocks of type air
with light value set to them (it will be equal to the number in the end of the name).
It can be used to illuminate some cubes with poor illumination.
