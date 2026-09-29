<!-- Source: https://learn.microsoft.com/en-us/defender-cloud-apps/general-setup -->
<!-- Sitemap-Last-Modified: 2026-08-08 -->

# Basic setup for Defender for Cloud Apps

The following procedure gives you instructions for customizing your Microsoft Defender for Cloud Apps environment.

## Prerequisites

For portal access requirements, see [Portal access](https://learn.microsoft.com/en-us/defender-cloud-apps/network-requirements#portal-access).

## Set up your Defender for Cloud Apps environment

Perform the following steps to set up your Defender for Cloud Apps environment:

1. In the Microsoft Defender Portal, select **Settings**. Then choose **Cloud Apps**.
2. Under **System** -> **Organization details**, it's important that you provide an **Organization display name** for your organization.
3. Provide an **Environment name** \(tenant\). This information is especially important if you manage more than one tenant.
4. \(Optional\) Upload a **Logo** file to be displayed in email notifications and web pages sent from the system. The logo must be a .PNG file with a maximum size of 150 x 50 pixels, on a transparent background.

   Logos are stored in publicly accessible storage. The source URL for your image is protected and stored internally.

   Providing this image is voluntary, it’s up to you to decide if you want to share this data with us. You can also choose to delete the logo at any time, and the logo file will be deleted from our storage. This decision does not affect the security of your organization or your users in any way.
5. Make sure you add a list of your **Managed domains** to identify internal users. Adding managed domains is a crucial step. Defender for Cloud Apps uses the managed domains to determine which users are internal, external, and where files should and shouldn't be shared. Managed domain data is used for reports and alerts.

   - Users in domains that aren't configured as internal are marked as external. People outside the organization aren't scanned for activities or files.

6. If you're integrating with Microsoft Purview Information Protection, make sure you first enable the [App connector for Microsoft 365](https://learn.microsoft.com/en-us/defender-cloud-apps/connect-office-365). Then see [Microsoft Purview Information Protection Integration](https://learn.microsoft.com/en-us/defender-cloud-apps/azip-integration) for setup information.

## Enable Identity inventory integration

Enable Identity Inventory Integration to ingest cloud app accounts into the [Identity inventory](https://learn.microsoft.com/en-us/defender-for-identity/identity-inventory), providing a centralized view of identities across on-premises, cloud, and SaaS environments.

Warning

After you enable Identity Inventory Integration, the integration can't be disabled.

Review the following important considerations before enabling this setting:

- As Microsoft Defender moves toward a fully unified identity platform, some Defender for Cloud Apps data pipelines remain separate. These improvements **don't currently affect the following Defender for Cloud Apps capabilities**:

  - Built-in detections
  - UEBA \(User and Entity Behavior Analytics\)
  - Scoped deployment
  - Governance actions
  - Defender for Cloud Apps policies
  - Activity log
  - Cloud discovery user enrichment and anonymization
  - RBAC scoping


  These features continue to use the Cloud Application Accounts inventory. For more information, see [Cloud app accounts](https://learn.microsoft.com/en-us/defender-cloud-apps/accounts).

- The existing **Cloud Apps Accounts view remains available** to ensure backward compatibility.

### Prerequisites

To view the configuration page, you need any read or write role.

To change the configuration, you need one of the following roles:

- **Microsoft Entra ID roles**: Global Administrator, Security Administrator, or Cloud App Administrator
- **Defender for Cloud Apps built-in roles**: Global administrator

Tip

Use the least-privileged role that's sufficient for the task. Security Administrator or Cloud App Administrator is preferred over Global Administrator. If Global Administrator access is needed, consider using [Privileged Identity Management \(PIM\)](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/pim-configure) for just-in-time access.

To enable the integration:

1. In the Microsoft Defender portal, select **Settings**. Then choose **Cloud Apps**.
2. Under **System**, select **Identity Inventory Integration**.
3. On the **Identity Inventory Integration** page, select the **Enable Identity Inventory Integration** checkbox.

   Note

   If Defender for Cloud Apps scoping is enabled for your tenant, the checkbox is unavailable.
4. Select **Confirm**.

After the integration is enabled, SaaS and cloud accounts are ingested into the Identity inventory. These accounts appear in the **Human identities** tab on the [Identity inventory](https://learn.microsoft.com/en-us/defender-for-identity/identity-inventory) page.

## Next steps

[Set up cloud discovery](https://learn.microsoft.com/en-us/defender-cloud-apps/set-up-cloud-discovery)

If you run into any problems, we're here to help. To get assistance or support for your product issue, please [open a support ticket](https://learn.microsoft.com/en-us/defender-xdr/contact-defender-support).
