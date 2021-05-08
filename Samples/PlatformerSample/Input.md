---
layout: default
title: Input
parent: Platformer Sample
grand_parent: Samples
nav_order: 2
---

# Input

`PlatformerPlayerInputsSystem` gathers input from Unity's input system, and writes those inputs to all `PlatformerPlayerInputs` components present in the world.

`PlatformerPlayerInputsToCharacterInputsSystem` takes the inputs from `PlatformerPlayerInputs` components, and converts them to inputs that the character system can understand in the `PlatformerCharacterInputs` component.

This separation of input handling in two separate phases ("player" inputs and "character" inputs) is done so that AI characters can easily be supported.