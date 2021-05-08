---
layout: default
title: Moving Platforms
parent: How-To
nav_order: 3
---

# Moving Platforms

## Standing on moving platforms

In order to have a character that can stand on other physics bodies (like a moving platform), you must:
* set that body entity as the `KinematicCharacterBody.ParentEntity`
* make sure that body entity has a `TrackedTransform` component (via the `TrackedTransformAuthoring` component)

A `KinematicCharacterUtilities.DefaultMovingPlatformDetection` utility function is available for you to call in your character update, if you want to automatically set the `KinematicCharacterBody.ParentEntity` to whatever body the grounding detection has detected as the ground hit every frame. The default code-generated character already has this, but you can remove it if you want.

## Pushing and Getting pushed by moving platforms

In order to have proper character velocity handling and to avoid jitter when pushing or getting pushed by moving bodies, it is necessary for those moving bodies to be moved with their physics velocity instead of simply moving their transforms. The character uses the other body's velocities (linear and angular) in its solving of the collision velocities.