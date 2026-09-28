<!-- Source: https://learn.microsoft.com/en-us/entra/external-id/customers/reference-user-permissions -->
<!-- Sitemap-Last-Modified: 2025-03-18 -->

# Default user permissions in external tenants

**Applies to**: ![Green circle with a white check mark symbol that indicates the following content applies to external tenants.](https://learn.microsoft.com/en-us/entra/external-id/media/common/applies-to-yes.png) External tenants \([learn more](https://learn.microsoft.com/en-us/entra/external-id/tenant-configurations)\)

A Microsoft Entra tenant in an *external* configuration is used exclusively for [Microsoft Entra External ID](https://learn.microsoft.com/en-us/entra/external-id/customers/overview-customers-ciam) scenarios. An external tenant provides clear separation between your corporate workforce directory and your customer-facing app directory. By default, users created in your external tenant are restricted from accessing information about other users, groups, or devices in the external tenant. All users have default permissions unless you assign them an admin role.

To better understand the typical use cases for users in an external tenant, we can categorize them as follows:

- **External users** are consumers and business customers who use the apps registered in your external tenant. They typically retain default user permissions, meaning you don't assign them administrative roles. These users are usually created through self-service sign-up, but you can create them with the [Create new external user](https://learn.microsoft.com/en-us/entra/fundamentals/how-to-create-delete-users#create-a-new-external-user) option in the Microsoft Entra admin center or with Microsoft Graph.
- **Internal users** are usually admins to whom you assign [Microsoft Entra roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference). You can create internal users and assign roles using the [Create new user](https://learn.microsoft.com/en-us/entra/fundamentals/how-to-create-delete-users#create-a-new-user) option in the admin center or with Microsoft Graph.
- **Invited users** are usually admins you invite to the external tenant and to whom you assign [Microsoft Entra roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference). If they're not assigned a role, they have default user permissions. You can invite users and assign roles using the [Invite external user](https://learn.microsoft.com/en-us/entra/fundamentals/how-to-create-delete-users#invite-an-external-user) option in the admin center or with Microsoft Graph.

When users are created in an external tenant, they all start with default permissions. However, you can assign [Microsoft Entra roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference) to those users who need to perform administrative tasks within the external tenant.

## Default permissions

The following table describes the default permissions assigned to a user in an external tenant, including:

- Users who use self-service sign-up
- Users who are created by administrators
- Users who are invited

| **Area** | **Default user permissions** |
| --- | --- |
| Users and contacts | - Read and update their own profile through the app profile management experience<br>- Change their own password<br>- Sign in with a local or social account |
| Applications | - Access applications<br>- Revoke consent to applications |

## Microsoft Graph APIs and permissions

The following table indicates the API operations that enable customers to manage their profile information. The user ID or userPrincipalName is always the signed-in user's.

| User operation | API operation | Permissions required |
| --- | --- | --- |
| Read profile | [GET /me](https://learn.microsoft.com/en-us/graph/api/user-get) or [GET /users/{id or userPrincipalName}](https://learn.microsoft.com/en-us/graph/api/user-get) | User.Read |
| Update profile | [PATCH /me](https://learn.microsoft.com/en-us/graph/api/user-update) or [PATCH /users/{id or userPrincipalName}](https://learn.microsoft.com/en-us/graph/api/user-update)  <br>  <br>The following properties are updatable: city, country, displayName, givenName, jobTitle, postalCode, state, streetAddress, surname, and preferredLanguage | User.ReadWrite |
| Change password | [POST /me/changePassword](https://learn.microsoft.com/en-us/graph/api/user-changepassword) | Directory.AccessAsUser.All |
