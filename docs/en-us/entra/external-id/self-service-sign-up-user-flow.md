<!-- Source: https://learn.microsoft.com/en-us/entra/external-id/self-service-sign-up-user-flow -->
<!-- Sitemap-Last-Modified: 2026-08-24 -->

# Add self-service sign-up user flows for B2B collaboration

**Applies to**: ![Green circle with a white check mark symbol that indicates the following content applies to workforce tenants.](https://learn.microsoft.com/en-us/entra/external-id/media/common/applies-to-yes.png) Workforce tenants \([learn more](https://learn.microsoft.com/en-us/entra/external-id/tenant-configurations)\)

Tip

This article applies to B2B collaboration user flows in workforce tenants. For information about external tenants, see [Create a sign-up and sign-in user flow](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-user-flow-sign-up-sign-in-customers).

For applications you build, you can create user flows that allow a user to sign up for an app and create a new guest account. A self-service sign-up user flow defines the series of steps the user follows during sign-up, the [identity providers](https://learn.microsoft.com/en-us/entra/external-id/identity-providers) you allow them to use, and the user attributes you want to collect. You can associate one or more applications with a single user flow.

Note

You can associate user flows with apps built by your organization. User flows can't be used for Microsoft apps, like SharePoint or Teams.

## Prerequisites

Before you begin, you might need to add identity providers and define custom attributes.

### Add identity providers \(optional\)

Microsoft Entra ID is the default identity provider for self-service sign-up. This means users can sign up by default with a Microsoft Entra account. In your self-service sign-up user flows, you can also include social identity providers like Google and Facebook, Microsoft Account, and the email one-time passcode feature. For more information, see these articles:

- [Add Google to your list of social identity providers](https://learn.microsoft.com/en-us/entra/external-id/google-federation)
- [Add Facebook to your list of social identity providers](https://learn.microsoft.com/en-us/entra/external-id/facebook-federation)
- [Add Microsoft account as an identity provider](https://learn.microsoft.com/en-us/entra/external-id/microsoft-account)
- [Email one-time passcode authentication](https://learn.microsoft.com/en-us/entra/external-id/one-time-passcode)

### Define custom attributes \(optional\)

User attributes are values collected from the user during self-service sign-up. Microsoft Entra External ID comes with a built-in set of attributes, but you can create custom attributes for use in your user flow. You can also read and write these attributes by using the Microsoft Graph API. See [Define custom attributes for user flows](https://learn.microsoft.com/en-us/entra/external-id/user-flow-add-custom-attributes).

## Enable self-service sign-up for your tenant

Before you can add a self-service sign-up user flow to your applications, you need to enable the feature for your tenant. Then controls become available that let you associate the user flow with an application.

Note

This setting can also be configured with the [authenticationFlowsPolicy](https://learn.microsoft.com/en-us/graph/api/resources/authenticationflowspolicy?view=graph-rest-1.0&preserve-view=true) resource type in the Microsoft Graph API.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [User Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#user-administrator).
2. Browse to **Entra ID** > **External Identities** > **External collaboration settings**.
3. Set the **Enable guest self-service sign up via user flows** toggle to **Yes**.

   ![Screenshot of the enable guest self-service sign-up toggle.](https://learn.microsoft.com/en-us/entra/external-id/media/self-service-sign-up-user-flow/enable-self-service-sign-up.png)
4. Select **Save**.

## Create the user flow for self-service sign-up

Next, you create the user flow for self-service sign-up and add it to an application.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [User Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#user-administrator).
2. Browse to **Entra ID** > **External Identities** > **User flows**, and then select **New user flow**.

   ![Screenshot of the new user flow button.](https://learn.microsoft.com/en-us/entra/external-id/media/self-service-sign-up-user-flow/new-user-flow.png)
3. On the **Create** page, enter a **Name** for the user flow. The name is automatically prefixed with **B2X\_1\_**.
4. In the **Identity providers** list, select one or more identity providers that your external users can use to log into your application. \(See *Before you begin* earlier in this article to learn how to add identity providers.\)
5. Under **User attributes**, choose the attributes you want to collect from the user. For more attributes, select **Show more**. For example, select **Show more**, and then choose attributes and claims for **Country/Region**, **Display Name**, and **Postal Code**. Select **OK**.

   ![Screenshot of the new user flow creation page.](https://learn.microsoft.com/en-us/entra/external-id/media/self-service-sign-up-user-flow/create-user-flow.png)

   Note

   You can only collect attributes when a user signs up for the first time. After a user signs up, they're no longer prompted to collect attribute information, even if you change the user flow.
6. Select **Create**.
7. The new user flow appears in the **User flows** list. If necessary, refresh the page.

## Select the layout of the attribute collection form

You can choose the order in which the attributes are displayed on the sign-up page.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [User Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#user-administrator).
2. Browse to **Entra ID** > **External Identities** > **User flows**.
3. Select the self-service sign-up user flow from the list.
4. Under **Customize**, select **Page layouts**.
5. The attributes you chose to collect are listed. To change the order of display, select an attribute, and then select **Move up**, **Move down**, **Move to top**, or **Move to bottom**.
6. Select **Save**.

## Add applications to the self-service sign-up user flow

Now you associate applications with the user flow to enable sign-up for those applications. New users who access the associated applications are presented with your new self-service sign-up experience.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [User Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#user-administrator).
2. Browse to **Entra ID** > **External Identities** > **User flows**
3. Select the self-service sign-up user flow from the list.
4. In the left menu, under **Use**, select **Applications**.
5. Select **Add application**.

   ![Screenshot of adding an application to the user flow.](https://learn.microsoft.com/en-us/entra/external-id/media/self-service-sign-up-user-flow/assign-app-to-user-flow.png)
6. Select the application from the list. Or use the search box to find the application, and then select it.
7. Choose **Select**.

## Related content

- [Add Google to your list of social identity providers](https://learn.microsoft.com/en-us/entra/external-id/google-federation)
- [Add Facebook to your list of social identity providers](https://learn.microsoft.com/en-us/entra/external-id/facebook-federation)
- [Use API connectors to customize and extend your user flows via web APIs](https://learn.microsoft.com/en-us/entra/external-id/api-connectors-overview)
