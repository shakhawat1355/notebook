# MAS.FloraFire.ClientPortal Architecture Documentation

## Overview

The FloraFire ClientPortal architecture follows a layered design pattern, typical in enterprise applications that use .NET and adhere to Domain-Driven Design (DDD) principles. This architecture is designed to separate concerns, promoting modularity, scalability, and maintainability of the application. Each component in the architecture has a specific role and responsibility, facilitating easier management and development, especially beneficial in team environments.

## Project Descriptions

### Application Layer

- **MAS.FloraFire.ClientPortal.Application**
  - This project contains the application logic and business rules. It coordinates tasks and acts as a bridge between the presentation layer and the domain layer.

- **MAS.FloraFire.ClientPortalApplication.Contracts**
  - Defines interfaces and data transfer objects (DTOs) for the application. It abstracts and encapsulates all application logic that can be exposed to outer layers or clients.

### Infrastructure Layer

- **MAS.FloraFire.ClientPortal.DbMigrator**
  - A utility project for database migrations, managing changes to the database schema and data to keep the database updated in sync with the application's evolution.

- **MAS.FloraFire.ClientPortal.EntityFrameworkCore**
  - Implements the persistence layer using Entity Framework Core, including the database context, configurations, and repositories for data access and mapping between domain models and database tables.

### Domain Layer

- **MAS.FloraFire.ClientPortal.Domain**
  - Contains the domain model (entities, value objects, domain events), representing business and behavior objects in the system. This is the core layer with no dependencies on other application layers.

- **MAS.FloraFire.ClientPortal.Domain.Shared**
  - Holds shared elements common across multiple domain models, such as interfaces, enums, or constants used throughout the domain layer.

### API Layer

- **MAS.FloraFire.ClientPortal.HttpApi**
  - Contains controllers and API models that handle HTTP requests and responses, serving as the application's interface with the external world.

- **MAS.FloraFire.ClientPortal.HttpApi.Client**
  - Provides a client library that external clients or services can use to interact with the application's HTTP API.

- **MAS.FloraFire.ClientPortal.HttpApi.Host**
  - Hosts the web API, configuring and running the web application as the entry point for the HTTP server.

### Test Projects

- **MAS.FloraFire.ClientPortal.Application.Tests**
  - Unit tests for the Application layer, verifying the business logic and application tasks.

- **MAS.FloraFire.ClientPortal.Domain.Tests**
  - Tests for the Domain layer, ensuring the integrity and behavior of the domain model.

- **MAS.FloraFire.ClientPortal.EntityFrameworkCore.Tests**
  - Tests for the EntityFrameworkCore layer, focusing on data access logic and database mappings.

- **MAS.FloraFire.ClientPortal.HttpApi.Client.ConsoleTestApp**
  - A console application for testing or demonstrating the use of the HTTP API client library.

- **MAS.FloraFire.ClientPortal.TestBase**
  - Provides common testing utilities or setups used across multiple test projects.


## The ABP Framework

To get a more deep understanding of the project, you can read the [ABP Framework documentation](https://docs.abp.io/en/abp/latest/Tutorials/Todo/Overall).


## Frontend Overviews

Angular 17 has been used as a frontend framework in MAS florafire clientend project. Follow this [Installation Guide](https://angular.dev/tools/cli/setup-local/)

