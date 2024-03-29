Back to [How To](../how-to.md)

# Networking

(for a full example of predicted character networking, see the OnlineFPS sample)

## Synchronized data

Predicted character networking typically requires the following data to be synchronized over network. This is the data that represents the required initial character state that will always result in the same outcome after you run a character update with it:
* `Translation`
* `Rotation` (unless your character doesn't rotate, or unless the character rotation is fully calculated from other data that is already synchronized over network, such as velocity direction or camera angles. Also note that if your character only rotates around its Y axis, you can only synchronize the Y angle of the rotation, and then reconstruct the rotation from that)
* `KinematicCharacterBody.RelativeVelocity` (unless your velocity calculation is completely stateless and doesn't rely on any previous velocity)
* `KinematicCharacterBody.IsGrounded` (only necessary if you use grounding detection for this character)
* `KinematicCharacterBody.ParentEntity` (only necessary if you use the ParentEntity mechanism in your game, like for moving platforms)

The rest of the fields in `KinematicCharacterBody` typically don't need to be synchronized unless you manually modify them. For example, you don't need to synchronize `KinematicCharacterBody.EvaluateGrounding` unless you manually set it to a different value at some points in your code. This field doesn't change by itself otherwise.

Several other fields of `KinematicCharacterBody`, such as `GroundHit`, `WasGroundedBeforeCharacterUpdate`, `ParentVelocity`, `PreviousParentEntity`, etc... are all calculated entirely during the frame, and therefore never need to be synchronized. However, you need to make sure that none of your game code accesses those values before `KinematicCharacterUtilities.InitializationUpdate` has run (this is where they are reset).

And finally, you must synchronize any field in your own custom character components that are important to the character's "state" (the fields that are needed at the beginning of the character update in order to always give the same outcome, and that can change during the game).


## Prediction loop

In order to include the character logic in DOTS NetCode's prediction loop, the following steps are necessary:
* The character system must update in the `GhostPredictionSystemGroup`
* The CollisionWorld used by the character update must be a collision world that represents the world at the time where the predicting tick happened. You can either use NetCode's `PhysicsWorldHistory` to get the CollisionWorld at the predicted tick, or create a system in the prediction group that rebuilds the `PhysicsWorld` before the character update
* Make sure to call `GhostPredictionSystemGroup.ShouldPredict` before running the character update. We must only update the character logic if we must predict.
* Make sure to use the player commands from the predicted tick as inputs for the character movement.

## Networking moving platforms

todo: will come at a later date


## Sample

A fully-functional Online FPS sample is included with Rival's samples. Read more about it on the [Sample](../samples.md) page.

Note: In the sample project, the synchronization of character component fields is declared in a `OnlineFPSGhostOverrides` class instead of in the inspector of the character prefab. We do this because of an issue with DOTS netcode where the ghost inspector sometimes won't work under certain conditions, but it should get fixed in a future release of netcode