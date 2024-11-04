# Adding an Entity in R-Type

## Overview

The `HandleEntitySpawnSystem` class is responsible for managing the spawning of entities within the R-Type game. Entities are defined using JSON configuration files that specify their properties and behaviors. This document outlines the steps required to add a new entity to the game.

## Steps to Add a New Entity

1. **Create a JSON Configuration File**

   Each entity must have a corresponding JSON file located in the `./config/entities/` directory. The filename should match the entity type you wish to create (e.g., `my_entity.json`).

   ### JSON Structure

   Here’s a basic structure of the JSON file:

   ``` json
   {
       "sprite":"./ressources/types/path",
       "scale": {
           "x": 1.0,
           "y": 1.0
       },
       "rect": {
           "x": 0,
           "y": 0,
           "width": 32,
           "height": 32
       },
       "health": 100,
       "damage": 20,
       "speed": 5,
       "pattern": 1,
       "isShooting": true,
       "intervalShoot": 0.5,
       "attack": ["basic_attack", "special_attack"],
       "score": 50
   }
   ```
   - `sprite`: Defines the sprite of the entity.
   - `scale`: Defines the scale of the entity.
   - `rect`: Specifies the bounding box for the entity (x, y, width, height).
   - `health`: The health points of the entity (if applicable).
   - `damage`: The damage dealt by the entity (if applicable).
   - `speed`: Movement speed of the entity.
   - `pattern`: An integer that indicates the movement pattern (refer to your movement pattern definitions).
   - `isShooting`: Boolean indicating if the entity can shoot.
   - `intervalShoot`: The time interval between shots (if applicable).
   - `attack`: An array of strings representing the attack patterns the entity can perform.
   - `score`: The score awarded when the entity is destroyed.

2. **Update the Entity Type Map**

   Open the `createEntityMap` function in `HandleEntitySpawnSystem` and add a new entry for your entity type:

   ``` cpp
   _entityTypeMap[E_MY_ENTITY] = "my_entity";
   ```

   Replace `E_MY_ENTITY` with a unique enumeration value representing your entity.

3. **Implement Behavior in Lua (if necessary)**

   If your entity requires specific behavior defined in Lua, ensure to update the corresponding Lua files. You can push the relevant functions into the Lua state in the `effect` method, where entity updates occur.

4. **Test Your Entity**

   After creating the JSON file and updating the code, test your entity in the game. Ensure it spawns correctly and behaves as expected according to the configurations provided in the JSON file.

## Notes

- Ensure that all required components are properly defined and linked to your new entity.
- The JSON parsing is handled by the `createEntity` method in `HandleEntitySpawnSystem`. Ensure that your JSON adheres to the expected structure to avoid parsing errors.
- Any logging or error messages during the loading of the entity will appear in the console, so monitor for any issues.

## Conclusion

By following these steps, you can successfully add a new entity to the R-Type game. This process involves creating a configuration file, updating the entity type map, and ensuring that any necessary behavior is implemented. Testing is crucial to ensure that the new entity interacts correctly within the game environment.
