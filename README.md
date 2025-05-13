# umbraco-13-starter-one

Last Updated:

13-05-2025

A Simple Web Application by Umbraco CMS 13 serving as a Basic Starter

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

# Settings for Production

Go to appsettings.json and make sure that your Umbraco Site have at least the settings:

- Hosting:Debug:false

- UseHTTPS:true

- WebRouting:UmbracoApplicationUrl:your.domain.com

Note: Check your settings in appsettings.Development.json for

- Hosting:Debug

# Sync your remote Prod changes to your local Dev

Yor will need to commit the changes from the sqlite-wal file to sqlite.db at the Web Hotel before downloading to local Dev:

- Open web.config and save - This is a work around for stop / start the app pool

- Download the sqlite.db

- Download Views, media files or whatever files that you worked with at Prod

Happy use Umbraco :-)

