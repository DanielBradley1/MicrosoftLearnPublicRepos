<!-- Source: https://learn.microsoft.com/en-us/entra/external-id/b2b-tutorial-require-mfa -->
<!-- Sitemap-Last-Modified: 2026-04-24 -->

# Tutorial: Enforce multifactor authentication for B2B guest users

**Applies to**: ![Green circle with a white check mark symbol that indicates the following content applies to workforce tenants.](https://learn.microsoft.com/en-us/entra/external-id/media/common/applies-to-yes.png) Workforce tenants \([learn more](https://learn.microsoft.com/en-us/entra/external-id/tenant-configurations)\)

When you collaborate with external B2B guest users, protect your apps with multifactor authentication policies. External users need more than just a username and password to access your resources. In Microsoft Entra ID, you can accomplish this goal with a Conditional Access policy that requires MFA for access. You can enforce MFA policies at the tenant, app, or individual guest user level, just like for members of your own organization. The resource tenant is responsible for Microsoft Entra multifactor authentication for users, even if the guest user's organization has multifactor authentication capabilities.

Example:

![Diagram showing a guest user signing into a company's apps.](https://learn.microsoft.com/en-us/entra/external-id/media/tutorial-mfa/b2b-mfa-example.png)

1. An admin or employee at Company A invites a guest user to use a cloud or on-premises application that is configured to require MFA for access.
2. The guest user signs in with their own work, school, or social identity.
3. The user is asked to complete an MFA challenge.
4. The user sets up MFA with Company A and chooses their MFA option. The user is allowed access to the application.

Note

Microsoft Entra multifactor authentication is performed by the resource tenant to ensure predictability. When the guest user signs in, they see the resource tenant sign-in page displayed in the background, and their own home tenant sign-in page and company logo in the foreground.

In this tutorial, you will:

- Test the sign-in experience before setting up MFA.
- Create a Conditional Access policy that requires MFA for access to a cloud app in your environment. In this tutorial, we’ll use the Azure Resource Manager app to illustrate the process.
- Use the What If tool to simulate MFA sign-in.
- Test your Conditional Access policy.
- Clean up the test user and policy.

If you don't have an Azure subscription, create a [free account](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn) to get started.

## Prerequisites

To complete the scenario in this tutorial, you need:

- **Access to Microsoft Entra ID P1 or P2 edition**, which includes Conditional Access policy capabilities. To enforce MFA, create a Microsoft Entra Conditional Access policy. MFA policies are always enforced at your organization, even if the partner doesn't have MFA capabilities.
- **A valid external email account** that you can add to your tenant directory as a guest user and use to sign in. If you don't know how to create a guest account, follow the steps in [Add a B2B guest user in the Microsoft Entra admin center](https://learn.microsoft.com/en-us/entra/external-id/add-users-administrator).

## Create a test guest user in Microsoft Entra ID

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [User Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#user-administrator).
2. Browse to **Entra ID** > **Users**.
3. Select **New user** and then **Invite external user**.

   [![Screenshot of where to select the new guest user option.](https://learn.microsoft.com/en-us/entra/external-id/media/tutorial-mfa/tutorial-mfa-new-user.png)](https://learn.microsoft.com/en-us/entra/external-id/media/tutorial-mfa/tutorial-mfa-new-user.png#lightbox)
4. Under **Identity** on the **Basics** tab, enter the email address of the external user. You can optionally include a display name and welcome message.

   ![Screenshot of where to enter the guest email.](https://learn.microsoft.com/en-us/entra/external-id/media/tutorial-mfa/tutorial-mfa-new-user-identity.png)
5. You can optionally add further details to the user under the **Properties** and **Assignments** tabs.
6. Select **Review + invite** to automatically send the invitation to the guest user. A **Successfully invited user** message appears.
7. After you send the invitation, the user account is added to the directory as a guest.

## Test the sign-in experience before MFA setup

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) using your test user name and password.
2. Access the Microsoft Entra admin center using only your sign-in credentials. No other authentication is required.
3. Sign out of the Microsoft Entra admin center.

## Create a Conditional Access policy that requires MFA

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Conditional Access Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#conditional-access-administrator).
2. Browse to **Entra ID** > **Conditional Access** > **Policies**.
3. Select **New policy**.
4. Name your policy, like **Require MFA for B2B portal access**. Create a meaningful standard for naming policies.
5. Under **Assignments**, select **Users or workload identities**.

   1. Under **Include**, choose **Select users and groups**, and then select **Guest or external users**. You can assign the policy to different [external user types](https://learn.microsoft.com/en-us/entra/external-id/authentication-conditional-access#assign-conditional-access-policies-to-external-user-types), built-in directory roles, or users and groups.


   ![Screenshot showing selecting all guest users.](https://learn.microsoft.com/en-us/entra/external-id/media/tutorial-mfa/tutorial-mfa-user-access.png)

6. Under **Target resources** > **Resources \(formerly cloud apps\)** > **Include** > **Select resources**, choose **Azure Resource Manager**, and then **Select** the resource.

   [![Screenshot showing the Cloud apps page and the Select option.](https://learn.microsoft.com/en-us/entra/external-id/media/tutorial-mfa/tutorial-mfa-app-access.png)](https://learn.microsoft.com/en-us/entra/external-id/media/tutorial-mfa/tutorial-mfa-app-access.png#lightbox)
7. Under **Access controls** > **Grant**, select **Grant access**, **Require multifactor authentication**, and select **Select**.

   ![Screenshot showing the option for requiring multifactor authentication.](https://learn.microsoft.com/en-us/entra/external-id/media/tutorial-mfa/tutorial-mfa-grant-access.png)
8. Under **Enable policy**, select **On**.
9. Select **Create**.

## Use the What If option to simulate sign-in

The **Conditional Access What If policy tool** helps you understand the effects of Conditional Access policies in your environment. Instead of manually testing your policies with multiple sign-ins, you can use this tool to simulate a user's sign-in. The simulation predicts how this sign-in will affect your policies and generates a report. For more information, see [Use the What If tool to understand Conditional Access policies](https://learn.microsoft.com/en-us/entra/identity/conditional-access/what-if-tool).

## Test your Conditional Access policy

1. Use your test user name and password to sign in to the [Microsoft Entra admin center](https://entra.microsoft.com).
2. You should see a request for more authentication methods. It can take some time for the policy to take effect.

   ![Screenshot of the 'More information required' message.](https://learn.microsoft.com/en-us/entra/external-id/media/tutorial-mfa/mfa-required.png)

   Note

   You can also configure [cross-tenant access settings](https://learn.microsoft.com/en-us/entra/external-id/cross-tenant-access-overview) to trust the MFA from the Microsoft Entra home tenant. This allows external Microsoft Entra users to use the MFA registered in their own tenant rather than register in the resource tenant.
3. Sign out.

## Clean up resources

When no longer needed, remove the test user and the test Conditional Access policy.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [User Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#user-administrator).
2. Browse to **Entra ID** > **Users**.
3. Select the test user, and then select **Delete user**.
4. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Conditional Access Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#conditional-access-administrator).
5. Browse to **Entra ID** > **Conditional Access** > **Policies**.
6. In the **Policy Name** list, select the context menu \(…\) for your test policy, then select **Delete**, and confirm by selecting **Yes**.

## Next steps

In this tutorial, you created a Conditional Access policy that requires guest users to use MFA when signing in to one of your cloud apps. To learn more about adding guest users for collaboration, go to [Add Microsoft Entra B2B collaboration users in the Microsoft Entra admin center](https://learn.microsoft.com/en-us/entra/external-id/add-users-administrator).
