<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/mimecast-personal-portal-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-25 -->

# Configure Mimecast for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Mimecast with Microsoft Entra ID. When you integrate Mimecast with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Mimecast.
- Enable your users to be automatically signed-in to Mimecast with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- Mimecast single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- Mimecast supports **SP and IDP** initiated SSO.

## Add Mimecast from the gallery

To configure the integration of Mimecast into Microsoft Entra ID, you need to add Mimecast from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Mimecast** in the search box.
4. Select **Mimecast** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards.](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides)

## Configure and test Microsoft Entra SSO for Mimecast

Configure and test Microsoft Entra SSO with Mimecast using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Mimecast.

To configure and test Microsoft Entra SSO with Mimecast, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure Mimecast SSO](#configure-mimecast-sso)** - to configure the single sign-on settings on application side.

   1. **[Create Mimecast test user](#create-mimecast-test-user)** - to have a counterpart of B.Simon in Mimecast that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Mimecast** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section, if you wish to configure the application in IDP initiated mode, perform the following steps:

   a. In the **Identifier** textbox, type a URL using one of the following patterns:

   | Region | Value |
   | --- | --- |
   | Europe | `https://eu-api.mimecast.com/sso/<accountcode>` |
   | United States | `https://us-api.mimecast.com/sso/<accountcode>` |
   | South Africa | `https://za-api.mimecast.com/sso/<accountcode>` |
   | Australia | `https://au-api.mimecast.com/sso/<accountcode>` |
   | Offshore | `https://jer-api.mimecast.com/sso/<accountcode>` |


   Note


   You find the `accountcode` value in the Mimecast under **Account** > **Settings** > **Account Code**. Append the `accountcode` to the Identifier.


   b. In the **Reply URL** textbox, type one of the following URLs:


   | Region | Value |
   | --- | --- |
   | Europe | `https://eu-api.mimecast.com/login/saml` |
   | United States | `https://us-api.mimecast.com/login/saml` |
   | South Africa | `https://za-api.mimecast.com/login/saml` |
   | Australia | `https://au-api.mimecast.com/login/saml` |
   | Offshore | `https://jer-api.mimecast.com/login/saml` |

6. If you wish to configure the application in **SP** initiated mode:

   In the **Sign-on URL** textbox, type one of the following URLs:

   | Region | Value |
   | --- | --- |
   | Europe | `https://eu-api.mimecast.com/login/saml` |
   | United States | `https://us-api.mimecast.com/login/saml` |
   | South Africa | `https://za-api.mimecast.com/login/saml` |
   | Australia | `https://au-api.mimecast.com/login/saml` |
   | Offshore | `https://jer-api.mimecast.com/login/saml` |

7. Select **Save**.
8. On the **Set up single sign-on with SAML** page, In the **SAML Signing Certificate** section, select copy button to copy **App Federation Metadata Url** and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-metadataurl.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure Mimecast SSO

1. In a different web browser window, sign into Mimecast Administration Console.
2. Navigate to **Administration** > **Services** > **Applications**.

   ![Screenshot shows Mimecast window with Applications selected.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/mimecast-personal-portal-tutorial/services.png)

3. Select **Authentication Profiles** tab.

   ![Screenshot shows the Application tab with Authentication Profiles selected.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/mimecast-personal-portal-tutorial/authentication-profiles.png)

4. Select **New Authentication Profile** tab.

   ![Screenshot shows new Authentication Profile selected.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/mimecast-personal-portal-tutorial/new-authenticatio-profile.png)

5. Provide a valid description in the **Description** textbox and select **Enforce SAML Authentication for Mimecast** checkbox.

   ![Screenshot shows New Authentication Profile selected.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/mimecast-personal-portal-tutorial/selecting-personal-portal.png)

6. On the **SAML Configuration for Mimecast** page, perform the following steps:

   ![Screenshot shows where to select Enforce SAML Authentication for Administration Console.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/mimecast-personal-portal-tutorial/sso-settings.png)


   a. For **Provider**, select **Microsoft Entra ID** from the Dropdown.


   b. In the **Metadata URL** textbox, paste the **App Federation Metadata URL** value, which you copied previously.


   c. Select **Import**. After importing the Metadata URL, the fields are populated automatically, no need to perform any action on these fields.


   d. Make sure you uncheck **Use Password protected Context** and **Use Integrated Authentication Context** checkboxes.


   e. Select **Save**.

### Create Mimecast test user

1. In a different web browser window, sign into Mimecast Administration Console.
2. Navigate to **Administration** > **Directories** > **Internal Directories**.

   ![Screenshot shows the SAML Configuration for Mimecast where you can enter the values described.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/mimecast-personal-portal-tutorial/internal-directories.png)

3. Select your domain, if the domain is mentioned below, otherwise please create a new domain by selecting the **New Domain**.

   ![Screenshot shows Mimecast window with Internal Directories selected.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/mimecast-personal-portal-tutorial/domain-name.png)

4. Select **New Address** tab.

   ![Screenshot shows the domain selected.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/mimecast-personal-portal-tutorial/new-address.png)

5. Provide the required user information on the following page:

   ![Screenshot shows the page where you can enter the values described.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/mimecast-personal-portal-tutorial/user-information.png)


   a. In the **Email Address** textbox, enter the email address of the user like `B.Simon@yourdomainname.com`.


   b. In the **Global Name** textbox, enter the **Full name** of the user.


   c. In the **Password** and **Confirm Password** textboxes, enter the password of the user.


   d. Select **Force Change at Login** checkbox.


   e. Select **Save**.


   f. To assign roles to the user, select **Role Edit** and assign the required role to user as per your organization requirement.


   ![Screenshot shows Address Settings where you can select Role Edit.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/mimecast-personal-portal-tutorial/assign-role.png)

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

#### SP initiated:

- Select **Test this application**, this option redirects to Mimecast Sign on URL where you can initiate the login flow.
- Go to Mimecast Sign-on URL directly and initiate the login flow from there.

#### IDP initiated:

- Select **Test this application**, and you should be automatically signed in to the Mimecast for which you set up the SSO.

You can also use Microsoft My Apps to test the application in any mode. When you select the Mimecast tile in the My Apps, if configured in SP mode you would be redirected to the application sign on page for initiating the login flow and if configured in IDP mode, you should be automatically signed in to the Mimecast for which you set up the SSO. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

Once you configure Mimecast you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-any-app).
