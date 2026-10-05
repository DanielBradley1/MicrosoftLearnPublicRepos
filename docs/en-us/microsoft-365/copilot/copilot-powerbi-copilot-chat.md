<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/copilot-powerbi-copilot-chat -->
<!-- Sitemap-Last-Modified: 2026-09-24 -->

# Use Power BI data in Microsoft Copilot

Microsoft Copilot can answer user questions using Power BI reports and semantic models. Copilot will ground responses in Power BI data, including scenarios where users share a specific report and scenarios where Copilot finds the right report automatically. This feature is enabled by default.

Note

Fabric IQ integrates with Microsoft Copilot Chat to bring trusted business data from Power BI into Copilot conversations. Through MCP-based integration, users can ask natural-language questions about their data and combine business data with the broader context available in Copilot Chat. The experience respects existing Power BI permissions and security controls while helping users access data-driven insights. Learn more: [Fabric IQ in Microsoft 365 Copilot Chat](https://learn.microsoft.com/en-us/fabric/iq/connectors/microsoft-365-copilot-overview).

## Manage Fabric data in Microsoft Copilot

1. Go to the [Microsoft 365 admin center](https://admin.microsoft.com/) and select **Copilot** > **Settings**.
2. On the **Copilot settings** page, select **View all**.
3. Select **Fabric data in Microsoft Copilot**.
4. Under **Step 1**, choose which users can access Fabric data in Microsoft Copilot: **No users**, **All users**, or **Specific groups**.
5. Select **Save**.

   ![Screenshot: Image showing steps on how to make Fabric data available in Microsoft Copilot.](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/fabric-data-available2.png)

For more information about creating security groups, see [Create a security group](https://learn.microsoft.com/en-us/microsoft-365/admin/email/create-edit-or-delete-a-security-group).

This setting allows Microsoft Copilot to connect to Power BI enterprise data and return grounded answers based on Power BI reports and semantic models.

## Turn on Fabric data in Microsoft Copilot

If you want Fabric data to be indexed and searchable in Microsoft 365 services, a [Fabric administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference) will need to enable the Share data with your Microsoft 365 services tenant setting in the Fabric admin portal.

1. Go to the [Microsoft 365 admin center](https://admin.microsoft.com/) and select **Copilot** > **Settings**.
2. On the **Copilot settings** page, select **View all**.
3. Select **Fabric data in Microsoft Copilot**.
4. Under **Step 2**, choose **[Go to the Fabric admin portal](https://app.fabric.microsoft.com/admin-portal).**
5. In Fabric, enable **Share Fabric data with your Microsoft 365 services** in **Admin portal -> Tenant settings**. This setting controls whether Fabric metadata is shared with Microsoft 365 services.

For more information, see [Microsoft Fabric](https://learn.microsoft.com/en-us/fabric/admin/admin-share-power-bi-metadata-microsoft-365-services) documentation.

Important

When you allow Microsoft Copilot users to search and retrieve data stored in Fabric, their query data from Microsoft Copilot will be shared with Fabric. Fabric operates separately from Microsoft Copilot and has different commitments. Data processed in Fabric is subject to [Fabric Product Terms](https://www.microsoft.com/licensing/terms/productoffering/onlineservices).
