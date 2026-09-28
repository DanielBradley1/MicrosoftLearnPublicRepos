<!-- Source: https://learn.microsoft.com/en-us/graph/notifications-integration-e2e-overview -->
<!-- Sitemap-Last-Modified: 2024-11-07 -->

# Integrate with Microsoft Graph notifications \(deprecated\)

Important

The Microsoft Graph notifications API is deprecated and stopped returning data in January 2022. For an alternative notification experience, see [Microsoft Azure Notification Hubs](https://learn.microsoft.com/en-us/azure/notification-hubs). For more information, see the blog post [Retiring Microsoft Graph notifications API \(beta\)](https://devblogs.microsoft.com/microsoft365dev/retiring-microsoft-graph-notifications/).

You can integrate your apps with Microsoft Graph notifications with a few simple steps, as shown in the following diagram.

![Image showing the steps to onboard notifications: registration, cross-device onboarding, server integration, and client integration](https://learn.microsoft.com/en-us/graph/images/notifications-integration-e2e-overview.png)

1. [Register](https://learn.microsoft.com/en-us/graph/notifications-integration-app-registration) your application in the Microsoft Entra admin center.
2. [Onboard](https://learn.microsoft.com/en-us/graph/notifications-integration-cross-device-experiences-onboarding) to Partner Center/Windows Dev Center for cross-platform application identity and push notification credentials for Windows, iOS, and Android.
3. [Set up your app server](https://learn.microsoft.com/en-us/graph/notifications-integrating-app-server) to send notifications via Microsoft Graph.
4. [Integrate](https://learn.microsoft.com/en-us/graph/notifications-integrating-with-windows) the new [notifications client SDK](https://aka.ms/GNSDK) into your Windows, iOS, Android, or web clients to receive and manage notifications.

Note

We recommend using the new and improved, lightweight [notification SDK](https://aka.ms/GNSDK) instead of the cross-device [Project Rome SDK](https://github.com/microsoft/project-rome).
