<!-- Source: https://learn.microsoft.com/en-us/entra/workload-id/workload-identity-federation-block-using-azure-policy -->
<!-- Sitemap-Last-Modified: 2025-01-29 -->

# Block workload identity federation on managed identities using a policy

This article describes how to block the creation of federated identity credentials on user-assigned managed identities by using Azure Policy. By blocking the creation of federated identity credentials, you can block everyone from using [workload identity federation](https://learn.microsoft.com/en-us/entra/workload-id/workload-identity-federation) to access Microsoft Entra protected resources. [Azure Policy](https://learn.microsoft.com/en-us/azure/governance/policy/overview) helps enforce certain business rules on your Azure resources and assess compliance of those resources.

The Not allowed resource types built-in policy can be used to block the creation of federated identity credentials on user-assigned managed identities.

## Create a policy assignment

To create a policy assignment for the Not allowed resource types that blocks the creation of federated identity credentials in a subscription or resource group:

1. Sign in to the [Azure portal](https://portal.azure.com).
2. Navigate to **Policy** in the Azure portal.
3. Go to the **Definitions** pane.
4. In the **Search** box, search for "Not allowed resource types" and select the *Not allowed resource types* policy in the list of returned items. ![Screenshot showing search results in the Azure Policy Definitions pane.](https://learn.microsoft.com/en-us/entra/workload-id/media/workload-identity-federation-block-using-azure-policy/azure-policy-search.png)
5. After selecting the policy, you can now see the **Definition** tab.
6. Click the **Assign** button to create an Assignment. ![Screenshot showing Policy Definition pane.](https://learn.microsoft.com/en-us/entra/workload-id/media/workload-identity-federation-block-using-azure-policy/azure-policy-assign.png)
7. In the **Basics** tab, fill out **Scope** by setting the **Subscription** and optionally set the **Resource Group**.
8. In the **Parameters** tab, select **userAssignedIdentities/federatedIdentityCredentials** from the **Not allowed resource types** list. Select **Review and create**. ![Screenshot showing Parameters tab.](https://learn.microsoft.com/en-us/entra/workload-id/media/workload-identity-federation-block-using-azure-policy/azure-policy-assign-parameters.png)
9. Apply the Assignment by selecting **Create**.
10. View your assignment in the **Assignments** tab next to **Definition**.

## Next steps

Learn how to [manage a federated identity credential on a user-assigned managed identity](https://learn.microsoft.com/en-us/entra/workload-id/workload-identity-federation-create-trust-user-assigned-managed-identity) in Microsoft Entra ID.
