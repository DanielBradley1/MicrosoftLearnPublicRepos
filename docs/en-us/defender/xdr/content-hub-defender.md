<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/content-hub-defender -->
<!-- Sitemap-Last-Modified: 2026-09-23 -->

# Use Content hub with ISOC in Microsoft Defender \(preview\)

Use Content hub with Integrated Security Operations Center \(ISOC\) in Microsoft Defender to discover and install supported Microsoft Sentinel content for your ISOC workspace.

Note

During this preview, Content hub supports data connectors. If a solution includes multiple content types, only its data connectors are available for installation.

## Prerequisites

Before you begin, make sure the following requirements are met:

- Your tenant is [eligible for ISOC](https://learn.microsoft.com/en-us/defender-xdr/isoc-overview).
- You have an [ISOC workspace](https://learn.microsoft.com/en-us/defender-xdr/onboard-isoc-workspace).
- You have the following permissions:

  - In Unified RBAC:

    - **Content hub read**
    - **Content hub manage**

  - In Azure, **Deploy** permission on the resource group to install solutions.

## Discover content

1. Sign in to the [Microsoft Defender portal](https://security.microsoft.com).
2. Go to **SIEM** > **Content management** > **Content hub**.
3. Search for a solution or use the available filters to find content.
4. Select a solution to view its details and available data connectors.

## Install data connectors

1. Sign in to the [Microsoft Defender portal](https://security.microsoft.com).
2. Go to **SIEM** > **Content management** > **Content hub**.
3. Search for and select the solution that contains the data connector you want to install.
4. Select **View details**.
5. Select **Create**.
6. On the **Basics** tab, select the subscription, resource group, and workspace where you want to deploy the solution.
7. Select **Next** to review the available configuration.
8. On the **Review + create** tab, wait for validation to complete.
9. Select **Create**.

Only supported data connectors from the solution are available for installation. Other content types included in the solution aren't installed during the ISOC preview.

After installation, configure the data connector to start ingesting data into your ISOC workspace.

## Update an installed solution

If an installed solution has an available update, you can update it from Content hub.

1. Sign in to the [Microsoft Defender portal](https://security.microsoft.com).
2. Go to **SIEM** > **Content management** > **Content hub**.
3. Search for and select the installed solution.
4. Select **View details**.
5. Select **Update**.
6. Review the solution configuration.
7. Select **Review + create**.
8. Wait for validation to complete.
9. Select **Update**.

Note

During this preview, updates apply only to supported data connector content.

## Related content

- [Connect your data sources](https://learn.microsoft.com/en-us/azure/sentinel/data-connectors-reference)
- [Workbooks with ISOC in Microsoft Defender](https://learn.microsoft.com/en-us/defender-xdr/siem-defender-workbooks)
- [Automation with ISOC in Microsoft Defender](https://learn.microsoft.com/en-us/defender-xdr/siem-defender-automation)
- [Add UEBA to Microsoft 365 E5 data](https://learn.microsoft.com/en-us/defender-xdr/extend-ueba)
