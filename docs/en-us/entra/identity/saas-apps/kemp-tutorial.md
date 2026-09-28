<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/kemp-tutorial -->
<!-- Sitemap-Last-Modified: 2026-06-04 -->

# Configure Kemp LoadMaster Microsoft Entra integration for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Kemp LoadMaster Microsoft Entra integration with Microsoft Entra ID. When you integrate Kemp LoadMaster Microsoft Entra integration with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Kemp LoadMaster Microsoft Entra integration.
- Enable your users to be automatically signed-in to Kemp LoadMaster Microsoft Entra integration with their Microsoft Entra accounts.
- Manage your accounts in one central location.

Kemp LoadMaster is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government | China operated by 21Vianet |
| :---: | :---: | :---: |
| ✅ | ✅ |  |

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- Kemp LoadMaster Microsoft Entra integration single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- Kemp LoadMaster Microsoft Entra integration supports **IDP** initiated SSO.

## Add Kemp LoadMaster Microsoft Entra integration from the gallery

To configure the integration of Kemp LoadMaster Microsoft Entra integration into Microsoft Entra ID, you need to add Kemp LoadMaster Microsoft Entra integration from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Kemp LoadMaster Microsoft Entra integration** in the search box.
4. Select **Kemp LoadMaster Microsoft Entra integration** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards.](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides)

## Configure and test Microsoft Entra SSO for Kemp LoadMaster Microsoft Entra integration

Configure and test Microsoft Entra SSO with Kemp LoadMaster Microsoft Entra integration using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Kemp LoadMaster Microsoft Entra integration.

To configure and test Microsoft Entra SSO with Kemp LoadMaster Microsoft Entra integration, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure Kemp LoadMaster Microsoft Entra integration SSO](#configure-kemp-loadmaster-azure-ad-integration-sso)** - to configure the single sign-on settings on application side.
3. **[Publishing Web Server](#publishing-web-server)**

   1. **[Create a Virtual Service](#create-a-virtual-service)**
   2. **[Certificates and Security](#certificates-and-security)**
   3. **[Kemp LoadMaster Microsoft Entra integration SAML Profile](#kemp-loadmaster-azure-ad-integration-saml-profile)**
   4. **[Verify the changes](#verify-the-changes)**

4. **[Configuring Kerberos Based Authentication](#configuring-kerberos-based-authentication)**

   1. **[Create a Kerberos Delegation Account for Kemp LoadMaster Microsoft Entra integration](#create-a-kerberos-delegation-account-for-kemp-loadmaster-azure-ad-integration)**
   2. **[Kemp LoadMaster Microsoft Entra integration KCD \(Kerberos Delegation Accounts\)](#kemp-loadmaster-azure-ad-integration-kcd-kerberos-delegation-accounts)**
   3. **[Kemp LoadMaster Microsoft Entra integration ESP](#kemp-loadmaster-azure-ad-integration-esp)**
   4. **[Create Kemp LoadMaster Microsoft Entra integration test user](#create-kemp-loadmaster-azure-ad-integration-test-user)** - to have a counterpart of B.Simon in Kemp LoadMaster Microsoft Entra integration that's linked to the Microsoft Entra representation of user.

5. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Kemp LoadMaster Microsoft Entra integration** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section, enter the values for the following fields:

   a. In the **Identifier \(Entity ID\)** text box, type a URL: `https://<KEMP-CUSTOMER-DOMAIN>.com/`

   b. In the **Reply URL** text box, type a URL: `https://<KEMP-CUSTOMER-DOMAIN>.com/`

   Note

   These values aren't real. Update these values with the actual Identifier and Reply URL. Contact [Kemp LoadMaster Microsoft Entra integration Client support team](mailto:support@kemp.ax) to get these values. You can also refer to the patterns shown in the Basic SAML Configuration section.
6. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section, find **Certificate \(Base64\)** and **Federation Metadata XML**, select **Download** to download the certificate and federation metadata XML files and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/kemp-tutorial/certificate-base-64.png)

7. On the **Set up Kemp LoadMaster Microsoft Entra integration** section, copy the appropriate URL\(s\) based on your requirement.

   ![Copy configuration URLs](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure Kemp LoadMaster Microsoft Entra integration SSO

## Publishing Web Server

### Create a Virtual Service

1. Go to Kemp LoadMaster Microsoft Entra integration LoadMaster Web UI > Virtual Services > Add New.
2. Select Add New.
3. Specify the Parameters for the Virtual Service.

   ![Screenshot that shows the "Please Specify the Parameters for the Virtual Service" page with example values in the boxes.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/kemp-tutorial/kemp-1.png)


   a. Virtual Address


   b. Port


   c. Service Name \(Optional\)


   d. Protocol

4. Navigate to Real Servers section.
5. Select Add New.
6. Specify the Parameters for the Real Server.

   ![Screenshot that shows the "Please Specify the Parameters for the Real Server" page with example values in the boxes.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/kemp-tutorial/kemp-2.png)


   a. Select Allow Remote Addresses


   b. Type in Real Server Address


   c. Port


   d. Forwarding method


   e. Weight


   f. Connection Limit


   g. Select Add This Real Server

## Certificates and Security

### Import certificate on Kemp LoadMaster Microsoft Entra integration

1. Go to Kemp LoadMaster Microsoft Entra integration Web Portal > Certificates & Security > SSL Certificates.
2. Under Manage Certificates > Certificate Configuration.
3. Select Import Certificate.
4. Specify the name of the file that contains the certificate. The file can also hold the private key. If the file doesn't contain the private key, then the file containing the private key must also be specified. The certificate can be in either .PEM or .PFX \(IIS\) format.
5. Select Choose file on Certificate File.
6. Select Key File \(optional\).
7. Select Save.

### SSL Acceleration

1. Go to Kemp LoadMaster Web UI > Virtual Services > View/Modify Services.
2. Select in Modify under Operation.
3. Select SSL Properties, \(which operates at Layer 7\).

   ![Screenshot that shows the "S S L Properties" section with "S S L Acceleration - Enabled" selected and an example certificate selected.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/kemp-tutorial/kemp-3.png)


   a. Select Enabled in SSL Acceleration.


   b. Under Available Certificates, select the imported certificate and select `>` symbol.


   c. Once the desired SSL certificate appears in Assigned Certificates, select **Set Certificates**.


   Note


   Make sure you select the **Set Certificates**.

## Kemp LoadMaster Microsoft Entra integration SAML Profile

### Import IdP certificate

Go to Kemp LoadMaster Microsoft Entra integration Web Console.

1. Select Intermediate Certificates under Certificates and Authority.

   ![Screenshot that shows the "Currently installed Intermediate Certificates" section with an example certificate selected.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/kemp-tutorial/kemp-6.png)


   a. Select choose file in Add a new Intermediate Certificate.


   b. Navigate to certificate file previously downloaded from Microsoft Entra Enterprise Application.


   c. Select Open.


   d. Provide a Name in Certificate Name.


   e. Select Add Certificate.

### Create Authentication Policy

Go to Manage SSO under Virtual Services.

![Screenshot that shows the "Manage S S O" page.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/kemp-tutorial/kemp-7.png)

a. Select Add under Add new Client Side Configuration after giving it a name.

b. Select SAML under Authentication Protocol.

c. Select MetaData File under IdP Provisioning.

d. Select Choose File.

e. Navigate to previously downloaded XML from Azure portal.

f. Select Open and select Import IdP MetaData file.

g. Select the intermediate certificate from IdP Certificate.

h. Set the SP Entity ID which should match the identity created in Azure portal.

i. Select Set SP Entity ID.

### Set Authentication

On Kemp LoadMaster Microsoft Entra integration Web Console.

1. Select Virtual Services.
2. Select View/Modify Services.
3. Select Modify and navigate to ESP Options.

   ![Screenshot that shows the "View/Modify Services" page, with the "ESP Options" and "Real Servers" sections expanded.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/kemp-tutorial/kemp-8.png)


   a. Select Enable ESP.


   b. Select SAML in Client Authentication Mode.


   c. Select previously created Client Side Authentication in SSO Domain.


   d. Type in host name in Allowed Virtual Hosts and select Set Allowed Virtual Hosts.


   e. Type /\* in Allowed Virtual Directories \(based on access requirements\) and select Set Allowed Directories.

### Verify the changes

Browse to the application URL.

You should see your tenanted login page instead of unauthenticated access previously.

![Screenshot that shows the tenanted "Sign in" page.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/kemp-tutorial/kemp-9.png)

## Configuring Kerberos Based Authentication

### Create a Kerberos Delegation Account for Kemp LoadMaster Microsoft Entra integration

1. Create a user Account \(in this example AppDelegation\).

   a. Select the Attribute Editor tab.

   b. Navigate to servicePrincipalName.

   c. Select servicePrincipalName and select Edit.

   d. Type http/kcduser in the Value to add field and select Add.

   e. Select Apply and OK. The window must close before you open it again \(to see the new Delegation tab\).
2. Open the user properties window again and the Delegation tab becomes available.
3. Select the Delegation tab.

   ![Screenshot that shows the "kcd user Properties" window with the "Delegation" tab selected.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/kemp-tutorial/kemp-11.png)


   a. Select Trust this user for delegation to specified services only.


   b. Select Use any authentication protocol.


   c. Add the Real Servers and add http as the service.


   d. Select the Expanded check box.


   e. You can see all servers with both the host name and the FQDN.


   f. Select OK.

Note

Set the SPN on the Application / Website as applicable. To access application when the application pool identity has been set. To access the IIS application by using the FQDN name, go to Real Server command prompt and type SetSpn with required parameters. For example, `Setspn –S HTTP/sescoindc.sunehes.co.in suneshes\kdcuser`.

### Kemp LoadMaster Microsoft Entra integration KCD \(Kerberos Delegation Accounts\)

Go to Kemp LoadMaster Microsoft Entra integration Web Console > Virtual Services > Manage SSO.

![Screenshot that shows the "Manage S S O - Manage Domain" page.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/kemp-tutorial/kemp-12.png)

a. Navigate to Server Side Single Sign On Configurations.

b. Type Name in Add new Server-Side Configuration and select Add.

c. Select Kerberos Constrained Delegation in Authentication Protocol.

d. Type Domain Name in Kerberos Realm.

e. Select Set Kerberos realm.

f. Type Domain Controller IP Address in Kerberos Key Distribution Center.

g. Select Set Kerberos KDC.

h. Type KCD user name in Kerberos Trusted User Name.

i. Select Set KDC trusted user name.

j. Type password in Kerberos Trusted User Password.

k. Select Set KCD trusted user password.

### Kemp LoadMaster Microsoft Entra integration ESP

Go to Virtual Services > View/Modify Services.

![Kemp LoadMaster Microsoft Entra integration webserver](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/kemp-tutorial/kemp-13.png)

a. Select Modify on the Nick Name of the Virtual Service.

b. Select ESP Options.

c. Under Server Authentication Mode, select KCD.

d. Under Server-Side configuration, select the previously created server-side profile.

### Create Kemp LoadMaster Microsoft Entra integration test user

In this section, you create a user called B.Simon in Kemp LoadMaster Microsoft Entra integration. Work with [Kemp LoadMaster Microsoft Entra integration Client support team](mailto:support@kemp.ax) to add the users in the Kemp LoadMaster Microsoft Entra integration platform. Users must be created and activated before you use single sign-on.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application**, and you should be automatically signed in to the Kemp LoadMaster Microsoft Entra integration for which you set up the SSO.
- You can use Microsoft My Apps. When you select the Kemp LoadMaster Microsoft Entra integration tile in the My Apps, you should be automatically signed in to the Kemp LoadMaster Microsoft Entra integration for which you set up the SSO. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

Once you configure Kemp LoadMaster Microsoft Entra integration you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-any-app).
