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

To configure Keycloak run this command **docker run -p 8080:8080 -e KEYCLOAK_ADMIN=admin -e KEYCLOAK_ADMIN_PASSWORD=admin quay.io/keycloak/keycloak:20.0.2 start-dev**

Wait image until image configure

When it finish access **localhost:8080** in your brwoser

Use "admin" for username and password fields

![image](https://github.com/gustaVASSIO/auth_dotnet_keycloak/assets/104386638/392eb6de-fbea-4fc6-ba16-8415174640d8)


dotnet add package Microsoft.AspNetCore.Authentication.JwtBearer
dotnet add package IdentityModel
dotnet add package IdentityModel.AspNetCore.OAuth2Introspection

