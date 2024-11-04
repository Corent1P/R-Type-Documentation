# R-Type Encoder Documentation

## Overview
The `Encoder` class is responsible for encoding various packets of data that are communicated between the client and the server in the R-Type game.

## Packet Types
The following enumerated types define the different types of packets that can be sent:

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

## Encoder Class

### Methods

#### `header(std::uint16_t size, unsigned char type)`
Encodes the header of the packet.

- **Parameters:**
  - `size`: Total size of the packet, excluding the header.
  - `type`: Type of the packet.
- **Returns:** `U_STRING` - Encoded header with 2 bytes free to input the packet number later.

#### `connexion()`
Encodes the connexion packet.

- **Returns:** `U_STRING` - Encoded connexion packet.

#### `disconnexion()`
Encodes the disconnexion packet.

- **Returns:** `U_STRING` - Encoded disconnexion packet.

#### `newEntity(std::uint8_t type, std::uint16_t id, std::uint16_t x, std::uint16_t y, std::uint16_t entityToFollow = 0)`
Encodes the new entity packet.

- **Parameters:**
  - `type`: Type of the entity.
  - `id`: The unique ID of the entity.
  - `x`: The x position of the entity.
  - `y`: The y position of the entity.
  - `entityToFollow`: (Optional) The entity to follow.
- **Returns:** `U_STRING` - Encoded new entity packet.

#### `deleteEntity(std::uint16_t id)`
Encodes the delete entity packet.

- **Parameters:**
  - `id`: The unique ID of the entity.
- **Returns:** `U_STRING` - Encoded delete entity packet.

#### `moveEntity(std::uint16_t id, std::uint16_t x, std::uint16_t y, std::uint8_t rotation)`
Encodes the entity movement packet.

- **Parameters:**
  - `id`: The unique ID of the entity.
  - `x`: The new x position of the entity.
  - `y`: The new y position of the entity.
  - `rotation`: The new rotation of the entity.
- **Returns:** `U_STRING` - Encoded move entity packet.

#### `infoLevel(std::uint8_t level)`
Encodes the level information packet.

- **Parameters:**
  - `level`: The level of the game.
- **Returns:** `U_STRING` - Encoded level information packet.

#### `infoScore(std::uint16_t score)`
Encodes the score information packet.

- **Parameters:**
  - `score`: The score of the game.
- **Returns:** `U_STRING` - Encoded score information packet.

#### `infoEntity(std::uint16_t id, std::uint8_t type, std::uint16_t x, std::uint16_t y, std::uint8_t rotation, std::uint8_t life)`
Encodes the entity information packet.

- **Parameters:**
  - `id`: The unique ID of the entity.
  - `type`: The type of the entity.
  - `x`: The x position of the entity.
  - `y`: The y position of the entity.
  - `rotation`: The rotation of the entity.
  - `life`: The life of the entity.
- **Returns:** `U_STRING` - Encoded entity information packet.

#### `movePlayer(std::int8_t x, std::int8_t y)`
Encodes the player movement packet.

- **Parameters:**
  - `x`: The inputs of the player in the x axis.
  - `y`: The inputs of the player in the y axis.
- **Returns:** `U_STRING` - Encoded player movement packet.

#### `actionPlayer(bool action1, bool action2, bool action3, bool action4)`
Encodes the player action packet.

- **Parameters:**
  - `action1`: Corresponds to the shoot action.
  - `action2`: Corresponds to the charged shoot action.
  - `action3`: Additional action.
  - `action4`: Additional action.
- **Returns:** `U_STRING` - Encoded player action packet.

#### `gameStart()`
Encodes the game start packet.

- **Returns:** `U_STRING` - Encoded game start packet.

#### `gameEnd()`
Encodes the game end packet.

- **Returns:** `U_STRING` - Encoded game end packet.

## Example Usage

Here’s an example of how to use the `Encoder` class to encode various packets:

```cpp
U_STRING connectionPacket = Encoder::connexion();
U_STRING entityPacket = Encoder::newEntity(entityType, entityId, posX, posY);
```

## Conclusion
The `Encoder` class provides a robust way to encode data packets necessary for communication between the client and server in the R-Type game, enabling effective handling of game state and interactions.
