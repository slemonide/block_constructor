# block_constructor
A mod for minetest for generating constructions

## Types
* Cube Spawner
...Simply an invisible object that gets to be at the *center* of the cube

   Has a field called *name*
        name :: String

Has a field called *groups*
... groups :: [String]

..*Has a field that contains a dictionary in the format
... Position | Name or Group
... --- | ---
... (x,y,z) | {"name", "group:group", ...}

... This field tells
* Cube
...A part of a bigger construction
