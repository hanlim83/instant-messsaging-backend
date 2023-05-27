# Tiktok Tech Immersion 2023 Project

[![Tests](https://github.com/hanlim83/instant-messsaging-backend/actions/workflows/test.yml/badge.svg)](https://github.com/hanlim83/instant-messsaging-backend/actions/workflows/test.yml)

This is a completed project for backend assignment of 2023 TikTok Tech Immersion. A front-end can be built from this project but it is not in the scope of the assignment at this time.

This project is possible with the assistance of [Peng Weixing](https://github.com/weixingp) 

This README.md is authored by Hansen Lim.

## Project Components

![Architecture Design](/img/UML%20diagram.jpg "Architecture Design]")

- Redis Cache: To store all messages created
- Remote Procedure Call (RPC) Server: Contains the business logic to handle Create/Read operations of chat messages
- HTTP Server: A proxy to convert HTTP requests from clients to RPC calls and RPC call responses back to HTTP responses for the clients to be consumed

## Running the project
### Requirements
- [GoLang](https://go.dev)
- [Docker Desktop](https://www.docker.com/products/docker-desktop/)
- Either [GoLand](https://www.jetbrains.com/go/) or [Visual Studio Code](https://code.visualstudio.com/)

- [Postman]()
### Setup steps
Either run the `docker-compose` in the project's directory or make use of the extensions in either GoLand or VS Code to build the containers and setup the project automatically.

Reference: [Docker-compose - Getting Started](https://docs.docker.com/compose/gettingstarted/)
### Testing

Using Postman, make HTTP POST (To create messages) / Get (To retrieve messages) to the endpoint `localhost:8080`:
- HTTP GET **/api/pull** parameters
    - chat: Chat room (sender:receiver) 
    - text: Actual message content
    - sender: Identity of the sender
- HTTP POST **/api/send** parameters
    - chat: Chat room (sender:receiver) 
    - cursor: Staring index of all messages matching that requesting chat room
    - limit: Limits how many messages are being returned 
    - reverse: Specifies if the messages should be returned based timestamp (Latest message is first instead of based on message ID)

![HTTP POST /api/send request via Postman](/img/image%20(2).png "HTTP POST /api/send request via Postman")
![HTTP GET /api/pull request via Postman](/img/image.png "HTTP GET /api/pull request via Postman")
![HTTP GET /api/pull request via Postman](/img/image%20(1).png "HTTP GET /api/pull request via Postman")
