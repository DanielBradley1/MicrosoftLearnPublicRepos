<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/lighthouse/m365-lighthouse-view-your-roles?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2025-04-10 -->

# View your assigned roles in Microsoft 365 Lighthouse

Lighthouse role-based access control \(RBAC\) roles and Microsoft Entra roles determine the actions you can perform in Microsoft 365 Lighthouse:

- *Lighthouse RBAC roles* determine the data you can access and change within your partner tenant. Lighthouse RBAC roles don't provide access to customer data.
- *Microsoft Entra roles* provide access to customer data and are based on the granular delegated administrative privileges \(GDAP\) relationships you set up with your customers.

## Before you begin

You must have access to a partner tenant that has onboarded to the Microsoft 365 Lighthouse service.

## View your assigned roles

There are two ways to view your assigned roles:

- In the left navigation pane in [Lighthouse](https://go.microsoft.com/fwlink/p/?linkid=2168110), select **Roles** > **Assigned roles**.
- To view the roles you hold for a specific tenant:

  1. In the left navigation pane in [Lighthouse](https://go.microsoft.com/fwlink/p/?linkid=2168110), select **Tenants**.
  2. From the list of tenants, select any tenant name to open the tenant details page.
  3. Under **Your permissions**, select **View role**.

     On the **Roles** page, if you hold one or more roles in a customer tenant, you'll see a green checkmark in the **Enabled** column for that tenant, along with the number of roles you hold. If you don't hold any roles in a tenant, you'll see a red **X**.
  4. For customer tenants with a green checkmark next to them, expand the tenant to see the list of roles you hold in that tenant. For more information about Microsoft Entra roles and the permissions they grant, see [Microsoft Entra built-in roles](https://learn.microsoft.com/en-us/azure/active-directory/roles/permissions-reference).

     The **Roles** page also shows any custom tags that are applied to your tenants. You can filter the data on the page by assigned roles or tags.

## Next steps

If you don't have permission to perform an action that you need to perform in Lighthouse, reach out to someone who holds the Administrator role in Lighthouse and ask them to assign you an appropriate role for the action you're trying to perform.

## Related content

[Overview of permissions in Microsoft 365 Lighthouse](https://learn.microsoft.com/en-us/microsoft-365/lighthouse/m365-lighthouse-overview-of-permissions?view=o365-worldwide) \(article\)  
[Manage Lighthouse RBAC permissions in Microsoft 365 Lighthouse](https://learn.microsoft.com/en-us/microsoft-365/lighthouse/m365-lighthouse-manage-lighthouse-rbac-permissions?view=o365-worldwide) \(article\)  
[Microsoft Entra built-in roles](https://learn.microsoft.com/en-us/azure/active-directory/roles/permissions-reference) \(article\)
