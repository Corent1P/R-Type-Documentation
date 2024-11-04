# `RType::Game` Class Documentation

The `RType::Game` class manages the game loop, entities, systems, and communication with the server in the R-Type game. It incorporates SFML for graphics and provides the necessary methods for creating and managing game entities, handling user input, and rendering.

## Constructor

```cpp
RType::Game::Game(boost::asio::io_context &ioContext, const std::string &host, const std::string &port);
```

- **Parameters:**
  - `ioContext`: The Boost ASIO context for handling asynchronous operations.
  - `host`: The address of the game server.
  - `port`: The port number on which the server is listening.

- **Description:** 
  Initializes the game environment, including loading resources, creating the game window, setting up the ECS (Entity-Component-System), and establishing a connection to the server.

## Destructor

```cpp
RType::Game::~Game();
```

- **Description:**
  Cleans up the resources, including stopping the game loop and disconnecting from the server.

## Member Functions

### `void RType::Game::gameLoop()`

```cpp
void RType::Game::gameLoop();
```

- **Description:**
  The main game loop that processes game logic, updates entities, and renders graphics. It controls the frame rate and handles the overall game state.

### `const RType::Coordinator &RType::Game::getCoordinator() const`

```cpp
const RType::Coordinator &RType::Game::getCoordinator() const;
```

- **Returns:** 
  A constant reference to the game’s coordinator, which manages all entities and systems in the ECS.

- **Description:** 
  Provides access to the coordinator for querying and manipulating game entities.

### `bool RType::Game::getGameHasStarted() const`

```cpp
bool RType::Game::getGameHasStarted() const;
```

- **Returns:** 
  A boolean indicating whether the game has started or not.

- **Description:** 
  Checks if the game has been initiated.

## Private Member Functions

### `void RType::Game::connectToServer()`

```cpp
void RType::Game::connectToServer();
```

- **Description:**
  Establishes a connection to the server using the specified host and port.

### `void RType::Game::loopReceive()`

```cpp
void RType::Game::loopReceive();
```

- **Description:**
  Continuously listens for incoming messages from the server, processing and updating the game state accordingly.

### `void RType::Game::createPlayer()`

```cpp
void RType::Game::createPlayer();
```

- **Description:**
  Creates and initializes a player entity within the game.

### `void RType::Game::createEntity(const RType::EntityType &type, const int &posX, const int &posY, const int &idToFollow = -1)`

```cpp
void RType::Game::createEntity(const RType::EntityType &type, const int &posX, const int &posY, const int &idToFollow = -1);
```

- **Parameters:**
  - `type`: The type of the entity being created.
  - `posX`: The X-coordinate position for the entity.
  - `posY`: The Y-coordinate position for the entity.
  - `idToFollow`: Optional parameter indicating the ID of another entity to follow.

- **Description:**
  Creates a new game entity at the specified coordinates.

### `void RType::Game::createEntity(const long &serverId, const RType::EntityType &type, const int &posX, const int &posY, const int &idToFollow = -1)`

```cpp
void RType::Game::createEntity(const long &serverId, const RType::EntityType &type, const int &posX, const int &posY, const int &idToFollow = -1);
```

- **Parameters:**
  - `serverId`: The ID assigned by the server to the entity.
  - `type`: The type of the entity being created.
  - `posX`: The X-coordinate position for the entity.
  - `posY`: The Y-coordinate position for the entity.
  - `idToFollow`: Optional parameter indicating the ID of another entity to follow.

- **Description:**
  Creates a new game entity based on server data.

### `void RType::Game::createWindow()`

```cpp
void RType::Game::createWindow();
```

- **Description:**
  Initializes and creates the game window using SFML.

### `void RType::Game::createMenu()`

```cpp
void RType::Game::createMenu();
```

- **Description:**
  Constructs the main menu interface for the game, allowing players to start the game or access options.

### `void RType::Game::createOptionMenu()`

```cpp
void RType::Game::createOptionMenu();
```

- **Description:**
  Sets up the options menu where players can modify game settings such as audio and controls.

### `void RType::Game::createDeathMenu()`

```cpp
void RType::Game::createDeathMenu();
```

- **Description:**
  Creates a menu that appears when the player dies, offering options to restart or exit.

### `void RType::Game::createWinMenu()`

```cpp
void RType::Game::createWinMenu();
```

- **Description:**
  Constructs a menu that appears when the player wins the game, providing options for replaying or exiting.

### `void RType::Game::createMappingInputButton(std::shared_ptr<RType::MappingInputComponent> mappingInput)`

```cpp
void RType::Game::createMappingInputButton(std::shared_ptr<RType::MappingInputComponent> mappingInput);
```

- **Parameters:**
  - `mappingInput`: A shared pointer to the component that handles key mappings.

- **Description:**
  Creates buttons in the options menu for remapping game controls.

### `std::shared_ptr<RType::Entity> RType::Game::createButton(int x, int y, std::string text)`

```cpp
std::shared_ptr<RType::Entity> RType::Game::createButton(int x, int y, std::string text);
```

- **Parameters:**
  - `x`: The X-coordinate position of the button.
  - `y`: The Y-coordinate position of the button.
  - `text`: The text to display on the button.

- **Returns:** 
  A shared pointer to the created button entity.

- **Description:**
  Creates a button entity with specified coordinates and text.

### `std::shared_ptr<RType::Entity> RType::Game::createText(int x, int y, std::string text)`

```cpp
std::shared_ptr<RType::Entity> RType::Game::createText(int x, int y, std::string text);
```

- **Parameters:**
  - `x`: The X-coordinate position of the text.
  - `y`: The Y-coordinate position of the text.
  - `text`: The text content to display.

- **Returns:** 
  A shared pointer to the created text entity.

- **Description:**
  Creates a text entity at the specified coordinates.

### `void RType::Game::createGameSystem()`

```cpp
void RType::Game::createGameSystem();
```

- **Description:**
  Initializes and sets up the various systems for the ECS that handle different aspects of the game (e.g., rendering, physics).

### `std::shared_ptr<RType::Entity> RType::Game::getPlayerEntity()`

```cpp
std::shared_ptr<RType::Entity> RType::Game::getPlayerEntity();
```

- **Returns:** 
  A shared pointer to the player entity.

- **Description:**
  Retrieves the player entity from the ECS.

### `std::shared_ptr<RType::TextureComponent> RType::Game::getTextureComponent(const std::string &path)`

```cpp
std::shared_ptr<RType::TextureComponent> RType::Game::getTextureComponent(const std::string &path);
```

- **Parameters:**
  - `path`: The file path of the texture.

- **Returns:** 
  A shared pointer to the texture component.

- **Description:**
  Loads and returns a texture component from the specified path.

### `std::shared_ptr<RType::SoundBufferComponent> RType::Game::getSoundBufferComponent(const std::string &path)`

```cpp
std::shared_ptr<RType::SoundBufferComponent> RType::Game::getSoundBufferComponent(const std::string &path);
```

- **Parameters:**
  - `path`: The file path of the sound buffer.

- **Returns:** 
  A shared pointer to the sound buffer component.

- **Description:**
  Loads and returns a sound buffer component from the specified path.

### `std::size_t RType::Game::getMaxClientId()`

```cpp
std::size_t RType::Game::getMaxClientId();
```

- **Returns:** 
  The maximum client ID currently in use.

- **Description:** 
  Retrieves the highest client ID from the current game session.

### `sf::Vector2f RType::Game::getBulletPosition(int type, int posX, int posY)`

```cpp
sf::Vector2f RType::Game::getBulletPosition(int type, int posX, int posY);
```

- **Parameters:**
  - `type`: The type of bullet.
  - `posX`: The X-coordinate for the bullet.
  - `posY`: The Y-coordinate for the bullet.

- **Returns:** 
  A `sf::Vector2f` representing the bullet's position.

- **Description:**
  Calculates and returns the position of a bullet based on its type and initial coordinates.

### `void RType::Game::setGameHasStarted(bool started)`

```cpp
void RType::Game::setGameHasStarted(bool started);
```

- **Parameters:**
  - `started`: A boolean indicating the new game state.

- **Description:**
  Sets the game’s start state to the provided value.

## Member Variables

- `sf::RenderWindow window`: The SFML window for rendering the game.
- `RType::Coordinator coordinator`: The coordinator for managing entities and systems.
- `std::shared_ptr<RType::Entity> playerEntity`: A shared pointer to the player entity.
- `bool gameHasStarted`: A flag indicating whether the game has started.
- `std::mutex mutex`: A mutex for synchronizing access to shared resources.

## Example Usage

```cpp
boost::asio::io_context ioContext;
RType::Game game(ioContext, "localhost", "8080");
game.gameLoop();
```

- **Description:**
  Example of initializing the game and starting the game loop with a specified server host and port.

## Conclusion

The `RType::Game` class provides a comprehensive interface for managing the game’s core functionality, including entity management, rendering, input handling, and server communication. It leverages SFML for graphics and audio, making it suitable for developing 2D games in C++.
