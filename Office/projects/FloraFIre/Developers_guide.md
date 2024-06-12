# FloraFire Project

## Introduction

**FloraFire Software** , Powered by MAS Direct Network, provides the shop owner with all the necessary tools to manage and streamline the business. 

Note, **This project has two parts, this repository holds the ecom portal which handles  client subscription , the another repository handles the client portal.**


## Getting Started

### Tools We Use

- **Visual Studio 2022**: Our primary development environment.
- **NopCommerce**: An open-source e-commerce solution.
- **SQL Server**: For database management.
- **Git**: For version control.
- **Azure Web Service**: For project hosting.
### Tools Needed to Run This Project

- **Visual Studio 2022**: Download and install from [Visual Studio](https://visualstudio.microsoft.com/).
- **SQL Server**: Download and install from [Microsoft SQL Server](https://www.microsoft.com/en-us/sql-server/sql-server-downloads).
- **.NET 8.0 SDK**: Ensure it's installed from [.NET SDK](https://dotnet.microsoft.com/download/dotnet/8.0).
- **Git**: Download and install from [Git](https://git-scm.com/).

## Project Structure

The NopCommerce project is structured into several key areas:

- **Core**: Contains the core libraries and functionalities of the application.
- **Data**: Manages the database context, entities, and data access logic.
- **Services**: Provides the business logic and service layer between the data layer and the web layer.
- **Web**: Handles the presentation layer, including controllers, views, and front-end assets.

## Database Configuration

First, the  database backup needs to be restored from a backup file of existing database.
After that to configure the database, update the `appsettings.json` file in the Web project with your SQL Server connection string:

```json
{
  "ConnectionStrings": {
    "DefaultConnection": "Data Source=your_server_name\\your_SQL_instance_name;Initial Catalog=your_database_name;Integrated Security=True;Persist Security Info=False;Trust Server Certificate=True""
  }
}
```
## Deployment

For deployment, we follow these steps:

1. **Build**: Ensure the project builds successfully in Visual Studio 2022.
2. **Publish**: Use Visual Studio's Publish feature to create a deployment package.
3. **Configure Server**: The published version of Visual Studio will be deployed to Azure web server.
4. **Database Update**: Ensure the database is updated with any new migrations.

## Coding Style

We adhere to the following coding styles and best practices:

- **C# Coding Conventions**: Follow the [Microsoft C# Coding Conventions](https://docs.microsoft.com/en-us/dotnet/csharp/fundamentals/coding-style/coding-conventions).
- **NopCommerce Guidelines**: Nop Commerce has its own coding conventions. Visit this [NopCommerce Coding Convensions](https://docs.nopcommerce.com/en/developer/tutorials/coding-standards.html).
## Gitflow

We have our own Gitflow policy that implements the best practices for versioning. Visit our gitflow process documentation -

[Flora Git Flow Process](gitFlow.md).
