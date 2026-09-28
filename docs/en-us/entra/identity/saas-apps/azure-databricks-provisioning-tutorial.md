<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/azure-databricks-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-07-23 -->

# Configure Azure Databricks for automatic user provisioning with Microsoft Entra ID

This article describes how to set up SCIM provisioning to the Azure Databricks account using Microsoft Entra ID.

Note

You can also sync users and groups from Microsoft Entra ID using [automatic identity management](https://learn.microsoft.com/en-us/azure/databricks/admin/users-groups/automatic-identity-management/). Automatic identity management does not require you to configure an application in Microsoft Entra ID. It also supports syncing Microsoft Entra ID service principals and nested groups to Azure Databricks, which is not supported using SCIM provisioning. Automatic identity management is enabled by default for accounts created after August 1, 2025.

Note

- The Microsoft Entra ID SCIM provisioning connector is not available in Azure China regions.
- SCIM provisioning is separate from configuring authentication for Azure Databricks. Authentication is handled automatically by Microsoft Entra ID, using the OpenID Connect protocol flow.

## Prerequisites

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- An Azure Databricks account with the [Premium plan](https://databricks.com/product/pricing/platform-addons).
- The **Cloud Application Administrator** role in Microsoft Entra ID.
- A **Premium edition** Microsoft Entra ID account to provision groups. Provisioning users is available for any Microsoft Entra ID edition.
- You must be an **Azure Databricks account admin**.

Note

To enable the account console and establish your first account admin, see [Establish your first account admin](https://learn.microsoft.com/en-us/azure/databricks/admin/admin-concepts#establish-first-account-admin).

## Step 1: Configure Azure Databricks

1. As an Azure Databricks account admin, sign in to the Azure Databricks [account console](https://accounts.azuredatabricks.net).
2. Select **Security**.
3. Select **User provisioning**.
4. Select **Set up user provisioning**.
5. Copy the **SCIM token** and the **Account SCIM URL**. You use these values to configure your Microsoft Entra ID enterprise application.

Note

The SCIM token is restricted to the Account SCIM API `/api/2.1/accounts/{account_id}/scim/v2/` and cannot be used to authenticate to other Databricks REST APIs.

## Step 2: Add Azure Databricks from the gallery

Before configuring Azure Databricks for automatic user provisioning with Microsoft Entra ID, you need to add Azure Databricks from the Microsoft Entra application gallery to your list of managed SaaS applications.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, search for and select **Azure Databricks SCIM Provisioning Connector**.
4. Enter a **Name** for the application and select **Add**.

## Step 3: Configure automatic user provisioning to Azure Databricks

This section guides you through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users and groups in Azure Databricks based on user and group assignments in Microsoft Entra ID.

Important

If you already have SCIM connectors that sync identities directly to your workspaces, you must disable those SCIM connectors when the account-level SCIM connector is enabled. See [Migrate workspace-level SCIM provisioning to the account level](https://learn.microsoft.com/en-us/azure/databricks/admin/users-groups/scim/aad#migrate).

### Configure provisioning credentials

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**, and select your **Azure Databricks SCIM Provisioning Connector** application.
3. Under the **Manage** menu, select **Provisioning**.
4. Set **Provisioning Mode** to **Automatic**.
5. Under **Admin Credentials**, set the **Tenant URL** to the **Account SCIM URL** you copied in Step 1.
6. Set the **Secret Token** to the **SCIM token** you generated in Step 1.
7. Select **Test Connection** and wait for the message confirming that the credentials are authorized to enable provisioning.
8. Select **Save**.

### Assign users and groups to the application

Users and groups assigned to the SCIM application will be provisioned to the Azure Databricks account. If you have existing Azure Databricks workspaces, Databricks recommends that you add all existing users and groups in those workspaces to the SCIM application.

Note

Microsoft Entra ID does not support the automatic provisioning of service principals to Azure Databricks. You can add service principals to your Azure Databricks account by following [Add service principals to your account](https://learn.microsoft.com/en-us/azure/databricks/admin/users-groups/manage-service-principals#add-sp).

Microsoft Entra ID does not support the automatic provisioning of nested groups to Azure Databricks. Microsoft Entra ID can only read and provision users that are immediate members of the explicitly assigned group. As a workaround, explicitly assign the groups that contain the users who need to be provisioned.

1. Go to **Manage** > **Properties**.
2. Set **Assignment required** to **No**. Databricks recommends this option, which allows all users to sign in to the Azure Databricks account.
3. Go to **Manage** > **Provisioning**.
4. To start synchronizing Microsoft Entra ID users and groups to Azure Databricks, set the **Provisioning Status** toggle to **On**.
5. Select **Save**.
6. Go to **Manage** > **Users and groups**.
7. Select **Add user/group**, select the users and groups, and select the **Assign** button.
8. Wait a few minutes and check that the users and groups exist in your Azure Databricks account.

Users and groups that you add and assign will automatically be provisioned to the Azure Databricks account when Microsoft Entra ID schedules the next sync.

Note

If you remove a user from the account-level SCIM application, that user is deactivated from the account and from their workspaces, regardless of whether or not identity federation has been enabled.

## Step 4: Monitor your deployment

Once you configure provisioning, use the following resources to monitor your deployment:

1. Use the [provisioning logs](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-provisioning-logs) to determine which users are provisioned successfully or unsuccessfully
2. Check the [progress bar](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-when-will-provisioning-finish-specific-user) to see the status of the provisioning cycle and how close it's to completion
3. If the provisioning configuration seems to be in an unhealthy state, the application goes into quarantine. Learn more about quarantine states the [application provisioning quarantine status](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-quarantine-status) article.

## Provisioning tips

- Users and groups that existed in the Azure Databricks account prior to enabling provisioning exhibit the following behavior upon provisioning sync:

  - Users and groups are **merged** if they also exist in Microsoft Entra ID.
  - Users and groups are **ignored** if they don't exist in Microsoft Entra ID. Users that don't exist in Microsoft Entra ID cannot sign in to Azure Databricks.

- Individually assigned user permissions that are duplicated by membership in a group remain even after the group membership is removed for the user.
- Directly removing users from an Azure Databricks account using the account console has the following effects:

  - The removed user loses access to that Azure Databricks account and all workspaces in the account.
  - The removed user will not be synced again using Microsoft Entra ID provisioning, even if they remain in the enterprise application.

- The initial Microsoft Entra ID sync is triggered immediately after you enable provisioning. Subsequent syncs are triggered every 20–40 minutes, depending on the number of users and groups in the application.
- You cannot update the email address of an Azure Databricks user. If you need to update an email address, contact your Azure Databricks account team.
- You cannot sync nested groups or Microsoft Entra ID service principals from the **Azure Databricks SCIM Provisioning Connector** application. You can use the [Databricks Terraform provider](https://registry.terraform.io/providers/databricks/databricks/latest/docs) or custom scripts that target the Azure Databricks SCIM API to sync nested groups or Microsoft Entra ID service principals.
- Updates to group names in Microsoft Entra ID do not sync into Azure Databricks.
- The parameters `userName` and `emails.value` must match. A mismatch can lead to Azure Databricks rejecting user creation requests from the Microsoft Entra ID SCIM application. For cases such as external users or aliased emails, you might need to change the enterprise application's default SCIM mapping to use `userPrincipalName` rather than `mail`.

## \(Optional\) Automate SCIM provisioning using Microsoft Graph

[Microsoft Graph](https://learn.microsoft.com/en-us/graph/auth/auth-concepts) includes authentication and authorization libraries that you can integrate into your application to automate provisioning of users and groups to your Azure Databricks account or workspaces, instead of configuring a SCIM provisioning connector application.

1. Follow the [instructions for registering an application with Microsoft Graph](https://learn.microsoft.com/en-us/graph/auth-register-app-v2). Make a note of the **Application ID** and the **Tenant ID** for the application.
2. Go to the application's **Overview** page:

   1. Configure a client secret for the application, and make a note of the secret.
   2. Grant the application these permissions:

      - `Application.ReadWrite.All`
      - `Application.ReadWrite.OwnedBy`

3. Ask a Microsoft Entra ID administrator to [grant admin consent](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/grant-admin-consent).
4. Update your application's code to [add support for Microsoft Graph](https://learn.microsoft.com/en-us/graph/migrate-azure-ad-graph-planning-checklist).

## Troubleshooting

### Users and groups do not sync

- Verify that the Azure Databricks SCIM token used to set up provisioning is still valid in the account console.
- Do not attempt to sync nested groups, which are not supported by Microsoft Entra ID automatic provisioning.

### Microsoft Entra ID service principals do not sync

The **Azure Databricks SCIM Provisioning Connector** application does not support syncing service principals.

### After initial sync, users and groups stop syncing

After the initial sync, Microsoft Entra ID does not sync immediately after you change user or group assignments. It schedules a sync after a delay, based on the number of users and groups. To request an immediate sync, go to **Manage** > **Provisioning** for the enterprise application and select **Clear current state and restart synchronization**.

### Microsoft Entra ID provisioning service IP range not accessible

The Microsoft Entra ID provisioning service operates under specific IP ranges. If you need to restrict network access, you must allow traffic from the IP addresses for `AzureActiveDirectory` in the [Azure IP Ranges and Service Tags – Public Cloud](https://www.microsoft.com/en-us/download/) file. Use the `AzureActiveDirectory` service tag, not a subtag such as `AzureActiveDirectory.ServiceEndpoint`. Subtag IP ranges do not include all SCIM provisioning traffic IPs. For more information, see [IP Ranges](https://learn.microsoft.com/en-us/azure/active-directory/app-provisioning/use-scim-to-provision-users-and-groups).

## Additional resources

- [Managing user account provisioning for Enterprise Apps](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/configure-automatic-user-provisioning-portal)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)

## Related content

- [Learn how to review logs and get reports on provisioning activity](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning)
