# R-Type Decoder Documentation

## Overview
The `Decoder` class is responsible for decoding various packets of data that are received from the client and server in the R-Type game.

## Packet Types
The following enumerated types define the different types of packets that can be received:

```cpp
enum PacketType {
    PACKET_ERROR = -1,
    CONNEXION = 0,
    DISCONNEXION = 1,
    NEW_ENTITY = 2,
    DELETE_ENTITY = 3,
    MOVE_ENTITY = 4,
    INFO_LEVEL = 5,
    INFO_ENTITY = 6,
    MOVE_PLAYER = 7,
    ACTION_PLAYER = 8,
    GAME_START = 9,
    GAME_END = 10,
    INFO_SCORE = 11
};
```

## Decoder Class

### Methods

#### `COMMAND_INFO getCommandInfo(U_STRING &packet)`
Decodes the command information from a given packet.

- **Parameters:**
  - `packet`: The packet to decode.
- **Returns:** `COMMAND_INFO` - A pair containing the packet type and its arguments.

#### `PacketType getType(U_STRING &packet)`
Extracts the packet type from a given packet.

- **Parameters:**
  - `packet`: The packet from which to extract the type.
- **Returns:** `PacketType` - The type of the packet.

#### `std::size_t getSize(U_STRING &packet)`
Calculates the size of the packet based on its header.

- **Parameters:**
  - `packet`: The packet from which to determine the size.
- **Returns:** `std::size_t` - The size of the packet.

#### `COMMAND_ARGS newEntity(U_STRING &packet)`
Decodes a new entity packet and extracts its arguments.

- **Parameters:**
  - `packet`: The packet containing new entity information.
- **Returns:** `COMMAND_ARGS` - Arguments for the new entity.

#### `COMMAND_ARGS deleteEntity(U_STRING &packet)`
Decodes a delete entity packet and extracts its arguments.

- **Parameters:**
  - `packet`: The packet containing delete entity information.
- **Returns:** `COMMAND_ARGS` - Arguments for deleting an entity.

#### `COMMAND_ARGS moveEntity(U_STRING &packet)`
Decodes a move entity packet and extracts its arguments.

- **Parameters:**
  - `packet`: The packet containing move entity information.
- **Returns:** `COMMAND_ARGS` - Arguments for moving an entity.

#### `COMMAND_ARGS infoLevel(U_STRING &packet)`
Decodes an info level packet and extracts its arguments.

- **Parameters:**
  - `packet`: The packet containing level information.
- **Returns:** `COMMAND_ARGS` - Arguments for level information.

#### `COMMAND_ARGS infoScore(U_STRING &packet)`
Decodes an info score packet and extracts its arguments.

- **Parameters:**
  - `packet`: The packet containing score information.
- **Returns:** `COMMAND_ARGS` - Arguments for score information.

#### `COMMAND_ARGS infoEntity(U_STRING &packet)`
Decodes an info entity packet and extracts its arguments.

- **Parameters:**
  - `packet`: The packet containing entity information.
- **Returns:** `COMMAND_ARGS` - Arguments for entity information.

#### `COMMAND_ARGS movePlayer(U_STRING &packet)`
Decodes a move player packet and extracts its arguments.

- **Parameters:**
  - `packet`: The packet containing player movement information.
- **Returns:** `COMMAND_ARGS` - Arguments for player movement.

#### `COMMAND_ARGS actionPlayer(U_STRING &packet)`
Decodes an action player packet and extracts its arguments.

- **Parameters:**
  - `packet`: The packet containing player action information.
- **Returns:** `COMMAND_ARGS` - Arguments for player actions.

## Example Usage

Here’s an example of how to use the `Decoder` class to decode various packets:

```cpp
U_STRING packet = /* some incoming packet */;
COMMAND_INFO commandInfo = Decoder::getCommandInfo(packet);
```

## Conclusion
The `Decoder` class provides a robust way to decode data packets necessary for interpreting communication between the client and server in the R-Type game, enabling effective handling of game state and interactions.
