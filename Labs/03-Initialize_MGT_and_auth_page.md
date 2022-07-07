## Part 3 - Integrate authentication with MSAL2 Provider

- [Part 0 - Environment Setup](/Labs/00-Setup.md)
- [Part 1 - Create a new web app](/Labs/01-Create_new_app.md)
- [Part 2 - Register your application in Azure Active Directory](/Labs/02-Register_your_app_in_Azure_AD.md)
- [Part 3 - Integrate authentication with MSAL2 Provider](/Labs/03-Initialize_MGT_and_auth_page.md) ( **📍 You are here** )
- [Part 4 - Design your One Productivity Hub by using Microsoft Graph Toolkit components](/Labs/04-Design_your_app_using_MGT_components.md)
- [Part 5 - Test your web app](/Labs/05-Test_your_app.md)

Let's start building the app in Visual Studio Code.

### Enabling authentication with the Microsoft Graph Toolkit

To use the Microsoft Graph Toolkit via mgt-loader, add the following reference in `index.html` under the `<head></head>` section:

```HTML
  <script src="https://unpkg.com/@microsoft/mgt@2.5.1/dist/bundle/mgt-loader.js"></script>
```

### Initialize the MSAL2 provider

In `index.html`, add the MSAL2 provider in the `<head></head>` section as following:

```HTML
  <mgt-msal2-provider 
      client-id="<YOUR_CLIENT_ID>"
      scopes="User.Read,
      User.ReadBasic.All,
      Calendars.Read,
      Files.Read,
      Files.Read.All,
      Sites.Read.All,
      Tasks.Read,
      Tasks.ReadWrite,
      People.Read,
      User.ReadBasic.All">    
  </mgt-msal2-provider>
```

> **📌 NOTE 📌 :** The following scopes defined in the provider will be shown as a list of required permissions to request user's consent during the authentication process: `User.Read, User.ReadBasic.All, Calendars.Read, Files.Read, Files.Read.All, Sites.Read.All, Tasks.Read, Tasks.ReadWrite, People.Read, User.ReadBasic.All`.

Replace `<YOUR_CLIENT_ID>` with the client ID copied from the Azure AD application.

Final version of `index.html` will be as shown below:

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset='utf-8'>
  <meta http-equiv='X-UA-Compatible' content='IE=edge'>
  <title>One Productivity Hub</title>
  <meta name='viewport' content='width=device-width, initial-scale=1'>
  <link rel='stylesheet' type='text/css' media='screen' href='imainndex.css'>
  <script src='main.js'></script>

  <script src="https://unpkg.com/@microsoft/mgt@2.5.1/dist/bundle/mgt-loader.js"></script>

  <mgt-msal2-provider 
      client-id="<YOUR_CLIENT_ID>"
      scopes="User.Read,
      User.ReadBasic.All,
      Calendars.Read,
      Files.Read,
      Files.Read.All,
      Sites.Read.All,
      Tasks.Read,
      Tasks.ReadWrite,
      People.Read,
      User.ReadBasic.All">    
  </mgt-msal2-provider>

</head>
<body>
   
</body>
</html>

```

## References

- Microsoft Docs - [Build a web application with the Microsoft Graph Toolkit](https://docs.microsoft.com/en-us/graph/toolkit/get-started/build-a-web-app?tabs=html%2CHTML)

## Next Step

> ▶️ **[Part 4 - Design your One Productivity Hub by using Microsoft Graph Toolkit components](/Labs/04-Design_your_app_using_MGT_components.md)**
