# umbraco-13-starter-one

Last Updated:

17-05-2025

A Simple Web Application by Umbraco CMS 13 serving as a Basic Starter

# Create a global json

dotnet new globaljson --sdk-version 8.0.203 --force

# Installation

- dotnet new install Umbraco.Templates::13.*

- dotnet new umbraco --name MyProject

- cd MyProject

- dotnet run

- Open https : // localhost:44316 in your Browser and follow the instructions

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

Login to your Umbraco and perform a Health Check under Settings

Open your web.config file at your Web hotel and be aware of the Excessive Headers that:

- Could be revealing information in its headers that gives away unnecessary details about the technology used to build and host

- Add code to web.config which contains:

- httpProtocol - customHeaders - remove - name=X-Powered-By

- security - requestFiltering - RemoveServerHeader=true

Take a look in file Program.cs and the code about security by the HTTP Headers:

- Click-Jacking Protection

- Content / MIME Sniffing Protection

- Cookie hijacking and protocol downgrade attacks Protection

Go to appsettings.json and make sure that your Umbraco Site have the settings:

- Hosting:Debug:false

- UseHTTPS:true

- WebRouting:UmbracoApplicationUrl:your.domain.com

Note: Check your settings in appsettings.Development.json for

- Hosting:Debug

# Performance tuning / Eliminate Render-Blocking => Slow first Page load

- Use Google Pege Speed

- I optimized CSS and JS in the Master View 

- In web.config I added Rewrite Rule to force HTTP request to HTTPS 

# Sync your remote Prod changes to your local Dev

Yor will need to commit the changes from the sqlite-wal file to sqlite.db at the Web Hotel before downloading to local Dev:

- Open web.config and save - This is a work around for stop / start the app pool

- Download the sqlite.db

- Download Views, media files or whatever files that you worked with at Prod

Happy use Umbraco :-)

