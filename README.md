# BevoJump

Program Structure:

-   Render loop
-   ...

Questions:

1. Should the rendering be generalized so we can switch screens? IE. don't use pixels, use general units and write fns / macros to convert from general units to pixels for our screen.
    - I don't like how bad the viewing angles are on this screen. Also it's fairly small and low-res.
    - To be fair it's probably all the TM4C can handle
    - Calls into question a bigger issue of whether we should try to generalize the code to the degree that it can be played on other platforms too. (outlined in question 2)
2. Should we build a general "game engine" then build our game inside of it. Also should it be general enough that it can be adapted to different MCUs or other platforms.
    - Biggest problem I see with this is stuff like systick that are very specific. Maybe that would have to be platform-specific but the render loop and game logic could be cross platform.
    - Ideally we should have layers of abstraction. The core layer is the game engine itself. Above it is the compatibility layer with the specific platform we are on. Below it is the specific game we are building. _<-- Take a look at this Ethan, it is an interesting conept._

Structures: (because we are using C++ we can do OOP and inheritance)

-   Position/Velocity/Accel - ? better name ?
    -   X, Y position in (pixels?/units?)
    -   X, Y velocity in (pixels?/units?)
    -   X, Y, acceleration in (pixels?/units?)
-   HitBoxBounds
    -   X, Y relative size of hit box - calculated from top left of player (CHECK FLIPPING OF BMPS)
-   Sprite object

    -   Position/Velocity/Accel
    -   texture map - should texture be an array so we can have multiple states? (EG. open/compressed spring, happy/sad bevo)
    -   Hit box
    -   _SubSprites[]_ - sprites attached to original sprite with relative coordinates
        -   Ex: springs on platform
        -   Ex: Bevo's head if it can change/turn. That way we dont have to update the whole thing

-   Sprite :: Player

    -   ...sprite members
    -   isActive - is this the player being played or a multiplayer "ghost"
    -   ...

-   Sprite :: Platform
    -   ...sprite members
    -   type of platform - how to add graphic for spring for example? I think it should be separately added as a subSprite.

Helper Functions:

-   Collision detection
-

[Trello Board](https://trello.com/b/5CG38WG3/software)
