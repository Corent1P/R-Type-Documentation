# Prerequisites

To set up and build this project, make sure to install the following dependencies:

- **vcpkg** - [vcpkg installation guide](https://example.com/vcpkg-install-guide)
- **ninja** - [ninja installation guide](https://example.com/ninja-install-guide)
- **cmake** - [cmake installation guide](https://example.com/cmake-install-guide)
- **Visual Studio** (for Windows users) - [Visual Studio installation guide](https://example.com/visual-studio-install-guide)

Each of these tools is essential for the development and build process. Follow the links to ensure each dependency is installed correctly.

# Installation

To install the project, you need to execute the following commands :

1. **Clone** the repository
   ```sh
   git clone https://github.com/Corent1P/R-Type.git
   ```

2. If you are on **windows**, exec the *install.exe* file
   ```powershell
   .\build.bat
   ```

3. If you are on **Linux**, you need to exec the *build.sh* file
    ```sh
    ./build.sh
    ```

Once you've done all the previous steps, you should have if you are on windows a folder application where you will find **two binaries** (one for the server and one for the client). And if you are on Linux, you should have two executables files at the root of the project: *r-type_server* and *r-type_client*

# Execution

To run the project, you need to execute the following commands :

## Server

To have help on how to run the server, you can use the following command :

```sh
./r-type_server -h (or) --help
```

To run the server, you can use the following command :

```sh
    ./r-type_server <port>
```
- **port** : The port on which the server will listen (by default 4242)

## Client

To have help on how to run the client, you can use the following command :

```sh
./r-type_client -h (or) --help
```

To run the client, you can use the following command :

```sh
    ./r-type_client <ip> <port>
```
- **ip** : The ip of the server (by default localhost)
- **port** : The port on which the server is listening (by default 4242)


<a href="https://github.com/Corent1P">
<img src="https://github.com/Corent1P.png" width="60px;"/>
</a>