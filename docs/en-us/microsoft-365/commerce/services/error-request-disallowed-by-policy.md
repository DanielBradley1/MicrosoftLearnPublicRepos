<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/commerce/services/error-request-disallowed-by-policy?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-02-02 -->

# Fix the "RequestDisallowedByPolicy" error

This article describes how to fix the **RequestDisallowedByPolicy** error when you create resources in the Azure portal.

If you see the error code **RequestDisallowedByPolicy**, an Azure policy assigned in your environment blocked the creation of a resource. This error often occurs when a policy doesn't explicitly allow certain resource types, such as the GM Resource Standards policy.

## What causes this error?

Your organization applied a policy, typically called "Allowed resource types," to control which Azure resources you can create. If you try to deploy a resource type that's not listed in this policy, Azure blocks the request and shows this error.

## Steps to resolve the policy error

To fix this error, update the policy assignment to include the resource types you're trying to deploy. For example, you might add resource types for document processing for Microsoft 365 scenarios.

1. Sign in to the [Azure portal](https://portal.azure.com).
2. In the top search bar, type *Policy* and then select it.
3. In the **Policy** blade, select **Assignments** from the left navigation.
4. Locate the policy assignment with the name "Allowed resource types." This policy assignment is usually tied to the GM Resource Standards initiative.
5. Select the policy, and then select **Edit assignment**.
6. Under **Parameters**, add the resource types you want to allow:

   - Microsoft.Syntex/accounts
   - Microsoft.Syntex/documentProcessors

7. Select **Save** to apply the changes.
8. Try creating the resource again.

### Need visual help?

Check out the following screenshots for each step in the Azure portal to guide you through the process.

![Screenshot of the Assign Policy page in Azure portal with policy configuration options.](https://learn.microsoft.com/en-us/microsoft-365/media/services/azure-assign-policy.png?view=o365-worldwide)

![Screenshot of the Policy Assignments page displaying available policies in the Azure portal.](https://learn.microsoft.com/en-us/microsoft-365/media/services/azure-policy-assignments.png?view=o365-worldwide)

![Screenshot of the Allowed resource types configuration page in Azure portal.](https://learn.microsoft.com/en-us/microsoft-365/media/services/azure-allowed-resource-types.png?view=o365-worldwide)

## ![Screenshot of the Assign Policy page showing specific policy assignment details in Azure portal.](https://learn.microsoft.com/en-us/microsoft-365/media/services/azure-assign-policy-full-page.png?view=o365-worldwide)
