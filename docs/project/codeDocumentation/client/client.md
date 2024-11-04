# RType::Client Class Documentation

## Overview
The Client class implements network communication functionality for the R-Type game client, handling UDP-based message exchange with the game server using [Boost.Asio](https://www.boost.org/doc/libs/release/doc/html/boost_asio.html).

## Class Definition
Located in `/home/antoinegrand/Delivery/B-CPP/B-CPP-500/R-Type/src/client/communication/Client.hh`

## Construction
```cpp
Client(boost::asio::io_context &ioContext, const std::string &host, const std::string &port)
```
Creates a new client instance connecting to specified host and port:
- `ioContext`: Boost asio context for async operations
- `host`: Server host address
- `port`: Server port number

Throws `ClientError` if connection is invalid.

## Public Methods

### Message Sending
```cpp
void send(const std::basic_string<unsigned char> &message)
```
Sends a binary message to the server endpoint. Throws `ClientError` if send fails.

### Message Receiving
```cpp
std::basic_string<unsigned char> receive(void)
```
Receives messages from the server:
- Buffer size: 128 bytes
- Returns received data as unsigned char string

### Connection Management
```cpp
void cancel(void)
```
Cancels the socket connection (currently only prints "cancel Socket")

## Private Members

### Network Components
- `_ioContext`: Reference to Boost asio IO context
- `_endpoint`: UDP endpoint for server connection
- `_socket`: UDP socket for network communication

## Dependencies
- Boost.Asio for networking
- [UDP](https://en.wikipedia.org/wiki/User_Datagram_Protocol) protocol implementation
- Custom ClientError class for error handling

## Thread Safety
The class is not explicitly thread-safe and should be synchronized externally if used across multiple threads.

## Error Handling
- Throws `ClientError` for connection issues
- Throws `ClientError` for message sending failures

## Notes
- Uses UDP protocol for communication
- Implements basic send/receive functionality
- Designed for asynchronous network operations
