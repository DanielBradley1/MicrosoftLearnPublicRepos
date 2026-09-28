<!-- Source: https://learn.microsoft.com/en-us/entra/identity-platform/multi-service-web-app-clean-up-resources -->
<!-- Sitemap-Last-Modified: 2025-04-16 -->

# Tutorial: Clean up resources

If you completed all the steps in this multipart tutorial, you created an app service, app service hosting plan, and a storage account in a resource group. You also created an app registration in Microsoft Entra ID. When no longer needed, delete these resources and app registration so that you don't continue to accrue charges.

In this tutorial, you:

- Delete the Azure resources created while following the tutorial.

## Delete the resource group

In the [Azure portal](https://portal.azure.com), select **Resource groups** from the portal menu and select the resource group that contains your app service and app service plan.

Select **Delete resource group** to delete the resource group and all the resources.

![Screenshot that shows deleting the resource group.](https://learn.microsoft.com/en-us/entra/identity-platform/media/multi-service-web-app-clean-up-resources/delete-resource-group.png)

This command might take several minutes to run.

## Delete the app registration

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least an [Application Developer](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-developer).
2. Browse to **Entra ID** > **App registrations**.
3. Select the application you created.
4. In the app registration overview, select **Delete**.
