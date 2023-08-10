# DiscordServerStats
A web application that displays a discord server's statistics, like most popular messages, users, and more. 
I am currently in the design phase of this project, so this README is subject to change. 


# Current Sprint 0:
I want to get an environment done. I've decided on using the NERP stack. (NodeJS Express React Postgres), 
along with the discord API.

# Sprint 1: 
Create a function using discord's API that returns the person with the most messages.




# Schema Design for Discord Message Reactions
This is the current preliminary design I have for the databases in PostgresSQL. 

## User Table
- `id` (UUID): Primary key for the user.
- `username` (TEXT): The username of the user.
- `discriminator` (TEXT): A discriminator value to distinguish users with the same username.
- `avatar` (TEXT): URL to the user's avatar.
- `created_at` (TIMESTAMP): The timestamp when the user was created.

## Server Table
- `id` (UUID): Primary key for the server.
- `name` (TEXT): The name of the server.
- `created_at` (TIMESTAMP): The timestamp when the server was created.

## Message Table
- `id` (UUID): Primary key for the message.
- `server_id` (UUID): Foreign key reference to the Server table.
- `author_id` (UUID): Foreign key reference to the User table (author of the message).
- `content` (TEXT): The content of the message.
- `created_at` (TIMESTAMP): The timestamp when the message was created.

## Reaction Table
- `id` (UUID): Primary key for the reaction.
- `message_id` (UUID): Foreign key reference to the Message table.
- `reactor_id` (UUID): Foreign key reference to the User table (user who reacted).
- `emoji_name` (TEXT): The name of the emoji used for the reaction (e.g., ":smile:").
- `created_at` (TIMESTAMP): The timestamp when the reaction was added. 

## Components
#1. Discord API
The Discord API is responsible for interacting with the Discord platform. It receives and sends messages in real-time using WebSockets. The API handles incoming messages from Discord users and sends outgoing messages back to the Discord platform.

#2. Custom RESTful API
The Custom RESTful API acts as an intermediary between the Discord API and the Statistics functions. It receives data from the Discord API, processes it, and then interacts with the Statistics functions to perform various statistical analyses and calculations. The Custom RESTful API exposes endpoints that allow external applications to interact with the system.

#3. Statistics Functions
The Statistics Functions form the core of the system's statistical capabilities. These functions handle various statistical analyses and calculations based on the data received from the Discord API. They provide functionalities such as calculating message frequency, user engagement metrics, word usage statistics, and more. The Statistics functions are designed to be modular, making it easier to add additional features in the future.


