<!-- Source: https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-register-saml-app -->
<!-- Sitemap-Last-Modified: 2025-10-07 -->

# Register a SAML app in your external tenant

**Applies to**: ![Green circle with a white check mark symbol that indicates the following content applies to external tenants.](https://learn.microsoft.com/en-us/entra/external-id/media/common/applies-to-yes.png) External tenants \([learn more](https://learn.microsoft.com/en-us/entra/external-id/tenant-configurations)\)

In external tenants, you can register applications that use the OpenID Connect \(OIDC\) or Security Assertion Markup Language \(SAML\) protocol for authentication and single sign-on. The [app registration](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-register-ciam-app) process is designed specifically for OIDC apps. But you can use the Enterprise applications feature to create and register your SAML app. This process generates a unique application ID \(client ID\) and adds your app to the App registrations, where you can view and manage its properties.

This article describes how to register your own SAML application in your external tenant by creating a *non-gallery* app in **Enterprise applications**.

## Prerequisites

- An Azure account that has an active subscription. [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- A Microsoft Entra [external tenant](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-create-external-tenant-portal).
- [A sign-up and sign-in user flow](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-user-flow-sign-up-sign-in-customers).

## Create and register a SAML app

1. Sign in to the Microsoft Entra admin center as at least an Application Administrator.
2. If you have access to multiple tenants, use the **Settings** icon ![](https://learn.microsoft.com/en-us/entra/external-id/customers/media/common/admin-center-settings-icon.png) in the top menu and switch to your external tenant from the **Directories** menu.
3. Go to **Identity** > **Applications**> **Enterprise applications**.
4. Select **New application**, and then select **Create your own application**.

   ![Screenshot of the Create your own application option in the Microsoft Entra Gallery.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-register-saml-app/create-your-own-application.png)
5. On the **Create your own application** pane, enter a name for your app.
6. Select **Integrate any other application you don't find in the gallery \(Non-gallery\)**.
7. Select **Create**.
8. The app **Overview** page opens. In the left menu under **Manage**, select **Properties**. Switch the **Assignment required?** toggle to **No** so that users can use self-service sign-up, and then select **Save**.

   ![Screenshot of the Assignment required toggle.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-register-saml-app/assignment-toggle-no.png)
9. In the left menu under **Manage**, select **Single sign-on**.
10. Under **Select a single sign-on method**, select **SAML**.

    ![Screenshot of the Single sign-on method tile.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-register-saml-app/select-single-sign-on-method.png)
11. On the **SAML-based Sign-on** page, do one of the following:

    - Select **Upload metadata file**, browse to the file containing your metadata, and then select **Add**. Select **Save**.
    - Or, use the **Edit** pencil option to update each section, and then select **Save**.

12. At the third section under **SAML Certificates**, note that there's no **Download** button next to **Federation Metadata XML**. This button appears only in workforce tenants, not in external tenants. To download the metadata file in an external tenant, copy the link and paste it into your browser.

    ![Screenshot of the federation metadata xml link.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-register-saml-app/federation-metadata-xml.png)
13. Select **Test**, and then select the **Test sign-in** button to see if single sign-on is working. This test verifies that your current admin account can sign in using the `https://login.microsoftonline.com` endpoint.

    ![Screenshot of the test single sign-on option.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-register-saml-app/test-application.png)

    You can test external user sign-in with these steps:

    - [Create a sign-up and sign-in user flow](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-user-flow-sign-up-sign-in-customers) if you haven't already.
    - [Add your SAML application to the user flow](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-user-flow-add-application).
    - Run your application.
