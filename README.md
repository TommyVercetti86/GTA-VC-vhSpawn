# GTA-VC-vhSpawn

--> This code spawns a vehicle in Grand Theft Auto Vice City

--> The code has been created by using "Sanny Builder 3" IDE and is based on the Youtube video "Cleo coding tutorial in Vice City : Basics" made by "Jwalin Bhatt"


--> Before starting, it is worth clarifying that, although the code is quite simple, it follows a very specific syntax. You can learn more about it on this site, where the IDE's documentation is shown: https://docs.sannybuilder.com/


At first glance, you will find a 4-blocks structure. Each block is named "label" and performs a specific action:

- label 1 : Resquests the vehicle model that we want to use. In this case the model will be the PCJ600

- label 2 : Using an "if" statement, the code will check if the model is available. If considered true, then the code jumps to the next block, otherwise it will return to label 1 and try again.

- label 3 : AAfter requesting and verifying the model, the code will generate the car at specific coordinates.

- label 4 : This last block is use for spawn. It tells the game to spawn the vehicle when a certain key is pressed.


--> Code:


                {$CLEO .cs} // This is the directive to compile a CLEO script
    
                0000: NOP //This is used to avoid a jump-at-zero-offset
                
                  :label4
                      0001: wait 0 ms                     // This is the "wait" command. It has one input argument that defines how long the game should "wait" until it can proceed to the next instruction 
                      00D6: if                            // This will create a loop where the model will be spawned every time we press a specefic key
                      00E1:   key_pressed 0 18            // With this command, we specify which key is going to be used to generate the vehicle. In this case, we will use "18", which is the "crouch" key.
                      004D: jump_if_false @label4 
                      0002: jump @label3
                      
                  :label1
                      0001: wait 0 ms
                      0247: request_model #PCJ600         // This will request the model that we will use. To specify the model, use # and type the vehicle name
                  
                  :label2
                      00D6: if
                      0248:   model #PCJ600 available    // This will check if the model is available. If not, it will be considered false and the loop will repeat until the model is available.
                      004D: jump_if_false @label1
                      0002: jump @label3
                  
                  :label3
                      04C4: create_coordinate 1@ 2@ 3@ from_actor $PLAYER_ACTOR offset 0.0 1.0 -1.0
                      00A5: 0@ = create_car #PCJ600 at 241.107 -1283.7081 10.9015                         // This sets the vehicle ID (0@) and spawns it at specific coordinates
                      0249: release_model #PCJ600                                                         // This will release the model to save memory
                      01C3: remove_references_to_car 0@                                                   // For turning a vehicle into a random car
                      0001: wait 0 ms
                      0002: jump @label4
                      05DC: end_custom_thread
