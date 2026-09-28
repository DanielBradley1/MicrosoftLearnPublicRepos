<!-- Source: https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/how-to-view-managed-identity-activity -->
<!-- Sitemap-Last-Modified: 2024-06-06 -->

# View update and sign-in activities for Managed identities

This article explains how to view updates carried out to managed identities, and sign-in attempts made by managed identities.

## Prerequisites

- If you're unfamiliar with managed identities for Azure resources, check out the [overview section](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/overview).
- If you don't already have an Azure account, [sign up for a free account](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).

## View updates made to user-assigned managed identities

This procedure demonstrates how to view updates carried out to user-assigned managed identities.

1. In the Azure portal, browse to **Activity Log**.

   ![Screenshot showing how to browse to the activity log in the Azure portal](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/media/how-to-view-managed-identity-activity/browse-to-activity-log.png)
2. Select the **Add Filter** search pill and select **Operation** from the list.

   ![Screenshot showing how to start building the search filter](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/media/how-to-view-managed-identity-activity/start-adding-search-filter.png)
3. In the **Operation** dropdown list, enter these operation names: "Delete User Assigned Identity" and "Write UserAssignedIdentities".

   ![Screenshot showing how to add operations to the search filter](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/media/how-to-view-managed-identity-activity/add-operations-to-search-filter.png)
4. When matching operations are displayed, select one to view the summary.

   ![Screenshot showing the summary of the operation](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/media/how-to-view-managed-identity-activity/view-summary-of-operation.png)
5. Select the **JSON** tab to view more detailed information about the operation, and scroll to the **properties** node to view information about the identity that was modified.

   ![Screenshot showing operation details](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/media/how-to-view-managed-identity-activity/view-json-of-operation.png)

## View role assignments added and removed for managed identities

Note

You'll need to search by the object \(principal\) ID of the managed identity that you want to view role assignment changes for.

1. Locate the managed identity you wish to view the role assignment changes for. If you're looking for a system-assigned managed identity, the object ID is displayed in the **Identity** screen under the resource. If you're looking for a user-assigned identity, the object ID is displayed in the **Overview** page of the managed identity.

User-assigned identity:

![Screenshot showing how to get the object ID of user-assigned identity](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/media/how-to-view-managed-identity-activity/get-object-id-of-user-assigned-identity.png)

System-assigned identity:

![Screenshot showing how to get the object ID of system-assigned identity](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/media/how-to-view-managed-identity-activity/get-object-id-of-system-assigned-identity.png)

1. Copy the object ID.
2. Browse to the **Activity log**.

   ![Screenshot showing how to browse to the activity log in the Azure portal](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/media/how-to-view-managed-identity-activity/browse-to-activity-log.png)
3. Select the **Add Filter** search pill and select **Operation** from the list.

   ![Screenshot showing how to start building the search filter](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/media/how-to-view-managed-identity-activity/start-adding-search-filter.png)
4. In the **Operation** dropdown list, enter these operation names: **Create role assignment** and **Delete role assignment**.

   ![Screenshot showing how to add role assignment operations to the search filter](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/media/how-to-view-managed-identity-activity/add-role-assignment-operations-to-search-filter.png)
5. Paste the object ID in the search box; the results are filtered automatically.

   ![Screenshot showing how to search by object ID](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/media/how-to-view-managed-identity-activity/search-by-object-id.png)
6. When matching operations are displayed, select one to view the summary.

   ![Screenshot showing the summary of role assignment for managed identity](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/media/how-to-view-managed-identity-activity/summary-of-role-assignment-for-msi.png)

## View authentication attempts by managed identities

1. Browse to **Microsoft Entra ID**.

   ![Screenshot showing how to browse to active directory](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/media/how-to-view-managed-identity-activity/browse-to-entra.png)
2. Select **Sign-in logs** from the **Monitoring** section.

   ![Screenshot showing sign-in logs selection](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/media/how-to-view-managed-identity-activity/sign-in-logs-menu-item.png)
3. Select the **Managed identity sign-ins** tab.

   ![Screenshot of the managed identities activity section showing all columns](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/media/how-to-view-managed-identity-activity/sign-in-logs.png)
4. To view the identity's Enterprise application in Microsoft Entra ID, select the "Managed Identity ID" column.
5. To view the Azure resource or user-assigned managed identity, search by name in the search bar of the Azure portal.

   ![Screenshot showing managed identity sign-in events](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/media/how-to-view-managed-identity-activity/msi-sign-in-events.png)

Note

Since managed identity authentication requests originate within the Azure infrastructure, the IP Address value is excluded here.

## Next steps

- [Managed identities for Azure resources](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/overview)
- [Azure Activity log](https://learn.microsoft.com/en-us/azure/azure-monitor/essentials/activity-log)
- [Microsoft Entra sign-in log](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-sign-ins)
