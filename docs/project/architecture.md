# Architecture Overview

## ECS

The architecture of the project is based on the following components:

In both our client and server, we use the ECS (Entity Component System) pattern. This pattern is a way to structure our code in a way that is more efficient and easier to maintain. It is based on the following components:

- **Entity**: An entity is an object that exists in the game world. Entities can be anything, from a player to a bullet or a button. An entity is essentially a container for components.

- **Component**: A component is a piece of data that is attached to an entity. Components are used to add functionality to an entity. For example, a `PositionComponent` could be used to store the position of an entity.

- **System**: A system is a piece of code that operates on entities that have a specific set of components. Systems are used to update the state of the game world. For example, a `MovementSystem` could be used to update the position of entities based on their velocity.

To coordinate the interactions between entities, components, and systems, we use a `Coordinator` class. The `Coordinator` class is responsible for creating and managing entities, components, and systems.

## CommandFactory

The `CommandFactory` class is responsible for creating and executing commands. When a client sends a command to the server, the `CommandFactory` class is used to create the appropriate command object. The command object is then executed by the server.

The `CommandFactory` create a `ICommand` object based on the command type and the parameters received from the client. The class `ACommand` inherits from the interface `ICommand` and is the base class for all the commands. Then we have a class for each command that inherits from `ACommand` (for example `ActionPlayerCommand`, `MovePlayerCommand`...).

## Project files architecture

The project is divided into several directories:

```tree
.
├── config *All the configuration files*
│   ├── entities
│   │   └── *All the entities config files*
│   └── level
│       └── *All the levels config files*
├── ressources
│   └── *All the ressources needed for the game*
└── src
    ├── client
    │   ├── ClientError.cpp
    │   ├── ClientError.hh
    │   ├── CMakeLists.txt
    │   ├── communication
    │   │   ├── Client.cpp
    │   │   └── Client.hh
    │   ├── Game.cpp
    │   ├── Game.hh
    │   └── main.cpp
    ├── ecs
    │   ├── ASystem.cpp
    │   ├── ASystem.hh
    │   ├── CMakeLists.txt
    │   ├── Components
    │   │   └── *All the components*
    │   ├── Coordinator.cpp
    │   ├── Coordinator.hh
    │   ├── EcsError.cpp
    │   ├── EcsError.hh
    │   ├── Entity.cpp
    │   ├── Entity.hpp
    │   ├── IComponent.hh
    │   ├── Include.hh
    │   ├── ISystem.cpp
    │   ├── ISystem.hh
    │   └── Systems
    │       └── *All the systems*
    ├── protocolHandler
    │   ├── CMakeLists.txt
    │   ├── Decoder.cpp
    │   ├── Decoder.hh
    │   ├── Encoder.cpp
    │   └── Encoder.hh
    └── server
        ├── clientServer
        │   ├── ClientServer.cpp
        │   └── ClientServer.hh
        ├── CMakeLists.txt
        ├── command
        │   ├── ACommand.cpp
        │   ├── ACommand.hh
        │   ├── commands
        │   │   └── *All the commands*
        │   ├── factory
        │   │   ├── CommandFactory.cpp
        │   │   └── CommandFactory.hh
        │   └── ICommand.hh
        ├── Error.cpp
        ├── Error.hh
        ├── includes.hh
        ├── main.cpp
        └── server
            ├── Server.cpp
            └── Server.hh
```