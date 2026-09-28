<!-- Source: https://learn.microsoft.com/en-us/entra/external-id/customers/quickstart-tenant-setup -->
<!-- Sitemap-Last-Modified: 2025-04-08 -->

# Quickstart: Use your Azure subscription to create an external tenant

**Applies to**: ![Green circle with a white check mark symbol that indicates the following content applies to external tenants.](https://learn.microsoft.com/en-us/entra/external-id/media/common/applies-to-yes.png) External tenants \([learn more](https://learn.microsoft.com/en-us/entra/external-id/tenant-configurations)\)

Microsoft Entra External ID offers a customer identity access management \(CIAM\) solution that lets you create secure, customized sign-in experiences for your apps and services. You'll need to create a tenant with external configurations in the Microsoft Entra admin center to get started. Once the tenant with external configurations is created, you can access it in both the Microsoft Entra admin center and the Azure portal.

In this quickstart, you'll learn how to create a tenant with external configurations if you already have an Azure subscription.

## Prerequisites

- An Azure subscription.
- An Azure account that's been assigned at least the [Tenant Creator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#tenant-creator) role scoped to the subscription.

## Create a new tenant with external configurations

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com).
2. Browse to **Entra ID** > **Overview** > **Manage tenants**.
3. Select **Create**.

   ![Screenshot of the create tenant option.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-create-external-tenant-portal/create-tenant.png)
4. Select **External**, and then select **Continue**.

   ![Screenshot of the select tenant type screen.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-create-external-tenant-portal/select-tenant-type.png)
5. On the **Basics** tab, in the **Create a tenant** page, enter the following information:

   ![Screenshot of the Basics tab.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-create-external-tenant-portal/add-basics-to-external-tenant.png)

   - Type your desired **Tenant Name** \(for example *Contoso Customers*\).
   - Type your desired **Domain Name** \(for example *Contosocustomers*\).
   - Select your desired **Location**. This selection can't be changed later.

6. Select **Next: Add a subscription**.
7. On the **Add a subscription** tab, enter the following information:

   - Next to **Subscription**, select your subscription from the menu.
   - Next to **Resource group**, select a resource group from the menu. If there are no available resource groups, select **Create new**, add a name, and then select **OK**.
   - If **Resource group location** appears, select the geographic location of the resource group from the menu.


   ![Screenshot that shows the subscription settings.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-create-external-tenant-portal/add-subscription.png)

8. Select **Next: Review + create**. If the information that you entered is correct, select **Create**. The tenant creation process can take up to 30 minutes. You can monitor the progress of the tenant creation process in the **Notifications** pane. Once the tenant is created, you can access it in both the Microsoft Entra admin center and the Azure portal.

   ![Screenshot that shows the link to the new tenant.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-create-external-tenant-portal/tenant-successfully-created.png)

## Customize your tenant with a guide

Our guide will walk you through the process of setting up a user and configuring a sample app in just a few minutes. This means that you can quickly and easily test out different sign-in and sign-up options and set up a sample app to see what works best for you. This guide is available in any external tenant.

Note

The guide won’t run automatically in external tenants that you created with the steps above. If you want to run the guide, follow the steps below.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com).
2. If you have access to multiple tenants, use the **Settings** icon ![](https://learn.microsoft.com/en-us/entra/external-id/customers/media/common/admin-center-settings-icon.png) in the top menu to switch to your external tenant from the **Directories + subscriptions** menu.
3. Browse to **Home** > **Tenant overview**.
4. On the Get started tab, select **Start the guide**.

   ![Screenshot that shows how to start the guide.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-create-external-tenant-portal/guide-link.png)

This link will take you to the [guide](https://learn.microsoft.com/en-us/entra/external-id/customers/quickstart-get-started-guide), where you can customize your tenant in three easy steps.

Note

You can also set up and customize your external tenant directly within Visual Studio Code using the [Microsoft Entra External ID extension for Visual Studio Code](https://aka.ms/ciamvscode/quickstarts/marketplace). For more information, see our [quickstart guide](https://aka.ms/ciamvscode/quickstartguide).

## Related content

- To learn more about the set-up guide and how to customize your tenant, see the [Get started guide](https://learn.microsoft.com/en-us/entra/external-id/customers/quickstart-get-started-guide) article.
- To learn how to delete your tenant, see the [Delete an external tenant](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-delete-external-tenant-portal) article.
- To learn how to migrate users from another identity provider, see the [How to migrate users](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-migrate-users) article.
