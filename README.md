# umbraco-13-starter-one

A Simple Web Application by Umbrco CMS 13

# Create a global json

dotnet new globaljson --sdk-version 8.0.203 --force

# Functionality of the Web App

- Simple web Application with an Umbraco Backend

# Tech used for creating the Web App

- .NET 8
- Umbraco CMS 13
- SQLite DB for both Dev + Prod
- A traditional Webhotel for hosting
- VS Code

# Development

dotnet run

# Production

Create a self contained build for production at the remote server / traditionel web hotel

dotnet publish myproject.csproj --configuration Release --runtime win-x86 --self-contained

Upload the build to remote server

At my remote servers the web.config needs to be without the folowing:

hostingModel="inprocess"

Upload the SQLite DB to the remote server

Start to use Umbraco :-)

