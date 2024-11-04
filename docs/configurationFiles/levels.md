# Creating a New Level Script
## 1. Setting Up Level Boundaries
At the top of your new level script, define the vertical limits for enemy spawns:

``` lua
local LIMIT_TOP = 200
local LIMIT_BOTTOM = 850
```
These values control the range of heights where enemies can appear, ensuring they stay within the playable area.
## 2. Define the Enemy Structure
``` lua
Ennemy = {
    name = "",
    timeStamp = 0.0,
    height = 0
}

function Ennemy:new(o, name, timeStamp, height)
    o = o or {}
    setmetatable(o, self)
    self.__index = self
    o.name = name
    o.timeStamp = timeStamp
    o.height = height
    return o
end
```

This defines the enemy structure and provides a constructor method to create new enemy instances.

## 3. Creating the Level Table
``` lua
Level = {}
```
The Level table will store all enemy spawn information and methods for adding enemies in various formations.
Adding Enemies to the Level
## 4. Basic Enemy Addition
``` lua
function Level.addEnnemy(name, timeStamp, height)
    if name == "fly" or name == "octopus" then
        height = math.max(LIMIT_TOP, math.min(height, LIMIT_BOTTOM))
    end
    table.insert(Level, Ennemy:new(nil, name, timeStamp, height))
end
```

-Parameters:
    - name: The type of enemy (e.g., "fly", "octopus", "item_heal").
    - timeStamp: The time at which the enemy appears.
    - height: The vertical position where the enemy will spawn.
## 5. Enemy Formation Functions
Here are several predefined formation functions you can use:

### Column: Spawns a vertical column of enemies.

``` lua
function Level.spawnColumn(name, timeStamp, height, spacing, count)
    spacing = spacing or 50
    count = count or 10
    for i = 0, count - 1 do
        Level.addEnnemy(name, timeStamp + (i * 0.2), height - (i * spacing))
    end
end
```

### Pack: Spawns a small group of enemies at slightly varied positions.

``` lua
function Level.spawnPack(name, timeStamp, height)
    Level.addEnnemy(name, timeStamp, height)
    Level.addEnnemy(name, timeStamp + 0.2, height - 40)
    Level.addEnnemy(name, timeStamp + 0.4, height + 60)
    Level.addEnnemy(name, timeStamp + 0.6, height)
end
```

### Mixed Wave: Alternates between two enemy types in a wave formation.

``` lua
function Level.spawnMixedWave(name1, name2, timeStamp, height, spacing, count)
    spacing = spacing or 60
    count = count or 5
    local timeSpacing = 0.25

    for i = 0, count - 1 do
        local name = i % 2 == 0 and name1 or name2
        Level.addEnnemy(name, timeStamp + (i * timeSpacing), height + (i * spacing))
    end
end
```

### V Formation: Arranges enemies in a "V" shape.

``` lua
function Level.spawnVFormation(name, timeStamp, height, spread)
    spread = spread or 30
    Level.addEnnemy(name, timeStamp, height)
    Level.addEnnemy(name, timeStamp + 0.1, height + spread)
    Level.addEnnemy(name, timeStamp + 0.2, height - spread)
    Level.addEnnemy(name, timeStamp + 0.3, height + (spread * 2))
    Level.addEnnemy(name, timeStamp + 0.4, height - (spread * 2))
end
```

### Horizontal Line: Spawns a line of enemies horizontally.

``` lua
function Level.spawnHorizontalLine(name, timeStamp, height, spacing, count)
    spacing = spacing or 80
    count = count or 6
    for i = 0, count - 1 do
        Level.addEnnemy(name, timeStamp + (i * 0.15), height)
    end
end
```

### Circle: Arranges enemies in a circular pattern.

``` lua
function Level.spawnCircle(name, timeStamp, centerY, radius, count)
    count = count or 8
    local angleStep = (2 * math.pi) / count
    for i = 0, count - 1 do
        local angle = i * angleStep
        local height = math.max(LIMIT_TOP, math.min(centerY + math.sin(angle) * radius, LIMIT_BOTTOM))
        Level.addEnnemy(name, timeStamp + (i * 0.1), height)
    end
end
```

### Zigzag: Spawns enemies in a zigzag pattern.

``` lua
function Level.spawnZigzag(name, timeStamp, startHeight, amplitude, count, timeStep)
    amplitude = amplitude or 100
    count = count or 10
    timeStep = timeStep or 0.2
    for i = 0, count - 1 do
        local height = startHeight + (i % 2 == 0 and amplitude or -amplitude)
        height = math.max(LIMIT_TOP, math.min(height, LIMIT_BOTTOM))
        Level.addEnnemy(name, timeStamp + (i * timeStep), height)
    end
end
```

## Example Enemy Spawn Configuration
Here is how you might structure a new level using the provided functions:

``` lua
Level.addEnnemy("item_heal", 5, 1080 / 4)
Level.addEnnemy("item_heal", 5, 1080 / 2)
Level.addEnnemy("item_heal", 5, 1080 / 4 * 3)

Level.spawnPack("fly", 10, 600)
Level.spawnHorizontalLine("fly", 12.5, 300, 80, 4)
Level.spawnZigzag("octopus", 13, 400, 100, 6, 0.3)
Level.spawnCircle("fly", 14, 600, 150, 8)
```

## 6. Updating Level Count
To make your new level accessible, you may need to modify the game's maximum level value:

Locate the configuration file where the maxLevel variable is defined in src/ecs/Systems/HandleCollisionSystem.cpp.

``` cpp
    if (level->getLevel() == 4)
```

## Finalizing and Testing
Save your new level script in the appropriate directory, such as config/level/lvl3.``` lua.
Launch the game and test your new level to ensure that all enemy formations and spawns behave as expected.
Feel free to adjust enemy types, timing, and formations to create a challenging and engaging experience.