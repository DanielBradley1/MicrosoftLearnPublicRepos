<!-- Source: https://learn.microsoft.com/en-us/entra/external-id/external-collaboration-settings-configure -->
<!-- Sitemap-Last-Modified: 2026-04-24 -->

# Configure external collaboration settings for B2B in Microsoft Entra External ID

**Applies to**: ![Green circle with a white check mark symbol that indicates the following content applies to workforce tenants.](https://learn.microsoft.com/en-us/entra/external-id/media/common/applies-to-yes.png) Workforce tenants \([learn more](https://learn.microsoft.com/en-us/entra/external-id/tenant-configurations)\)

External collaboration settings let you specify what roles in your organization can invite external users for B2B collaboration. These settings also include options for [allowing or blocking specific domains](https://learn.microsoft.com/en-us/entra/external-id/allow-deny-list), and options for restricting what external guest users can see in your Microsoft Entra directory. The following options are available:

- **Determine guest user access**: Microsoft Entra External ID allows you to restrict what external guest users can see in your Microsoft Entra directory. For example, you can limit guest users' view of group memberships, or allow guests to view only their own profile information.
- **Specify who can invite guests**: By default, all users in your organization, including B2B collaboration guest users, can invite external users to B2B collaboration. If you want to limit the ability to send invitations, you can turn invitations on or off for everyone, or limit invitations to certain roles.
- **Enable guest self-service sign-up via user flows**: For applications you build, you can create user flows that allow a user to sign up for an app and create a new guest account. You can enable the feature in your external collaboration settings, and then [add a self-service sign-up user flow to your app](https://learn.microsoft.com/en-us/entra/external-id/self-service-sign-up-user-flow).
- **Allow or block domains**: You can use collaboration restrictions to allow or deny invitations to the domains you specify. For details, see [Allow or block domains](https://learn.microsoft.com/en-us/entra/external-id/allow-deny-list).

For B2B collaboration with other Microsoft Entra organizations, you should also review your [cross-tenant access settings](https://learn.microsoft.com/en-us/entra/external-id/cross-tenant-access-settings-b2b-collaboration) to ensure your inbound and outbound B2B collaboration and scope access to specific users, groups, and applications.

Note

Microsoft began rolling out an update to the guest user sign-in experience for B2B collaboration in July 2025, and the rollout completed by the end of 2025. With this update, guest users are redirected to their own organization's sign-in page to provide credentials. Guest users see the branding and URL endpoint of their home tenant. Following successful authentication in their own organization, guest users are returned to your organization to complete sign-in. In the following example, the company branding for Woodgrove Groceries appears on the left. The example on the right displays the custom branding for the user's home tenant.

![Screenshot showing guest user login flow.](https://learn.microsoft.com/en-us/entra/external-id/media/external-collaboration-settings-configure/guest-login-flow.png)

## Configure settings in the portal

In the Microsoft Entra admin center, you need a role that can update external collaboration settings, such as Global Administrator or External Identity Provider Administrator. When using Microsoft Graph, lesser-privileged roles might be available for individual settings. See [Configure settings with Microsoft Graph](#configure-settings-with-microsoft-graph) later in this article.

### To configure guest user access

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com).
2. Browse to **Entra ID** > **External Identities** > **External collaboration settings**.
3. Under **Guest user access**, choose the level of access you want guest users to have:

   ![Screenshot showing Guest user access settings.](https://learn.microsoft.com/en-us/entra/external-id/media/external-collaboration-settings-configure/guest-user-access.png)


   - **Guest users have the same access as members \(most inclusive\)**: This option gives guests the same access to Microsoft Entra resources and directory data as member users.
   - **Guest users have limited access to properties and memberships of directory objects**: \(Default\) This setting blocks guests from certain directory tasks, like enumerating users, groups, or other directory resources. Guests can see membership of all non-hidden groups. [Learn more about default guest permissions](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#member-and-guest-users).
   - **Guest user access is restricted to properties and memberships of their own directory objects \(most restrictive\)**: With this setting, guests can access only their own profiles. Guests aren't allowed to see other users' profiles, groups, or group memberships.

### To configure guest invite settings

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com).
2. Browse to **Entra ID** > **External Identities** > **External collaboration settings**.
3. Under **Guest invite settings**, choose the appropriate settings:

   ![Screenshot showing Guest invite settings.](https://learn.microsoft.com/en-us/entra/external-id/media/external-collaboration-settings-configure/guest-invite-settings.png)


   - **Anyone in the organization can invite guest users including guests and non-admins \(most inclusive\)**: To allow guests in the organization to invite other guests including users who aren't members of an organization, select this radio button.
   - **Member users and users assigned to specific admin roles can invite guest users including guests with member permissions**: To allow member users and users who have specific administrator roles to invite guests, select this radio button.
   - **Only users assigned to specific admin roles can invite guest users**: To allow only those users with [User Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#user-administrator) or [Guest Inviter](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#guest-inviter) roles to invite guests, select this radio button.
   - **No one in the organization can invite guest users including admins \(most restrictive\)**: To deny everyone in the organization from inviting guests, select this radio button.

### To configure guest self-service sign-up

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com).
2. Browse to **Entra ID** > **External Identities** > **External collaboration settings**.
3. Under **Enable guest self-service sign up via user flows**, select **Yes** if you want to be able to create user flows that let users sign up for apps. For more information about this setting, see [Add a self-service sign-up user flow to an app](https://learn.microsoft.com/en-us/entra/external-id/self-service-sign-up-user-flow).

   ![Screenshot showing Self-service sign up via user flows setting.](https://learn.microsoft.com/en-us/entra/external-id/media/external-collaboration-settings-configure/self-service-sign-up-setting.png)

### To configure external user leave settings

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com).
2. Browse to **Entra ID** > **External Identities** > **External collaboration settings**.
3. Under **External user leave settings**, you can control whether external users can remove themselves from your organization.

   - **Yes**: Users can leave the organization themselves without approval from your admin or privacy contact.
   - **No**: Users can't leave your organization themselves. They see a message guiding them to contact your admin or privacy contact to request removal from your organization.


   Important


   You can configure **External user leave settings** only if you have [added your privacy information](https://learn.microsoft.com/en-us/entra/fundamentals/properties-area) to your Microsoft Entra tenant. Otherwise, this setting will be unavailable.


   ![Screenshot showing External user leave settings in the portal.](https://learn.microsoft.com/en-us/entra/external-id/media/external-collaboration-settings-configure/external-user-leave-settings.png)

### To configure collaboration restrictions \(allow or block domains\)

Important

Microsoft recommends that you use roles with the fewest permissions. This practice helps improve security for your organization. Global Administrator is a highly privileged role that should be limited to emergency scenarios or when you can't use an existing role.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com).
2. Browse to **Entra ID** > **External Identities** > **External collaboration settings**.
3. Under **Collaboration restrictions**, you can choose whether to allow or deny invitations to the domains you specify and enter specific domain names in the text boxes. For multiple domains, enter each domain on a new line. For more information, see [Allow or block invitations to B2B users from specific organizations](https://learn.microsoft.com/en-us/entra/external-id/allow-deny-list).

   ![Screenshot showing Collaboration restrictions settings.](https://learn.microsoft.com/en-us/entra/external-id/media/external-collaboration-settings-configure/collaboration-restrictions.png)

## Configure settings with Microsoft Graph

External collaboration settings can be configured by using the Microsoft Graph API:

- For **Guest user access restrictions** and **Guest invite restrictions**, use the [authorizationPolicy](https://learn.microsoft.com/en-us/graph/api/resources/authorizationpolicy?view=graph-rest-1.0&preserve-view=true) resource type.
- For the **Enable guest self-service sign up via user flows** setting, use the [authenticationFlowsPolicy](https://learn.microsoft.com/en-us/graph/api/resources/authenticationflowspolicy?view=graph-rest-1.0&preserve-view=true) resource type.
- For **External user leave settings**, use the [externalidentitiespolicy](https://learn.microsoft.com/en-us/graph/api/resources/externalidentitiespolicy?view=graph-rest-1.0&preserve-view=true) resource type.
- For email one-time passcode settings \(now on the **All identity providers** page in the Microsoft Entra admin center\), use the [emailAuthenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/emailAuthenticationMethodConfiguration?view=graph-rest-1.0&preserve-view=true) resource type.

## Assign the Guest Inviter role to a user

With the [Guest Inviter](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#guest-inviter) role, you can give individual users the ability to invite guests without assigning them a higher privilege administrator role. Users with the Guest Inviter role are able to invite guests even when the option **Only users assigned to specific admin roles can invite guest users** is selected \(under **Guest invite settings**\).

Here's an example that shows how to use Microsoft Graph PowerShell to add a user to the `Guest Inviter` role:

```powershell

Import-Module Microsoft.Graph.Identity.DirectoryManagement

$roleName = "Guest Inviter"
$role = Get-MgDirectoryRole | where {$_.DisplayName -eq $roleName}
$userId = <User Id/User Principal Name>

$DirObject = @{
  "@odata.id" = "https://graph.microsoft.com/v1.0/directoryObjects/$userId"
  }

New-MgDirectoryRoleMemberByRef -DirectoryRoleId $role.Id -BodyParameter $DirObject
```

## Sign-in logs for B2B users

When a B2B user signs into a resource tenant to collaborate, a sign-in log is generated in both the home tenant and the resource tenant. These logs include information such as the application being used, email addresses, tenant name, and tenant ID for both the home tenant and the resource tenant.

## Next steps

See the following articles on Microsoft Entra B2B collaboration:

- [What is Microsoft Entra B2B collaboration?](https://learn.microsoft.com/en-us/entra/external-id/what-is-b2b)
- [Adding a B2B collaboration user to a role](https://learn.microsoft.com/en-us/entra/external-id/add-users-administrator)
