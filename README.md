# 🔐 JWT Authentication API (Rust + Actix Web)

Simple JWT Authentication REST API built with Rust and Actix Web.
This project demonstrates the basic concepts of login, JWT token generation, and protected endpoints using the `jsonwebtoken` crate.

Suitable for:
- Learning the Rust backend
- API authentication practice
- Basics before diving into JWT middleware and security testing

---

## 🚀 Tech Stack

- Rust
- Actix Web v4
- JSON Web Token (`jsonwebtoken`)
- Serde
- Chrono

---

## 📂 Project Structure
```bash
JWT_Auth/
├── Cargo.toml
└── src
└── main.rs
```

---

## Authentication Flow

1. User performs **POST /login**
2. Server verifies username & password
3. If valid → server returns **JWT token**
4. Token is used on the **/protected** endpoint
5. If token is valid → access is granted

---

## 📌 Hardcoded Credentials (Demo Only)

```text
Username: admin
Password: password
```

⚠️ Note:
This is for educational purposes only. Do not use hardcoded credentials in production.

## ▶️ Running a Project
### 1. Clone Repository
```bash
git clone https://github.com/Kucing-Dev/JWT-Authentication-in-Actix-Web.git
cd JWT_Auth
```

### 2. Install Dependencies
```bash
[dependencies]
actix-web = "4"
jsonwebtoken = "9"
serde = { version = "1", features = ["derive"] }
serde_json = "1"
chrono = "0.4"
```
```bash
cargo build
```
### 3. Run the Server
```bash
cargo run

```

The server will run on:

```bash
http://127.0.0.1:8080

```

## 🔐 Endpoint API
### ✅ Login (Generate JWT)
Request
```bash
POST /login
Content-Type: application/json
```

Body
```bash
{
  "username": "admin",
  "password": "password"
}
```

Response
```bash
{
  "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9..."
}
```

### 🔒 Protected Endpoint
Request
```bash
GET /protected
Authorization: Bearer <JWT_TOKEN>
```

Response (Success)
```bash
Welcome, admin!
```

Response (Invalid / Missing Token)
```bash
Invalid token
```

or
```bash
Authorization header missing or malformed
```

