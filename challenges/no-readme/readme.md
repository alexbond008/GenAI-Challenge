# Compact Disc Catalog API

## Introduction

The Compact Disc Catalog API is a RESTful application built with **Spring Boot** for managing a catalog of compact discs (CDs) and their associated tracks. It provides CRUD (Create, Read, Update, Delete) operations for CDs and tracks, allowing users to interact with the catalog programmatically via API endpoints or through a frontend interface.

The application integrates with a **MySQL database**, includes **Swagger API documentation**, and supports deployment in both local and Dockerized environments.

---

## Features

- **REST API**: Exposes endpoints for managing CDs and their tracks.
- **Database Integration**: Uses MySQL to persist CD and track data.
- **Frontend Pages**: Includes static HTML pages for interacting with the API.
- **Swagger Documentation**: Provides interactive API documentation.
- **Logging**: Configured with Log4j2 for detailed application logs.
- **Docker Support**: Easily deployable in a containerized environment.

---

## Project Structure

The project follows a standard **Spring Boot** structure:

```
src/
├── main/
│   ├── java/
│   │   └── com/conygre/spring/boot/
│   │       ├── controllers/       # REST controllers for API endpoints
│   │       ├── entities/          # JPA entities for database tables
│   │       ├── repositories/      # JPA repositories for database access
│   │       ├── services/          # Service layer for business logic
│   │       └── SwaggerConfig.java # Swagger configuration
│   ├── resources/
│       ├── static/                # Frontend HTML files
│       ├── application.properties # Application configuration
│       ├── application-docker.properties # Docker-specific configuration
│       └── log4j2.properties      # Logging configuration
└── test/                          # Unit and integration tests
```

---

## Dependencies

The project uses the following key dependencies:

- **Spring Boot**: Framework for building the application.
- **Spring Data JPA**: For database interaction.
- **MySQL Driver**: For connecting to the MySQL database.
- **Swagger**: For API documentation.
- **Log4j2**: For logging.
- **Docker**: For containerized deployment.

---

## Available Endpoints

### Compact Disc Endpoints

- **GET /api/compactdiscs**  
  Retrieve all CDs in the catalog.

- **GET /api/compactdiscs/{id}**  
  Retrieve a specific CD by its ID.

- **POST /api/compactdiscs**  
  Add a new CD to the catalog.  
  **Request Body** (JSON):  
  ```json
  {
    "title": "Album Title",
    "artist": "Artist Name",
    "price": 19.99,
    "tracks": [
      { "title": "Track 1", "duration": 180 },
      { "title": "Track 2", "duration": 200 }
    ]
  }
  ```

- **DELETE /api/compactdiscs/{id}**  
  Delete a CD by its ID.

- **DELETE /api/compactdiscs**  
  Delete a CD by passing its details in the request body.

---

## Data Structure

### Compact Disc Entity
- **Fields**:
  - `id` (Primary Key)
  - `title`
  - `artist`
  - `price`
  - `tracks` (List of associated tracks)

### Track Entity
- **Fields**:
  - `id` (Primary Key)
  - `title`
  - `duration`
  - `cd_id` (Foreign Key referencing `compact_discs.id`)

---

## Frontend Pages

The project includes static HTML pages for interacting with the API:

- **`index.html`**: Displays a table of CDs fetched from the API.
- **`listcds.html`**: Uses DataTables to display and manage CDs.
- **`constructorfunctionajax.html`**: Demonstrates adding and fetching CDs using AJAX.
- **`promisefetch.html`**: Uses the Fetch API to retrieve CD data.
- **`temp.html`**: Contains a form for sending JSON data (incomplete implementation).

---

## Deployment

### Local Deployment

1. Clone the repository:
   ```bash
   git clone <repository-url>
   cd <repository-folder>
   ```

2. Configure the database connection in `application.properties`:
   ```properties
   spring.datasource.url=jdbc:mysql://localhost:3306/your_database
   spring.datasource.username=your_username
   spring.datasource.password=your_password
   ```

3. Run the application:
   ```bash
   ./mvnw spring-boot:run
   ```

### Docker Deployment

1. Build the Docker image:
   ```bash
   docker build -t compact-disc-api .
   ```

2. Run the container:
   ```bash
   docker run -p 8080:8080 compact-disc-api
   ```

---

## API Documentation

Swagger is available at:  
`http://localhost:8080/swagger-ui.html`

---

## Logging

Logs are configured using Log4j2. The configuration file is located at:  
`src/main/resources/log4j2.properties`

---

## Database Schema

The application uses the following database schema:

### Tables

1. **`compact_discs`**
   - `id` (Primary Key)
   - `title`
   - `artist`
   - `price`

2. **`tracks`**
   - `id` (Primary Key)
   - `title`
   - `duration`
   - `cd_id` (Foreign Key referencing `compact_discs.id`)

---

## Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository.
2. Create a new branch for your feature or bugfix.
3. Submit a pull request with a detailed description of your changes.

---

## License

This project is licensed under the MIT License. See the `LICENSE` file for details.

---

## Contact

For any questions or issues, please contact the project maintainer at:  
`maintainer@example.com`
