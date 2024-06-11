# FloraFire Project

## Introduction

**FloraFire** is an innovative e-commerce platform designed to provide a seamless shopping experience for all your floral needs. Our purpose is to offer a wide variety of flowers and floral arrangements to customers through an easy-to-use online storefront, bringing the beauty of nature directly to their doorstep.

## Getting Started

### Tools We Use

- **Visual Studio 2022**: Our primary development environment.
- **NopCommerce**: An open-source e-commerce solution.
- **SQL Server**: For database management.
- **Git**: For version control.

### Tools Needed to Run This Project

- **Visual Studio 2022**: Download and install from [Visual Studio](https://visualstudio.microsoft.com/).
- **SQL Server**: Download and install from [Microsoft SQL Server](https://www.microsoft.com/en-us/sql-server/sql-server-downloads).
- **.NET 6.0 SDK**: Ensure it's installed from [.NET SDK](https://dotnet.microsoft.com/download/dotnet/6.0).
- **Git**: Download and install from [Git](https://git-scm.com/).

## Project Structure

The NopCommerce project is structured into several key areas:

- **Core**: Contains the core libraries and functionalities of the application.
- **Data**: Manages the database context, entities, and data access logic.
- **Services**: Provides the business logic and service layer between the data layer and the web layer.
- **Web**: Handles the presentation layer, including controllers, views, and front-end assets.

## Database Configuration

To configure the database, update the `appsettings.json` file in the Web project with your SQL Server connection string:

```json
{
  "ConnectionStrings": {
    "DefaultConnection": "Server=your_server_name;Database=your_database_name;User Id=your_username;Password=your_password;"
  }
}
```
## Deployment

For deployment, we follow these steps:

1. **Build**: Ensure the project builds successfully in Visual Studio 2022.
2. **Publish**: Use Visual Studio's Publish feature to create a deployment package.
3. **Configure Server**: Set up the server environment (e.g., IIS) with the necessary configurations.
4. **Deploy Package**: Transfer the deployment package to the server and extract it.
5. **Database Update**: Ensure the database is updated with any new migrations.

## Coding Style

We adhere to the following coding styles and best practices:

- **C# Coding Conventions**: Follow the [Microsoft C# Coding Conventions](https://docs.microsoft.com/en-us/dotnet/csharp/fundamentals/coding-style/coding-conventions).
- **NopCommerce Guidelines**: Maintain consistency with NopCommerce's existing codebase and architecture.

## Gitflow

[Flora Git Flow Process](gitFlow.md).



## Contributors

This project is built by a dedicated team of developers passionate about e-commerce and floral arrangements:

- **Mahbubur Rahman**: Project Manager
- **Afia Apu**: Team Lead