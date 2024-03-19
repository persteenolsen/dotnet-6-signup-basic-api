# dotnet-6-signup-basic-api

.NET 6.0 - User Registration and Login Tutorial with Example API

# Functionality of the Web App

- JWT authentication
- CRUD Account management routes with role based access control

# Tech used for creating the Web App

- A .NET 6 Web API
- An Angular 14 Web Client for the Frontend
- Entity Framework
- SQLite as a local DB
- SQLite for Production
- A traditional Webhotel for hosting
- VS Code


# Updated EF Core tool to the latest version - Version 8.03
dotnet tool update --global dotnet-ef

# Development
# Create the Initial Migration for SQLite DB - should work for any DB
set ASPNETCORE_ENVIRONMENT=Development

Make sure that the connection String points to the SQLite ( locally ) in the "appsettings.Development" 

"WebApiDatabase": "Data Source=LocalDatabase.db"

dotnet ef migrations add InitialCreate --context SqliteDataContext --output-dir Migrations/SqliteMigrations 


# Production - SQLite as well
# Create a self contained build for production at the remote server / traditionel web hotel
dotnet publish webapi.csproj --configuration Release --runtime win-x86 --self-contained

# Upload the build to remote server ( without SQLite DB )

# At my remote servers the web.config needs to be without the folowing 
hostingModel="inprocess"

# Create the remote SQLite DB at the remote server
https://remote-host.com/users

