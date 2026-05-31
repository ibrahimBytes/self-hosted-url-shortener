<img width="1892" height="945" alt="trimly" src="https://github.com/user-attachments/assets/47bfbe01-54bb-4256-8f4e-a9fef59b3aa6" />
# Trimly

A high-performance, self-hosted URL management platform by Ibrahim, built with Node.js and Express. Maintain complete ownership of your links with robust analytics, security, and flexible database support.

---

## Technical Features

* **URL Compression:** Compress long URLs into short, trackable links.
* **Custom Aliases:** Specify unique names for your shortened URLs.
* **Link Security:** Password-protect links and configure custom expiration times.
* **User Management:** Built-in authentication with user and admin dashboards.
* **Analytics Platform:** Monitor private link metrics and user tracking details.
* **Developer Ready:** Exposes a full RESTful API for programmatic access.
* **Database Agnostic:** Supports SQLite, PostgreSQL, and MySQL using Knex.js.
* **Caching and Limits:** Optional Redis integration for rate-limiting and fast caching.

---

## Tech Stack

* **Backend Framework:** Node.js (v20), Express.js
* **Database Layer:** Knex.js Query Builder
* **Supported Databases:** PostgreSQL, MySQL, SQLite (better-sqlite3)
* **Caching Engine:** Redis
* **Frontend Engine:** Handlebars (HBS) with custom static assets
* **Containerization:** Docker, Docker Compose

---

## Project Structure

```text
.
├── custom/          # Brand overrides, custom views, and user styles
│   ├── css/
│   ├── images/
│   └── views/
├── db/              # Local database files (SQLite storage)
├── docker/          # Environment-specific Docker configuration files
├── server/          # Core application logic (routes, models, controllers)
├── static/          # Core frontend assets (CSS, JS, system images)
├── knexfile.js      # Relational database migration rules
└── package.json     # Node.js dependencies and script registry
```

---

## Getting Started

### Prerequisites

* **Node.js** (v20 or higher recommended)
* **npm** (v10 or higher)
* **Optional Engines:** Docker, PostgreSQL, Redis

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com
   cd ibrahim-url-shortner
   ```

2. Install project dependencies:
   ```bash
   npm install
   ```

### Configuration

Create a `.env` file in the root directory:

```env
PORT=3000
SITE_NAME="Trimly"
DEFAULT_DOMAIN="localhost:3000"
JWT_SECRET="your_secure_random_string_here"
DB_CLIENT="better-sqlite3"
DB_FILENAME="db/data.sqlite"
REDIS_ENABLED=false
```

### Database Initialization

Run database migrations to initialize tables:
```bash
npm run migrate
```

### Execution

* **Development Mode (Hot Reload):**
  ```bash
  npm run dev
  ```
* **Production Deployment:**
  ```bash
  npm start
  ```

---

## Docker Deployment

Deploy instantly using the standard SQLite configuration:
```bash
docker compose up -d
```

Deploy with advanced database backends (PostgreSQL/Redis):
```bash
docker compose -f docker/docker-compose.postgres.yml up -d
```

---

## REST API Reference

**Base URL:** `http://localhost:3000/api/v1`

### Authentication


| Method | Endpoint | Description | Auth Required |
| :--- | :--- | :--- | :--- |
| `POST` | `/auth/register` | Register a new user account | No |
| `POST` | `/auth/login` | Authenticate user and receive JWT | No |

### Link Management


| Method | Endpoint | Description | Auth Required |
| :--- | :--- | :--- | :--- |
| `POST` | `/links` | Generate a new short URL | Yes |
| `GET` | `/links` | List all links created by the user | Yes |
| `GET` | `/links/:id` | Fetch metadata for a single link | Yes |
| `DELETE`| `/links/:id` | Remove a shortened link | Yes |

### Analytics


| Method | Endpoint | Description | Auth Required |
| :--- | :--- | :--- | :--- |
| `GET` | `/analytics/:id` | Fetch hit counts, referrers, and geo-data | Yes |

---

## UI Customization

Apply branding updates without modifying core template files by using the `custom/` folder:

* Add custom stylesheets to `custom/css/` to override root styling rules.
* Replace layout files in `custom/views/` to alter template structures.

---

## Project Roadmap

* Advanced analytical dashboards with automated graphing systems.
* Smart auto-alias suggestions using alphanumeric keys.
* GeoIP lookup integration for localized traffic mapping.
* Custom rate-limiting tiers managed per individual user profile.

---

## License

MIT License

Copyright (c) 2026 Ibrahim

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE. 


## Author

Developed and maintained by **Ibrahim** ([@ibrahimBytes](https://github.com)). 
