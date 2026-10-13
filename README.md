# Book Social Network

A Java and Spring Boot learning project for a book-sharing backend, with authentication, borrowing workflows, and reader feedback.

## Stack

Java 17 · Spring Boot 3.5.5 · Spring Security · JWT · Spring Data JPA · PostgreSQL · OpenAPI · Docker Compose

## Modules

- **Authentication:** registration, login, and email activation.
- **Books:** book management, sharing, and borrowing operations.
- **Feedback:** reader feedback and ratings.
- **History:** book transaction records.
- **Files:** book cover uploads.
- **API infrastructure:** pagination, auditing, and centralized exception handling.

## Local setup

Requirements: JDK 17 and Docker with Docker Compose.

From the repository root:

```bash
docker compose up -d
cd book-network
bash mvnw spring-boot:run
```

On Windows, use `mvnw.cmd spring-boot:run`.

| Component | Local address |
| --- | --- |
| API base | `http://localhost:8088/api/v1/` |
| PostgreSQL | `localhost:5432` |
| MailDev inbox | `http://localhost:1080` |
| MailDev SMTP | `localhost:1025` |

The `dev` profile is active by default. Docker Compose and the development datasource configuration use matching local database settings.

The configured activation link points to `http://localhost:4200/activate-account`; a frontend for that address is not included in this repository.

## Configuration

Review `book-network/src/main/resources/application-dev.yml` for database, email, JWT, upload, and server settings. For a separate environment, override settings with environment variables, including:

- `SPRING_DATASOURCE_URL`
- `SPRING_DATASOURCE_USERNAME`
- `SPRING_DATASOURCE_PASSWORD`
- `APPLICATION_SECURITY_JWT_SECRET_KEY`

Use a separate JWT signing key and credentials for any deployed environment.

## Project layout

| Path | Purpose |
| --- | --- |
| `book-network/` | Spring Boot application and Maven wrapper |
| `book-network/src/main/java/com/alhader/book/` | Feature modules |
| `book-network/src/main/resources/` | Configuration and activation email template |
| `docker-compose.yml` | Local PostgreSQL and MailDev services |

## Tests

```bash
cd book-network
bash mvnw test
```

Application context tests may need the local services running. Setup commands and features were documented from the repository; a successful build or test run is not claimed.
