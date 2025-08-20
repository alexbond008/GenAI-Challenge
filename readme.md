# Compact Disc REST Service

## Introduction

This application is a Java-based RESTful web service built using the Spring Boot framework. It provides API endpoints to manage a catalog of Compact Discs (CDs). It uses MySQL for data persistence and integrates Swagger for API documentation.

## Project Structure

The project is organized into the following main directories:

-   `src/`: Contains the Java source code for the application, following standard Maven layout.
    -   `src/main/java`: Application source files, including entities, repositories, services, and the REST controller.
    -   `src/main/resources`: Application configuration files, like `application.properties`, and static web content.
        - `static/`: Contains HTML, CSS, and JavaScript files for simple front-end interaction with the API.
    -   `src/test/java`: Unit and integration tests (currently not implemented).
-   `sql/`: Contains SQL scripts for database setup, such as creating the schema and tables (`createTables.sql`).
-   `rest/`: Contains files for testing the REST API endpoints (`.rest` files).
-   `pom.xml`: The Maven Project Object Model file. It defines project dependencies, plugins, and build configurations.

## Prerequisites

To build and run this project, you will need:
-   Java Development Kit (JDK), version 11 or later.
-   Apache Maven.
-   A running instance of MySQL.

## Setup and Installation

1.  **Database Setup**:
    -   Connect to your MySQL server.
    -   Run the SQL script located in `sql/createTables.sql` to create the `conygre` database, the `compact_discs` and `tracks` tables, and populate them with initial data.

2.  **Application Configuration**:
    -   Open the `src/main/resources/application.properties` file.
    -   Update the database connection properties (`spring.datasource.url`, `spring.datasource.username`, `spring.datasource.password`) to match your MySQL environment.

## Building and Running the Application

1.  **Build the project**:
    Open a terminal in the project root and run the following Maven command to compile the code and package it into a JAR file.
    ```sh
    mvn clean install
    ```

2.  **Run the application**:
    You can run the application using the Spring Boot Maven plugin:
    ```sh
    mvn spring-boot:run
    ```
    Alternatively, you can run the packaged JAR file directly:
    ```sh
    java -jar target/CompactDiscRestDataBoot-0.0.1-SNAPSHOT.jar
    ```
    Once started, the application will be accessible at `http://localhost:8080`.

## API Endpoints

The application exposes several REST endpoints for managing compact discs. You can find sample requests in the `rest/` directory.

-   `GET /api/compactdiscs`: Retrieves a list of all compact discs.
-   `GET /api/compactdiscs/{id}`: Retrieves a single compact disc by its ID.
-   `POST /api/compactdiscs`: Creates a new compact disc. The request body should contain the CD's JSON representation.
-   `DELETE /api/compactdiscs/{id}`: Deletes a compact disc by its ID.
-   `DELETE /api/compactdiscs`: Deletes a compact disc by passing its JSON representation in the request body.

## API Documentation (Swagger)

This project uses Swagger to provide interactive API documentation. Once the application is running, you can access the Swagger UI at:

-   **Swagger UI**: `http://localhost:8080/swagger-ui.html`

This interface allows you to view all available endpoints and test them directly from your browser.