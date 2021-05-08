---
layout: default
title: Particularities
parent: Tips
nav_order: 2
---

# Particularities
* Always make sure the root character entity has (1,1,1) scale. You are allowed to scale child entities
* The character entity (the one with the `KinematicCharacterBody` component) must never be a child of another entity
* All physics bodies that the character can stand on, or all bodies that can be set as the character's `ParentEntity`, must have a `TrackedTransform` component in order to work properly
* You must enable the `SynchronizeCollisionWorld` option on the PhysicsStep component if you want to eliminate jitter and visual lag when moving against other moving bodies