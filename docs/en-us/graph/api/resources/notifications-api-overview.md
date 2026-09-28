<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/notifications-api-overview?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-03-12 -->

# Use the notifications REST API in Microsoft Graph \(deprecated\)

Important

The Microsoft Graph notifications API is deprecated and will stop returning data by the end of January 2022. For an alternative notification experience, see [Microsoft Azure Notification Hubs](https://learn.microsoft.com/en-us/azure/notification-hubs), and [see this blog post](https://devblogs.microsoft.com/microsoft365dev/retiring-microsoft-graph-notifications/) for more information.

You can use the notifications API in Microsoft Graph to send push notifications to a user. Post a notification to your target user, and the platform will deliver the notification to all device endpoints registered to that user. The high-level flow is as follows:

1. User signs in to your application, which creates a subscription with the Microsoft Graph notification service. A specific user notification subscription ID or UNSID will be returned to the calling application.
2. The application sends this UNSID to your application service.
3. When ready to send a notification, your application service [authenticates with the Microsoft identity platform](https://learn.microsoft.com/en-us/azure/active-directory/develop/v1-oauth2-client-creds-grant-flow) and posts a notification via the Microsoft Graph notification service, providing the auth token, target user's UNSID, and notification payload.
4. The Microsoft Graph notification service fans-out notifications to all endpoints of the user with an active subscription.

This type of user-centric notification is represented by the [notification](https://learn.microsoft.com/en-us/graph/api/resources/projectrome-notification?view=graph-rest-beta) resource and is stored within the Microsoft Graph notification service. It can then be accessed and managed by the client application via the [client-side SDK APIs](https://aka.ms/GNSDK). If you're new to the Microsoft Graph notification service, check out the [notification overview](https://learn.microsoft.com/en-us/graph/notifications-concept-overview) section to learn more.

## Next steps

- See the [notification resource](https://learn.microsoft.com/en-us/graph/api/resources/projectrome-notification?view=graph-rest-beta) and create notifications to engage with your users.
- Try the API in the [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer).
- Get started with client integration by following the steps in the [integration overview](https://learn.microsoft.com/en-us/graph/notifications-integration-e2e-overview) topic.
