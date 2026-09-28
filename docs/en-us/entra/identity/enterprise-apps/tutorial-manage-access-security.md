<!-- Source: https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/tutorial-manage-access-security -->
<!-- Sitemap-Last-Modified: 2025-04-25 -->

# Tutorial: Manage application access and security

The IT administrator at Fabrikam has added and configured an application from the Microsoft Entra application gallery. They now need to understand the features that are available to manage access to the application and make sure the application is secure. Using the information in this tutorial, an administrator learns how to:

- Grant consent for the application on behalf of all users
- Enable multifactor authentication to make sign-in more secure
- Communicate a term of use to users of the application
- Create a collection in the My Apps portal

## Prerequisites

- An Azure account with an active subscription. [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles: Privileged Role Administrator, Cloud Application Administrator, or Application Administrator.
- An enterprise application that has been configured in your Microsoft Entra tenant.
- At least one user account added and assigned to the application. For more information, see [Quickstart: Create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users).

## Grant tenant wide admin consent

For the application that the administrator added to their tenant, they want to set it up so that all users in the organization can use it and not have to individually request consent to use it. To avoid the need for user consent, they can grant consent for the application on behalf of all users in the organization. For more information, see [Consent and permissions overview](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/user-admin-consent-overview).

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**.
3. Select the application to which you want to grant tenant-wide admin consent.
4. Under **Security**, select **Permissions**.
5. Carefully review the permissions that the application requires. If you agree with the permissions the application requires, select **Grant admin consent**.

## Create a Conditional Access policy

The administrator wants to make sure that only the people they assign to the application can securely sign in. To do this, they can configure a Conditional Access policy for a group of users that enforces multifactor authentication. For more information, see [What is Conditional Access?](https://learn.microsoft.com/en-us/entra/identity/conditional-access/overview).

### Create a group

It's easier for an administrator to manage access to the application by assigning all users of the application to a group. The administrator can then manage access at a group level.

1. In the left menu of the tenant overview, select **Groups** > **All groups**.
2. Select **New group** at the top of the pane.
3. Enter *MFA-Test-Group* for the name of the group.
4. Select No members selected, and then choose the user account that you assigned to the application.
5. Select **Create**.

### Create a Conditional Access policy for the group

1. In the left menu of the tenant overview, select **Entra ID** > **Conditional Access**.
2. Select **+ New policy**, and then select **Create new policy**.
3. Enter a name for the policy, such as *MFA Pilot*.
4. Under **Assignments**, select **Users or workload identities**.
5. On the **Include** tab, choose **Select users and groups**, and then select **Users and groups**.
6. Browse for and select the *MFA-Test-Group* that you previously created, and then choose **Select**.
7. Don't select **Create** yet, you add MFA to the policy in the next section.

### Configure multifactor authentication

In this tutorial, the administrator can find the basic steps to configure the application, but they should consider creating a plan for MFA before starting. For more information, see [Plan a Microsoft Entra multifactor authentication deployment](https://learn.microsoft.com/en-us/entra/identity/authentication/howto-mfa-getstarted).

1. Under **Cloud apps or actions**, select **No cloud apps, actions, or authentication contexts selected**. For this tutorial, on the **Include** tab, choose **Select resources**.
2. Search for and select your application, and then select **Select**.
3. Under **Access controls** and **Grant**, select **0 controls selected**.
4. Check the box for **Require multifactor authentication**, and then choose **Select**.
5. Set **Enable policy** to **On**.
6. To apply the Conditional Access policy, select **Create**.

### Test multifactor authentication

1. Open a new browser window in InPrivate or incognito mode and browse to the URL of the application.
2. Sign in with the user account that you assigned to the application. You're required to register for and use Microsoft Entra multifactor authentication. Follow the prompts to complete the process and verify you successfully sign in to the Microsoft Entra admin center.
3. Close the browser window.

## Create a terms of use statement

Juan wants to make sure that certain terms and conditions are known to users before they start using the application. For more information, see [Microsoft Entra terms of use](https://learn.microsoft.com/en-us/entra/identity/conditional-access/terms-of-use).

1. In Microsoft Word, create a new document.
2. Type My terms of use, and then save the document on your computer as *mytou.pdf*.
3. Under **Manage**, in the **Conditional Access** menu, select **Terms of use**.
4. In the top menu, select **+ New terms**.
5. In the **Name** textbox, type *My TOU*.
6. In the **Display name** textbox, type *My TOU*.
7. Upload your terms of use PDF file.
8. For **Language**, select **English**.
9. For **Require users to expand the terms of use**, select **On**.
10. For **Enforce with Conditional Access policy templates**, select **Custom policy**.
11. Select **Create**.

### Add the terms of use to the policy

1. Browse to **Entra ID** > **Conditional Access** > **Policies**.
2. From the list of policies, select the *MFA Pilot* policy.
3. Under **Access controls** and **Grant**, select the controls selected link.
4. Select *My TOU*.
5. Select **Require all the selected controls**, and then choose **Select**.
6. Select **Save**.

## Create a collection in the My Apps portal

The My Apps portal enables administrators and users to manage the applications used in the organization. For more information, see [End-user experiences for applications](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/end-user-experiences).

Note

Applications only appear in a user's my Apps portal after the user is assigned to the application and the application is configured to be visible to users. See [Configure application properties](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-configure) to learn how to make the application visible to users.

By default, all applications are listed together on a single page. But you can use collections to group together related applications and present them on a separate tab, making them easier to find. For example, you can use collections to create logical groupings of applications for specific job roles, tasks, projects, and so on. In this section, you create a collection and assign it to users and groups.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** .
3. Under **Manage**, select **App launchers** > **Collections**.
4. Select **New collection**. In the New collection page, enter a **Name** for the collection \(it's recommended to not use "collection" in the name\). Then enter a **Description**.
5. Select the **Applications** tab. Select **+ Add application**, and then in the Add applications page, select all the applications you want to add to the collection, or use the Search box to find applications.
6. When you're finished adding applications, select **Add**. The list of selected applications appears. You can use the arrows to change the order of applications in the list.
7. Select the **Owners** tab. Select **+ Add users and groups**, and then in the Add users and groups page, select the users or groups you want to assign ownership to. When you're finished selecting users and groups, choose **Select**.
8. Select the **Users and groups** tab. Select **+ Add users and groups**, and then in the **Add users and groups** page, select the users or groups you want to assign the collection to. Or use the Search box to find users or groups. When you're finished selecting users and groups, choose **Select**.
9. Select **Review + Create**, and then select **Create**. The properties for the new collection appear.

### Check the collection in the My Apps portal

1. Open a new browser window in InPrivate or incognito mode and browse to the [My Apps](https://myapps.microsoft.com/) portal.
2. Sign in with the user account that you assigned to the application.
3. Check that the collection you created appears in the My Apps portal.
4. Close the browser window.

## Clean up resources

You can keep the resources for future use, or if you're not going to continue to use the resources created in this tutorial, delete them with the following steps.

### Delete the application

1. In the left menu, select **Enterprise applications**. The **All applications** pane opens and displays a list of the applications in your Microsoft Entra tenant. Search for and select the application that you want to delete.
2. In the **Manage** section of the left menu, select **Properties**.
3. At the top of the **Properties** pane, select **Delete**, and then select **Yes** to confirm you want to delete the application from your Microsoft Entra tenant.

### Delete the Conditional Access policy

1. Under **Entra ID** > **Conditional Access** > **Policies**.
2. Search for and select **MFA Pilot**.
3. Select **Delete** at the top of the pane.

### Delete the group

1. Select **Entra ID** > **Groups**.
2. From the **All groups** page, search for and select the **MFA-Test-Group** group.
3. On the overview page, select **Delete**.

## Next steps

For information about how you can make sure that your application is healthy and being used correctly, see:

[Govern and monitor your application](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/tutorial-govern-monitor)
