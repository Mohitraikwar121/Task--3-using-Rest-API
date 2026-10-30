# 🔗 Task 3: RESTful API with Node.js & Express 

A lightweight RESTful API built with **Node.js** and **Express.js** that implements full CRUD (Create, Read, Update, Delete) operations on a `tasks` resource, with consistent JSON responses, input validation, and proper HTTP status codes.

<p align="center">
  <img src="https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=nodedotjs&logoColor=white" alt="Node.js" />
  <img src="https://img.shields.io/badge/Express.js-000000?style=for-the-badge&logo=express&logoColor=white" alt="Express.js" />
  <img src="https://img.shields.io/badge/API-REST-blue?style=for-the-badge" alt="REST API" />
  <img src="https://img.shields.io/badge/Data-JSON-orange?style=for-the-badge" alt="JSON" />
  <img src="https://img.shields.io/badge/Purpose-Educational-green?style=for-the-badge" alt="Educational Project" />
</p>

---

## ⚡ Quick Start

```bash
git clone https://github.com/Mohitraikwar121/Task--3-using-Rest-API.git
cd Task--3-using-Rest-API
npm install
npm start
```

Then open **http://localhost:3000/api/tasks** in your browser or API client. You should see a JSON response.

---

## 📑 Table of Contents

- [Overview](#-overview)
- [Features](#-features)
- [Tech Stack](#-tech-stack)
- [Project Structure](#-project-structure)
- [Installation and Setup](#-installation-and-setup)
- [API Reference](#-api-reference)
- [Examples](#-examples)
- [Error Handling](#-error-handling)
- [HTTP Status Codes](#-http-status-codes)
- [Testing](#-testing)
- [Troubleshooting](#-troubleshooting)
- [Roadmap](#-roadmap)
- [Contributing](#-contributing)
- [License](#-license)
- [Author](#-author)

---

## 📌 Overview

This project is a hands-on implementation of a RESTful API. It exposes resource-oriented endpoints for managing tasks through standard HTTP methods, and it is designed to be easy to read, run, and extend.

### 🎯 Learning Objectives

- Understand REST architecture and when to use each HTTP method.
- Implement CRUD operations with Express.js routing and middleware.
- Parse JSON requests and return structured JSON responses.
- Design clean, predictable endpoints.
- Use HTTP status codes and basic error handling correctly.
- Lay the groundwork for database integration and a scalable backend.

---

## ✨ Features

| Feature | Description |
|---|---|
| ➕ **Create** | Add a new task with `POST /api/tasks`. |
| 📖 **Read** | Fetch all tasks or a single task by ID with `GET`. |
| ✏️ **Update** | Modify an existing task with `PUT /api/tasks/:id`. |
| 🗑️ **Delete** | Remove a task with `DELETE /api/tasks/:id`. |
| 📦 **JSON in, JSON out** | All requests and responses use `application/json`. |
| 🛡️ **Validation & errors** | Invalid input and missing resources return clear error responses. |
| 🔌 **RESTful routing** | Resource-based URLs with standard HTTP verbs. |

---

## 🛠️ Tech Stack

| Technology | Purpose |
|---|---|
| [Node.js](https://nodejs.org/) | JavaScript runtime. |
| [Express.js](https://expressjs.com/) | Routing and middleware framework. |
| JSON | Request and response data format. |
| npm | Dependency management. |
| Postman / Thunder Client / cURL | API testing. |

> **Data storage:** Tasks are held in an **in-memory array**, so data resets whenever the server restarts. See the [Roadmap](#-roadmap) for persistent storage options such as MongoDB or PostgreSQL.

---

## 📂 Project Structure

<!-- TODO: Replace this tree with your actual structure if it differs. -->

```text
Task--3-using-Rest-API/
├── src/
│   ├── routes/
│   │   └── taskRoutes.js        # Endpoint definitions
│   ├── controllers/
│   │   └── taskController.js    # Request-handling logic
│   ├── models/
│   │   └── taskModel.js         # Data access (in-memory store)
│   └── app.js                   # Express setup, middleware, route mounting
├── .env                         # Local configuration (not committed)
├── .gitignore
├── package.json
├── package-lock.json
└── README.md
```

| Path | Responsibility |
|---|---|
| `routes/` | Maps URLs and HTTP methods to controller functions. |
| `controllers/` | Validates input, calls the model, and shapes responses. |
| `models/` | Holds the task data and the functions that operate on it. |
| `app.js` | Configures Express, JSON parsing, routes, and error middleware. |
| `.env` | Environment-specific settings such as `PORT`. |

---

## ⚙️ Installation and Setup

### Prerequisites

- [Node.js](https://nodejs.org/) (current LTS recommended) and npm
- Git
- An API client such as Postman, Thunder Client, or cURL

### Steps

**1. Clone the repository**

```bash
git clone https://github.com/Mohitraikwar121/Task--3-using-Rest-API.git
cd Task--3-using-Rest-API
```

**2. Install dependencies**

```bash
npm install
```

<details>
<summary>Starting from scratch without a <code>package.json</code>?</summary>

```bash
npm init -y
npm install express
```

</details>

**3. Configure environment variables (optional)**

Create a `.env` file in the project root:

```env
PORT=3000
```

| Variable | Default | Description |
|---|---|---|
| `PORT` | `3000` | Port the server listens on. |

> If you use a `.env` file, install `dotenv` (`npm install dotenv`) and load it at the top of `app.js` with `require('dotenv').config()`. On Node 20.6+ you can instead run `node --env-file=.env src/app.js`.

**4. Start the server**

```bash
npm start
```

For auto-restart during development (requires a `dev` script, for example using `nodemon`):

```bash
npm run dev
```

The API is now available at `http://localhost:3000`.

### Available Scripts

<!-- TODO: Keep this table in sync with your package.json "scripts". -->

| Script | Command | Purpose |
|---|---|---|
| `npm start` | `node src/app.js` | Run the server. |
| `npm run dev` | `nodemon src/app.js` | Run with automatic restarts. |

---

## 🔌 API Reference

**Base URL:** `http://localhost:3000/api/tasks`

| Method | Endpoint | Description | Success |
|---|---|---|---|
| `GET` | `/api/tasks` | List all tasks. | `200 OK` |
| `GET` | `/api/tasks/:id` | Get one task by ID. | `200 OK` |
| `POST` | `/api/tasks` | Create a task. | `201 Created` |
| `PUT` | `/api/tasks/:id` | Update a task. | `200 OK` |
| `DELETE` | `/api/tasks/:id` | Delete a task. | `200 OK` |

### Task Object

| Field | Type | Required | Description |
|---|---|---|---|
| `id` | number | Auto-generated | Unique identifier assigned by the server. |
| `title` | string | Yes | Short description of the task. Must not be empty. |
| `completed` | boolean | No | Completion status. Defaults to `false`. |

---

## 🧑‍💻 Examples

Each example includes a cURL command you can copy and run.

### 1. Create a Task

```bash
curl -X POST http://localhost:3000/api/tasks \
  -H "Content-Type: application/json" \
  -d '{"title": "Learn REST APIs", "completed": false}'
```

**Response:** `201 Created`

```json
{
  "id": 1,
  "title": "Learn REST APIs",
  "completed": false
}
```

### 2. Get All Tasks

```bash
curl http://localhost:3000/api/tasks
```

**Response:** `200 OK`

```json
[
  {
    "id": 1,
    "title": "Learn REST APIs",
    "completed": false
  }
]
```

### 3. Get a Task by ID

```bash
curl http://localhost:3000/api/tasks/1
```

**Response:** `200 OK`

```json
{
  "id": 1,
  "title": "Learn REST APIs",
  "completed": false
}
```

### 4. Update a Task

```bash
curl -X PUT http://localhost:3000/api/tasks/1 \
  -H "Content-Type: application/json" \
  -d '{"title": "Master REST APIs", "completed": true}'
```

**Response:** `200 OK`

```json
{
  "id": 1,
  "title": "Master REST APIs",
  "completed": true
}
```

### 5. Delete a Task

```bash
curl -X DELETE http://localhost:3000/api/tasks/1
```

**Response:** `200 OK`

```json
{
  "message": "Task deleted successfully"
}
```

> **Windows users:** In PowerShell or Command Prompt, single quotes around JSON do not work the same way. Use Postman or Thunder Client, or escape the quotes: `-d "{\"title\":\"Learn Express\",\"completed\":false}"`. On PowerShell, call `curl.exe` rather than `curl`, which is an alias for `Invoke-WebRequest`.

---

## 🚨 Error Handling

Errors return a JSON body with a consistent shape:

```json
{
  "error": "Task not found"
}
```

| Scenario | Status | Example response |
|---|---|---|
| Task ID does not exist | `404 Not Found` | `{ "error": "Task not found" }` |
| `title` is missing or empty | `400 Bad Request` | `{ "error": "Title is required" }` |
| Malformed JSON body | `400 Bad Request` | `{ "error": "Invalid JSON" }` |
| Unexpected server failure | `500 Internal Server Error` | `{ "error": "Internal server error" }` |

<!-- TODO: Make the messages above match what your code actually returns. -->

---

## 📊 HTTP Status Codes

| Code | Meaning | Used for |
|---|---|---|
| `200 OK` | Request succeeded | Reading, updating, or deleting a task. |
| `201 Created` | Resource created | Successful `POST`. |
| `400 Bad Request` | Invalid input | Missing or invalid fields. |
| `404 Not Found` | Resource missing | Unknown task ID. |
| `500 Internal Server Error` | Server failure | Unhandled errors. |

---

## 🧪 Testing

### With Postman or Thunder Client

1. Start the server with `npm start`.
2. Set the URL to `http://localhost:3000/api/tasks`.
3. Choose the HTTP method.
4. For `POST` and `PUT`, set **Body → raw → JSON** and enter the payload.
5. Send the request and check the status code and response body.
6. Also test the failure paths: a non-existent ID, a missing `title`, and malformed JSON.

### Suggested Test Checklist

- [ ] `POST` returns `201` and an object with a generated `id`.
- [ ] `GET /api/tasks` returns an array containing the new task.
- [ ] `GET /api/tasks/:id` returns the right task, and `404` for an unknown ID.
- [ ] `PUT` changes the stored values.
- [ ] `DELETE` removes the task, and a follow-up `GET` returns `404`.
- [ ] `POST` without a `title` returns `400`.

---

## 🩺 Troubleshooting

| Problem | Likely cause and fix |
|---|---|
| `EADDRINUSE: address already in use` | Another process is using the port. Stop it or change `PORT` in `.env`. |
| `Cannot GET /` | The API lives under `/api/tasks`; there is no route at `/`. |
| `req.body` is `undefined` | Make sure `app.use(express.json())` is registered before your routes, and that the request sends `Content-Type: application/json`. |
| Tasks disappear after a restart | Expected behavior with in-memory storage. Add a database for persistence. |
| `npm start` fails | Confirm a `start` script exists in `package.json` and that you ran `npm install`. |

---

## 🚀 Roadmap

- [ ] Persistent storage with MongoDB or PostgreSQL
- [ ] Schema validation with Joi or `express-validator`
- [ ] Centralized error-handling middleware
- [ ] Pagination, filtering, and sorting
- [ ] Authentication and authorization with JWT
- [ ] Automated tests with Jest and Supertest
- [ ] API documentation with Swagger / OpenAPI
- [ ] Docker support
- [ ] Deployment on Render, Railway, or similar

---

## 🤝 Contributing

Contributions and suggestions are welcome.

1. Fork the repository.
2. Create a feature branch: `git checkout -b feature/your-feature`.
3. Commit your changes: `git commit -m "Add your feature"`.
4. Push the branch: `git push origin feature/your-feature`.
5. Open a pull request describing your changes.

## 📄 License

This project was created for educational and practice purposes and currently has no formal open-source license. If you plan to share or reuse it, add a `LICENSE` file (for example, MIT).


## 👨‍💻 Author

**Mohit Raikwar**
- GitHub: [@Mohitraikwar121](https://github.com/Mohitraikwar121)
- LinkedIn: [Mohit Raikwar](https://linkedin.com/in/mohit-raikwar-7541232b8)


<p align="center">
  <b>Built with Node.js and Express.js 🚀</b>
  <br />
  <sub>Learning backend development, one API at a time.</sub>
</p>
