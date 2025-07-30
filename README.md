# .NET E-Commerce Platform with Microservice Architecture

This project is a fully-featured e-commerce backend built with **.NET 8**, demonstrating a distributed, scalable, and resilient system using a **Microservice Architecture**. Each core business capability (Catalog, Basket, Order, etc.) is developed and deployed as an independent service.

## Project Purpose and Problem Solved

The primary goal is to showcase a real-world application of microservices in an e-commerce context. This architecture solves the limitations of traditional monolithic applications by allowing services to be developed, deployed, and scaled independently. It enhances maintainability and allows for the use of the best technology for each specific job.

## Core Features

- **Microservice Architecture:** The application is broken down into independent services, each handling a specific business domain (`Catalog`, `Basket`, `Discount`, `Order`, `Photo`).
- **API Gateway (Ocelot):** A single entry point for all client requests, routing them to the appropriate downstream service. This simplifies the client-side code and provides a centralized place for cross-cutting concerns.
- **Asynchronous Communication (RabbitMQ & MassTransit):** Services communicate asynchronously using a message bus, ensuring loose coupling and improving fault tolerance.
- **Centralized Identity & Authentication (IdentityServer):** A dedicated service for user authentication and authorization, providing secure access to the entire platform using JWT.
- **Containerization (Docker):** The entire application, including all services and databases, is fully containerized using Docker and can be orchestrated with a single `docker-compose` command.
- **Polyglot Persistence:** Each service uses the database technology best suited to its needs (**PostgreSQL**, **MongoDB**, and **Redis**).
- **CQRS Pattern:** The ordering service utilizes the Command Query Responsibility Segregation pattern for a clear separation of read and write operations.

## Tech Stack & Architecture

- **Backend:** .NET 8, C#
- **Architecture:** Microservices, CQRS Design Pattern, Onion Architecture
- **API Gateway:** Ocelot
- **Asynchronous Messaging:** RabbitMQ with MassTransit
- **Containerization:** Docker, Docker-Compose
- **Authentication:** IdentityServer4, JWT
- **Databases:**
    - **PostgreSQL:** Main database for Catalog and Discount services.
    - **MongoDB:** Used by the Photo Stock service for storing image metadata.
    - **Redis:** Used by the Basket service for high-performance caching.
- **ORM/Data Access:** Dapper, Entity Framework Core
- **Frontend:** ASP.NET Core MVC (for Web UI)

## Architectural Diagram

This diagram provides a high-level overview of the microservice architecture and the flow of communication between services.


## How to Run the Project

The entire application is designed to be run easily using Docker.

1.  **Prerequisites:**
    -   Docker Desktop must be installed and running.
2.  **Clone the repository:**
    ```bash
    git clone [https://github.com/SefaBudak/Microservice-Ecommerce-Platform.git](https://github.com/SefaBudak/Microservice-Ecommerce-Platform.git)
    ```
3.  **Navigate to the root directory:**
    ```bash
    cd Microservice-Ecommerce-Platform
    ```
4.  **Run Docker Compose:**
    ```bash
    docker-compose up -d
    ```
    This command will build and start all the services, databases, and the RabbitMQ message broker in detached mode. It might take a few minutes the first time.

5.  **Accessing the Services:**
    -   **API Gateway:** `http://localhost:5000`
    -   **Web UI:** `http://localhost:5001`
    -   **IdentityServer:** `http://localhost:5005`

## Acknowledgment & Personal Note

The foundational concepts and core structure of this project were inspired by the "Asp.Net Core MultiShop Mikroservis E-Ticaret Kursu" on Udemy. Building on the excellent patterns and technologies taught in the course, I have refactored, updated, and customized several components to deepen my understanding and demonstrate my ability to work with complex, distributed systems.
