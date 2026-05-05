# CoreServices2

Spring Boot user service with signup and signin endpoints backed by PostgreSQL. The application creates user accounts, validates credentials, and returns a JWT for successful signins.

## Tech Stack

- Java 17
- Spring Boot 4
- Spring Web MVC
- Spring Data JPA
- PostgreSQL
- JJWT
- Springdoc OpenAPI / Swagger UI
- Maven Wrapper

## Prerequisites

- Java 17 or later
- PostgreSQL
- Maven is optional because the project includes Maven Wrapper scripts

## Database Configuration

The application is configured in `src/main/resources/application.properties`:

```properties
server.port=8001
spring.datasource.url=jdbc:postgresql://localhost:5432/mth
spring.datasource.username=postgres
spring.datasource.password=root
spring.jpa.hibernate.ddl-auto=update
```

Create a PostgreSQL database named `mth`, or update the datasource values to match your local database.

## Run the Application

On Windows:

```powershell
.\mvnw.cmd spring-boot:run
```

On macOS/Linux:

```bash
./mvnw spring-boot:run
```

The service starts on:

```text
http://localhost:8001
```

## API Endpoints

### Signup

```http
POST /user/signup
Content-Type: application/json
```

Request body:

```json
{
  "fullname": "Demo User",
  "phone": "9876543210",
  "email": "demo@example.com",
  "password": "password123"
}
```

Successful response:

```json
{
  "code": 200,
  "message": "User account has been created."
}
```

### Signin

```http
POST /user/signin
Content-Type: application/json
```

Request body:

```json
{
  "username": "demo@example.com",
  "password": "password123"
}
```

Successful response:

```json
{
  "code": 200,
  "jwt": "<token>"
}
```

## Swagger UI

After starting the application, open:

```text
http://localhost:8001/swagger-ui/index.html
```

## Run Tests

On Windows:

```powershell
.\mvnw.cmd test
```

On macOS/Linux:

```bash
./mvnw test
```
