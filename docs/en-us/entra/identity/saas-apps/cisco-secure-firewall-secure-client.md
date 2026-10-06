<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/cisco-secure-firewall-secure-client -->
<!-- Sitemap-Last-Modified: 2026-10-01 -->

# Configure Cisco Secure Firewall - Secure Client for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Cisco Secure Firewall - Secure Client with Microsoft Entra ID. When you integrate Cisco Secure Firewall - Secure Client with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Cisco Secure Firewall - Secure Client.
- Enable your users to be automatically signed-in to Cisco Secure Firewall - Secure Client with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- Cisco Secure Firewall - Secure Client single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- Cisco Secure Firewall - Secure Client supports only **IDP** initiated SSO.

## Adding Cisco Secure Firewall - Secure Client from the gallery

To configure the integration of Cisco Secure Firewall - Secure Client into Microsoft Entra ID, you need to add Cisco Secure Firewall - Secure Client from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Cisco Secure Firewall - Secure Client** in the search box.
4. Select **Cisco Secure Firewall - Secure Client** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure and test Microsoft Entra SSO for Cisco Secure Firewall - Secure Client

Configure and test Microsoft Entra SSO with Cisco Secure Firewall - Secure Client using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Cisco Secure Firewall - Secure Client.

To configure and test Microsoft Entra SSO with Cisco Secure Firewall - Secure Client, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure Cisco Secure Firewall - Secure Client SSO](#configure-cisco-secure-firewall---secure-client-sso)** - to configure the single sign-on settings on application side.

   1. **[Create Cisco Secure Firewall - Secure Client test user](#create-cisco-secure-firewall---secure-client-test-user)** - to have a counterpart of B.Simon in Cisco Secure Firewall - Secure Client that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Cisco Secure Firewall - Secure Client** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the edit/pen icon for **Basic SAML Configuration** to edit the settings.

   ![Screenshot shows to edit Basic SAML Configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Set up single sign-on with SAML** page, enter the values for the following fields:

   1. In the **Identifier** text box, type a URL using the following pattern:  
      `https://<YOUR_CISCO_FQDN>/saml/sp/metadata/<Tunnel_Group_Name>`
   2. In the **Reply URL** text box, type a URL using the following pattern:  
      `https://<YOUR_CISCO_ANYCONNECT_FQDN>/+CSCOE+/saml/sp/acs?tgname=<Tunnel_Group_Name>`


   Important


   The **Identifier** and **Reply URL** values shown in this article are examples only. Before you configure SSO, verify that these values reference the correct endpoints for your Cisco Secure Firewall environment. Don't use example or placeholder domains in production. Contact Cisco TAC or the [Cisco Secure Firewall - Secure Client support team](https://www.cisco.com/c/en/us/support/index.html) for the appropriate values.


   Note


   `<Tunnel_Group_Name>` is a case-sensitive and the value must not contain dots "." and slashes "/".


   Note


   For clarification about these values, contact Cisco TAC support. Update these values with the actual Identifier and Reply URL provided by Cisco TAC. Contact the [Cisco Secure Firewall - Secure Client support team](https://www.cisco.com/c/en/us/support/index.html) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.


   Important


   **Security best practice:** For new and existing deployments, verify that all configured **Identifier** and **Reply URL** values reference the intended endpoints and trusted domains before you enable SAML SSO. Example or placeholder domains are for documentation purposes only and must not be used in production.

6. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section, find **Certificate \(Base64\)** and select **Download** to download the certificate file and save it on your computer.

   ![Screenshot shows the Certificate download link.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/certificatebase64.png "Certificate")

7. On the **Set up Cisco Secure Firewall - Secure Client** section, copy the appropriate URL\(s\) based on your requirement.

   ![Screenshot shows to copy configuration URLs.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png "Metadata")

Note

If you would like to on board multiple TGTs of the server then you need to add multiple instances of the Cisco Secure Firewall - Secure Client application from the gallery. You can also choose to upload your own certificate in Microsoft Entra ID for all these application instances. That way you can have same certificate for the applications but you can configure different Identifier and Reply URL for every application.

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure Cisco Secure Firewall - Secure Client SSO

1. You're going to do this on the CLI first, you might come back through and do an ASDM walk-through at another time.
2. Connect to your VPN Appliance, you're going to be using an ASA running 9.8 code train, and your VPN clients are 4.6+.
3. First you create a Trustpoint and import our SAML cert.

   ```
    config t

    crypto ca trustpoint AzureAD-AC-SAML
      revocation-check none
      no id-usage
      enrollment terminal
      no ca-check
    crypto ca authenticate AzureAD-AC-SAML
    -----BEGIN CERTIFICATE-----
    …
    PEM Certificate Text from download goes here
    …
    -----END CERTIFICATE-----
    quit
   ```

4. The following commands will provision your SAML IdP.

   ```
    webvpn
    saml idp https://sts.windows.net/xxxxxxxxxxxxx/ (This is your Azure AD Identifier from the Set up Cisco Secure Firewall - Secure Client section in the Azure portal)
    url sign-in https://login.microsoftonline.com/xxxxxxxxxxxxxxxxxxxxxx/saml2 (This is your Login URL from the Set up Cisco Secure Firewall - Secure Client section in the Azure portal)
    url sign-out https://login.microsoftonline.com/common/wsfederation?wa=wsignout1.0 (This is Logout URL from the Set up Cisco Secure Firewall - Secure Client section in the Azure portal)
    trustpoint idp AzureAD-AC-SAML
    trustpoint sp (Trustpoint for SAML Requests - you can use your existing external cert here)
    no force re-authentication
    no signature
    base-url https://my.asa.com
   ```

5. Now you can apply SAML Authentication to a VPN Tunnel Configuration.

   ```
   tunnel-group AC-SAML webvpn-attributes
      saml identity-provider https://sts.windows.net/xxxxxxxxxxxxx/
      authentication saml
   end

    write mem
   ```


   Note


   There's a work around with the SAML IdP configuration. If you make changes to the IdP configuration you need to remove the saml identity-provider configuration from your Tunnel Group and re-apply it for the changes to become effective.

### Create Cisco Secure Firewall - Secure Client test user

In this section, you create a user called Britta Simon in Cisco Secure Firewall - Secure Client. Work with [Cisco Secure Firewall - Secure Client support team](https://www.cisco.com/c/en/us/support/index.html) to add the users in the Cisco Secure Firewall - Secure Client platform. Users must be created and activated before you use single sign-on.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application**, and you should be automatically signed in to the Cisco Secure Firewall - Secure Client for which you set up the SSO
- You can use Microsoft Access Panel. When you select the Cisco Secure Firewall - Secure Client tile in the Access Panel, you should be automatically signed in to the Cisco Secure Firewall - Secure Client for which you set up the SSO. For more information about the Access Panel, see [Introduction to the Access Panel](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

Once you configure Cisco Secure Firewall - Secure Client you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-any-app).
