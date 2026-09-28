<!-- Source: https://learn.microsoft.com/en-us/graph/toolkit/get-started/add-aad-app-registration -->
<!-- Sitemap-Last-Modified: 2025-09-04 -->

# Create a Microsoft Entra app to use with the Microsoft Graph Toolkit

Caution

The Microsoft Graph Toolkit is deprecated. The retirement period begins September 1, 2025, with full retirement planned for August 28, 2026. Developers should migrate to using the Microsoft Graph SDKs or other supported Microsoft Graph tools for building web experiences. For more information, see the [deprecation announcement](https://devblogs.microsoft.com/microsoft365dev/microsoft-graph-toolkit-retirement/).

Microsoft Graph, the API that you use to connect to Microsoft 365, is secured with OAuth 2.0. In order to connect your app to Microsoft 365, you need to create an app in Microsoft Entra ID and grant this app a set of permissions to access specific resources on behalf of the person using your app. This article describes how to register and configure a web application to use with Microsoft Graph Toolkit.

## Add new application registration in Microsoft Entra ID

To create an application in Microsoft Entra ID, you need to add a new application registration, and then configure an app name and URL location.

To create the app in Microsoft Entra ID:

1. Go to the [Microsoft Entra admin center](https://entra.microsoft.com).
2. Expand the **Identity** menu > expand **Applications** > select **App registrations** > select the **New registration** button.
3. Enter the name for your app; for example, `My M365 app`.
4. For the type of [supported account types](https://learn.microsoft.com/en-us/azure/active-directory/develop/single-and-multi-tenant-apps#who-can-sign-in-to-your-app), select **Accounts in any organizational directory \(Any Microsoft Entra ID tenant - Multitenant\)**.
5. For the **Redirect URI** field, select **Single Page Application \(SPA\)**, and in the URL field, enter your redirect URL \(and/or `http://localhost` if testing locally\).
6. Confirm changes by selecting the **Register** button.

## Enable authorization code flow \(for MsalProvider and TeamsProvider\)

In most cases, you use Microsoft Graph Toolkit in client-side applications that consist only of client-side code. We recommend that you use the [authorization code flow with PKCE](https://learn.microsoft.com/en-us/entra/identity-platform/scenario-spa-app-registration#redirect-uri-msaljs-20-with-auth-code-flow) that provides a more secure way to authenticate users.

1. In the Microsoft Entra admin center, open your newly created app registration.
2. From the menu, choose **Authentication**.
3. In the **Platform configurations** section, select **Add a platform**, then choose **Single-page application**.
4. In the **Redirect URIs** section, enter your redirect URL, or `http://localhost` if you run the code locally, or both.
5. In the **Implicit grant and hybrid flows** section, ensure that **ID tokens** and **Access tokens** aren't selected.
6. Select **Configure** to add the redirect URL and finalize the setup.

## Next steps

- [Build a web application](https://learn.microsoft.com/en-us/graph/toolkit/get-started/build-a-web-app) \(vanilla JavaScript\)
- [Build a Microsoft Teams tab](https://learn.microsoft.com/en-us/graph/toolkit/get-started/build-a-microsoft-teams-tab)
- [Use the Toolkit with React](https://learn.microsoft.com/en-us/graph/toolkit/get-started/use-toolkit-with-react)
- [Use the Toolkit with Angular](https://learn.microsoft.com/en-us/graph/toolkit/get-started/use-toolkit-with-angular)
