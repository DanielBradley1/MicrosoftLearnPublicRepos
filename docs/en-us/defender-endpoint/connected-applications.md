<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/connected-applications -->
<!-- Sitemap-Last-Modified: 2026-01-15 -->

# Connected applications in Microsoft Defender for Endpoint

Connected applications integrates with the Defender for Endpoint platform using APIs.

Applications use standard OAuth 2.0 protocol to authenticate and provide tokens for use with Microsoft Defender for Endpoint APIs. In addition, Microsoft Entra applications allow tenant admins to set explicit control over which APIs can be accessed using the corresponding app.

You'll need to follow [these steps](https://learn.microsoft.com/en-us/defender-endpoint/api/apis-intro) to use the APIs with the connected application.

From the left navigation menu, select **Partners & APIs** \(under **Endpoints**\) > **Connected applications**.

## View connected application details

The Connected applications page provides information about the Microsoft Entra applications connected to Microsoft Defender for Endpoint in your organization. You can review the usage of the connected applications: last seen, number of requests in the past 24 hours, and request trends in the last 30 days.

[![The connected applications](https://learn.microsoft.com/en-us/defender-endpoint/media/connected-apps.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/connected-apps.png#lightbox)

## Edit, reconfigure, or delete a connected application

The **Open application settings** link opens the corresponding Microsoft Entra application management page in the Azure portal. From the Azure portal, you can manage permissions, reconfigure, or delete the connected applications.
