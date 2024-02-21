# GTA-VC-vhSpawn

-- This code spawns a vehicle in Grand Theft Auto Vice City

-- The code has been created by using "Sanny Builder 3" IDE and is based on the Youtube video "Cleo coding tutorial in Vice City : Basics" made by "Jwalin Bhatt"

-> Before starting, it is worth clarifying that, although the code is quite simple, it follows a very specific syntax. You can learn more about it on this site, where the IDE's documentation is shown: https://docs.sannybuilder.com/

-   At first glance, you will find a 4-blocks structure. Each block is named "label" and performs a specific action:

        label 1 : Resquests the vehicle model that we want to use. In this case the model will be the PCJ600

        label 2 : Using an "if" statement, the code will check if the model is available. If considered true, then the code jumps to the next block, otherwise it will return to label 1 and try again.

        label 3 : AAfter requesting and verifying the model, the code will generate the car at specific coordinates.

        label 4 : This last block is use for spawn. It tells the game to spawn the vehicle when a certain key is pressed. 
