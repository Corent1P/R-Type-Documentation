# Component

## Overview

> A Component is an class inheriting form the IComponent class, a Component holds attributes associated to an entity.

## Class Definition

Located in `R-TYPE/src/ecs/IComponent.hpp`.

## Construction
A Component Constructor differs depending on which data are about to be assigned based on the Component theme.

>Example of Component Constructor:
```cpp
DamageComponent(int damage);
```
Creaction of the DamageComponent.
- `int damage`: the damage value set.

```cpp
SpriteComponent(std::shared_ptr<sf::Texture> texture, sf::Vector2f pos, sf::Vector2f scale, sf::IntRect rect);
```
Creaction of the SpriteComponent
- `std::shared_ptr<sf::Texture> texture`: a shared pointer of type sf::Texture assigned to the sprite.
- `sf::Vector2f pos`: a sf::Vecotor2f of the position assigned to the sprite.
- `sf::Vector2f scale`: a sf::Vecotor2f of the scale assigned to the sprite.
- `sf::IntRect rect`: a sf::IntRect of the rectangle assigned to the sprite.
## Destruction

## Attribute

A basic Component is composed of attribute in association with the Component theme.

>For example:

- `int _damage`: for the Damage Component.
- `int _health`: for the Health Component.
- `std::shared_ptr<sf::Spirte> _sprite`: for the Sprite Component.
-  `float _scaleX`, `float _scaleY`: for the scale Component.


## Methods

Those attributes are accessible and modifiable with methods to do so.
Most of Components have setter and getter methods:

- for the VelocityComponent:
    ```cpp
    void setVelocity(int velocity);
    int getVelocity() const;
    ````
- for the PositionComponent:
    ```cpp
    void setPositions(int x, int y);
    void setX(int x);
    void setY(int y);
    int getPositionX() const;
    int getPositionY() const;
    ```

Our Component are designed to be composed of only one kind of specific attribute to be as reusable as possible.

For Example:

To handle SFML Sprites we have various Component dedicated to each part of the SFML Sprite creation but can also be used for other purposes.
- `PositionComponent`
- `TextureComponent`
- `IntRectComponent`
- `SpriteComponent`
- `ScaleComponent`

All those Components are independents and used to manage different kind of tasks but are used during the creation of the sprite Component.

## Usage Exemple

### How to create your own Component
>1. Create your own components files in the `/src/ecs/Components/` folder:
- Filename: `YourComponent.cpp` | `YourComponent.hh`
- Add your component `YourComponent.cpp` file to the CMakeLists.txt in the `src/ecs/` folder.
```cmake
set(SRC_COMPONENTS ./Components/YourComponent.cpp);
```

>2. File content:
`YourComponent.hh:`
- Use the RType namespace.
- Inherit the IComponent class.
- Methods: must only be getters/setters methods
- Attributes: must be private.

```cpp
#ifndef YOUR_COMPONENT_HH
#define YOUR_COMPONENT_HH

#include <string>

namespace RType {
    class YourComponent: public IComponent {
        public:
        //Constructor Example
        YourComponent(int exampleValue, const std::string& exampleText)
            : exampleValue(exampleValue), exampleText(exampleText);

        //Getters Example
        int getExampleValue() const;
        const std::string& getExampleText() const;

        //Setters Example
        void setExampleValue(int value);
        void setExampleText(const std::string& text);

        private:
            //Component data members
            int exampleValue;
            std::string exampleText;
    };
}
#endif // YOUR_COMPONENT_HH
```

`YourComponent.cpp:`
- Implementation of YourComponent methods

```cpp
    #include "YourComponent.hh"

    RType::YourComponent::YourComponent(int exampleValue, const std::string& exampleText)
        : exampleValue(exampleValue), exampleText(exampleText) {

    }

    int RType::YourComponent::getExampleValue() const {
        return exampleValue;
    }

    void RType::YourComponent::setExampleValue(int value) {
        exampleValue = value;
    }

    const std::string& RType::YourComponent::getExampleText() const {
        return exampleText;
    }

    void RType::YourComponent::setExampleText(const std::string& text) {
        exampleText = text;
    }
```

This example demonstrates a basic creation of a Component in our ECS design pattern.