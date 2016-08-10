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

## Actions
### Cube Spawner Replication
Cube spawners will replicate at certain time intervals in all directions that
are set by *neightbours* field and *not occupied* by other cube spawners.

When choosing which cube spawners are to be placed, **[String]** part of the
*neightbours* field will be used. A table will be created that contains all
cube spawners in *groups* listed in **[String]** and all cube spawners with
*names* listed in **[String]**.
