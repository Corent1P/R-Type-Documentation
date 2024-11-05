# ECS design pattern Documentation

## Overview

The ECS (Entity Component System) pattern is a way to structure our code in a way that is more efficient and easier to maintain. It is based on the following components:

- [Entity](./project/codeDocumentation/ecs/entity): An entity is an object that exists in the game world. Entities can be anything, from a player to a bullet or a button. An entity is essentially a container for components.
- [Component](./project/codeDocumentation/ecs/component): A component is a piece of data that is attached to an entity. Components are used to add functionality to an entity. For example, a `PositionComponent` could be used to store the position of an entity.
- [System](./project/codeDocumentation/ecs/system): A system is a piece of code that operates on entities that have a specific set of components. Systems are used to update the state of the game world. For example, a `MovementSystem` could be used to update the position of entities based on their velocity.

---

<img src="_media/ECS.drawio.svg" style="width:auto; height:auto;" alt="Cover Image">