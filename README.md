# Spring Boot React CRUD App

A full-stack user management application built with React, Spring Boot, Spring Data JPA, and MySQL. The application provides a browser-based interface for creating, viewing, editing, and deleting user records through a REST API.

## Features

- View all users in a table
- Create a new user with a name, username, and email
- View an individual user's details
- Edit an existing user's details
- Delete a user and refresh the user list
- REST API error handling for requests for users that do not exist
- Client-side navigation between the user list, add, edit, and view screens
- Responsive layouts using Bootstrap

## Technology Stack

### Backend

- Java 17
- Spring Boot 4.0.2
- Spring Web MVC
- Spring Data JPA
- Hibernate
- MySQL
- Maven

### Frontend

- React 19
- React Router
- Axios
- Bootstrap 5
- Create React App
- npm

## Application Architecture

The project is organized into separate frontend and backend applications:

```text
springboot-react-crud-app/
├── fullstack-backend/
│   ├── src/main/java/
│   │   └── com/project1/fullstack_backend/
│   │       ├── controller/       # REST endpoints
│   │       ├── exception/        # Not-found exception and handler
│   │       ├── model/            # JPA entity
│   │       └── repository/       # Spring Data repository
│   └── src/main/resources/
│       └── application.properties
└── fullstack-front/
    ├── public/
    └── src/
        ├── layout/               # Navigation
        ├── pages/                # Main user list page
        └── users/                # Add, edit, and view screens
```

The React frontend communicates with the Spring Boot backend using Axios. The backend persists users through Spring Data JPA and MySQL.

## REST API

The backend runs on port `8080` by default.

| Method | Endpoint | Purpose |
|---|---|---|
| `POST` | `/user` | Create a user |
| `GET` | `/users` | Retrieve all users |
| `GET` | `/user/{id}` | Retrieve one user |
| `PUT` | `/user/{id}` | Update a user |
| `DELETE` | `/user/{id}` | Delete a user |

Requests for a user ID that does not exist return an HTTP `404 Not Found` response through the application's centralized exception handler.

## Prerequisites

- Java 17 or later
- Maven, or the included Maven Wrapper
- Node.js and npm
- MySQL

## Database Setup

Create a MySQL database named `fullstack`:

```sql
CREATE DATABASE fullstack;
```

Before starting the backend, configure the local MySQL username and password in:

```text
fullstack-backend/src/main/resources/application.properties
```

Do not commit real passwords or other credentials to the repository.

## Running the Backend

From the backend directory:

```bash
cd fullstack-backend
./mvnw spring-boot:run
```

On Windows, use:

```powershell
cd fullstack-backend
.\mvnw.cmd spring-boot:run
```

The API will be available at `http://localhost:8080`.

## Running the Frontend

In a second terminal:

```bash
cd fullstack-front
npm install
npm start
```

The frontend will be available at `http://localhost:3000`.

Make sure the backend and MySQL are running before using the CRUD actions.

## Build and Test

Create an optimized frontend production build:

```bash
cd fullstack-front
npm run build
```

Run the frontend test command:

```bash
npm test
```

Run backend tests:

```bash
cd fullstack-backend
./mvnw test
```

The backend context test loads the JPA configuration and therefore requires a reachable MySQL environment. The current backend test setup is not database-independent.

## Manual CRUD Verification

With MySQL, the backend, and the frontend running:

1. Open `http://localhost:3000`.
2. Select **Add User**, enter the fields, and submit the form.
3. Confirm the new user appears in the table.
4. Select **View** and confirm the user's details.
5. Select **Edit**, change a field, submit, and confirm the updated value.
6. Select **Delete** and confirm the user is removed from the table.

## Scope and Current Limitations

This project intentionally focuses on the core CRUD workflow. It does not currently include:

- Authentication or authorization
- Input validation or form error messages
- Search, filtering, or pagination
- Docker or cloud deployment configuration
- API documentation tooling
- Comprehensive automated endpoint tests

## Resume Description

This project demonstrates full-stack CRUD development with a React frontend, Spring Boot REST API, Spring Data JPA persistence, and MySQL database integration. It is suitable for discussing component-based UI development, REST endpoint design, asynchronous API communication, entity persistence, routing, and basic exception handling.
