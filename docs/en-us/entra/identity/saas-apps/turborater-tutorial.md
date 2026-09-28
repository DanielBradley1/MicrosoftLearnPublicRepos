<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/turborater-tutorial -->
<!-- Sitemap-Last-Modified: 2025-05-20 -->

# Configure TurboRater for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate TurboRater with Microsoft Entra ID.

Integrating TurboRater with Microsoft Entra ID provides you with the following benefits:

- You can control in Microsoft Entra ID who has access to TurboRater.
- You can enable your users to be automatically signed in to TurboRater \(single sign-on\) with their Microsoft Entra accounts.
- You can manage your accounts in one central location: the Azure portal.

For details about software as a service \(SaaS\) app integration with Microsoft Entra ID, see [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on).

## Prerequisites

To configure Microsoft Entra integration with TurboRater, you need the following items:

- A Microsoft Entra subscription. If you don't have an Azure subscription, [create a free account](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn) before you begin.
- A TurboRater subscription with single sign-on enabled.

## Scenario description

In this article, you configure and test Microsoft Entra single sign-on in a test environment.

TurboRater supports IDP-initiated single sign-on \(SSO\).

## Add TurboRater from the Azure Marketplace

To configure the integration of TurboRater into Microsoft Entra ID, you need to add TurboRater from the Azure Marketplace to your list of managed SaaS apps:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **TurboRater** in the search box.
4. Select **TurboRater** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

## Configure and test Microsoft Entra single sign-on

In this section, you configure and test Microsoft Entra single sign-on with TurboRater based on a test user named **B Simon**. For single sign-on to work, you must establish a link between a Microsoft Entra user and the related user in TurboRater.

To configure and test Microsoft Entra single sign-on with TurboRater, you need to complete the following building blocks:

1. **[Configure Microsoft Entra single sign-on](#configure-azure-ad-single-sign-on)** to enable your users to use this feature.
2. **[Configure TurboRater single sign-on](#configure-turborater-single-sign-on)** to configure the single sign-on settings on the application side.
3. **Create a Microsoft Entra test user** to test Microsoft Entra single sign-on with B. Simon.
4. **Assign the Microsoft Entra test user** to enable B. Simon to use Microsoft Entra single sign-on.
5. **[Create a TurboRater test user](#create-a-turborater-test-user)** so that there's a user named B. Simon in TurboRater who's linked to the Microsoft Entra user named B. Simon.
6. **[Test single sign-on](#test-single-sign-on)** to verify whether the configuration works.

### Configure Microsoft Entra single sign-on

In this section, you enable Microsoft Entra single sign-on.

To configure Microsoft Entra single sign-on with TurboRater, take the following steps:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **TurboRater** application integration page, select **Single sign-on**.

   ![Configure single sign-on option](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/select-sso.png)

3. On the **Select a single sign-on method** pane, select **SAML/WS-Fed** mode to enable single sign-on.

   ![Single sign-on select mode](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/select-saml-option.png)

4. On the **Set up Single Sign-On with SAML** page, select **Edit** \(the pencil icon\) to open the **Basic SAML Configuration** pane.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. In the **Basic SAML Configuration** pane, do the following steps:

   ![TurboRater domain and URLs single sign-on information](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/idp-intiated.png)


   1. In the **Identifier \(Entity ID\)** box, enter a URL:

      `https://www.itcdataservices.com`
   2. In the **Reply URL \(Assertion Consumer Service URL\)** box, enter a URL by using the following pattern:
      | Environment | URL |
      | --- | --- |
      | Test | `https://ratingqa.itcdataservices.com/webservices/imp/saml/login` |
      | Live | `https://www.itcratingservices.com/webservices/imp/saml/login` |


   Note


   These values aren't real. Update these values with the actual identifier and reply URL. To get these values, contact the [TurboRater support team](https://www.getitc.com/support). You can also refer to the patterns shown in the **Basic SAML Configuration** pane.

6. On the **Set up Single Sign-On with SAML** pane, in the **SAML Signing Certificate** section, select **Download** to download the **Federation Metadata XML** from the given options and save it on your computer.

   ![The Federation Metadata XML download option](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/metadataxml.png)

7. In the **Set up TurboRater** section, copy the URL or URLs that you need:

   - **Login URL**
   - **Microsoft Entra Identifier**
   - **Logout URL**


   ![Copy configuration URLs](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png)

### Configure TurboRater single sign-on

To configure single sign-on on the TurboRater side, you need to send the downloaded Federation Metadata XML and the appropriate copied URLs to the [TurboRater support team](https://www.getitc.com/support). The TurboRater team will make sure the SAML SSO connection is set properly on both sides.

### Create a Microsoft Entra test user

In this section, you create a test user named Britta Simon.

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

In this section, you enable B. Simon to use Azure single sign-on by granting their access to TurboRater.

1. Browse to **Entra ID** > **Enterprise apps** > **TurboRater**.

   ![Enterprise applications pane](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/enterprise-applications.png)

2. In the applications list, select **TurboRater**.

   ![TurboRater in the applications list](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/all-applications.png)

3. In the left pane, under **MANAGE**, select **Users and groups**.

   ![The "Users and groups" option](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/users-groups-blade.png)

4. Select **+ Add user**, and then select **Users and groups** in the **Add Assignment** pane.

   ![The Add Assignment pane](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/add-assign-user.png)

5. In the **Users and groups** pane, select **B. Simon** in the **Users** list, and then choose **Select** at the bottom of the pane.
6. If you're expecting a role value in the SAML assertion, then in the **Select Role** pane, select the appropriate role for the user from the list. At the bottom of the pane, choose **Select**.
7. In the **Add Assignment** pane, select **Assign**.

### Create a TurboRater test user

In this section, you create a user called B. Simon in TurboRater. Work with the [TurboRater support team](https://www.getitc.com/support) to add B. Simon as a user in TurboRater. Users must be created and activated before you use single sign-on.

### Test single sign-on

In this section, you test your Microsoft Entra single sign-on configuration by using the My Apps portal.

When you select **TurboRater** in the My Apps portal, you should be automatically signed in to the TurboRater subscription for which you set up single sign-on. For more information about the My Apps portal, see [Access and use apps on the My Apps portal](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Additional resources

- [List of articles for integrating SaaS applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/saas-apps/tutorial-list)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)
- [What is Conditional Access in Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/conditional-access/overview)
