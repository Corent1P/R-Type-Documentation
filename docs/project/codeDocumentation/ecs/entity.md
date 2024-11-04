# Entity

## Overview

> The Entity class is designed to hold and manage all the component belonging to it, and is identifiable by his own id.

## Class Definition

Located in `R-TYPE/src/ecs/Entity.hpp`.

## Construction

```cpp
    Entity(uint16_t id, std::shared_ptr<std::mutex> mtx, int serverId = -1);
```

Create a new entity.

- `id`: the unique identifier for this entity.
- `mtx`: Shared pointer to a std::mutex for ensuring thread-safe access to components.
- `serverId`: (Optional) - the server id associated with this entity.

## Destructor

```cpp
    ~Entity();
```

Destruct a entity.

## Attributes

> PRIVATE ATTRIBUTES

```cpp
std::unordered_map<std::type_index, std::shared_ptr<IComponent>> _typedComponents;
```

Map of components associated with the entity, indexed by type.

```cpp
uint16_t _id;
```

the unique identifier for this entity.

```cpp
std::shared_ptr<std::mutex> _mtx;
```

Shared pointer to a std::mutex for ensuring thread-safe access to components.

```cpp
int _serverId;
```

Identifier for the server associated with the entity.

## Methods

### Publics methods:

```cpp

const std::unordered_map<std::type_index, std::shared_ptr<RType::IComponent>> &getComponents(void) const;
```

Get access to the map of components associated with an entity.

```cpp
uint16_t getId(void) const;
```

Get access to the identifier of an entity.

```cpp
int getServerId(void) const;
```

Get access to the identifier of the server associated with an entity.

```cpp
void setServerId(int serverId);
```

Set the identifier of the server associated with an entity.

```cpp
void clearComponents(void);
```
Remove all the components in the component map.

```cpp
    static bool compareEntity(const std::shared_ptr<RType::Entity> &entity1, const std::shared_ptr<RType::Entity> &entity2);
```

Compare two entities identifier in order to sort them.

- `entity1`: Shared pointer to a first entity.
- `entity2`: Shared pointer to a second entity.

### Template methods

```cpp
template <typename T>

std::shared_ptr<T> pushComponent(std::shared_ptr<T> component) {
    std::unique_lock<std::mutex> lock(*_mtx);
    _typedComponents[typeid(T)] = component;
    return component;
}
```
Add a new Component of type T to the entity component map.
- `component`: A shared pointer of type T to the component added.

```cpp
template <typename T>

std::shared_ptr<T> getComponent() const {
    std::unique_lock<std::mutex> lock(*_mtx);
    auto it = _typedComponents.find(typeid(T));
    if (it != _typedComponents.end()) {
        return std::static_pointer_cast<T>(it->second);
    }
    return nullptr;
}
```
Get a specific component of type T from the entity component map.


## Usage example

```cpp
//Create a new entity with id 1, a mutex, and serverId 42
auto entity = std::make_shared<RType::Entity>(1, std::make_shared<std::mutex>(), 42);

//Add a component of type YourComponentX
entity->pushComponent(std::make_shared<YourComponent>());

//Get the component if it exists
auto component = entity->getComponent<YourComponent>();

//Print entity details
std::cout << *entity << std::endl;
```
This example demonstrates the basic usage of the Entity class, handling a Component.