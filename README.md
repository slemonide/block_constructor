# block_constructor
A mod for minetest for generating constructions

## Types
* Cube Spawner

    Simply an invisible object that gets to be at the *center* of the cube

    Has a field called *name*

        name :: String

    Has a field called *groups*
        groups :: [String]

    Has a field called *neightbours*

        neightbours :: {(Int, Int, Int) = [String]}
        
        Example: neightbours = {(x1,y1,z1) = ["name1", "group:group1", ..], (x2,y2,z2) = ... }

* Cube

    A part of a bigger construction. A Cube is spawned by Cube Spawner.
    
    Simply a decorative element.

## Actions
