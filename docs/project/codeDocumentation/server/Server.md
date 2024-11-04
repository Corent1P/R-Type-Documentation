# The Server class

## Overview
The Server class is the core networking component of the R-Type game server. It handles client connections, game state management, and network communication using UDP protocol via Boost.Asio.

## Construction

```cpp
Server(boost::asio::io_context &ioContext, int port)
```

Creates a new server instance listening on the specified port. Initializes the game systems and starts the game loop and CLI thread.

## Key Features

### Network Communication
- **UDP Socket Management**: Handles asynchronous message reception and transmission
- **Client Management**: Maintains a list of connected clients and their states
- **Protocol Handling**: Processes incoming packets and sends responses using custom protocol encoders/decoders

### Game Management
- **Entity Coordination**: Uses an ECS (Entity Component System) architecture
- **Game Loop**: Runs the main game logic in a separate thread
- **System Management**: Initializes and manages various game systems like:
  - Movement System
  - Collision System
  - Shooting System
  - Pattern System
  - Boss Attack System

### Administrative Features
- **CLI Interface**: Provides administrative commands:
  - Player listing
  - Difficulty adjustment
  - Player kick functionality
  - Level management
  - Friendly fire toggle
  - Server shutdown

## Key Methods

### Network Operations
- `startReceive()`: Initiates asynchronous message reception
- `handleReceive()`: Processes received messages
- `sendToAllClient()`: Broadcasts messages to all connected clients
- `handleConnection()`: Processes new client connections
- `handleDisconnection()`: Manages client disconnections

### Client Management
- `createClient()`: Creates a new client instance
- `removeClient()`: Removes a client from the server
- `getConnectedClient()`: Retrieves a client based on endpoint information

### Game Control
- `gameLoop()`: Main game loop running game logic
- `initSystem()`: Initializes all game systems
- `sendAllEntity()`: Syncs game state with new clients
- `removeAllEnnemies()`: Clears all enemies from the game

### Administrative Commands
- `listPlayers()`: Displays connected players
- `changeDifficulty()`: Modifies game difficulty
- `kickPlayer()`: Removes a player from the game
- `changeLevel()`: Changes the current game level
- `printCliHelp()`: Displays available CLI commands

## Thread Safety
The server implements thread safety using mutex locks for critical sections, particularly around the coordinator and client list access.

## Dependencies
- Boost.Asio for networking
- Custom Protocol Handler (Encoder/Decoder)
- Entity Component System (Coordinator)
- Command Factory for packet handling

## Notes
- The server runs on [UDP protocol](https://en.wikipedia.org/wiki/User_Datagram_Protocol)
- Supports multiple simultaneous client connections
- Implements a custom game protocol for client-server communication
- Uses a fixed frame rate for game logic (20 FPS)
