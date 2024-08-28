# MAS FloraFire ClientPortal Developer Guide

## Overview

The FloraFire ClientPortal architecture follows a layered design pattern, typical in enterprise applications that use .NET and adhere to Domain-Driven Design (DDD) principles. This architecture is designed to separate concerns, promoting modularity, scalability, and maintainability of the application. Each component in the architecture has a specific role and responsibility, facilitating easier management and development, especially beneficial in team environments.

Read more at [Project Overview](Project_Overview.md).

## Tools and Frameworks

### The ABP Framework

To get a more deep understanding of the project, you can read the [ABP Framework documentation](https://docs.abp.io/en/abp/latest/Tutorials/Todo/Overall).

## Coding Conversions
Follow these guidelines for coding conversions.
1.  [ABP framework coding conversion](https://abp.io/docs/latest/framework/architecture/best-practices?_redirected=B8ABF606AA1BDF5C629883DF1061649A)
2.  [Angular framework coding conversion](https://angular.dev/style-guide)

## PR Review Guideline
follow the [PR Guideline](PR_Review_Guide.md) to create and Reveiw Pull Requests.



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

### 6. Installing the Client-Side Packages
Navigate to root directory of the project and run the command to install the client-side packages.
command:
```
abp install-libs
```

## Frontend Installation 

### 1. Setup Angular Project

- **Navigate to Angular Folder**: Change directory to the angular folder within the project.
- **Install Dependencies**:
  ```bash
  npm install
  ```
- **Alternate way**:
if npm install is showing error then try this command to install 
all dependencies. Before you run this command make sure yarn is installed globally. 
  ```bash
  yarn install
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






