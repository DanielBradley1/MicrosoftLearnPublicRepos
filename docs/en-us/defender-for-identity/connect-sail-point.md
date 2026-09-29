<!-- Source: https://learn.microsoft.com/en-us/defender-for-identity/connect-sail-point -->
<!-- Sitemap-Last-Modified: 2026-08-08 -->

# Connect SailPoint Identity Security Cloud to Microsoft Defender for Identity \(Preview\)

This article describes how to connect SailPoint Identity Security Cloud to Microsoft Defender for Identity by using the API connector in the Microsoft Defender portal. After you set up this integration, security administrators can gain visibility into SailPoint-managed identities, investigate identity-related threats, and monitor account activity directly from Defender for Identity. Before you start, make sure you have the required SailPoint IdentityNow Admin role and the necessary Microsoft Entra or Defender XDR permissions. For full details, review the [prerequisites for connecting SailPoint](#prerequisites).

## Prerequisites

Make sure you meet these requirements before you start:

**SailPoint Identity Security Cloud roles**

- The IdentityNow Admin role is required only to create an application.

**Microsoft Entra and Defender role-based access options**

Your account needs one of these access options to set up the connector:

- **Microsoft Entra roles:**

  - Security Operator
  - Security Admin

- **Defender Unified RBAC permission:**

  - Core security settings \(manage\)

## Connect SailPoint Identity Security Cloud to Microsoft Defender for Identity

To set up the connection, create a personal access token in SailPoint and then configure the connector in the Defender portal.

### Create a SailPoint Identity Security Cloud Personal Access Token

Before you begin, create a dedicated SailPoint Identity Security Cloud user for this integration. Then create a personal access token for that user:

1. Sign in to SailPoint Identity Security Cloud as the dedicated user.
2. Go to **User's Preferences > Personal Access Tokens**.
3. Select **New Token**.
4. Add the following scopes to the token:

   1. idn:accounts:read
   2. idn:entitlement:read
   3. sp:search:read
   4. idn:accounts-state:manage

5. Copy the **Client ID** and **Secret**. You need these values later to finish the setup.

### Connect SailPoint Identity Security Cloud to Defender for Identity

Use the Defender portal to configure the SailPoint connector:

1. Sign in to the [Microsoft Defender Portal](https://security.microsoft.com).
2. Go to **System > Data Management > Data Connectors**.
3. Select **Catalog > SailPoint Identity Security Cloud**.
4. Select **Connect a connector**

   1. Enter a name for your connector.
   2. Enter your SailPoint Identity Security Cloud API Endpoint URL. Use the value after `https://` and make sure 'api' is included in the URL. For example, `contoso.api.identitynow.com`.
   3. Enter your **Client ID** and **Client Secret**.


   [![Screenshot that shows where to enter the client ID and Client Secret in the Defender portal.](https://learn.microsoft.com/en-us/defender-for-identity/media/connect-sail-point/name-and-connection-details.png)](https://learn.microsoft.com/en-us/defender-for-identity/media/connect-sail-point/name-and-connection-details.png#lightbox)

5. Select **Next**.
6. Select **Protection Types > Identity**, and then select **Next**.

   [![Screenshot that shows the selection of protection types in the Defender portal.](https://learn.microsoft.com/en-us/defender-for-identity/media/connect-sail-point/select-product-microsoft-defender-for-identity.png)](https://learn.microsoft.com/en-us/defender-for-identity/media/connect-sail-point/select-product-microsoft-defender-for-identity.png#lightbox)
7. Review the information and select **Connect**.
8. Verify that the SailPoint Identity connector appears in the **My Connector** table as **Connection Status: Ok**.

## Related content

- [How Microsoft Defender for Identity protects your SailPoint identity accounts](https://learn.microsoft.com/en-us/defender-for-identity/sail-point-overview)
