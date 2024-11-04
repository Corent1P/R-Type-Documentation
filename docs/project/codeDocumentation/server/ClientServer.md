# The ClientServer class

## Overview
The ClientServer class represents a client connection in the R-Type game server, managing individual client state and communication endpoints using UDP protocol via Boost.Asio.

## Construction
```cpp
ClientServer(boost::asio::ip::udp::endpoint endpoint)
```
Creates a new client instance with the specified endpoint, initializing connection state and network parameters.

## Key Features

### Network Management
- **Endpoint Handling**: Maintains UDP endpoint information for client communication
- **Connection State**: Tracks client connection status
- **Message Transmission**: Provides asynchronous message sending capabilities

### Player Management
- **Entity Association**: Links clients with their in-game entity representation
- **Connection Status**: Manages client connection state

## Key Methods

### Network Operations
- `sendMessage(udp::socket &socket, const std::string &message)`: Sends string messages (deprecated)
- `sendMessage(udp::socket &socket, const std::basic_string<unsigned char> &message)`: Sends binary messages
- `getEndpoint()`: Retrieves client's network endpoint

### State Management
- `setIsConnected(bool)`: Updates client connection status
- `getIsConnected()`: Retrieves current connection status
- `setEntity(std::shared_ptr<Entity>)`: Associates client with game entity
- `getEntity()`: Retrieves client's associated entity

### Network Information
- `setAddress(boost::asio::ip::address)`: Sets client IP address
- `getAddress()`: Retrieves client IP address
- `setPortNumber(std::size_t)`: Sets client port number
- `getPortNumber()`: Retrieves client port number

## Member Variables
- `_endpoint`: UDP endpoint for client communication
- `_portNumber`: Client's port number
- `_address`: Client's IP address
- `_isConnected`: Connection status flag
- `_entity`: Associated game entity pointer

## Thread Safety
The class provides basic state management but relies on external synchronization when used in multi-threaded contexts.

## Dependencies
- [Boost.Asio](https://www.boost.org/doc/libs/release/doc/html/boost_asio.html) for networking functionality
- RType::Entity for game entity management

## Notes
- Implements UDP-based communication
- Supports both string and binary message formats
- Provides comparison operations for client identification
- Uses shared pointers for entity management
