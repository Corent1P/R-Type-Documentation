# RType Command Classes Documentation

## Overview
The Command system implements a command pattern for handling network messages in the R-Type game server. All commands inherit from `ACommand` which implements the `ICommand` interface.

## Base Classes

### ICommand Interface
Located in `/home/antoinegrand/Delivery/B-CPP/B-CPP-500/R-Type/src/server/command/ICommand.hh`
- Defines the base interface for all commands
- Key method: `execute(std::shared_ptr<ClientServer>, FUNCTION_SEND, FUNCTION_SEND, Coordinator&)`

### ACommand Abstract Class
Located in `/home/antoinegrand/Delivery/B-CPP/B-CPP-500/R-Type/src/server/command/ACommand.hh`
- Abstract base class implementing `ICommand`
- Constructor takes data vector and packet type
- Provides common functionality for all command classes

## Command Classes

### ActionPlayerCommand
Located in `/home/antoinegrand/Delivery/B-CPP/B-CPP-500/R-Type/src/server/command/commands/ActionPlayerCommand.hh`
- Handles player actions (like shooting)
- Contains bullet positioning and sizing logic
- Takes vector of arguments for initialization

### ConnexionCommand
Located in `/home/antoinegrand/Delivery/B-CPP/B-CPP-500/R-Type/src/server/command/commands/ConnexionCommand.hh`
- Manages client connection requests
- Processes initial client connection setup

### DeleteEntityCommand
Located in `/home/antoinegrand/Delivery/B-CPP/B-CPP-500/R-Type/src/server/command/commands/DeleteEntityCommand.hh`
- Handles entity removal from the game
- Takes entity identifier as argument

### MoveEntityCommand
Located in `/home/antoinegrand/Delivery/B-CPP/B-CPP-500/R-Type/src/server/command/commands/MoveEntityCommand.hh`
- Processes entity movement requests
- Updates entity positions in the game world

### MovePlayerCommand
Located in `/home/antoinegrand/Delivery/B-CPP/B-CPP-500/R-Type/src/server/command/commands/MovePlayerCommand.hh`
- Specifically handles player movement
- Processes player position updates

### NewEntityCommand
Located in `/home/antoinegrand/Delivery/B-CPP/B-CPP-500/R-Type/src/server/command/commands/NewEntityCommand.hh`
- Creates new entities in the game
- Handles entity initialization

### GameStartCommand
Located in `/home/antoinegrand/Delivery/B-CPP/B-CPP-500/R-Type/src/server/command/commands/GameStartCommand.hh`
- Manages game session start
- Initializes game state

### InfoLevelCommand
Located in `/home/antoinegrand/Delivery/B-CPP/B-CPP-500/R-Type/src/server/command/commands/InfoLevelCommand.hh`
- Handles level information updates
- Processes level-related data

### GameEndCommand
Located in `/home/antoinegrand/Delivery/B-CPP/B-CPP-500/R-Type/src/server/command/commands/GameEndCommand.hh`
- Manages game session termination
- Handles end-game state

### InfoEntityCommand
Located in `/home/antoinegrand/Delivery/B-CPP/B-CPP-500/R-Type/src/server/command/commands/InfoEntityCommand.hh`
- Processes entity information updates
- Handles entity state synchronization

## Command Factory
Located in `/home/antoinegrand/Delivery/B-CPP/B-CPP-500/R-Type/src/server/command/factory/CommandFactory.hh`
- Creates command instances based on packet types
- Centralizes command object creation
- Implements factory pattern for command instantiation

## Common Features
All command classes share:
- Inheritance from `ACommand`
- Vector of arguments in constructor
- Implementation of `execute()` method
- Integration with the game's coordinator system
