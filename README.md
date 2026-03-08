# API Gin com Golang
This project is a RESTful API developed with Go and the Gin framework. It provides CRUD (Create, Read, Update, Delete) functionalities for managing student (`aluno`) records, with data persisted in a PostgreSQL database. The environment is containerized using Docker and Docker Compose for straightforward setup and development.

## Features

*   Full CRUD operations for students.
*   Search for students by unique ID or CPF.
*   Server-side data validation for student attributes.
*   Serves static HTML pages to display data.
*   Containerized with Docker for consistent and isolated environments.
*   Includes a suite of integration tests.
*   Continuous Integration configured with GitHub Actions.

## Technology Stack

*   **Language:** Go
*   **Web Framework:** Gin
*   **Database:** PostgreSQL
*   **ORM:** GORM
*   **Containerization:** Docker, Docker Compose

## Getting Started

### Prerequisites

*   Docker
*   Docker Compose

### Installation and Running

1.  **Clone the repository:**
    ```bash
    git clone https://github.com/karolaynel/teste-alura.git
    cd teste-alura.git
    ```

2.  **Start the services:**
    Use Docker Compose to build and run the application and the database containers.
    ```bash
    docker compose up -d
    ```
    The API will be running and accessible at `http://localhost:8080`.

## API Endpoints

The following endpoints are available:

| Method | Endpoint             | Description                                  |
|--------|----------------------|----------------------------------------------|
| `GET`  | `/alunos`            | Retrieves a list of all students.            |
| `POST` | `/alunos`            | Creates a new student.                       |
| `GET`  | `/alunos/:id`        | Retrieves a single student by their ID.      |
| `PATCH`| `/alunos/:id`        | Updates an existing student's information.   |
| `DELETE`| `/alunos/:id`       | Deletes a student by their ID.               |
| `GET`  | `/alunos/cpf/:cpf`   | Searches for a student by their CPF.         |
| `GET`  | `/:nome`             | Returns a simple JSON greeting to the name.  |
| `GET`  | `/index`             | Renders an HTML page listing all students.   |
| `ANY`  | `/*path`             | Returns a custom 404 page for unknown routes.|

### Example: Create a New Student

```bash
curl -X POST http://localhost:8080/alunos \
-H "Content-Type: application/json" \
-d '{
    "nome": "Jane Doe",
    "cpf": "12345678901",
    "rg": "123456789"
}'
```

## Running Tests

The project includes a set of tests to validate the functionality of the API controllers.

To run the test suite, first ensure the services are running, then execute the following command:
```bash
docker compose exec app go test -v main_test.go
```

## Makefile

A `Makefile` is located in the `routes/` directory to help automate common tasks. You can run these commands from the project root.

*   **Start services:**
    ```bash
    make -f routes/Makefile start
    ```
*   **Run tests:**
    ```bash
    make -f routes/Makefile test
    ```
*   **Run linter:**
    ```bash
    make -f routes/Makefile lint
    ```
*   **Run CI pipeline locally:**
    ```bash
    make -f routes/Makefile ci

## 📌 NOTE: About This Project

**Status: Work in Progress / Study Project**

This project was created for **educational purposes** during an Alura course on building APIs with Go, Gin, and implementing CI/CD pipelines.

Important notes:
- 🎯 Focused on learning and experimentation
- ⚠️ Not recommended for production use
- 🔄 Subject to significant changes
- 📚 Open to suggestions and improvements

Contributions are welcome, but remember: I'm still learning! 🌱
