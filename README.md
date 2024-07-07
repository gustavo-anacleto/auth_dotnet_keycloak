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

Use ***admin*** for username and password fields

![image](https://github.com/gustaVASSIO/auth_dotnet_keycloak/assets/104386638/392eb6de-fbea-4fc6-ba16-8415174640d8)

After enter, create a new **realm**
![image](https://github.com/gustaVASSIO/auth_dotnet_keycloak/assets/104386638/3681b0f4-4788-45db-92a5-7d03ab0b08ac)

Now you'll need create a client
In second step mark the option **Client authentication**
![image](https://github.com/gustaVASSIO/auth_dotnet_keycloak/assets/104386638/3e148596-1884-4ae1-9df1-debba89d978a)

After this, go to **Client Scopes** tab, create a client scope
![image](https://github.com/gustaVASSIO/auth_dotnet_keycloak/assets/104386638/3e68f738-f050-4c49-b304-86091b69c3fc)

When you create a clien scope the tab **Mappers** will be visible
Access this tab, click in **Configure new mapper**
![image](https://github.com/gustaVASSIO/auth_dotnet_keycloak/assets/104386638/597bc57f-9514-4af6-983b-ae9848d7e798)

Select the option **Audience**
In the field **Included Client Audience** you will pass the client that you created
![image](https://github.com/gustaVASSIO/auth_dotnet_keycloak/assets/104386638/58e9bf2e-022b-4edd-93d0-ffbab5661c46)

Now you will access the client tab
Enter in your client
Go to **Client Scopes**
Add the scope that you just created
Remember to mark the option **Default** when you add this scope
![image](https://github.com/gustaVASSIO/auth_dotnet_keycloak/assets/104386638/99ceb894-06b8-4356-bc29-dc1e13497ab6)
![image](https://github.com/gustaVASSIO/auth_dotnet_keycloak/assets/104386638/014123e0-4ef3-4feb-ba41-539b46b6e927)


To finish create a user to make login in the keycloak
![image](https://github.com/gustaVASSIO/auth_dotnet_keycloak/assets/104386638/88b2f8ab-b869-44e3-ac02-3196e7395691)

Go to tab credential and set a password, you'll use it afterwards
![image](https://github.com/gustaVASSIO/auth_dotnet_keycloak/assets/104386638/e93bd2dc-f665-4278-9378-74598b1dec51)

---

# .NET project

First create your a webApi project with .net 6

To create use the command **dotnet new webapi -n NAME_YOUR_PROJECT**

Enter in your project with the command **cd NAME_YOUR_PROJECT**

Install the dependencies
**dotnet add package Microsoft.AspNetCore.Authentication.JwtBearer**

**dotnet add package IdentityModel**

**dotnet add package IdentityModel.AspNetCore.OAuth2Introspection**

In your appsettings.json paste the block bellow
```
  "Keycloak": {
    "Authority": "http://localhost:8080/realms/YOUR_REALM_NAME",
    "ClientId": "YOUR_CLIENT_NAME"
  }
```

Now just copy the configuration of Program.cs of this repository
Don't forget to 


