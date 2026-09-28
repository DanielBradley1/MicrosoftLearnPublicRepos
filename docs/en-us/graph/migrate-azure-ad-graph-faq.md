<!-- Source: https://learn.microsoft.com/en-us/graph/migrate-azure-ad-graph-faq -->
<!-- Sitemap-Last-Modified: 2025-08-29 -->

# Azure AD Graph to Microsoft Graph migration FAQ

This article provides answers to frequently asked questions about migrating from Azure Active Directory \(Azure AD\) Graph to [Microsoft Graph](https://learn.microsoft.com/en-us/graph/overview).

## How is Microsoft Graph different from Azure AD Graph and why should I migrate my apps?

Azure AD Graph offers access to only Microsoft Entra ID \(formerly Azure AD\) services. Microsoft Graph offers a single unified endpoint to access [Microsoft Entra identity and network access family of services](https://learn.microsoft.com/en-us/entra/) and other Microsoft services such as Microsoft Teams, Microsoft Exchange, Microsoft Intune, and much more.

[Microsoft Graph](https://learn.microsoft.com/en-us/graph/overview) is also more secure and resilient than Azure AD Graph. For this reason, Azure AD Graph is currently in a phased retirement cycle as we move all investments to Microsoft Graph. Migrate to Microsoft Graph to avoid loss of existing functionality and to access new features and capabilities.

## As a developer, how do I identify apps that use Azure AD Graph?

Follow these steps to identify apps with a dependency on Azure AD Graph:

### Option 1: Check the Microsoft Entra recommendations

Sign in to an API client such as [Graph Explorer](https://aka.ms/ge) with the required permissions and roles to view Microsoft Entra ID recommendations. Run the [List recommendations](https://learn.microsoft.com/en-us/graph/api/directory-list-recommendation) Microsoft Graph API to retrieve the list of apps and service principals that use Azure AD Graph.

### Option 2: Use the appId of the app to identify its API permissions

#### Step 1: Scan the application source code

If you own an application's source code, search for the `https://graph.windows.net/` URI in the code. This value is the Azure AD Graph endpoint and apps that call this endpoint use Azure AD Graph. Record the value of the affected app's **appId**.

#### Step 2: Call the "Get application" API to read the app's API permissions

1. Sign in to an API client such as [Graph Explorer](https://aka.ms/ge) with at least the *Application Developer* Microsoft Entra role and granted the *Application.Read.All* delegated permission.
2. Call the [Get application](https://learn.microsoft.com/en-us/graph/api/application-get) API using the **appId** you retrieved in Step 1 and read the **requiredResourceAccess** property. The following properties show the permission details:

   - The **requiredResourceAccess** > **resourceAppId** property has the ID `00000002-0000-0000-c000-000000000000` for Azure AD Graph.
   - The **requiredResourceAccess** > **resourceAccess** property lists the ID and type of Azure AD Graph permissions the app uses. Use the [Permissions differences between Azure AD Graph and Microsoft Graph](https://learn.microsoft.com/en-us/graph/migrate-azure-ad-graph-permissions-differences) mapping guide to know the Azure AD Graph permission names.

## As an IT admin, how do I identify apps in my tenant that use Azure AD Graph?

Use the following four methods to identify apps in your tenant with a dependency on Azure AD Graph. Methods 1 and 2 identify your apps that use Azure AD Graph based on the actual app activities while methods 3 and 4 use static app configuration and consent status. You can combine these methods to find apps that have a dependency on Azure AD Graph.

### Method 1: Through network proxy logs

Check your network server traffic logs through a filter proxy for any apps calling the `https://graph.windows.net/` endpoint. These apps use Azure AD Graph.

### Method 2: Check the Microsoft Entra recommendations

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) with privileges to view Microsoft Entra ID recommendations. The following least privileged roles are supported for this operation: *Reports Reader*, *Security Reader*, and *Global Reader*.
2. Expand the **Identity** menu > select **Overview** > **Recommendations** tab. If a recommendation named *Migrate from Azure AD Graph APIs to Microsoft Graph* is listed, it means you have apps that use Azure AD Graph. Select the entry and you see the list of apps and service principals that use Azure AD Graph, and the corrective measures.

### Method 3: Use the App registrations menu of the Microsoft Entra admin center

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com).
2. Expand the **Identity** menu, select **Applications**, then select **App registrations**.
3. In the **App registrations** window, select the **All Applications** tab, then select **Add filters**. Choose the **Requested API** option from the list of available filters and select **Apply**. The **Requested API** filter pops up.

   ![Filter apps by their requested API.](https://learn.microsoft.com/en-us/graph/images/aadgraph-to-msgraph-migration/RequestedAPI.png)
4. Select **Microsoft APIs**. In the **Please select an API** drop down, choose **Azure Active Directory Graph**. Select **Apply**. This process narrows the list to all apps with a dependency on Azure AD Graph.

   ![Filter apps that use Azure AD Graph.](https://learn.microsoft.com/en-us/graph/images/aadgraph-to-msgraph-migration/RequestedAPI-AAD.png)

### Method 4: Use a PowerShell script

Download and run [this PowerShell script](https://github.com/microsoft/AzureADGraphApps). Use this method to retrieve apps with their home directory in your tenant and apps with their home directories in other tenants.

## Microsoft sent me an email with a list of app IDs for apps using Azure AD Graph. How do I find the details of each app, including the owner?

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) with at least the [default user permissions](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#compare-member-and-guest-default-permissions) to read application details.
2. Expand the **Identity** menu, select **Applications**, then select **App registrations**.
3. In the **App registrations** window, select the **All Applications** tab, then select **Add filters**. Choose the **Application \(client\) ID** option from the list of available filters and select **Apply**. A filter pops up.
4. Enter an app ID in the text box and select **Apply**. The list narrows to the specified app.

   ![Filter by apps by app ID.](https://learn.microsoft.com/en-us/graph/images/aadgraph-to-msgraph-migration/AppClientIDFilter.png)
5. Select the app. This step reveals the app's menu. From the left pane of the window, menu options such as **Owners** allow you to retrieve the app's details.

## Microsoft sent me an email with a list of app IDs for apps using Azure AD Graph. Are these all the affected apps?

This list captures only apps that were used within the last 28 days and that called the Azure AD Graph endpoint. For apps with seasonal use, their app ID might appear in one month's list but not in another. To retrieve the full list of affected apps, follow one of the [three methods](#as-an-it-admin-how-do-i-identify-apps-in-my-tenant-that-use-azure-ad-graph) listed previously.

## I'm a subscription owner and Microsoft sent me an email about Azure AD Graph deprecation with a list of app IDs. What should I do?

The email you receive includes the tenant IDs linked to the app IDs. Follow these steps to retrieve the technical contact details for the specific tenants.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com).
2. If you're a subscription owner in multiple Microsoft Entra tenants, first switch to the relevant tenant or directory.

   1. On the top right of the window, select your profile icon and choose **Switch directory**. This action reveals the **Portal settings \| Directories + subscriptions** window.
   2. From the list, use the **Switch** tab to switch to the directory whose Directory ID matches the tenant ID you received in the email. The active directory is marked **Current**.
   3. Close the window.

3. In the relevant directory, expand the **Identity** menu and select **Overview**.
4. In the **Overview** window, select **Properties**.
5. In the **Tenant properties** window, first verify the value of Tenant ID matches a tenant ID you received in the email. Retrieve the **Technical contact** details to contact the tenant so they can be aware of the deprecation.

   ![Find the technical contact for a tenant](https://learn.microsoft.com/en-us/graph/images/aadgraph-to-msgraph-migration/tenanttechnicalcontact.png)

## I know apps that are using Azure AD Graph. How do I migrate them to Microsoft Graph?

To migrate your apps from Azure AD Graph to Microsoft Graph, follow the [App migration planning checklist](https://learn.microsoft.com/en-us/graph/migrate-azure-ad-graph-planning-checklist).

## I don't own some apps in my tenant but they use Azure AD Graph. Can I find the owner of such apps?

First, confirm the full list of apps owned by your tenant or third-party applications integrated in your tenant.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a cloud application administrator.
2. Expand the **Identity** menu > select **Applications**
3. If the apps are registered in your tenant, select **App registrations**. If the apps are multitenant apps that you consented to in your tenant but are homed in another tenant, select **Enterprise applications**.
4. Select the **All Applications** tab.
5. Select the app to reveal its menu.
6. From the left pane of the window, under the **Manage** group, select the **Owners** menu.

   ![Find app owners.](https://learn.microsoft.com/en-us/graph/images/aadgraph-to-msgraph-migration/appowners.png)

## My organization runs Azure Stack Hub. What actions should I take?

If your organization runs Azure Stack Hub, the most important action is to follow the [Azure Stack Hub servicing policy](https://learn.microsoft.com/en-us/azure-stack/operator/azure-stack-servicing-policy).

To migrate, customers are notified through the Azure Stack Hub admin portal to update their home and guest tenant directories. The migration to Microsoft Graph is managed through the integrated system update experience.

## I need to add new Azure AD Graph permissions to my app, but I can't select Azure AD Graph as a required permission for my app registration. How can I add the Azure AD Graph permissions?

First, follow the [App migration planning checklist](https://learn.microsoft.com/en-us/graph/migrate-azure-ad-graph-planning-checklist) to help you transition your apps to the Microsoft Graph API.

If you find a gap where Microsoft Graph doesn't support a feature available in Azure AD Graph, let us know through Microsoft Q&A by using the tag [azure-ad-graph-deprecation](https://learn.microsoft.com/en-us/answers/topics/azure-ad-graph-deprecation.html).

If you still need to configure Azure AD Graph permissions for your applications, use one of the following workarounds:

- Use the Microsoft Entra admin center to find the APIs your organization uses.
- Update the application manifest on the Microsoft Entra admin center.
- Use the [Update application](https://learn.microsoft.com/en-us/graph/api/application-update) API in Microsoft Graph to update the [requiredResourceAccess](https://learn.microsoft.com/en-us/graph/api/resources/requiredresourceaccess) object. For more information, see [Assign permissions to an app](https://learn.microsoft.com/en-us/graph/tutorial-applications-basics?tabs=http#assign-permissions-to-an-app).
- Use Microsoft Graph APIs to [grant permissions programmatically](https://learn.microsoft.com/en-us/graph/permissions-grant-via-msgraph)
- Use the [Update-MgApplication](https://learn.microsoft.com/en-us/powershell/module/microsoft.graph.applications/update-mgapplication?view=graph-powershell-1.0&preserve-view=true) cmdlet in Microsoft Graph PowerShell SDK.

For examples using the listed workarounds, see [Use Microsoft Graph to configure required Azure AD Graph permissions for an app registration](https://learn.microsoft.com/en-us/graph/migrate-azure-ad-graph-configure-permissions).

Note

Adding Azure AD Graph permissions by using these workarounds won't be supported after the retirement of Azure AD Graph. Any app using Azure AD Graph stops functioning after the retirement.

## Related content

- [Checklist to migrate apps](https://learn.microsoft.com/en-us/graph/migrate-azure-ad-graph-request-differences)
