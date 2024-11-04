# Techonlogies

## Overview

During this project, we had to choose between many technologies, in this page we will try to explain why we choose these technologies. To explain how and why we choose these technologies, we will compare them to other technologies that we could have used, using a rating system that will differ and be explained beforhand.

## Network library

The first thing, we had to choose was the network library. After some research, our choices narrowed down to 2 libraries: **POCO** and **Boost**. We will compare these two libraries using the following rating system:\
- **Performance** : How fast the library is / 5
- **Documentation** : How well the library is documented / 5
- **Relability** : How reliable the library is / 5
- **Dependencies** : Does the lib require any dependicies to work / 5

### Boost.Asio
#### Performance
From what we read online, the Boost library is very fast and efficient. But no performance benchmark were available **4/5**

#### Documentation
The Boost library is very well documented, it has a lot of examples and tutorials on how to use it. It also has a very good reference documentation. **5/5**

#### Reliability
This is one of the main point of the Boost library, it is very reliable and has been used by many people for many years. It is a very stable library, some part of it are even used in the C++ standard library. **5/5**

#### Dependencies
The Boost library is a header only library, so it doesn't require any dependencies to work. **5/5**

#### Total
**19/20**

### POCO
#### Performance
From what we read online, the Boost library is very fast and efficient. But no performance benchmark were available **4/5**

#### Documentation
The POCO library is well documentated, but we found it less easy to understand what some methods were doing. Plus the community is smaller than Boost, so there are less examples and tutorials. **3/5**

#### Reliability
From what we read online, the POCO library is very reliable and has been used by many people for many years. It is a very stable library but not to the point of Boost that as multiple part of it integrated directly in the C++ standard library **5/5**

#### Dependencies
The POCO library is a header only library, so it doesn't require any dependencies to work. **5/5**

#### Total
**17/20**

### Conclusion
We choose to use the **Boost** library because it is more documented and has a bigger community than POCO. But POCO is still a very good library and could have been a good choice too.

## Graphic library

Now that we have chosen the network library, we had to choose the graphic library. Our choices narrowed down to 3 libraries : **SMFL**, **Raylib**, **OpenGL**. We will compare these three libraries using the following rating system:\
- **Prior knowledge** : How much we know about the library / 7.5
- **Capabilities** : What the library can do (ex can it do 3D or only 2D) / 5
- **Portability** : How easy it is to make the library work on multiple platforms / 5
- **Accessibility** : How easy is it to add other input / 2.5

### SFML

#### Prior knowledge
We know this library very well, we used it a lot during our first two years at EPITECH. **7.5/7.5**

#### Capabilities
SFML is a 2D library, it can't do 3D. **3/5**

#### Portability
SFML is very easy to make work on multiple platforms, it is a very portable library. **5/5**

#### Accessibility
SFML is very easy to add other input, it has a lot of examples and tutorials on how to do it. **2.5/2.5**

#### Total
**18/20**

### Raylib

#### Prior knowledge
We know this library a little bit, we used during a project at EPITECH. **5/7.5**

#### Capabilities
Raylib is a 3D library but it can also do 2D **5/5**

#### Portability
Raylib is very easy to make work on multiple platforms, it is a very portable library. **5/5**

#### Accessibility
Raylib is very easy to add other input, it has a lot of examples and tutorials on how to do it. **2.5/2.5**

#### Total
**17.5/20**

### OpenGL

#### Prior knowledge
We have never used this library before. **0/7.5**

#### Capabilities
OpenGL is a 3D library but it can also do 2D **5/5**

#### Portability
OpenGL is very easy to add other input, it has a lot of examples and tutorials on how to do it. **2.5/2.5**

#### Accessibility
OpenGL doesn't support controllers, so we would have to add this ourselves. **0/2.5**

#### Total
**7.5/20**

### Conclusion

We choose to use the **SFML** library because we know it very well and it is a very good library for 2D games. But **Raylib** could have been a good choice too, it is a very good library for 2D and 3D games. **OpenGL** is a very good library but we don't know it and it doesn't support controllers, so it would have been a bad choice for our project.

## Configuration file parser

Now that we have chosen the graphic library, we had to choose the configuration file parser. Firstly we decided that we wanted to use json for our configuration files, then we needed to look for the best json parser library and our had to narrowed our choice between two of them: **Boost.PropertyTree** and **JsonCpp**. We will compare these two libraries using the following rating system:\
- **Performance** : How fast the library is / 5
- **Documentation** : How well the library is documented / 5
- **Relability** : How reliable the library is / 5
- **Dependencies** : Does the lib require any dependicies to work / 5

### Boost.PropertyTree

#### Performance
If we believe this [website](https://230.jsondocs.prtest.cppalliance.org/libs/json/doc/html/json/benchmarks.html#json.benchmarks.parse_random_json) , the Boost library is very fast and efficient. But not the fastest when it came to random json with multiple type of data inside **3/5**

#### Documentation
The Boost library is very well documented, it has a lot of examples and tutorials on how to use it. It also has a very good reference documentation. **5/5**

#### Reliability
This is one of the main point of the Boost library, it is very reliable and has been used by many people for many years. It is a very stable library, some part of it are even used in the C++ standard library. **5/5**

#### Dependencies
The Boost library is a header only library, so it doesn't require any dependencies to work. Plus we already use Boost as our networking library **5/5**

#### Total
**18/20**

### JsonCpp

#### Performance
If we believe the creator of the library, the JsonCpp library as a complexity of O(n) for parsing a json file. **5/5**

#### Documentation
The JsonCpp library is well documentated, but we found it less easy to understand what some methods were doing. **4/5**

#### Reliability
From our usage, we found that the JsonCpp lib is very reliable. **4/5**

#### Dependencies
The JsonCpp library is a header only library, so it doesn't require any dependencies to work. **5/5**

#### Total
**18/20**

### Conclusion
So it is a tie. But we had to choose anyway to choose i tried to code a simple program using both libraries and i found that **JsonCpp** was easier to use and more intuitive than the **Boost.PropertyTree**. So we choose to use the **JsonCpp** library.

## Scripting language

We new that we wanted to use a scripting language for our game, so we had to choose between **Lua** and **Python**. But this time we used a different rating system, aka a simple google search to see which one was the most used in the video game industry, and we found that **Lua** was the most used scripting language in the video game industry. So we choose to use **Lua**. To parse it we used the official **Lua** library.










