<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/trend-micro-tutorial -->
<!-- Sitemap-Last-Modified: 2025-05-20 -->

# Configure Trend Micro Web Security \(TMWS\) for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Trend Micro Web Security \(TMWS\) with Microsoft Entra ID. When you integrate TMWS with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to TMWS.
- Enable your users to be automatically signed in to TMWS with their Microsoft Entra accounts.
- Manage your accounts in one central location: the Azure portal.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- A TMWS subscription that's enabled for SSO.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- TMWS supports **SP** initiated SSO.

## Add TMWS from the gallery

To configure the integration of TMWS into Microsoft Entra ID, you need to add TMWS from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, enter **Trend Micro Web Security \(TMWS\)** in the search box.
4. Select **Trend Micro Web Security \(TMWS\)** in the search results and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards.](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides)

## Configure and test Microsoft Entra SSO for TMWS

You'll configure and test Microsoft Entra SSO with TMWS by using a test user called B.Simon. For SSO to work, you need to establish a link between a Microsoft Entra user and the related user in TMWS.

You'll complete these basic steps to configure and test Microsoft Entra SSO with TMWS:

1. [Configure Microsoft Entra SSO](#configure-azure-ad-sso) to enable the feature for your users.

   1. [Create a Microsoft Entra user](#create-an-azure-ad-test-user) to test Microsoft Entra single sign-on.
   2. [Grant the Microsoft Entra test user](#grant-the-azure-ad-test-user-access-to-tmws) access to TMWS.
   3. [Configure user and group synchronization settings in Microsoft Entra ID](#configure-user-and-group-synchronization-settings-in-azure-ad).

2. [Configure TMWS SSO](#configure-tmws-sso) on the application side.
3. [Test SSO](#test-sso) to verify the configuration.

## Configure Microsoft Entra SSO

Complete these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Trend Micro Web Security \(TMWS\)** application integration page, in the **Manage** section, select **single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up Single Sign-On with SAML** page, select the pen button for **Basic SAML Configuration** to edit the settings:

   ![Edit the Basic SAML Configuration settings](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. In the **Basic SAML Configuration** section, enter values in the following boxes:

   a. In the **Identifier \(Entity ID\)** box, enter a URL in the following pattern:

   `https://auth.iws-hybrid.trendmicro.com/([0-9a-f]{16})`

   b. In the **Reply URL** box, enter this URL:

   `https://auth.iws-hybrid.trendmicro.com/simplesaml/module.php/saml/sp/saml2-acs.php/ics-sp`

   Note

   The identifier value in the previous step isn't the value that you should enter. You need to use the actual identifier. You can get this value in the **Service Provider Settings for the Azure Admin Portal** section on the **Authentication Method** page for Microsoft Entra ID from **Administration > Directory Services**.
6. TMWS expects the SAML assertions in a specific format, so you need to add custom attribute mappings to your SAML token attributes configuration. This screenshot shows the default attributes:

   ![Default attributes](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/default-attributes.png)

7. In addition to the attributes in the preceding screenshot, TMWS expects two more attributes to be passed back in the SAML response. These attributes are shown in the following table. The attributes are pre-populated, but you can change them to meet your requirements.
   | Name | Source attribute |
   | --- | --- |
   | `sAMAccountName` | `user.onpremisessamaccountname` |
   | `upn` | `user.userprincipalname` |
8. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section, find **Certificate \(Base64\)**. Select the **Download** link next to this certificate name to download the certificate and save it on your computer:

   ![Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/certificatebase64.png)

9. In the **Set up Trend Micro Web Security \(TMWS\)** section, copy the appropriate URL or URLs, based on your requirements:

   ![Copy the configuration URLs](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png)

### Create a Microsoft Entra test user

In this section, you create a test user called B.Simon.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [User Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#user-administrator).
2. Browse to **Entra ID** > **Users**.
3. Select **New user** > **Create new user**, at the top of the screen.
4. In the **User** properties, follow these steps:

   1. In the **Display name** field, enter `B.Simon`.
   2. In the **User principal name** field, enter the username@companydomain.extension. For example, `B.Simon@contoso.com`.
   3. Select the **Show password** check box, and then write down the value that's displayed in the **Password** box.
   4. Select **Review + create**.

5. Select **Create**.

### Grant the Microsoft Entra test user access to TMWS

In this section, you enable B.Simon to use single sign-on by granting access to TMWS.

1. Browse to **Entra ID** > **Enterprise apps**.
2. In the applications list, select **Trend Micro Web Security \(TMWS\)**.
3. In the app's overview page, in the **Manage** section, select **Users and groups**:
4. Select **Add user**, and then select **Users and groups** in the **Add Assignment** dialog box.
5. In the **Users and groups** dialog box, select **B.Simon** in the **Users** list, and then select the **Select** button at the bottom of the screen.
6. If you expect a role value in the SAML assertion, in the **Select Role** dialog box, select the appropriate role for the user from the list and then select the **Select** button at the bottom of the screen.
7. In the **Add Assignment** dialog box, select **Assign**.

### Configure user and group synchronization settings in Microsoft Entra ID

1. In the left pane, select **Microsoft Entra ID**.
2. Under **Manage**, select **App registrations**, and then select your new enterprise application under **All applications**.
3. Under **Manage**, select **Certificates & secrets**.
4. In the **Client secrets** area, select **New client secret**.
5. On the **Add a client secret screen**, optionally add a description and select an expiration period for the client secret, and then select **Add**. The new client secret appears in the **Client secrets** area.
6. Record the client secret value. Later, you enter it into TMWS.
7. Under **Manage**, select **API permissions**.
8. In the **API permissions** window, select **Add a permission**.
9. On the **Microsoft APIs** tab of the **Request API permissions** window, select **Microsoft Graph** and then **Application permissions**.
10. Locate and add these permissions:

    - Group.Read.All
    - User.Read.All

11. Select **Add permissions**. A message appears to confirm that your settings were saved. The new permissions appear in the **API permissions** window.
12. In the **Grant consent** area, select **Grant admin consent for *your administrator account* \(Default Directory\)**, and then select **Yes**. A message appears to confirm that the admin consent for the requested permissions was granted.
13. Select **Overview**.
14. Record the **Application \(client\) ID** and **Directory \(tenant\) ID** that you see in the right pane. Later, you enter that information into TMWS.

## Configure TMWS SSO

Complete these steps to configure TMWS SSO on the application side.

1. Sign in to the TMWS management console, and go to **Administration** > **USERS & AUTHENTICATION** > **Directory Services**.
2. Select **here** on the upper area of the screen.
3. On the **Authentication Method** page, select **Microsoft Entra ID**.
4. Select **On** or **Off** to configure whether to allow Microsoft Entra users in your organization to visit websites through TMWS if their data isn't synchronized to TMWS.

   Note

   Users who aren't synchronized from Microsoft Entra ID can be authenticated only through known TMWS gateways or the dedicated port for your organization.
5. In the **Identity Provider Settings** section, complete these steps:

   a. In the **Service URL** box, enter the **Login URL** value that you copied.

   b. In the **Logon name attribute** box, enter the **User claim name** with the **user.onpremisessamaccountname** source attribute.

   c. In the **Public SSL certificate** box, use the downloaded **Certificate \(Base64\)**.
6. In the **Synchronization Settings** section, complete these steps:

   a. In the **Tenant** box, enter the **Directory \(tenant\) ID** or **Custom domain name** value.

   b. In the **Application ID** box, enter the **Application \(client\) ID** value.

   c. In the **Client secret** box, enter the **Client secret**.

   d. Select **Synchronization schedule** to synchronize with Microsoft Entra ID manually or according to a schedule. If you select **Manually**, whenever there are changes to Active Directory user information, remember to go back to the **Directory Services** page and perform manual synchronization so that information in TMWS remains current.

   e. Select **Test Connection** to check whether the Microsoft Entra service can be successfully connected.

   f. Select **Save**.

Note

For more information on how to configure TMWS with Microsoft Entra ID, see [Configuring Microsoft Entra Settings on TMWS](https://docs.trendmicro.com/en-us/enterprise/trend-micro-web-security-online-help/administration/directory-services/azure-active-directo/configuring-azure-ad.aspx).

## Test SSO

After you configure the Microsoft Entra service and specify Microsoft Entra ID as the user authentication method, you can sign in to the TMWS proxy server to verify your setup. After the Microsoft Entra sign-in verifies your account, you can visit the internet.

Note

TMWS doesn't support testing single sign-on, under **Overview** > **Single sign-on** > **Set up Single Sign-on with SAML** > **Test** of your new enterprise application.

1. Clear the browser of all cookies and then restart the browser.
2. Point your browser to the TMWS proxy server. For details, see [Traffic Forwarding Using PAC Files](https://docs.trendmicro.com/en-us/enterprise/trend-micro-web-security-online-help/administration/pac-files/traffic-forwarding-u.aspx).
3. Visit any internet website. TMWS directs you to the TMWS captive portal.
4. Specify an Active Directory account \(format: *domain*\\*sAMAccountName* or *sAMAccountName*@*domain*\), email address, or UPN, and then select **Log On**. TMWS sends you to the Microsoft Entra sign-in window.
5. In the Microsoft Entra sign-in window, enter your Microsoft Entra account credentials. You should now be signed in to TMWS.

## Related content

Once you configure TMWS you can enforce session control, which protects exfiltration and infiltration of your organization's sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
