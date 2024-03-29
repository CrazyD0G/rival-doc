Back to [Samples](../../samples.md)

# OnlineFPS Sample - Input and Player Commands

`OnlineFPSPlayerInputsSystem` gathers input from Unity's input system, and writes those inputs to all `OnlineFPSPlayerInputs` components present in the world.

`OnlineFPSPlayerCommandsSystem` reads raw input from the `OnlineFPSPlayerInputs` components, and converts them to commands that are added to the `OnlineFPSPlayerCommands` DynamicBuffer. 

This separation of input handling in two separate phases ("player" inputs and "commands") is done so that AI characters can easily be supported, and also because in a real game, not all local player inputs should necessarily be part of the commands that are sent over network (ex: input related to opening menus, etc...).