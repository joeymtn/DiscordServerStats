# DiscordServerStats
A web application that displays a discord server's statistics, like most popular messages, users, and more. 
I am currently in the design phase of this project, so this README is subject to change. 


# Current Sprint 0:
I want to get an environment done. I've decided on using the NERP stack. (NodeJS Express React Postgres), 
along with the discord API. 




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

