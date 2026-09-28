<!-- Source: https://learn.microsoft.com/en-us/entra/identity-platform/enterprise-app-role-management -->
<!-- Sitemap-Last-Modified: 2024-06-19 -->

# Configure the role claim

You can customize the role claim in the access token that is received after an application is authorized. Use this feature if your application expects custom roles in the token. You can create as many roles as you need.

## Prerequisites

- A Microsoft Entra subscription with a configured tenant. For more information, see [Quickstart: Set up a tenant](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-create-new-tenant).
- An enterprise application that has been added to the tenant. For more information, see [Quickstart: Add an enterprise application](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal).
- Single sign-on \(SSO\) configured for the application. For more information, see [Enable single sign-on for an enterprise application](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-setup-sso).
- A user account that is assigned to the role. For more information, see [Quickstart: Create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users).

Note

This article explains how to create, update, or delete application roles on the service principal using APIs. To use the new user interface for App Roles, see [Add app roles to your application and receive them in the token](https://learn.microsoft.com/en-us/entra/identity-platform/howto-add-app-roles-in-apps).

## Locate the enterprise application

Use the following steps to locate the enterprise application:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **All applications**.
3. Enter the name of the existing application in the search box, and then select the application from the search results.
4. After the application is selected, copy the object ID from the overview pane.

## Add roles

Use the Microsoft Graph Explorer to add roles to an enterprise application.

1. Open [Microsoft Graph Explorer](https://developer.microsoft.com/graph/graph-explorer) in another window and sign in using the administrator credentials for your tenant.

   Note

   The Cloud Application Administrator and Application Administrator role won't work in this scenario, use the Privileged Role Administrator.
2. Select **modify permissions**, select **Consent** for the `Application.ReadWrite.All` and the `Directory.ReadWrite.All` permissions in the list.
3. Replace `<objectID>` in the following request with the object ID that was previously recorded and then run the query:

   `https://graph.microsoft.com/v1.0/servicePrincipals/<objectID>`
4. An enterprise application is also referred to as a service principal. Record the **appRoles** property from the service principal object that was returned. The following example shows the typical appRoles property:

   ```json
   {
     "appRoles": [
       {
         "allowedMemberTypes": [
           "User"
         ],
         "description": "msiam_access",
         "displayName": "msiam_access",
         "id": "00aa00aa-bb11-cc22-dd33-44ee44ee44ee",
         "isEnabled": true,
         "origin": "Application",
         "value": null
       }
     ]
   }
   ```

5. In Graph Explorer, change the method from **GET** to **PATCH**.
6. Copy the appRoles property that was previously recorded into the **Request body** pane of Graph Explorer, add the new role definition, and then select **Run Query** to execute the patch operation. A success message confirms the creation of the role. The following example shows the addition of an *Admin* role:

   ```json
   {
     "appRoles": [
       {
         "allowedMemberTypes": [
           "User"
         ],
         "description": "msiam_access",
         "displayName": "msiam_access",
         "id": "00aa00aa-bb11-cc22-dd33-44ee44ee44ee",
         "isEnabled": true,
         "origin": "Application",
         "value": null
       },
       {
         "allowedMemberTypes": [
           "User"
         ],
         "description": "Administrators Only",
         "displayName": "Admin",
         "id": "11bb11bb-cc22-dd33-ee44-55ff55ff55ff",
         "isEnabled": true,
         "origin": "ServicePrincipal",
         "value": "Administrator"
       }
     ]
   }
   ```


   You must include the `msiam_access` role object in addition to any new roles in the request body. Failure to include any existing roles in the request body removes them from the **appRoles** object. Also, you can add as many roles as your organization needs. The value of these roles is sent as the claim value in the SAML response. To generate the GUID values for the ID of new roles use the web tools, such as the [Online GUID / UUID Generator](https://www.guidgenerator.com/). The appRoles property in the response includes what was in the request body of the query.

## Edit attributes

Update the attributes to define the role claim that is included in the token.

1. Locate the application in the Microsoft Entra admin center, and then select **Single sign-on** in the left menu.
2. In the **Attributes & Claims** section, select **Edit**.
3. Select **Add new claim**.
4. In the **Name** box, type the attribute name. This example uses **Role Name** as the claim name.
5. Leave the **Namespace** box blank.
6. From the **Source attribute** list, select **user.assignedroles**.
7. Select **Save**. The new **Role Name** attribute should now appear in the **Attributes & Claims** section. The claim should now be included in the access token when signing into the application.

## Assign roles

After the service principal is patched with more roles, you can assign users to the respective roles.

1. Locate the application to which the role was added in the Microsoft Entra admin center.
2. Select **Users and groups** in the left menu and then select the user that you want to assign the new role.
3. Select **Edit assignment** at the top of the pane to change the role.
4. Select **None Selected**, select the role from the list, and then select **Select**.
5. Select **Assign** to assign the role to the user.

## Update roles

To update an existing role, perform the following steps:

1. Open [Microsoft Graph Explorer](https://developer.microsoft.com/graph/graph-explorer).
2. Sign in to the Graph Explorer site as a Privileged Role Administrator.
3. Using the object ID for the application from the overview pane, replace `<objectID>` in the following request with it and then run the query:

   `https://graph.microsoft.com/v1.0/servicePrincipals/<objectID>`
4. Record the **appRoles** property from the service principal object that was returned.
5. In Graph Explorer, change the method from **GET** to **PATCH**.
6. Copy the appRoles property that was previously recorded into the **Request body** pane of Graph Explorer, add update the role definition, and then select **Run Query** to execute the patch operation.

## Delete roles

To delete an existing role, perform the following steps:

1. Open [Microsoft Graph Explorer](https://developer.microsoft.com/graph/graph-explorer).
2. Sign in to the Graph Explorer site as a Privileged Role Administrator.
3. Using the object ID for the application from the overview pane in the Azure portal, replace `<objectID>` in the following request with it and then run the query:

   `https://graph.microsoft.com/v1.0/servicePrincipals/<objectID>`
4. Record the **appRoles** property from the service principal object that was returned.
5. In Graph Explorer, change the method from **GET** to **PATCH**.
6. Copy the appRoles property that was previously recorded into the **Request body** pane of Graph Explorer, set the **IsEnabled** value to **false** for the role that you want to delete, and then select **Run Query** to execute the patch operation. A role must be disabled before it can be deleted.
7. After the role is disabled, delete that role block from the **appRoles** section. Keep the method as **PATCH**, and select **Run Query** again.

## Next steps

- For information about customizing claims, see [Customize claims issued in the SAML token for enterprise applications](https://learn.microsoft.com/en-us/entra/identity-platform/saml-claims-customization).
