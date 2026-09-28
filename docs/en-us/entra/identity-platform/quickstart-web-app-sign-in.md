<!-- Source: https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-web-app-sign-in -->
<!-- Sitemap-Last-Modified: 2025-04-08 -->

# Quickstart: Sign in users in a sample web app

**Applies to**: ![Green circle with a white check mark symbol that indicates the following content applies to workforce tenants.](https://learn.microsoft.com/en-us/entra/external-id/media/common/applies-to-yes.png) Workforce tenants ![Green circle with a white check mark symbol that indicates the following content applies to external tenants.](https://learn.microsoft.com/en-us/entra/external-id/media/common/applies-to-yes.png) External tenants \([learn more](https://learn.microsoft.com/en-us/entra/external-id/tenant-configurations)\)

In this quickstart, you use a sample web app to show you how to sign in users and call Microsoft Graph API in your workforce tenant. The sample app uses the [Microsoft Authentication Library](https://learn.microsoft.com/en-us/entra/identity-platform/msal-overview) to handle authentication.

Before you begin, use the **Choose a tenant type** selector at the top of this page to select tenant type. Microsoft Entra ID provides two tenant configurations, [workforce](https://learn.microsoft.com/en-us/entra/external-id/tenant-configurations#workforce-tenants) and [external](https://learn.microsoft.com/en-us/entra/external-id/tenant-configurations#external-tenants). A workforce tenant configuration is for your employees, internal apps, and other organizational resources. An external tenant is for your customer-facing apps.

## Prerequisites

- An Azure account with an active subscription. If you don't already have one, [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- This Azure account must have permissions to manage applications. Any of the following Microsoft Entra roles include the required permissions:

  - Application Administrator
  - Application Developer

- A workforce tenant. You can use your Default Directory or [set up a new tenant](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-create-new-tenant).
- [Visual Studio Code](https://code.visualstudio.com/download) or another code editor.

- [Node](#tabpanel_1_node-workforce)
- [ASP.NET Core](#tabpanel_1_asp-dot-net-core-workforce)
- [Python Flask](#tabpanel_1_python-flask-workforce)

- Register a new app in the [Microsoft Entra admin center](https://entra.microsoft.com), configured for *Accounts in this organizational directory only*. Refer to [Register an application](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-register-app) for more details. Record the following values from the application **Overview** page for later use:

  - Application \(client\) ID
  - Directory \(tenant\) ID

- Add the following redirect URIs using the **Web** platform configuration. Refer to [How to add a redirect URI in your application](https://learn.microsoft.com/en-us/entra/identity-platform/how-to-add-redirect-uri) for more details.

  - **Redirect URI**: `http://localhost:3000/auth/redirect`
  - **Front-channel logout URL**: `https://localhost:5001/signout-callback-oidc`

- Add a client secret to your app registration. **Do not** use client secrets in production apps. Use certificates or federated credentials instead. For more information, see [add credentials to your application](https://learn.microsoft.com/en-us/entra/identity-platform/how-to-add-credentials?tabs=client-secret).
- [Node.js](https://nodejs.org/en/download/package-manager)

- Register a new app in the [Microsoft Entra admin center](https://entra.microsoft.com), configured for *Accounts in this organizational directory only*. Refer to [Register an application](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-register-app) for more details. Record the following values from the application **Overview** page for later use:

  - Application \(client\) ID
  - Directory \(tenant\) ID

- Add the following redirect URIs using the **Web** platform configuration. Refer to [How to add a redirect URI in your application](https://learn.microsoft.com/en-us/entra/identity-platform/how-to-add-redirect-uri) for more details.

  - **Redirect URI**: `https://localhost:5001/signin-oidc`
  - **Front-channel logout URL**: `https://localhost:5001/signout-callback-oidc`

- Add a self-signed certificate to your app registration. **Do not** use self-signed certificates in production apps. Use a certificate from a trusted certificate authority or federated credentials instead. For more information, see [add credentials to your application](https://learn.microsoft.com/en-us/entra/identity-platform/how-to-add-credentials?tabs=certificate). Create the certificate using the following command:

  ```console
  dotnet dev-certs https -ep ./certificate.crt --trust
  ```

- A minimum requirement of [.NET 8.0 SDK](https://dotnet.microsoft.com/download/dotnet)

- Register a new app in the [Microsoft Entra admin center](https://entra.microsoft.com), configured for *Accounts in this organizational directory only*. Refer to [Register an application](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-register-app) for more details. Record the following values from the application **Overview** page for later use:

  - Application \(client\) ID
  - Directory \(tenant\) ID

- Add the following redirect URIs using the **Web** platform configuration. Refer to [How to add a redirect URI in your application](https://learn.microsoft.com/en-us/entra/identity-platform/how-to-add-redirect-uri) for more details.

  - **Redirect URI**: `http://localhost:5000/getAToken`

- [Python 3 +](https://www.python.org/downloads/)
- Add a client secret to your app registration. **Do not** use client secrets in production apps. Use certificates or federated credentials instead. For more information, see [add credentials to your application](https://learn.microsoft.com/en-us/entra/identity-platform/how-to-add-credentials?tabs=client-secret).

## Clone or download sample web application

To obtain the sample application, you can either clone it from GitHub or download it as a *.zip* file.

- [Node](#tabpanel_2_node-workforce)
- [ASP.NET Core](#tabpanel_2_asp-dot-net-core-workforce)
- [Python Flask](#tabpanel_2_python-flask-workforce)

- [Download the .zip file](https://github.com/Azure-Samples/ms-identity-node/archive/refs/heads/main.zip), then extract it to a file path where the length of the name is fewer than 260 characters or clone the repository:
- To clone the sample, open a command prompt and navigate to where you wish to create the project, and enter the following command:

  ```console
  git clone https://github.com/Azure-Samples/ms-identity-node.git
  ```

- [Download the .zip file](https://github.com/Azure-Samples/ms-identity-docs-code-dotnet/archive/refs/heads/main.zip), then extract it to a file path where the length of the name is fewer than 260 characters or clone the repository:
- To clone the sample, open a command prompt and navigate to where you wish to create the project, and enter the following command:

  ```console
  git clone https://github.com/Azure-Samples/ms-identity-docs-code-dotnet.git
  ```

- [Download the Python code sample](https://github.com/Azure-Samples/ms-identity-docs-code-python/archive/refs/heads/main.zip) then extract it to a file path where the length of the name is fewer than 260 characters or clone the repository:
- To clone the sample, open a command prompt and navigate to where you wish to create the project, and enter the following command:

```Console
git clone https://github.com/Azure-Samples/ms-identity-docs-code-python/
```

## Configure the sample web app

For you to sign in users with the sample app, you need to update it with your app and tenant details:

- [Node](#tabpanel_3_node-workforce)
- [ASP.NET Core](#tabpanel_3_asp-dot-net-core-workforce)
- [Python Flask](#tabpanel_3_python-flask-workforce)

In the *ms-identity-node* folder, open the *App/.env* file, then replace the following placeholders:

| Variable | Description | Example\(s\) |
| --- | --- | --- |
| `Enter_the_Cloud_Instance_Id_Here` | The Azure cloud instance in which your application is registered | `https://login.microsoftonline.com/` \(include the trailing forward-slash\) |
| `Enter_the_Tenant_Info_here` | Tenant ID or Primary domain | `contoso.microsoft.com` or `aaaabbbb-0000-cccc-1111-dddd2222eeee` |
| `Enter_the_Application_Id_Here` | Client ID of the application you registered | `00001111-aaaa-2222-bbbb-3333cccc4444` |
| `Enter_the_Client_Secret_Here` | Client secret of the application you registered | `A1b-C2d_E3f.H4i,J5k?L6m!N7o-P8q_R9s.T0u` |
| `Enter_the_Graph_Endpoint_Here` | The Microsoft Graph API cloud instance that your app calls | `https://graph.microsoft.com/` \(include the trailing forward-slash\) |
| `Enter_the_Express_Session_Secret_Here` | A random string of characters used to sign the Express session cookie | `A1b-C2d_E3f.H4...` |

After you make changes, your file should look similar to the following snippet:

```env
CLOUD_INSTANCE=https://login.microsoftonline.com/
TENANT_ID=aaaabbbb-0000-cccc-1111-dddd2222eeee
CLIENT_ID=00001111-aaaa-2222-bbbb-3333cccc4444
CLIENT_SECRET=A1b-C2d_E3f.H4...

REDIRECT_URI=http://localhost:3000/auth/redirect
POST_LOGOUT_REDIRECT_URI=http://localhost:3000

GRAPH_API_ENDPOINT=https://graph.microsoft.com/

EXPRESS_SESSION_SECRET=6DP6v09eLiW7f1E65B8k
```

1. In your IDE, open the project folder, *ms-identity-docs-code-dotnet\\web-app-aspnet*, containing the sample.
2. Open *appsettings.json* and replace the file contents with the following snippet;

   ```json
   {
   "AzureAd": {
     "Instance": "https://login.microsoftonline.com/",
     "TenantId": "Enter the tenant ID obtained from the Microsoft Entra admin center",
     "ClientId": "Enter the client ID obtained from the Microsoft Entra admin center",
     "ClientCredentials": [
       {
         "SourceType": "StoreWithThumbprint",
         "CertificateStorePath": "CurrentUser/My",
         "CertificateThumbprint": "Enter the certificate thumbprint obtained the Microsoft Entra admin center"
       }   
     ],
     "CallbackPath": "/signin-oidc"
   },
     "DownstreamApis": {
       "MicrosoftGraph" :{
         "BaseUrl": "https://graph.microsoft.com/v1.0/",
         "RelativePath": "me",
         "Scopes": [ 
           "user.read" 
         ]
      }
     },
     "Logging": {
       "LogLevel": {
         "Default": "Information",
         "Microsoft.AspNetCore": "Warning"
       }
     },
     "AllowedHosts": "*"
   }
   ```


   - `TenantId` - The identifier of the tenant where the application is registered. Replace the text in quotes with the `Directory (tenant) ID` that was recorded earlier from the overview page of the registered application.
   - `ClientId` - The identifier of the application, also referred to as the client. Replace the text in quotes with the `Application (client) ID` value that was recorded earlier from the overview page of the registered application.
   - `ClientCertificates` - A self-signed certificate is used for authentication in the application. Replace the text of the `CertificateThumbprint` with the thumbprint of the certificate that was previously recorded.

1. Open the application you downloaded in an IDE and navigate to root folder of the sample app.

   ```console
   cd flask-web-app
   ```

2. Create an *.env* file in the root folder of the project using *.env.sample.entra-id* as a guide.

   ```python
   # The following variables are required for the app to run.
   CLIENT_ID=<Enter_your_client_id>
   CLIENT_SECRET=<Enter_your_client_secret>
   AUTHORITY=<Enter_your_authority_url>
   ```


   - Set the value of `CLIENT_ID` to the **Application \(client\) ID** for the registered application, available on the overview page.
   - Set the value of `CLIENT_SECRET` to the client secret you created in the **Certificates & Secrets** for the registered application.
   - Set the value of `AUTHORITY` to a `https://login.microsoftonline.com/<TENANT_GUID>`. The **Directory \(tenant\) ID** is available on the app registration overview page.


   The environment variables are referenced in *app\_config.py*, and are kept in a separate *.env* file to keep them out of source control. The provided *.gitignore* file prevents the *.env* file from being checked in.

## Run and test sample web app

You've configured your sample app. You can proceed to run and test it.

- [Node](#tabpanel_4_node-workforce)
- [ASP.NET Core](#tabpanel_4_asp-dot-net-core-workforce)
- [Python Flask](#tabpanel_4_python-flask-workforce)

1. To start the server, run the following commands from within the project directory:

   ```console
   cd App
   npm install
   npm start
   ```

2. Go to `http://localhost:3000/`.
3. Select **Sign in** to start the sign-in process.

The first time you sign in, you're prompted to provide your consent to allow the application to sign you in and access your profile. After you're signed in successfully, you'll be redirected back to the application home page.

### How the app works

The sample hosts a web server on localhost, port 3000. When a web browser accesses this address, the app renders the home page. Once the user selects **Sign in**, the app redirects the browser to Microsoft Entra sign-in screen, via the URL generated by the MSAL Node library. After user consents, the browser redirects the user back to the application home page, along with an ID and access token.

1. In your project directory, use the terminal to enter the following commands:

   ```console
   cd ms-identity-docs-code-dotnet/web-app-aspnet
   dotnet run
   ```

2. Copy the `https` URL that appears in the terminal, for example, `https://localhost:5001`, and paste it into a browser. We recommend using a private or incognito browser session.
3. Follow the steps and enter the necessary details to sign in with your Microsoft account. You're requested to provide an email address so a one time passcode can be sent to you. Enter the code when prompted.
4. The application requests permission to maintain access to data you have given it access to, and to sign you in and read your profile. Select **Accept**. The following screenshot appears. It indicates that you're signed-in to the application and are viewing your profile details from the Microsoft Graph API.

   [![Screenshot depicting the results of the API call.](https://learn.microsoft.com/en-us/entra/identity-platform/media/common-web-app/dotnet-core/display-api-call-results-dotnet-core.png)](https://learn.microsoft.com/en-us/entra/identity-platform/media/common-web-app/dotnet-core/display-api-call-results-dotnet-core.png#lightbox)

### Sign out from the application

1. Find the **Sign out** link in the top right corner of the page, and select it.
2. You're prompted to pick an account to sign out from. Select the account you used to sign in.
3. A message appears indicating that you signed out. You can now close the browser window.

1. Create a virtual environment for the app:

   - For **Windows**, run the following commands:


   ```console
   py -m venv .venv
   .venv\scripts\activate
   ```


   - For **macOS/Linux**, run the following commands:


   ```console
   python3 -m venv .venv
   source .venv/bin/activate
   ```

2. Install the requirements using `pip`:

   ```Console
   pip install -r requirements.txt
   ```

3. Run the app from the command line. Ensure your app is running on the same port as the redirect URI you configured earlier.

   ```Console
   flask run --debug --host=localhost --port=5000
   ```

4. Copy the https URL that appears in the terminal, for example, https://localhost:5000, and paste it into a browser. We recommend using a private or incognito browser session.
5. Follow the steps and enter the necessary details to sign in with your Microsoft account. You're requested to provide an email address and password to sign in.
6. The application requests permission to maintain access to data you allow access to, and to sign you in and then read your profile, as shown in the screenshot. Select **Accept**.

   ![Diagram that shows the sample app requesting for consent to access the required permissions.](https://learn.microsoft.com/en-us/entra/identity-platform/media/python-webapp/consent.png)
7. The following screenshot appears, which indicates that you've successfully signed in to the application.

![Diagram that shows how the sample app has successfully signed in a user.](https://learn.microsoft.com/en-us/entra/identity-platform/media/python-webapp/signed-in-user.png)

### How the app works

The following diagram demonstrates how the sample app works:

![Diagram that shows how the sample app generated by this quickstart works.](https://learn.microsoft.com/en-us/entra/identity-platform/media/quickstart-v2-python-webapp/topology.png)

1. The application uses the [`identity` package](https://github.com/azure-samples/ms-identity-python) to obtain an access token from the Microsoft identity platform. This package is built on top of the Microsoft Authentication Library \(MSAL\) for Python to simplify authentication and authorization in web apps.
2. The access token you obtain in the previous step is used as a bearer token to authenticate the user when calling the Microsoft Graph API.

## Related content

- [Node](#tabpanel_5_node-workforce)
- [ASP.NET Core](#tabpanel_5_asp-dot-net-core-workforce)
- [Python Flask](#tabpanel_5_python-flask-workforce)

- Learn how to build a Node.js web app that signs in users and calls Microsoft Graph API in [Tutorial: Sign in users and acquire a token for Microsoft Graph in a Node.js & Express web app](https://learn.microsoft.com/en-us/entra/identity-platform/tutorial-v2-nodejs-webapp-msal).

- Learn by building this ASP.NET web app with the series [Tutorial: Register an application with the Microsoft identity platform](https://learn.microsoft.com/en-us/entra/identity-platform/tutorial-web-app-dotnet-sign-in-users).
- [Quickstart: Protect an ASP.NET Core web API with the Microsoft identity platform](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-web-api-aspnet-core-protect-api).
- [Quickstart: Deploy an ASP.NET web app to Azure App Service](https://learn.microsoft.com/en-us/azure/app-service/quickstart-dotnetcore?tabs=net70&pivots=development-environment-vs)

- Learn how to build a Python web app that signs in users and calls a protected web API in [Tutorial: Web app that signs in users](https://learn.microsoft.com/en-us/entra/identity-platform/tutorial-web-app-python-register-app).

In this quickstart, you use a sample web app to show you how to sign in users in your external tenant. The sample app uses the [Microsoft Authentication Library](https://learn.microsoft.com/en-us/entra/identity-platform/msal-overview) to handle authentication.

Before you begin, use the **Choose a tenant type** selector at the top of this page to select tenant type. Microsoft Entra ID provides two tenant configurations, [workforce](https://learn.microsoft.com/en-us/entra/external-id/tenant-configurations#workforce-tenants) and [external](https://learn.microsoft.com/en-us/entra/external-id/tenant-configurations#external-tenants). A workforce tenant configuration is for your employees, internal apps, and other organizational resources. An external tenant is for your customer-facing apps.

## Prerequisites

- An Azure account with an active subscription. If you don't already have one, [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- This Azure account must have permissions to manage applications. Any of the following Microsoft Entra roles include the required permissions:

  - Application Administrator
  - Application Developer

- An external tenant. To create one, choose from the following methods:

  - Use the [Microsoft Entra External ID extension](https://aka.ms/ciamvscode/samples/marketplace) to set up an external tenant directly in Visual Studio Code. *\(Recommended\)*
  - [Create a new external tenant](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-create-external-tenant-portal) in the Microsoft Entra admin center.

- A user flow. For more information, refer to [create self-service sign-up user flows for apps in external tenants](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-user-flow-sign-up-sign-in-customers). This user flow can be used for multiple applications.
- [Visual Studio Code](https://code.visualstudio.com/download) or another code editor.

- [Node](#tabpanel_6_node-external)
- [ASP.NET Core](#tabpanel_6_asp-dot-net-core-external)
- [Python Django](#tabpanel_6_python-django-external)
- [Python Flask](#tabpanel_6_python-flask-external)

- Register a new app in the [Microsoft Entra admin center](https://entra.microsoft.com), configured for *Accounts in this organizational directory only*. Refer to [Register an application](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-register-app) for more details. Record the following values from the application **Overview** page for later use:

  - Application \(client\) ID
  - Directory \(tenant\) ID

- Add the following redirect URIs using the **Web** platform configuration. Refer to [How to add a redirect URI in your application](https://learn.microsoft.com/en-us/entra/identity-platform/how-to-add-redirect-uri) for more details.

  - **Redirect URI**: `http://localhost:3000/auth/redirect`
  - **Front-channel logout URL**: `https://localhost:5001/signout-callback-oidc`

- Add a client secret to your app registration. **Do not** use client secrets in production apps. Use certificates or federated credentials instead. For more information, see [add credentials to your application](https://learn.microsoft.com/en-us/entra/identity-platform/how-to-add-credentials?tabs=client-secret).
- [Add your application to the user flow](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-user-flow-add-application)
- [Node.js](https://nodejs.org/en/download/package-manager)

- Register a new app in the [Microsoft Entra admin center](https://entra.microsoft.com), configured for *Accounts in this organizational directory only*. Refer to [Register an application](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-register-app) for more details. Record the following values from the application **Overview** page for later use:

  - Application \(client\) ID
  - Directory \(tenant\) ID

- Add the following redirect URIs using the **Web** platform configuration. Refer to [How to add a redirect URI in your application](https://learn.microsoft.com/en-us/entra/identity-platform/how-to-add-redirect-uri) for more details.

  - **Redirect URI**: `https://localhost:5001/signin-oidc`
  - **Front-channel logout URL**: `https://localhost:5001/signout-callback-oidc`

- Add a client secret to your app registration. **Do not** use client secrets in production apps. Use certificates or federated credentials instead. For more information, see [add credentials to your application](https://learn.microsoft.com/en-us/entra/identity-platform/how-to-add-credentials?tabs=client-secret).
- [Add your application to the user flow](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-user-flow-add-application)
- A minimum version of [.NET 8.0 SDK](https://dotnet.microsoft.com/download/dotnet).

- Register a new app in the [Microsoft Entra admin center](https://entra.microsoft.com), configured for *Accounts in this organizational directory only*. Refer to [Register an application](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-register-app) for more details. Record the following values from the application **Overview** page for later use:

  - Application \(client\) ID
  - Directory \(tenant\) ID

- Add the following redirect URIs using the **Web** platform configuration. Refer to [How to add a redirect URI in your application](https://learn.microsoft.com/en-us/entra/identity-platform/how-to-add-redirect-uri) for more details.

  - **Redirect URI**: `http://localhost:5000/getAToken`

- [Add your application to the user flow](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-user-flow-add-application)
- [Python 3 +](https://www.python.org/downloads/)
- Add a client secret to your app registration. **Do not** use client secrets in production apps. Use certificates or federated credentials instead. For more information, see [add credentials to your application](https://learn.microsoft.com/en-us/entra/identity-platform/how-to-add-credentials?tabs=client-secret).

- Register a new app in the [Microsoft Entra admin center](https://entra.microsoft.com), configured for *Accounts in this organizational directory only*. Refer to [Register an application](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-register-app) for more details. Record the following values from the application **Overview** page for later use:

  - Application \(client\) ID
  - Directory \(tenant\) ID

- Add the following redirect URIs using the **Web** platform configuration. Refer to [How to add a redirect URI in your application](https://learn.microsoft.com/en-us/entra/identity-platform/how-to-add-redirect-uri) for more details.

  - **Redirect URI**: `http://localhost:5000/getAToken`

- [Add your application to the user flow](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-user-flow-add-application)
- [Python 3 +](https://www.python.org/downloads/)
- Add a client secret to your app registration. **Do not** use client secrets in production apps. Use certificates or federated credentials instead. For more information, see [add credentials to your application](https://learn.microsoft.com/en-us/entra/identity-platform/how-to-add-credentials?tabs=client-secret).

## Clone or download sample web application

- [Node](#tabpanel_7_node-external)
- [ASP.NET Core](#tabpanel_7_asp-dot-net-core-external)
- [Python Django](#tabpanel_7_python-django-external)
- [Python Flask](#tabpanel_7_python-flask-external)

To obtain the sample application, you can either clone it from GitHub or download it as a .zip file:

- To clone the sample, open a command prompt and navigate to where you wish to create the project, and enter the following command:

  ```console
  git clone https://github.com/Azure-Samples/ms-identity-ciam-javascript-tutorial.git
  ```

- Alternatively, [download the sample .zip file](https://github.com/Azure-Samples/ms-identity-ciam-javascript-tutorial/archive/refs/heads/main.zip), then extract it to a file path where the length of the name is fewer than 260 characters.

### Install project dependencies

1. Open a console window, and change to the directory that contains the Node.js sample app:

   ```console
   cd 1-Authentication\5-sign-in-express\App
   ```

2. Run the following commands to install app dependencies:

   ```console
   npm install
   ```

To obtain the sample application, you can either clone it from GitHub or download it as a .zip file.

- To clone the sample, open a command prompt and navigate to where you wish to create the project, and enter the following command:

  ```console
  git clone https://github.com/Azure-Samples/ms-identity-ciam-dotnet-tutorial.git
  ```

- [Download the .zip file](https://github.com/Azure-Samples/ms-identity-ciam-dotnet-tutorial/archive/refs/heads/main.zip). Extract it to a file path where the length of the name is fewer than 260 characters.

To obtain the sample application, you can either clone it from GitHub or download it as a .zip file.

- To clone the sample, open a command prompt and navigate to where you wish to create the project, and enter the following command:

  ```console
  git clone https://github.com/Azure-Samples/ms-identity-docs-code-python.git
  ```

- [Download the .zip file](https://github.com/Azure-Samples/ms-identity-docs-code-python/archive/refs/heads/main.zip). Extract it to a file path where the length of the name is fewer than 260 characters.

### Install project dependencies

1. Open a console window, and change to the directory that contains the Flask sample web app:

   ```console
   cd django-web-app
   ```

2. Set up virtual environment:

   - For **Windows**, run the following commands:


   ```console
   py -m venv .venv
   .venv\scripts\activate
   ```


   - For **macOS/Linux**, run the following commands:


   ```console
   python3 -m venv .venv
   source .venv/bin/activate
   ```

3. To install app dependencies, run the following commands:

   ```console
   python3 -m pip install -r requirements.txt
   ```

To obtain the sample application, you can either clone it from GitHub or download it as a .zip file.

- To clone the sample, open a command prompt and navigate to where you wish to create the project, and enter the following command:

  ```console
  git clone https://github.com/Azure-Samples/ms-identity-docs-code-python.git
  ```

- [Download the .zip file](https://github.com/Azure-Samples/ms-identity-docs-code-python/archive/refs/heads/main.zip). Extract it to a file path where the length of the name is fewer than 260 characters.

### Install project dependencies

1. Open a console window, and change to the directory that contains the Flask sample web app:

   ```console
   cd flask-web-app
   ```

2. Set up virtual environment:

   - For **Windows**, run the following commands:


   ```console
   py -m venv .venv
   .venv\scripts\activate
   ```


   - For **macOS/Linux**, run the following commands:


   ```console
   python3 -m venv .venv
   source .venv/bin/activate
   ```

3. To install app dependencies, run the following commands:

   ```console
   python3 -m pip install -r requirements.txt
   ```

## Configure the sample web app

For you to sign in users with the sample app, you need to update it with your app and tenant details:

- [Node](#tabpanel_8_node-external)
- [ASP.NET Core](#tabpanel_8_asp-dot-net-core-external)
- [Python Django](#tabpanel_8_python-django-external)
- [Python Flask](#tabpanel_8_python-flask-external)

1. In your code editor, open *App\\authConfig.js* file.
2. Find the placeholder:

   - `Enter_the_Application_Id_Here` and replace it with the Application \(client\) ID of the app you registered earlier.
   - `Enter_the_Tenant_Subdomain_Here` and replace it with the Directory \(tenant\) subdomain. For example, if your tenant primary domain is `contoso.onmicrosoft.com`, use `contoso`. If you don't have your tenant name, learn how to [read your tenant details](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-create-customer-tenant-portal#get-the-customer-tenant-details).
   - `Enter_the_Client_Secret_Here` and replace it with the app secret value you copied earlier.

1. Navigate to the root directory that contains the ASP.NET Core sample app:

   ```console
   cd 1-Authentication\1-sign-in-aspnet-core-mvc
   ```

2. Open the *appsettings.json* file.
3. In **Authority**, find `Enter_the_Tenant_Subdomain_Here` and replace it with the subdomain of your tenant. For example, if your tenant primary domain is *caseyjensen@onmicrosoft.com*, the value you should enter is *casyjensen*.
4. Find the `Enter_the_Application_Id_Here` value and replace it with the application ID \(clientId\) of the app you registered in the Microsoft Entra admin center.
5. Replace `Enter_the_Client_Secret_Here` with the client secret value you set up.

1. Open your project files on Visual Studio Code or the editor you're using.
2. Create an *.env* file in the root folder of the project using *.env.sample.external-id* file as a guide.
3. In your *.env* file, provide the following environment variables:

   1. `CLIENT_ID` which is the Application \(client\) ID of the app you registered earlier.
   2. `CLIENT_SECRET` which is the app secret value you copied earlier.
   3. `AUTHORITY` which is the URL that identifies a token authority. It should be of the format *https://{subdomain}.ciamlogin.com/{subdomain}.onmicrosoft.com*. Replace *subdomain* with the Directory \(tenant\) subdomain. For example, if your tenant primary domain is `contoso.onmicrosoft.com`, use `contoso`. If you don't have your tenant subdomain, learn how to [read your tenant details](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-create-external-tenant-portal#get-the-external-tenant-details).
   4. `REDIRECT_URI` which should be similar to the redirect URI you registered earlier should match your configuration.

1. Open your project files on Visual Studio Code or the editor you're using.
2. Create an *.env* file in the root folder of the project using *.env.sample.external-id* file as a guide.
3. In your *.env* file, provide the following environment variables:

   - `CLIENT_ID` which is the Application \(client\) ID of the app you registered earlier.
   - `CLIENT_SECRET` which is the app secret value you copied earlier.
   - `AUTHORITY` which is the URL that identifies a token authority. It should be of the format *https://{subdomain}.ciamlogin.com/{subdomain}.onmicrosoft.com*. Replace *subdomain* with the Directory \(tenant\) subdomain. For example, if your tenant primary domain is `contoso.onmicrosoft.com`, use `contoso`. If you don't have your tenant subdomain, learn how to [read your tenant details](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-create-customer-tenant-portal#get-the-customer-tenant-details).

4. Confirm that the redirect URI is well configured. The redirect URI you registered earlier should match your configuration. This sample by default sets the redirect URI path to `/getAToken`. This configuration is in the *app\_config.py* file as *REDIRECT\_PATH*.

## Run and test sample web app

- [Node](#tabpanel_9_node-external)
- [ASP.NET Core](#tabpanel_9_asp-dot-net-core-external)
- [Python Django](#tabpanel_9_python-django-external)
- [Python Flask](#tabpanel_9_python-flask-external)

You can now test the sample Node.js web app. You need to start the Node.js server and access it through your browser at `http://localhost:3000`.

1. In your terminal, run the following command:

   ```console
   npm start 
   ```

2. Open your browser, then go to `http://localhost:3000`. You should see the page similar to the following screenshot:

   ![Screenshot of sign in into a node web app.](https://learn.microsoft.com/en-us/entra/identity-platform/media/how-to-web-app-node-sample-sign-in/web-app-node-sign-in.png)
3. After the page completes loading, select **Sign in** when prompted.
4. On the sign-in page, type your **Email address**, select **Next**, type your **Password**, then select **Sign in**. If you don't have an account, select **No account? Create one** link, which starts the sign-up flow.
5. If you choose the sign-up option, after filling in your email, one-time passcode, new password, and more account details, you complete the whole sign-up flow. You see a page similar to the following screenshot. You see a similar page if you choose the sign-in option.

   ![Screenshot of view ID token claims.](https://learn.microsoft.com/en-us/entra/identity-platform/media/how-to-web-app-node-sample-sign-in/web-app-node-view-claims.png)
6. Select **Sign out** to sign the user out of the web app or select **View ID token claims** to view ID token claims returned by Microsoft Entra.

### How it works

When users select the **Sign in** link, the app initiates an authentication request and redirects users to Microsoft Entra External ID. On the sign-in or sign-up page that appears, once a user successfully signs in, or creates an account, Microsoft Entra External ID returns an ID token to the app. The app validates the ID token, reads the claims, and returns a secure page to the users.

When the users select the **Sign out** link, the app clears its session, then redirect the user to Microsoft Entra External ID sign-out endpoint to notify it that the user has signed out.

If you want to build an app similar to the sample you've run, complete the steps in [Sign in users in your own Node.js web application](https://learn.microsoft.com/en-us/entra/external-id/customers/tutorial-web-app-node-sign-in-prepare-tenant) article.

1. From your shell or command line, execute the following commands:

   ```console
   dotnet run
   ```

2. Open your web browser and navigate to `https://localhost:7274`.
3. Sign-in with an account registered to the external tenant.
4. Once signed in the display name is shown next to the **Sign out** button as shown in the following screenshot.

   ![Screenshot of sign in into a ASP.NET Core web app.](https://learn.microsoft.com/en-us/entra/identity-platform/media/tutorial-web-app-dotnet-sign-in-sign-in-out/display-aspnet-welcome.png)
5. To sign out from the application, select the **Sign out** button.

Run the app to see the sign-in experience at play.

1. In your terminal, run the following command:

   ```console
   python manage.py runserver localhost:5000                                             
   ```


   You can use a port number of your choice.

2. Open your browser, then go to `http://localhost:5000`. You should see a page similar to the following screenshot:

   ![Screenshot of Django web app sample sign-in page.](https://learn.microsoft.com/en-us/entra/identity-platform/media/sample-web-app-django-sign-in/django-sign-in-page.png)
3. After the page completes loading, select **Sign In** link. You're prompted to sign in.
4. On the sign-in page, type your **Email address**, select **Next**, type your **Password**, then select **Sign in**. If you don't have an account, select **No account? Create one** link, which starts the sign-up flow.
5. If you choose the sign-up option, you go through the sign-up flow. Fill in your email, one-time passcode, new password, and more account details to complete the whole sign-up flow.
6. After you sign in or sign up, you're redirected back to the web app. You see a page that looks similar to the following screenshot:

   ![Screenshot of flask web app sample after successful authentication.](https://learn.microsoft.com/en-us/entra/identity-platform/media/sample-web-app-django-sign-in/django-authenticated-page.png)
7. Select **Logout** to sign the user out of the web app or select **Call a downstream API** to make a call to a Microsoft Graph endpoint.

### How it works

When users select the **Sign in** link, the app initiates an authentication request and redirects users to Microsoft Entra External ID. A user then signs in or signs up page on the page that appears. After providing in the required credentials and consenting to required scopes, Microsoft Entra External ID redirects the user back to the web app with an authorization code. The web app then uses this authorization code to acquire a token from Microsoft Entra External ID.

When the users select the **Logout** link, the app clears its session, the redirect the user to Microsoft Entra External ID sign-out endpoint to notify it that the user has signed out. The user is then redirected back to the web app.

Run the app to see the sign-in experience at play.

1. In your terminal, run the following command:

   ```console
   python3 -m flask run --debug --host=localhost --port=3000
   ```


   You can use the port of your choice. This should be similar to the port of the redirect URI you registered earlier.

2. Open your browser, then go to `http://localhost:3000`. You should see the page similar to the following screenshot:

   ![Screenshot of flask web app sample sign-in page.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/includes/run-app/flask-sign-in-page.png)
3. After the page completes loading, select **Sign In** link. You're prompted to sign in.
4. On the sign-in page, type your **Email address**, select **Next**, type your **Password**, then select **Sign in**. If you don't have an account, select **No account? Create one** link, which starts the sign-up flow.
5. If you choose the sign-up option, you'll go through the sign-uo flow. Fill in your email, one-time passcode, new password and more account details to complete the whole sign-up flow.
6. After you sign in or sign up, you're redirected back to the web app. You'll see a page that looks similar to the following screenshot:

   ![Screenshot of flask web app sample after successful authentication.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/includes/run-app/flask-authenticated-page.png)
7. Select **Logout** to sign the user out of the web app or select **Call a downstream API** to make a call to a Microsoft Graph endpoint.

### How it works

When users select the **Sign in** link, the app initiates an authentication request and redirects users to Microsoft Entra External ID. A user then signs in or signs up page on the page that appears. After providing in the required credentials and consenting to required scopes, Microsoft Entra External ID redirects the user back to the web app with an authorization code. The web app then uses this authorization code to acquire a token from Microsoft Entra External ID.

When the users select the **Logout** link, the app clears its session, the redirect the user to Microsoft Entra External ID sign-out endpoint to notify it that the user has signed out. The user is then redirected back to the web app.

## Related content

- [Node](#tabpanel_10_node-external)
- [ASP.NET Core](#tabpanel_10_asp-dot-net-core-external)
- [Python Django](#tabpanel_10_python-django-external)
- [Python Flask](#tabpanel_10_python-flask-external)

- [Sign in users in your Node.js web application](https://learn.microsoft.com/en-us/entra/external-id/customers/tutorial-web-app-node-sign-in-prepare-tenant)
- [Quickstart - Sign in users and call a web API in sample Node.js web app](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-web-app-node-sign-in-call-api)
- [Quickstart - Edit profile in a sample Node.js web app](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-web-app-node-sign-in-edit-profile)

- [Use our multi-part tutorial series to build this ASP.NET web application from scratch](https://learn.microsoft.com/en-us/entra/external-id/customers/tutorial-web-app-dotnet-sign-in-prepare-app)
- [Enable password reset](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-enable-password-reset-customers)
- [Customize the default branding](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-customize-branding-customers)

- [Sign in users using a sample Flask web application](https://learn.microsoft.com/en-us/entra/external-id/customers/sample-web-app-python-flask-sign-in)
- [Enable password reset](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-enable-password-reset-customers)
- [Customize the default branding](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-customize-branding-customers)

- [Enable password reset](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-enable-password-reset-customers)
- [Customize the default branding](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-customize-branding-customers)
