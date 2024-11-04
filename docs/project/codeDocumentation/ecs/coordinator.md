# Coordinator


## Overview

>The coordinator class manage all Entities & Systems of our ECS design pattern. It containes all the Entities and System of the game, centralising their management.

## Class Definition
Located in `R-TYPE/src/ecs/Coordinator.hh`.

## Construction
```cpp
    Coordinator();
```
Create a new coordinator.

## Destructor
```cpp
    ~Coordinator();
```
Destruct a coordinator.

## Attributes

> PRIVATE ATTRIBUTES
System and Entities are stored in the coordinator thanks to vectors.

```cpp
std::vector<std::shared_ptr<Entity>> _entities;

```
A vector of object of class `RType::Entity`,  store each entity contained in the coordinator.

```cpp
std::vector<std::shared_prt<ISystem>> _systems;
```
A vector of object of class `RType::ISystem`, store each entity contained in the coordinator.


## Methods

> PUBLIC METHODS:

###   Entity methods:

```cpp
std::shared_ptr<Entity> generateNewEntity(uint16_t serverId = -1);
```
Create a new Entity and add it to the coordinator.
- `uint16_t serverId`: the server id.

```cpp
std::shared_ptr<Entity> addEntity(void);
```
Create a new Entity, passed to systems to create new entities based on specific events.

```cpp
void deleteEntity(std::shared_ptr<Entity> entityToDestroy, bool lock = true);
```
Delete a specific entity of the coordinator.
- `entityToDestroy`: the target entity supposed to be destroyed.
- `lock`: (optional) - If true, locks the operation for thread safety.

```cpp
const std::vector<std::shared_ptr<Entity>> &getEntities() const;
```
Get access to all entities stored in the coordinator.


###  System methods:

```cpp
void generateNewSystem(std::shared_ptr<ISystem> sys);
```
Create a new system and add it to the coordinator.
- `sys`: the system that we want to add to the coordinator.

```cpp
const std::vector<std::shared_ptr<ISystem>> &getSystems() const;
```
Get access to all system stored in the coordinator.

> PRIVATE METHODS

```cpp
std::size_t getNextEntityId(void);
```
Get the next entity id.

## Usage exemple:

```cpp
//Create a new coordinator.
RType::Coordinator coordinator;

//Add a new entity to the coordinator.
auto entity = coordinator.generateNewEntity();

//add a new system to the coordinator.
coordinator.generateNewSystem(std::make_shared<SomeSystem>());
```
This example demonstrates the basic usage of the Coordinator class, creating a new entity and system.