<!-- Source: https://learn.microsoft.com/en-us/entra/identity-platform/multi-service-web-app-overview -->
<!-- Sitemap-Last-Modified: 2024-02-07 -->

# Sign in users in App Service and access storage and Microsoft Graph

This tutorial describes a common application scenario: an internal employee dashboard web application. Your web app is hosted in Azure App Service and needs to connect to Microsoft Graph and Azure Storage in order to get data to visualize in the dashboard. In some cases, the web app needs to get data that only the signed-in user can access. In other cases, the web app needs to access data under the identity of the app itself, and not the signed-in user. Access to the web application needs to be restricted to users in your organization.

The goal of this tutorial *isn't* to show how to build the dashboard itself or visualize data. Rather, the tutorial focuses on the identity-related aspects of the described scenario. Learn how to:

- [Configure authentication for a web app](https://learn.microsoft.com/en-us/entra/identity-platform/multi-service-web-app-authentication-app-service) and limit access to users in your organization​. See A in the diagram.
- [Securely access Azure Storage](https://learn.microsoft.com/en-us/entra/identity-platform/multi-service-web-app-access-storage) from the web application using managed identities​. See B in the diagram.
- Access data in Microsoft Graph from the web application \(See C in the diagram\):

  - [as the signed-in user​](https://learn.microsoft.com/en-us/entra/identity-platform/multi-service-web-app-access-microsoft-graph-as-user)
  - [as the web application](https://learn.microsoft.com/en-us/entra/identity-platform/multi-service-web-app-access-microsoft-graph-as-app) using managed identities​

- [Clean up the resources](https://learn.microsoft.com/en-us/entra/identity-platform/multi-service-web-app-clean-up-resources) you created for this tutorial.

![Diagram that shows application scenarios in Microsoft identity platform.](https://learn.microsoft.com/en-us/entra/identity-platform/media/multi-service-web-app-overview/web-app.svg)

## Next steps

[Configure authentication for a web app](https://learn.microsoft.com/en-us/entra/identity-platform/multi-service-web-app-authentication-app-service)
