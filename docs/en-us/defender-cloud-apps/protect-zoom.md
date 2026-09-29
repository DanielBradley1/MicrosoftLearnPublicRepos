<!-- Source: https://learn.microsoft.com/en-us/defender-cloud-apps/protect-zoom -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# Connect Zoom to Microsoft Defender for Cloud Apps \(Preview\)

Zoom is an online video conferencing and collaboration tool. Zoom holds critical data of your organization, and this exposure makes Zoom a target for malicious actors. This article explains how to connect your Zoom environment to Microsoft Defender for Cloud Apps by using the API connector. After you complete this connection, you can monitor Zoom activity, detect threats, and review security posture recommendations to help protect your organization's Zoom data. Before you begin, review the prerequisites listed in the following section to make sure your environment is ready to connect Zoom to Defender for Cloud Apps.

Use this app connector to access SaaS Security Posture Management \(SSPM\) features, via security controls reflected in Microsoft Secure Score. [Learn more](https://learn.microsoft.com/en-us/microsoft-365/security/defender/microsoft-secure-score).

## SaaS security posture management

To see security posture recommendations for Zoom in Microsoft Secure Score, create an API connector via the **Connectors** tab, with `“account:read:admin`, `chat_channel:read:admin` and `user:read:admin”` permissions. In Secure Score, select **Recommended actions** and filter by **Product** = **Zoom**.

For example, recommendations for Zoom include:

- *Enable multifactor authentication \(MFA\)*
- Enable session timeout for web users
- *Enforce end to end encryption in all Zoom meetings*

If a connector already exists and you don't see Zoom recommendations yet, refresh the connection by disconnecting the API connector, and then reconnecting it with the `“account:read:admin`, `chat_channel:read:admin` and `user:read:admin”` permissions.

For more information about SaaS security posture management and Microsoft Secure Score, see:

- [Security posture management for SaaS apps](https://learn.microsoft.com/en-us/defender-cloud-apps/security-saas)
- [Microsoft Secure Score](https://learn.microsoft.com/en-us/microsoft-365/security/defender/microsoft-secure-score)

### Prerequisites

Before connecting Zoom to Defender for Cloud Apps, make sure that you have the following prerequisites:

- A Zoom PRO plan or higher
- Access to Zoom as an account owner or admin, which is required to access the Zoom API.

### Limitations

Be aware of the following limitations when connecting Zoom to Defender for Cloud Apps:

- The admin account is used only to grant initial consent while connecting Zoom to Defender for Cloud Apps. Defender for Cloud Apps uses an OAuth app for daily transactions.
- The authentication mechanism utilized in the Zoom connector doesn't support two separate connectors utilizing the same user credentials.
- Creating a new instance with an existing authentication token revokes the old connector token and will cause a "Bad credentials" error.

### Rate limits

The Zoom connector is subject to the following API rate limits:

- **Pro accounts**: 30 requests per second
- **Business accounts**: 80 requests per second

## How to connect Zoom to Defender for Cloud Apps

Perform the following steps to connect Zoom to Microsoft Defender for Cloud Apps:

1. Sign into Zoom as an account owner or admin.
2. In the Microsoft Defender Portal, select **Settings**. Then choose **Cloud Apps**. Under **Connected apps**, select **App Connectors**.
3. In the **App connectors** page, select **+ Connect an app**, and then **Zoom**.

   ![Screenshot of the App Connectors > Zoom pop-up.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/connect-zoom.png)
4. In the **Instance name** page of the pop-up, give the connector a descriptive name, and select **Next**.
5. In the **External link** page, select **Connect Zoom**. You're redirected to the Zoom page, where you're prompted to allow the connection.
6. In Zoom, select to allow the connection.

   In Microsoft Defender XDR, the **External link** page of the pop-up is updated to confirm that you're connected. For example:

   ![Screenshot of the success message in Microsoft Defender XDR.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/connect-zoom-success.png)
7. In the Microsoft Defender XDR pop-up, select **Done**.

   Note

   After the connector's **Status** is marked as **Connected**, the connector is live and works.

## Next steps

- [Control cloud apps with policies](https://learn.microsoft.com/en-us/defender-cloud-apps/control-cloud-apps-with-policies)
