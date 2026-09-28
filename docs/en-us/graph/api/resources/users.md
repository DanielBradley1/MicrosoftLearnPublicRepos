<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/users?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-03 -->

# Working with users in Microsoft Graph

Microsoft Graph lets you build app experiences based on users and their relationships with other objects like groups, emails, calendars, files, and administrative roles. You can access and manage user data through common API operations, authorization models, privileges, and sensitive action handling.

## Accessing users

Access users through Microsoft Graph in two ways:

- By their ID or userPrincipalName: `/users/{id}` or `/users/{userPrincipalName}`
- By using the `/me` alias for the signed-in user, which is the same as `/users/{signed-in user's id}`

## Common API operations

In Microsoft Graph, users are represented by the [user](https://learn.microsoft.com/en-us/graph/api/resources/user) resource type. The following table lists common operations that you can perform on users.

| Path | Description |
| --- | --- |
| [`/me`](https://learn.microsoft.com/en-us/graph/api/user-get) | Get the signed-in user's details. |
| [`/users`](https://learn.microsoft.com/en-us/graph/api/user-list) | Lists users in the organization. |
| [`/users/{id}`](https://learn.microsoft.com/en-us/graph/api/user-get) | Gets a specific user by ID. |
| [`/users/{id}/photo/$value`](https://learn.microsoft.com/en-us/graph/api/profilephoto-get) | Gets the user's profile photo. |
| [`/users/{id}/manager`](https://learn.microsoft.com/en-us/graph/api/user-list-manager) | Gets the user's manager. |
| [`/users/{id}/messages`](https://learn.microsoft.com/en-us/graph/api/user-list-messages) | Lists the user's email messages in their primary inbox. |
| [`/users/{id}/events`](https://learn.microsoft.com/en-us/graph/api/user-list-events) | Lists the user's upcoming events in their calendar. |
| [`/users/{id}/drive`](https://learn.microsoft.com/en-us/graph/api/drive-get) | Gets the user's OneDrive file store. |
| [`/users/{id}/memberOf`](https://learn.microsoft.com/en-us/graph/api/user-list-memberof) | Lists the groups that the user is a member of. |
| [`/users/{id}/joinedTeams`](https://learn.microsoft.com/en-us/graph/api/user-list-joinedteams) | Lists the Microsoft Teams that the user is a member of. |
| [`POST /invitations`](https://learn.microsoft.com/en-us/graph/api/invitation-post) | Invite a guest as part of business-to-business \(B2B\) collaboration in Microsoft Entra External ID |

## Authorization and privileges

Microsoft Graph supports [delegated and application permissions](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types) to manage user operations. Understanding these permissions is crucial for secure and efficient application development.

Some user operations can be performed by the signed-in user against their own details. For such operations, the user can grant the app Microsoft Graph permissions to access their own details. The [User.ReadBasic.All](https://learn.microsoft.com/en-us/graph/permissions-reference#userreadbasicall), [User.Read](https://learn.microsoft.com/en-us/graph/permissions-reference#userread), and [User.ReadWrite](https://learn.microsoft.com/en-us/graph/permissions-reference#userreadwrite) permissions are such permissions.

Other operations, including managing details for other users, require administrative privileges granted through Microsoft Graph permissions that only authorized administrators can consent to, and [Microsoft Entra roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json). In addition, some operations are considered sensitive and only limited administrators can perform them. For more information, see [Who can reset passwords](#who-can-reset-passwords) and [Who can update sensitive attributes](#who-can-perform-sensitive-actions) sections.

### Default user permissions in Microsoft Entra ID

There are two types of users in Microsoft Entra ID: members and guests. Members are created natively in the tenant. Guests join the tenant by redeeming their invitation and access the tenant as business-to-business \(B2B\) collaboration guests.

Users in Microsoft Entra ID have default permissions that allow them to perform certain operations. This set of default permissions depends on whether the user is a member or a guest user, and the tenant administrator can change the settings for these default permissions. For more information about what member users and guest users can do, see [What are the default user permissions in Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions?context=graph/context).

#### Default user permissions in external tenants

There are also default permissions for customers in Microsoft Entra ID in external tenants. The following table shows the API operations that customers can use to manage their own profile.

> The user ID or userPrincipalName is always the signed-in user's.

| User operation | API operation | Permissions required |
| --- | --- | --- |
| Read profile | `GET /me` or `GET /users/{id or userPrincipalName}` | User.Read |
| Update profile | `PATCH /me` or `PATCH /users/{id or userPrincipalName}`  <br>  <br>The following properties are updatable: city, country, displayName, givenName, jobTitle, postalCode, state, streetAddress, surname, and preferredLanguage | User.ReadWrite |
| Change password | `POST /me/changePassword` | Directory.AccessAsUser.All |

## User basic profile properties

The *User.ReadBasic.All* permission constrains app access to reading a limited set of properties for other users' work or school accounts. This basic profile includes only the following properties:

- displayName
- givenName
- id
- mail
- photo
- securityIdentifier
- surname
- userPrincipalName

In addition, the following scenario-specific permissions also allow apps to read the basic user profile which contains mostly identifier-related properties:

- *User-Mail.ReadWrite.All*
- *User-PasswordProfile.ReadWrite.All*
- *User-Phone.ReadWrite.All*
- *User-LifeCycleInfo.Read.All*
- *User-LifeCycleInfo.ReadWrite.All*

## Sensitive actions

The following actions against the user object are considered sensitive and might be locked down to only specific administrators. All users can read the sensitive properties.

| Sensitive action | Sensitive property name |
| --- | --- |
| Disable or enable users | accountEnabled |
| Update business phone | businessPhones |
| Update mobile phone | mobilePhone |
| Update on-premises immutable ID | onPremisesImmutableId |
| Update other emails | otherMails |
| Update password profile | passwordProfile |
| Update user principal name | userPrincipalName |
| Delete or restore users | Not applicable |

### Who can perform sensitive actions

In the following table, the columns list the roles that can perform sensitive actions. The rows list the roles for which the sensitive action can be performed upon.

The following table is for roles assigned at the scope of a tenant. For roles assigned at the scope of an administrative unit, [further restrictions apply](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/admin-units-assign-roles#roles-that-can-be-assigned-with-administrative-unit-scope).

| Role that sensitive action can be performed upon | Auth Admin | User Admin | Privileged Auth Admin | Global Admin |
| --- | --- | --- | --- | --- |
| Auth Admin | ✅ |  | ✅ | ✅ |
| Directory Readers | ✅ | ✅ | ✅ | ✅ |
| Global Admin |  |  | ✅ | ✅ |
| Groups Admin |  | ✅ | ✅ | ✅ |
| Guest Inviter | ✅ | ✅ | ✅ | ✅ |
| Helpdesk Admin |  | ✅ | ✅ | ✅ |
| Message Center Reader | ✅ | ✅ | ✅ | ✅ |
| Password Admin | ✅ | ✅ | ✅ | ✅ |
| Privileged Auth Admin |  |  | ✅ | ✅ |
| Privileged Role Admin |  |  | ✅ | ✅ |
| Reports Reader | ✅ | ✅ | ✅ | ✅ |
| User  <br>\(no admin role\) | ✅ | ✅ | ✅ | ✅ |
| User  <br>\(no admin role, but member or owner of a role-assignable group\) |  |  | ✅ | ✅ |
| User with a role scoped to a restricted management administrative unit |  |  | ✅ | ✅ |
| User Admin |  | ✅ | ✅ | ✅ |
| Usage Summary Reports Reader | ✅ | ✅ | ✅ | ✅ |
| All custom roles |  |  | ✅ | ✅ |

### Who can reset passwords

In the following table, the columns list the roles that can reset passwords and invalidate refresh tokens. The rows list the roles for which the user's password can be reset. For example, a Password Administrator can reset the password for Directory Readers, Guest Inviter, Password Administrator, and users with no administrator role. If a user is assigned any other role, the Password Administrator cannot reset their password.

The following table is for roles assigned at the scope of a tenant. For roles assigned at the scope of an administrative unit, [further restrictions apply](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/admin-units-assign-roles#roles-that-can-be-assigned-with-administrative-unit-scope).

| Role that password can be reset | Password Admin | Helpdesk Admin | Auth Admin | User Admin | Privileged Auth Admin | Global Admin |
| --- | --- | --- | --- | --- | --- | --- |
| Auth Admin |  |  | ✅ |  | ✅ | ✅ |
| Directory Readers | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| Global Admin |  |  |  |  | ✅ | ✅\* |
| Groups Admin |  |  |  | ✅ | ✅ | ✅ |
| Guest Inviter | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| Helpdesk Admin |  | ✅ |  | ✅ | ✅ | ✅ |
| Message Center Reader |  | ✅ | ✅ | ✅ | ✅ | ✅ |
| Password Admin | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| Privileged Auth Admin |  |  |  |  | ✅ | ✅ |
| Privileged Role Admin |  |  |  |  | ✅ | ✅ |
| Reports Reader |  | ✅ | ✅ | ✅ | ✅ | ✅ |
| User  <br>\(no admin role\) | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| User  <br>\(no admin role, but member or owner of a role-assignable group\) |  |  |  |  | ✅ | ✅ |
| User with a role scoped to a restricted management administrative unit |  |  |  |  | ✅ | ✅ |
| User Admin |  |  |  | ✅ | ✅ | ✅ |
| Usage Summary Reports Reader |  | ✅ | ✅ | ✅ | ✅ | ✅ |
| All custom roles |  |  |  |  | ✅ | ✅ |

The ability to reset a password includes updating the following sensitive properties required for [self-service password reset](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-sspr-howitworks):

> - businessPhones
> - mobilePhone
> - otherMails

## Common properties

✅ Applies to v1.0 only.

The following represent the default set of properties that are returned when getting a user or listing users in v1.0. These are a subset of all available properties in v1.0. To get more user properties, use the `$select` query parameter. Learn [how to use the $select query parameter](https://learn.microsoft.com/en-us/graph/query-parameters#select-parameter) and see [properties that support the $select query parameter](https://learn.microsoft.com/en-us/graph/api/resources/user#properties).

For details and a list of all properties, see the [user](https://learn.microsoft.com/en-us/graph/api/resources/user) object.

| Property | Description |
| :--- | :--- |
| id | The unique identifier for the user. |
| businessPhones | The user's phone numbers. |
| displayName | The name displayed in the address book for the user. |
| givenName | The first name of the user. |
| jobTitle | The user's job title. |
| mail | The user's email address. |
| mobilePhone | The user's cellphone number. |
| officeLocation | The user's physical office location. |
| preferredLanguage | The user's language of preference. |
| surname | The last name of the user. |
| userPrincipalName | The user's principal name. |

For details and a list of all the properties, see the [user](https://learn.microsoft.com/en-us/graph/api/resources/user) object.

## User and group search limitations for guests

User and group search capabilities allow the app to search for any user or group in an organization's directory by performing queries against the `/users` or `/groups` resource set \(for example, `https://graph.microsoft.com/v1.0/users`\). Both administrators and users who are members have this capability; however, guest users don't.

If the signed-in user is a guest user, depending on the permissions an app has been granted, it can read the profile of a specific user or group \(for example, `https://graph.microsoft.com/v1.0/users/241f22af-f634-44c0-9a15-c8cd2cea5531`\); however, it can't perform queries against the `/users` or `/groups` resource set that potentially returns more than a single resource.

With the appropriate permissions, the app can read the profiles of users or groups that it obtains by following links in navigation properties; for example, `/users/{id}/directReports` or `/groups/{id}/members`.

## Properties not returned by default

Some properties of the user object aren't returned by default and must be specified in a `$select` query parameter. For example, **birthday** and **skills**. Refer to the [properties table of the user entity](https://learn.microsoft.com/en-us/graph/api/resources/user#properties) to identify properties that are returned only when you `$select`.

## Properties stored outside the main data store

While the user resource data is mostly stored in Microsoft Entra ID, some of its properties, like **skills**, are stored in SharePoint Online. In most instances, you can't specify these properties in the same Create or Update request body as other user properties.

Properties stored outside the main data store also aren't supported as part of [change tracking](https://learn.microsoft.com/en-us/graph/delta-query-overview). Therefore, a change to any of these properties doesn't result in an object showing up in the delta query response.

The following properties on the user object are stored outside the main data store: **signInActivity**, **cloudLicensing**, **mailboxSettings**, **deviceEnrollmentLimit**, **print**, **aboutMe**, **birthday**, **hireDate**, **interests**, **mySite**, **pastProjects**, **preferredName**, **responsibilities**, **schools**, **skills**.

## Conclusion

Microsoft Graph provides powerful capabilities to manage and interact with user data. By understanding the different permissions, common API operations, and handling sensitive actions, you can build secure and efficient applications. For more information, see the related content and documentation links.

## Related content

- [What are the default user permissions in Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions?context=graph/context)
