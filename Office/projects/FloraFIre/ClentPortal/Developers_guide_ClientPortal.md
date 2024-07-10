# MAS FloraFire ClientPortal Developer Guide

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

## Tools and Frameworks

### The ABP Framework

To get a more deep understanding of the project, you can read the [ABP Framework documentation](https://docs.abp.io/en/abp/latest/Tutorials/Todo/Overall).


## Backend Installation 

### 1. Clone the Project
Ensure you have the correct access rights to clone the project repository.

### 2. Copy Two `appsettings` Files (Optional)
There are two appsettings files in the project repository. One in **MAS.FloraFire.ClientPortal.DbMigrator** and another in **MAS.FloraFire.ClientPortal.HttpApi.Host**. The appsettings templates are given below-
DbMigrator Appsettings:
```
{
  "ConnectionStrings": {
    "Default": "Server={serverName};Database=ClientPortal;Trusted_Connection=True;TrustServerCertificate=True"
  },
  "OpenIddict": {
    "Applications": {
      "ClientPortal_App": {
        "ClientId": "ClientPortal_App",
        "RootUrl": "http://localhost:4200"
      },
      "ClientPortal_Swagger": {
        "ClientId": "ClientPortal_Swagger",
        "RootUrl": "https://localhost:44317"
      }
    }
  }
}
```
HttpApi Host Appsettings:
```
{
  "App": {
    "SelfUrl": "https://localhost:44317",
    "ClientUrl": "http://localhost:4200",
    "CorsOrigins": "https://*.ClientPortal.com,http://localhost:4200",
    "RedirectAllowedUrls": "http://localhost:4200"
  },
  "ConnectionStrings": {
    "Default": "Server=(LocalDb)\\MSSQLLocalDB;Database=ClientPortal;Trusted_Connection=True;TrustServerCertificate=True"
  },
  "AuthServer": {
    "Authority": "https://localhost:44317",
    "RequireHttpsMetadata": false,
    "SwaggerClientId": "ClientPortal_Swagger"
  },
  "StringEncryption": {
    "DefaultPassPhrase": "ekR7ONAxKQiqIUcu"
  }
}
```
### 3. Check Connection Strings
- **Edit Connection Strings**: Ensure the connection strings in `appsettings` for both `MAS.FloraFire.ClientPortal.HttpApi.Host` and `MAS.FloraFire.ClientPortal.DbMigrator` are correct.
  Replace `{serverName}` with your local server name:


### 4. Install ABP (ASP.NET Boilerplate)
- **Navigate to the Project**: Right-click on the `MAS.FloraFire.ClientPortal.HttpApi.Host` project and select "Open in Terminal".
- **Install ABP CLI**: In the terminal, run the following command:
```
  dotnet tool install -g Volo.Abp.Cli
```

### 5. Install .NET Tools and Run Migrations
- **Check EF Tools Installation**: In `MAS.FloraFire.ClientPortal.HttpApi.Host`, check if EF tools are installed, if not, run:
```
dotnet tool install --global dotnet-ef
```
- **Update Database**: Make sure the connection string is correct, then open the **EntityFrameworkCore** in terminal and run:
```
dotnet ef database update
```
- **Alternative way to run migrations**:
open DbMigrator project in terminal and run-
```
dotnet run
```
it should update your database. Now set **MAS.FloraFire.ClientPortal.HttpApi.Host** as startup project and run the project.


## Frontend Installation 

### 1. Setup Angular Project

- **Navigate to Angular Folder**: Change directory to the angular folder within the project.
- **Install Dependencies**:
  ```bash
  npm install
  ```

### 2. Generate Proxy

- Run the following command:
  ```bash
  abp generate-proxy -t ng
  ```

### 3. Start Angular Project

- **Ensure Backend is Running**: Before serving the Angular project, confirm the backend server is up.
- **Serve Angular Project**:
  ```bash
  ng serve
  ```
## Notes:
1. ............






