<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/header-citrix-netscaler-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-25 -->

# Configure Citrix ADC \(header-based authentication\) for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Citrix ADC with Microsoft Entra ID. When you integrate Citrix ADC with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Citrix ADC.
- Enable your users to be automatically signed-in to Citrix ADC with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- Citrix ADC single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment. The article includes these scenarios:

- **SP-initiated** SSO for Citrix ADC
- **Just in time** user provisioning for Citrix ADC
- [Header-based authentication for Citrix ADC](#publish-the-web-server)
- [Kerberos-based authentication for Citrix ADC](https://learn.microsoft.com/en-us/entra/identity/saas-apps/citrix-netscaler-tutorial#publish-the-web-server)

## Add Citrix ADC from the gallery

To integrate Citrix ADC with Microsoft Entra ID, first add Citrix ADC to your list of managed SaaS apps from the gallery:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, enter **Citrix ADC** in the search box.
4. In the results, select **Citrix ADC**, and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure and test Microsoft Entra SSO for Citrix ADC

Configure and test Microsoft Entra SSO with Citrix ADC by using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Citrix ADC.

To configure and test Microsoft Entra SSO with Citrix ADC, perform the following steps:

1. [Configure Microsoft Entra SSO](#configure-azure-ad-sso) - to enable your users to use this feature.

   1. Create a Microsoft Entra test user - to test Microsoft Entra SSO with B.Simon.
   2. Assign the Microsoft Entra test user - to enable B.Simon to use Microsoft Entra SSO.

2. [Configure Citrix ADC SSO](#configure-citrix-adc-sso) - to configure the SSO settings on the application side.

   - [Create a Citrix ADC test user](#create-a-citrix-adc-test-user) - to have a counterpart of B.Simon in Citrix ADC that's linked to the Microsoft Entra representation of the user.

3. [Test SSO](#test-sso) - to verify whether the configuration works.

## Configure Microsoft Entra SSO

To enable Microsoft Entra SSO by using the Azure portal, complete these steps:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Citrix ADC** application integration pane, under **Manage**, select **Single sign-on**.
3. On the **Select a single sign-on method** pane, select **SAML**.
4. On the **Set up Single Sign-On with SAML** pane, select the pen **Edit** icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. In the **Basic SAML Configuration** section, to configure the application in **IDP-initiated** mode:

   1. In the **Identifier** text box, enter a URL that has the following pattern: `https://<Your FQDN>`
   2. In the **Reply URL** text box, enter a URL that has the following pattern: `https://<Your FQDN>/CitrixAuthService/AuthService.asmx`

6. To configure the application in **SP-initiated** mode, select **Set additional URLs** and complete the following step:

   - In the **Sign-on URL** text box, enter a URL that has the following pattern: `https://<Your FQDN>/CitrixAuthService/AuthService.asmx`


   Note


   - The URLs that are used in this section aren't real values. Update these values with the actual values for Identifier, Reply URL, and Sign-on URL. Contact the [Citrix ADC client support team](https://www.citrix.com/contact/technical-support.html) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.
   - To set up SSO, the URLs must be accessible from public websites. You must enable the firewall or other security settings on the Citrix ADC side to enable Microsoft Entra ID to post the token at the configured URL.

7. On the **Set up Single Sign-On with SAML** pane, in the **SAML Signing Certificate** section, for **App Federation Metadata Url**, copy the URL and save it in Notepad.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/certificatebase64.png)

8. The Citrix ADC application expects SAML assertions to be in a specific format, which requires you to add custom attribute mappings to your SAML token attributes configuration. The following screenshot shows the list of default attributes. Select the **Edit** icon and change the attribute mappings.

   ![Edit the SAML attribute mapping](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-attribute.png)

9. The Citrix ADC application also expects a few more attributes to be passed back in the SAML response. In the **User Attributes** dialog box, under **User Claims**, complete the following steps to add the SAML token attributes as shown in the table:
   | Name | Source attribute |
   | --- | --- |
   | mySecretID | user.userprincipalname |


   1. Select **Add new claim** to open the **Manage user claims** dialog box.
   2. In the **Name** text box, enter the attribute name that's shown for that row.
   3. Leave the **Namespace** blank.
   4. For **Attribute**, select **Source**.
   5. In the **Source attribute** list, enter the attribute value that's shown for that row.
   6. Select **OK**.
   7. Select **Save**.

10. In the **Set up Citrix ADC** section, copy the relevant URLs based on your requirements.

    ![Copy configuration URLs](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png)

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

### Assign the Microsoft Entra test user

In this section, you enable the user B.Simon to use Azure SSO by granting the user access to Citrix ADC.

1. Browse to **Entra ID** > **Enterprise apps**.
2. In the applications list, select **Citrix ADC**.
3. On the app overview, under **Manage**, select **Users and groups**.
4. Select **Add user**. Then, in the **Add Assignment** dialog box, select **Users and groups**.
5. In the **Users and groups** dialog box, select **B.Simon** from the **Users** list. Choose **Select**.
6. If you're expecting a role to be assigned to the users, you can select it from the **Select a role** dropdown. If no role has been set up for this app, you see "Default Access" role selected.
7. In the **Add Assignment** dialog box, select **Assign**.

## Configure Citrix ADC SSO

Select a link for steps for the kind of authentication you want to configure:

- [Configure Citrix ADC SSO for header-based authentication](#publish-the-web-server)
- [Configure Citrix ADC SSO for Kerberos-based authentication](https://learn.microsoft.com/en-us/entra/identity/saas-apps/citrix-netscaler-tutorial#publish-the-web-server)

### Publish the web server

To create a virtual server:

1. Select **Traffic Management** > **Load Balancing** > **Services**.
2. Select **Add**.

   ![Citrix ADC configuration - Services pane](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/header-citrix-netscaler-tutorial/web01.png)

3. Set the following values for the web server that's running the applications:

   - **Service Name**
   - **Server IP/ Existing Server**
   - **Protocol**
   - **Port**

     ![Citrix ADC configuration pane](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/header-citrix-netscaler-tutorial/web01.png)

### Configure the load balancer

To configure the load balancer:

1. Go to **Traffic Management** > **Load Balancing** > **Virtual Servers**.
2. Select **Add**.
3. Set the following values as described in the following screenshot:

   - **Name**
   - **Protocol**
   - **IP Address**
   - **Port**

4. Select **OK**.

   ![Citrix ADC configuration - Basic Settings pane](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/header-citrix-netscaler-tutorial/load01.png)

### Bind the virtual server

To bind the load balancer with the virtual server:

1. In the **Services and Service Groups** pane, select **No Load Balancing Virtual Server Service Binding**.

   ![Citrix ADC configuration - Load Balancing Virtual Server Service Binding pane](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/header-citrix-netscaler-tutorial/bind01.png)

2. Verify the settings as shown in the following screenshot, and then select **Close**.

   ![Citrix ADC configuration - Verify the virtual server services binding](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/header-citrix-netscaler-tutorial/bind02.png)

### Bind the certificate

To publish this service as TLS, bind the server certificate, and then test your application:

1. Under **Certificate**, select **No Server Certificate**.

   ![Citrix ADC configuration - Server Certificate pane](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/header-citrix-netscaler-tutorial/bind03.png)

2. Verify the settings as shown in the following screenshot, and then select **Close**.

   ![Citrix ADC configuration - Verify the certificate](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/header-citrix-netscaler-tutorial/bind04.png)

## Citrix ADC SAML profile

To configure the Citrix ADC SAML profile, complete the following sections:

### Create an authentication policy

To create an authentication policy:

1. Go to **Security** > **AAA – Application Traffic** > **Policies** > **Authentication** > **Authentication Policies**.
2. Select **Add**.
3. On the **Create Authentication Policy** pane, enter or select the following values:

   - **Name**: Enter a name for your authentication policy.
   - **Action**: Enter **SAML**, and then select **Add**.
   - **Expression**: Enter **true**.


   ![Citrix ADC configuration - Create Authentication Policy pane](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/header-citrix-netscaler-tutorial/policy01.png)

4. Select **Create**.

### Create an authentication SAML server

To create an authentication SAML server, go to the **Create Authentication SAML Server** pane, and then complete the following steps:

1. For **Name**, enter a name for the authentication SAML server.
2. Under **Export SAML Metadata**:

   1. Select the **Import Metadata** check box.
   2. Enter the federation metadata URL from the Azure SAML UI that you copied earlier.

3. For **Issuer Name**, enter the relevant URL.
4. Select **Create**.

![Citrix ADC configuration - Create Authentication SAML Server pane](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/header-citrix-netscaler-tutorial/server01.png)

### Create an authentication virtual server

To create an authentication virtual server:

1. Go to **Security** > **AAA - Application Traffic** > **Policies** > **Authentication** > **Authentication Virtual Servers**.
2. Select **Add**, and then complete the following steps:

   1. For **Name**, enter a name for the authentication virtual server.
   2. Select the **Non-Addressable** check box.
   3. For **Protocol**, select **SSL**.
   4. Select **OK**.


   ![Citrix ADC configuration - Authentication Virtual Server pane](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/header-citrix-netscaler-tutorial/server02.png)

### Configure the authentication virtual server to use Microsoft Entra ID

Modify two sections for the authentication virtual server:

1. On the **Advanced Authentication Policies** pane, select **No Authentication Policy**.

   ![Citrix ADC configuration - Advanced Authentication Policies pane](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/header-citrix-netscaler-tutorial/virtual01.png)

2. On the **Policy Binding** pane, select the authentication policy, and then select **Bind**.

   ![Citrix ADC configuration - Policy Binding pane](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/header-citrix-netscaler-tutorial/virtual02.png)

3. On the **Form Based Virtual Servers** pane, select **No Load Balancing Virtual Server**.

   ![Citrix ADC configuration - Form Based Virtual Servers pane](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/header-citrix-netscaler-tutorial/virtual03.png)

4. For **Authentication FQDN**, enter a fully qualified domain name \(FQDN\) \(required\).
5. Select the load balancing virtual server that you want to protect with Microsoft Entra authentication.
6. Select **Bind**.

   ![Citrix ADC configuration - Load Balancing Virtual Server Binding pane](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/header-citrix-netscaler-tutorial/virtual04.png)


   Note


   Be sure to select **Done** on the **Authentication Virtual Server Configuration** pane.

7. To verify your changes, in a browser, go to the application URL. You should see your tenant sign-in page instead of the unauthenticated access that you would have seen previously.

   ![Citrix ADC configuration - A sign-in page in a web browser](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/header-citrix-netscaler-tutorial/virtual05.png)

## Configure Citrix ADC SSO for header-based authentication

### Configure Citrix ADC

To configure Citrix ADC for header-based authentication, complete the following sections.

#### Create a rewrite action

1. Go to **AppExpert** > **Rewrite** > **Rewrite Actions**.

   ![Citrix ADC configuration - Rewrite Actions pane](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/header-citrix-netscaler-tutorial/header01.png)

2. Select **Add**, and then complete the following steps:

   1. For **Name**, enter a name for the rewrite action.
   2. For **Type**, enter **INSERT\_HTTP\_HEADER**.
   3. For **Header Name**, enter a header name \(in this example, we use *SecretID*\).
   4. For **Expression**, enter **aaa.USER.ATTRIBUTE\("mySecretID"\)**, where **mySecretID** is the Microsoft Entra SAML claim that was sent to Citrix ADC.
   5. Select **Create**.


   ![Citrix ADC configuration - Create Rewrite Action pane](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/header-citrix-netscaler-tutorial/header02.png)

#### Create a rewrite policy

1. Go to **AppExpert** > **Rewrite** > **Rewrite Policies**.

   ![Citrix ADC configuration - Rewrite Policies pane](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/header-citrix-netscaler-tutorial/header03.png)

2. Select **Add**, and then complete the following steps:

   1. For **Name**, enter a name for the rewrite policy.
   2. For **Action**, select the rewrite action you created in the preceding section.
   3. For **Expression**, enter **true**.
   4. Select **Create**.


   ![Citrix ADC configuration - Create Rewrite Policy pane](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/header-citrix-netscaler-tutorial/header04.png)

### Bind a rewrite policy to a virtual server

To bind a rewrite policy to a virtual server by using the GUI:

1. Go to **Traffic Management** > **Load Balancing** > **Virtual Servers**.
2. In the list of virtual servers, select the virtual server to which you want to bind the rewrite policy, and then select **Open**.
3. On the **Load Balancing Virtual Server** pane, under **Advanced Settings**, select **Policies**. All policies that are configured for your NetScaler instance appear in the list. ![Citrix ADC configuration - Load Balancing Virtual Server pane](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/header-citrix-netscaler-tutorial/header06.png)
4. Select the check box next to the name of the policy you want to bind to this virtual server.

   ![Citrix ADC configuration - Load Balancing Virtual Server Traffic Policy Binding pane](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/header-citrix-netscaler-tutorial/header08.png)

5. In the **Choose Type** dialog box:

   1. For **Choose Policy**, select **Traffic**.
   2. For **Choose Type**, select **Request**.


   ![Citrix ADC configuration - Policies dialog box](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/header-citrix-netscaler-tutorial/header07.png)

6. Select **OK**. A message in the status bar indicates that the policy has been configured successfully.

### Modify the SAML server to extract attributes from a claim

1. Go to **Security** > **AAA - Application Traffic** > **Policies** > **Authentication** > **Advanced Policies** > **Actions** > **Servers**.
2. Select the appropriate authentication SAML server for the application.

   ![Citrix ADC configuration - Configure Authentication SAML Server pane](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/header-citrix-netscaler-tutorial/header09.png)

3. In the **Attributes** pain, enter the SAML attributes that you want to extract, separated by commas. In our example, we enter the attribute `mySecretID`.

   ![Citrix ADC configuration - Attributes pane](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/header-citrix-netscaler-tutorial/header10.png)

4. To verify access, at the URL in a browser, look for the SAML attribute under **Headers Collection**.

   ![Citrix ADC configuration - Headers Collection at the URL](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/header-citrix-netscaler-tutorial/header11.png)

### Create a Citrix ADC test user

In this section, a user called B.Simon is created in Citrix ADC. Citrix ADC supports just-in-time user provisioning, which is enabled by default. There's no action for you to take in this section. If a user doesn't already exist in Citrix ADC, a new one is created after authentication.

Note

If you need to create a user manually, contact the [Citrix ADC client support team](https://www.citrix.com/contact/technical-support.html).

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application**, this option redirects to Citrix ADC Sign-on URL where you can initiate the login flow.
- Go to Citrix ADC Sign-on URL directly and initiate the login flow from there.
- You can use Microsoft My Apps. When you select the Citrix ADC tile in the My Apps, this option redirects to Citrix ADC Sign-on URL. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

Once you configure Citrix ADC you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-any-app).
