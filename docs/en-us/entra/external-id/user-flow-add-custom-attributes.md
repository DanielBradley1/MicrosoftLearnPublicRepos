<!-- Source: https://learn.microsoft.com/en-us/entra/external-id/user-flow-add-custom-attributes -->
<!-- Sitemap-Last-Modified: 2026-04-17 -->

# Collect custom user attributes during B2B collaboration sign-up

**Applies to**: ![Green circle with a white check mark symbol that indicates the following content applies to workforce tenants.](https://learn.microsoft.com/en-us/entra/external-id/media/common/applies-to-yes.png) Workforce tenants \([learn more](https://learn.microsoft.com/en-us/entra/external-id/tenant-configurations)\)

Tip

This article applies to B2B collaboration user flows in workforce tenants. For information about external tenants, see [Collect custom user attributes during external tenant sign-up](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-define-custom-attributes).

For each application, you might have different requirements for the information you want to collect during sign-up. Microsoft Entra External ID comes with a built-in set of information stored in attributes, such as Given Name, Surname, City, and Postal Code. With Microsoft Entra External ID, you can extend the set of attributes stored on a guest account when the external user signs up through a user flow.

You can create custom attributes in the Microsoft Entra admin center and use them in your [self-service sign-up user flows](https://learn.microsoft.com/en-us/entra/external-id/self-service-sign-up-user-flow). You can also read and write these attributes by using the [Microsoft Graph API](https://learn.microsoft.com/en-us/azure/active-directory-b2c/microsoft-graph-operations). Microsoft Graph API supports creating and updating a user with extension attributes. Extension attributes in the Graph API are named by using the convention `extension_<extensions-app-id>_attributename`. For example:

```JSON
"extension_831374b3bd5041bfaa54263ec9e050fc_loyaltyNumber": "212342"
```

The `<extensions-app-id>` is specific to your tenant. To find this identifier, navigate to **Entra ID** > **App registrations** > **All applications**. Search for the app that starts with "aad-extensions-app" and select it. On the app's Overview page, note the Application \(client\) ID.

## Create a custom attribute

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [User Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#user-administrator).
2. Browse to **Entra ID** > **External identities** > **Overview**.
3. Select **Custom user attributes**. The available user attributes are listed.

   [![Screenshot of the External identities overview page in the Microsoft Entra admin center, with Custom user attributes selected.](https://learn.microsoft.com/en-us/entra/external-id/media/user-flow-add-custom-attributes/user-attributes.png)](https://learn.microsoft.com/en-us/entra/external-id/media/user-flow-add-custom-attributes/user-attributes.png#lightbox)
4. To add an attribute, select **Add**.
5. In the **Add an attribute** pane, enter the following values:

   - **Name** - Provide a name for the custom attribute \(for example, "Shoe size"\).
   - **Data Type** - Choose a data type \(**String**, **Boolean**, or **Int**\).
   - **Description** - Optionally, enter a description of the custom attribute for internal use. This description isn't visible to the user.


   ![Screenshot of the Add an attribute pane showing Name, Data Type, and Description fields before creating a custom user attribute.](https://learn.microsoft.com/en-us/entra/external-id/media/user-flow-add-custom-attributes/add-an-attribute.png)

6. Select **Create**.

When you add a custom attribute to the list of user attributes, it becomes available for use in your user flows. However, the attribute is only created the first time it’s used in any user flow. Once you’ve created a new user through a user flow that includes the newly added custom attribute, the object can be queried in [Microsoft Graph Explorer](https://developer.microsoft.com/graph/graph-explorer). You should now see **ShoeSize** in the list of attributes collected during the sign-up journey on the user object. You can call the Graph API from your application to get the data from this attribute after it's added to the user object.

## Next steps

- [Add a self-service sign-up user flow to an app](https://learn.microsoft.com/en-us/entra/external-id/self-service-sign-up-user-flow)
- [Customize the user flow language](https://learn.microsoft.com/en-us/entra/external-id/user-flow-customize-language)
