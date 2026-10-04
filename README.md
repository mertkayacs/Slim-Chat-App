# Slim-Chat-App

A small chat API written in PHP with the Slim 3 framework. It exposes two POST endpoints, one for sending a message between two users and one for listing a user's messages, backed by a SQLite database through PDO.

## How to run

Requires PHP with the PDO SQLite extension enabled, and Composer.

```
composer install
php -S localhost:8000
```

The SQLite database file is included at `db/slimchatdatabase.db`. If you want to create the tables from scratch:

```sql
CREATE TABLE "users" (
    "userid"    INTEGER,
    "username"  TEXT,
    PRIMARY KEY("userid","username")
);

CREATE TABLE "messages" (
    "messageid"       INTEGER,
    "senderUserid"    INTEGER,
    "receiverUserid"  INTEGER,
    "message"         TEXT,
    PRIMARY KEY("messageid")
);
```

There is no user registration endpoint, so users must be inserted into the `users` table directly before messages can be sent between them.

### API

Both endpoints take parameters as form-data (key, value pairs).

`POST /getMessages`

- `username`: the user whose messages to list.
- Returns a JSON array of messages (messageid, sender username, receiver username, message text) ordered by messageid ascending. Returns 404 if the user does not exist.

`POST /postMessages`

- `senderUsername`, `receiverUsername`, `message`.
- Inserts the message into the database and returns a JSON status with code 201.

## Tech used

- PHP
- Slim Framework 3 (`slim/slim: ^3.0` in composer.json)
- SQLite via PDO
- Composer

## Status

Assignment project, 2021. No authentication or user registration (not part of the original assignment scope).

## License

MIT License. See LICENSE.
