# How to connect keycloak with .NET application

## Prerequirements 
- Docker Desktop
- .NET 6
- Visual Studio (or other IDE of your preference)
## Versions
- Keycloak 20.0.2
- .NET 6

## Configuration
First it necessary to configure the keycloak 
To configure Keycloak run this command *docker run -p 8080:8080 -e KEYCLOAK_ADMIN=admin -e KEYCLOAK_ADMIN_PASSWORD=admin quay.io/keycloak/keycloak:20.0.2 start-dev*

dotnet add package Microsoft.AspNetCore.Authentication.JwtBearer
dotnet add package IdentityModel
dotnet add package IdentityModel.AspNetCore.OAuth2Introspection

