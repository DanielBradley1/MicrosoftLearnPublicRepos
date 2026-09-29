<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/onboard-isoc-workspace -->
<!-- Sitemap-Last-Modified: 2026-09-23 -->

# Create an ISOC workspace in the Microsoft Defender portal \(preview\)

Use this procedure to create an Integrated Security Operations Center \(ISOC\) workspace in the Microsoft Defender portal for capabilities that require a workspace.

Before you begin, review the eligibility and workspace requirements in [ISOC in Microsoft Defender](https://learn.microsoft.com/en-us/defender-xdr/isoc-overview).

## Prerequisites

Before you begin, make sure the following requirements are met:

- Your tenant is [eligible for ISOC](https://learn.microsoft.com/en-us/defender-xdr/isoc-overview).
- You have an active Azure subscription.
- You have the **Security Administrator** role in Microsoft Entra ID.
- You have one of the following permission configurations on the Azure subscription:

  - Unconditional **Owner**.
  - **User Access Administrator** and **Microsoft Sentinel Contributor**.

## Create an ISOC workspace

1. Sign in to the [Microsoft Defender portal](https://security.microsoft.com/).
2. Go to **Setup & configuration** > **Settings** > **Microsoft Sentinel** > **SIEM workspaces**.
3. Select **+ Create workspace**.
4. In **Subscription**, select the Azure subscription where you want to create the workspace.

   [![Screenshot of the Connect Microsoft Sentinel to Defender dialog in the Microsoft Defender portal, where you select an Azure subscription to create and connect an ISOC workspace.](https://learn.microsoft.com/en-us/defender-xdr/media/onboard-isoc-workspace/connect-microsoft-sentinel-to-defender.png)](https://learn.microsoft.com/en-us/defender-xdr/media/onboard-isoc-workspace/connect-microsoft-sentinel-to-defender.png#lightbox)

   The portal checks whether you have the required permissions on the selected subscription.
5. After the permissions check succeeds, review the workspace details.

   The setup provides values for the resource group, workspace, and region.
6. To change the workspace configuration, select the edit icon next to **Workspace details**.
7. Update the resource group, workspace name, region, or tags as needed.
8. Select **Connect**.

The Defender portal creates the required Azure resources and connects the new workspace to the Defender portal.

Provisioning can take several minutes. During provisioning, the setup shows the following states:

- **Creating resources** - The required Azure resources are being deployed.
- **Connecting the workspace** - The newly created workspace is being connected to the Defender portal.

When provisioning is complete, a confirmation dialog appears and the workspace is listed on the **SIEM workspaces** page.

## Next steps

After you create the ISOC workspace, configure the capabilities that require it:

- [Add UEBA to Microsoft 365 E5 data](https://learn.microsoft.com/en-us/defender-xdr/extend-ueba)
- [Use Content hub in Microsoft Defender](https://learn.microsoft.com/en-us/defender-xdr/content-hub-defender)
- [Deploy content as code from your repository for an ISOC workspace](https://learn.microsoft.com/en-us/defender-xdr/deploy-content-integrated-security-operations)
- [Threat intelligence in Microsoft Defender](https://learn.microsoft.com/en-us/defender-xdr/defender-threat-intelligence)
- [Data ingestion and billing for ISOC](https://learn.microsoft.com/en-us/defender-xdr/integrated-security-operations-data-billing-retention)
