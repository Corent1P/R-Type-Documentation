# System


## Overview
A System is a class inheriting from the absotract class `ASystem`, used to take specific entities, and handle their components to modify their values to get a dedicated task to be done.

## Class Definition

Located in `R-TYPE/src/ecs/ISystem.hpp`.
Located in `R-TYPE/src/ecs/ASystem.hpp`.

The abstract Class `ASystem` is made in order to implement the most generic methods like:
- `effects()`: the method looping on each entities checking if they have the mandatory Components. (note: this method may be re-implemented on specifics system that require two distinct entity in their process).

## Construction

```cpp
ASystem(SystemType type = S_BASIC, std::function<std::shared_ptr<Entity>()> addEntity = nullptr, std::function<void(std::shared_ptr<Entity>)> deleteEntity = nullptr);
```
This constructor initializes the system with a specified type and functions for adding and deleting entities.
- `type`: the type of system created.
- `addEntity`: A function to add a entity to the coordinator.
- `deleteEntity`: A function to delete a entity to the coordinator.

## Protected Attributes

Common to all System:

```cpp
std::function<std::shared_ptr<Entity>()> _addEntity;
```
Add a new entity to the coordinator.

```cpp
std::function<void(std::shared_ptr<Entity>)> _deleteEntity;
```
Delete a entity from the coordinator.

Each System may have some specific private attribue based on their needs.

For example:

In `HandleEventSystem`:
```cpp
bool _isShooting;
```
boolean about the player shooting state.

```cpp
std::function<void(void)> _disconnexion;
```
a function disconnection a player.


## Public Methods

```cpp
void effects(std::vector<std::shared_ptr<RType::Entity>> entities);
```
Loop on all the coordinator entity, identifying on which entity the system action is about to be done. Can also be used if a system Require two different entities.
-`entities`: a vector of all entities contained in the coordinator.

```cpp
void effect(std::shared_ptr<RType::Entity> entity);
```
handle the specific system action on the specified entity.
-`entity`: a specific entity having the mandatory components.

```cpp
bool verifyRequiredComponent(std::shared_ptr<RType::Entity> entity);
```
Verifies if the provided entity has the required component for processing the system action.
-`entity`: The entity to verify.

```cpp
SystemType getType() const;
```
Get the type of the System.

## Usage example

### How to create your own System
>1. Create your own System files in the `/src/ecs/Systems/` folder:
- Filename: `HandleYourSystem.cpp` | `HandleYourSystem.hh`
- Add your system `HandleYourSystem.cpp` file to the CMakeLists.txt in the `src/ecs/` folder.
```cmake
set(SRC_SYSTEMS ./Systems/HandleYourSystem.cpp);
```

>2. File content:
`HandleYourSystem.hh:`
- Use the RType namespace.
- Inherit the ASystem abstract class.
- Attributes and specific new methods must be private.
- Include the mandatory Component .hh files.

```cpp
#ifndef HANDLE_YOUR_SYSTEM_HPP_
#define HANDLE_YOUR_SYSTEM_HPP_

#include "ASystem.hpp"
#include "Entity.hh"
#include "ComponentType.hpp"

#include <iostream>
#include <vector>
#include <memory>

namespace RType {
    class HandleYourSystem : public ASystem {
        public:
            HandleYourSystem(std::function<std::shared_ptr<Entity>()> addEntity = nullptr,
                             std::function<void(std::shared_ptr<Entity>)> deleteEntity = nullptr);
            void effects(std::vector<std::shared_ptr<Entity>> entities) override;
            void effect(std::shared_ptr<Entity> entity) override;
            bool verifyRequiredComponent(std::shared_ptr<Entity> entity) override;
    };
}

#endif /* HANDLE_YOUR_SYSTEM_HPP_ */
```

`HandleYourSystem.cpp:`
- Methods: re-implement the `verifyRequiredComponent()` method with the mandatory Components.
    \(optional) - Re-implement the `effects()` method if needed.

```cpp
#include "HandleYourSystem.hpp"

RType::HandleYourSystem::HandleYourSystem(std::function<std::shared_ptr<Entity>()> addEntity, std::function<void(std::shared_ptr<Entity>)> deleteEntity)
: ASystem(S_BASIC, addEntity, deleteEntity) {}

void RType::HandleYourSystem::effects(std::vector<std::shared_ptr<Entity>> entities) {
    for (auto &entity : entities) {
        if (verifyRequiredComponent(entity)) {
            effect(entity);
        }
    }
}

void RType::HandleYourSystem::effect(std::shared_ptr<Entity> entity) {
    //Applying effect to Entity
}

bool RType::HandleYourSystem::verifyRequiredComponent(std::shared_ptr<Entity> entity) {
    //Check if the entity have the right components
    if (entity->getComponent<RType::ComponentType>() == nullptr) {
        return false;
    }
}
```

This example demonstrates a basic create of a System in our ECS design pattern.