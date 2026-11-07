<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="docs/brand/svg/slim-chat-logo-on-dark.svg">
    <img src="docs/brand/svg/slim-chat-logo-on-light.svg" alt="Slim Chat" width="260">
  </picture>
</p>

<h1 align="center">A chat API in Slim and SQLite. Two endpoints, one database file.</h1>

<p align="center">
  Assignment project from 2021: a small chat backend in PHP with Slim 3.<br>
  <b>POST /getMessages. POST /postMessages. Form-data in, JSON out.</b>
</p>

<p align="center">
  <a href="LICENSE"><img alt="License: MIT" src="https://img.shields.io/badge/license-MIT-3b82f6?style=flat-square"></a>
  <img alt="PHP" src="https://img.shields.io/badge/PHP-777BB4?style=flat-square&logo=php&logoColor=white">
  <img alt="SQLite" src="https://img.shields.io/badge/SQLite-003B57?style=flat-square&logo=sqlite&logoColor=white">
  <img alt="Framework: Slim 3" src="https://img.shields.io/badge/framework-Slim%203-0F6B66?style=flat-square">
  <img alt="Assignment, 2021" src="https://img.shields.io/badge/project-assignment%202021-0F6B66?style=flat-square">
  <a href="https://github.com/mertkayacs/Slim-Chat-App"><img alt="GitHub stars" src="https://img.shields.io/github/stars/mertkayacs/Slim-Chat-App?style=flat-square&logo=github&color=8A6D3B"></a>
</p>

<p align="center">
  <a href="#quick-start"><img alt="Quick start" src="https://img.shields.io/badge/Quick%20start-0F6B66?style=for-the-badge&logo=data%3Aimage%2Fsvg%2Bxml%3Bbase64%2CPHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCIgd2lkdGg9IjI0IiBoZWlnaHQ9IjI0Ij48ZyBmaWxsPSJub25lIiBzdHJva2U9IiNmZmZmZmYiIHN0cm9rZS1saW5lY2FwPSJyb3VuZCIgc3Ryb2tlLWxpbmVqb2luPSJyb3VuZCIgc3Ryb2tlLXdpZHRoPSIyIj48cGF0aCBkPSJNMTIgMTV2NXMzLjAzLS41NSA0LTJjMS4wOC0xLjYyIDAtNSAwLTUiLz48cGF0aCBkPSJNNC41IDE2LjVjLTEuNSAxLjI2LTIgNS0yIDVzMy43NC0uNSA1LTJjLjcxLS44NC43LTIuMTMtLjA5LTIuOTFhMi4xOCAyLjE4IDAgMCAwLTIuOTEtLjA5Ii8%2BPHBhdGggZD0iTTkgMTJhMjIgMjIgMCAwIDEgMi0zLjk1QTEyLjg4IDEyLjg4IDAgMCAxIDIyIDJjMCAyLjcyLS43OCA3LjUtNiAxMWEyMi40IDIyLjQgMCAwIDEtNCAyeiIvPjxwYXRoIGQ9Ik05IDEySDRzLjU1LTMuMDMgMi00YzEuNjItMS4wOCA1IC4wNSA1IC4wNSIvPjwvZz48L3N2Zz4%3D&logoColor=white"></a>
  <a href="#api"><img alt="API" src="https://img.shields.io/badge/API-1E2A38?style=for-the-badge&logo=data%3Aimage%2Fsvg%2Bxml%3Bbase64%2CPHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCIgd2lkdGg9IjI0IiBoZWlnaHQ9IjI0Ij48ZyBmaWxsPSJub25lIiBzdHJva2U9IiNmZmZmZmYiIHN0cm9rZS1saW5lY2FwPSJyb3VuZCIgc3Ryb2tlLWxpbmVqb2luPSJyb3VuZCIgc3Ryb2tlLXdpZHRoPSIyIj48Y2lyY2xlIGN4PSI2IiBjeT0iMTkiIHI9IjMiLz48cGF0aCBkPSJNOSAxOWg4LjVhMy41IDMuNSAwIDAgMCAwLTdoLTExYTMuNSAzLjUgMCAwIDEgMC03SDE1Ii8%2BPGNpcmNsZSBjeD0iMTgiIGN5PSI1IiByPSIzIi8%2BPC9nPjwvc3ZnPg%3D%3D&logoColor=white"></a>
  <a href="index.php"><img alt="Source" src="https://img.shields.io/badge/Source-1E2A38?style=for-the-badge&logo=data%3Aimage%2Fsvg%2Bxml%3Bbase64%2CPHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCIgd2lkdGg9IjI0IiBoZWlnaHQ9IjI0Ij48ZyBmaWxsPSJub25lIiBzdHJva2U9IiNmZmZmZmYiIHN0cm9rZS1saW5lY2FwPSJyb3VuZCIgc3Ryb2tlLWxpbmVqb2luPSJyb3VuZCIgc3Ryb2tlLXdpZHRoPSIyIj48cGF0aCBkPSJNNiAyMmEyIDIgMCAwIDEtMi0yVjRhMiAyIDAgMCAxIDItMmg4YTIuNCAyLjQgMCAwIDEgMS43MDQuNzA2bDMuNTg4IDMuNTg4QTIuNCAyLjQgMCAwIDEgMjAgOHYxMmEyIDIgMCAwIDEtMiAyeiIvPjxwYXRoIGQ9Ik0xNCAydjVhMSAxIDAgMCAwIDEgMWg1Ii8%2BPHBhdGggZD0iTTEwIDEyLjUgOCAxNWwyIDIuNSIvPjxwYXRoIGQ9Im0xNCAxMi41IDIgMi41LTIgMi41Ii8%2BPC9nPjwvc3ZnPg%3D%3D&logoColor=white"></a>
</p>

Slim Chat is a small chat API written in PHP on the Slim 3 framework, as an assignment in 2021. It exposes two POST endpoints, one for sending a message between two users and one for listing a user's messages, backed by a SQLite database through PDO. The database file ships with the repository.

---

## Why Slim Chat

The API keeps the surface small.

|  |  |
|---|---|
| <img src="docs/assets/readme/icons/route.svg" width="18" height="18" alt=""> **Two endpoints** | `/postMessages` stores a message and `/getMessages` lists a user's messages, ordered by message id. |
| <img src="docs/assets/readme/icons/database.svg" width="18" height="18" alt=""> **One SQLite file** | [db/slimchatdatabase.db](db/slimchatdatabase.db) holds the users and messages tables, with a few test rows. |
| <img src="docs/assets/readme/icons/layers.svg" width="18" height="18" alt=""> **Small codebase** | Routes live in index.php. The message logic is in app/Message.php and the database connection in app/SQLiteConnectionEstablisher.php. |

## Features

- Form-data requests with JSON responses.
- A 404 response with an error message when a user does not exist.
- Slim 3.12 and its dependencies are committed under vendor/.

## Quick start

```sh
composer install
php -S localhost:8000
```

To create the tables from scratch:

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

There is no registration endpoint, so insert users into the users table directly before sending messages.

### Requirements

- PHP with the PDO SQLite extension.
- Composer.

### API

Both endpoints take form-data.

| Endpoint | Parameters | Response in the code |
|---|---|---|
| `POST /getMessages` | `username` | A JSON array of messages ordered by message id, or status 404 when the user does not exist. |
| `POST /postMessages` | `senderUsername`, `receiverUsername`, `message` | A JSON status with HTTP code 201. |

## FAQ

<details>
<summary><b>How do I create users?</b></summary>

Insert rows into the users table of the SQLite file. The API has no registration endpoint.
</details>

<details>
<summary><b>What format do requests use?</b></summary>

POST with form-data, as key and value pairs.
</details>

<details>
<summary><b>Is there authentication?</b></summary>

The assignment scope did not include authentication or registration, so the API has neither.
</details>

<details>
<summary><b>Which database does it use?</b></summary>

SQLite, through PDO, in the file named in app/Config.php.
</details>

If Slim Chat is useful to you, a ⭐ helps other people find it.

## License

[MIT License](LICENSE). See the LICENSE file for the full text.

[![views](https://hits.sh/github.com/mertkayacs/Slim-Chat-App.svg?view=today-total&style=flat-square&label=views&color=0F6B66&labelColor=1E2A38)](https://github.com/mertkayacs/Slim-Chat-App)
