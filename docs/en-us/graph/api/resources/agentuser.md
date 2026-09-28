<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/agentuser?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-01 -->

# agentUser resource type

Namespace: microsoft.graph

Represents a specialized subtype of user identity in Microsoft Entra ID designed for AI-powered applications \(agents\) that need to function as digital workers. Agent users enable agents to access APIs and services that specifically require user identities, receiving tokens with `idtyp=user` claims. Agent users are distinct from human [users](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) and they only interlinked to users through relationships such as owner, sponsor, and manager.

Each agent user maintains a one-to-one relationship with a parent agent identity and is authenticated through that parent's credentials. Agent users have user-like capabilities such as being added to groups, assigned licenses, and accessing collaborative features like mailboxes and chat, while operating under security constraints including no password authentication, no privileged admin role assignments, and permissions similar to guest users.

Inherits from [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0).

This resource is an open type that allows additional properties beyond those documented here.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/agentuser-list?view=graph-rest-1.0) | [agentUser](https://learn.microsoft.com/en-us/graph/api/resources/agentuser?view=graph-rest-1.0) collection | Get a list of **agentUser** objects. |
| [Create](https://learn.microsoft.com/en-us/graph/api/agentuser-post?view=graph-rest-1.0) | [agentUser](https://learn.microsoft.com/en-us/graph/api/resources/agentuser?view=graph-rest-1.0) | Create a new **agentUser** object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/agentuser-get?view=graph-rest-1.0) | [agentUser](https://learn.microsoft.com/en-us/graph/api/resources/agentuser?view=graph-rest-1.0) | Read properties and relationships of **agentUser** object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/agentuser-update?view=graph-rest-1.0) | [agentUser](https://learn.microsoft.com/en-us/graph/api/resources/agentuser?view=graph-rest-1.0) | Update **agentUser** object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/agentuser-delete?view=graph-rest-1.0) | None | Delete **agentUser** object. |
| **App role assignments** |  |  |
| [List app role assignments](https://learn.microsoft.com/en-us/graph/api/agentuser-list-approleassignments?view=graph-rest-1.0) | [appRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/approleassignment?view=graph-rest-1.0) collection | Get the app role assignments for this agent user. |
| [Create app role assignment](https://learn.microsoft.com/en-us/graph/api/agentuser-post-approleassignments?view=graph-rest-1.0) | [appRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/approleassignment?view=graph-rest-1.0) | Create a new app role assignment for this agent user. |
| **Deleted items** |  |  |
| [List](https://learn.microsoft.com/en-us/graph/api/directory-deleteditems-list?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Retrieve a list of recently deleted agent user objects. |
| [Get](https://learn.microsoft.com/en-us/graph/api/directory-deleteditems-get?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) | Retrieve the properties of a recently deleted agent user. |
| [Restore](https://learn.microsoft.com/en-us/graph/api/directory-deleteditems-restore?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) | Restore a recently deleted agent user. |
| [Permanently delete](https://learn.microsoft.com/en-us/graph/api/directory-deleteditems-delete?view=graph-rest-1.0) | None | Permanently delete an agent user. |
| **Directory objects** |  |  |
| [List owned objects](https://learn.microsoft.com/en-us/graph/api/agentuser-list-ownedobjects?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Get the directory objects owned by the agent user. |
| **Organizational relationships** |  |  |
| [List direct reports](https://learn.microsoft.com/en-us/graph/api/agentuser-list-directreports?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Get the users and contacts that report to the agent user. |
| [List manager](https://learn.microsoft.com/en-us/graph/api/agentuser-list-manager?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) | Get the user or contact that is this agent user's manager. |
| [Add manager](https://learn.microsoft.com/en-us/graph/api/agentuser-post-manager?view=graph-rest-1.0) | None | Assign the agent user's manager. |
| [Remove manager](https://learn.microsoft.com/en-us/graph/api/agentuser-delete-manager?view=graph-rest-1.0) | None | Remove the agent user's manager. |
| [List direct memberships](https://learn.microsoft.com/en-us/graph/api/agentuser-list-memberof?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Get the groups, directory roles, and administrative units that the agent user is a member of. |
| [List transitive memberships](https://learn.microsoft.com/en-us/graph/api/agentuser-list-transitivememberof?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Get the groups, directory roles, and administrative units that the agent user is a member of, including nested group memberships. |
| [List transitive reports](https://learn.microsoft.com/en-us/graph/api/agentuser-list-transitivereports?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Get the transitive reports for the agent user. |
| **Sponsors** |  |  |
| [List sponsors](https://learn.microsoft.com/en-us/graph/api/agentuser-list-sponsors?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Get the users and groups responsible for this agent user's privileges. |
| [Add sponsors](https://learn.microsoft.com/en-us/graph/api/agentuser-post-sponsors?view=graph-rest-1.0) | None | Add sponsors for the agent user. |
| [Remove sponsors](https://learn.microsoft.com/en-us/graph/api/agentuser-delete-sponsors?view=graph-rest-1.0) | None | Remove sponsors from the agent user. |

## Properties

Important

While this resource inherits from **user**, some properties are not applicable and return `null` or default values. These properties are excluded from the table below.

| Property | Type | Description |
| :--- | :--- | :--- |
| accountEnabled | Boolean | `true` if the account is enabled; otherwise, `false`. This property is required when creating the object. Inherited from [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0). |
| assignedLicenses | [assignedLicense](https://learn.microsoft.com/en-us/graph/api/resources/assignedlicense?view=graph-rest-1.0) collection | The licenses that are assigned to the agent user, including inherited \(group-based\) licenses. This property doesn't differentiate between directly assigned and inherited licenses. Use the **licenseAssignmentStates** property to identify the directly assigned and inherited licenses. Not nullable. Inherited from [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0). |
| assignedPlans | [assignedPlan](https://learn.microsoft.com/en-us/graph/api/resources/assignedplan?view=graph-rest-1.0) collection | The plans that are assigned to the agent user. Read-only. Not nullable. Inherited from [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0). |
| businessPhones | String collection | The telephone numbers for the agent user. Only one number can be set for this property. Read-only for users synced from on-premises directory. Inherited from [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0). |
| city | String | The city where the agent user is located. Maximum length is 128 characters. Inherited from [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0). |
| companyName | String | The name of the company the agent user is associated with. This property can be useful for describing the company that an external user comes from. The maximum length is 64 characters. Inherited from [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0). |
| country | String | The country or region where the agent user is located; for example, `US` or `UK`. Maximum length is 128 characters. Inherited from [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0). |
| createdDateTime | DateTimeOffset | The date and time the agent user was created in ISO 8601 format and UTC. The value cannot be modified and is automatically populated when the entity is created. Nullable. For on-premises users, the value represents when they were first created in Microsoft Entra ID. Property is `null` for some users created before June 2018 and on-premises users synced to Microsoft Entra ID before June 2018. Read-only. Inherited from [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0). |
| creationType | String | Read-only. Null. Inherited from [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0). |
| customSecurityAttributes | [customSecurityAttributeValue](https://learn.microsoft.com/en-us/graph/api/resources/customsecurityattributevalue?view=graph-rest-1.0) | An open complex type that holds the value of a custom security attribute that is assigned to a directory object. Nullable. Inherited from [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0). |
| deletedDateTime | DateTimeOffset | The date and time the user was deleted. Inherited from [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0). |
| department | String | The name of the department where the user works. Maximum length is 64 characters. Inherited from [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0). |
| displayName | String | The name displayed in the address book for the user. This value is usually the combination of the user's first name, middle initial, and last name. This property is required when a user is created, and it cannot be cleared during updates. Maximum length is 256 characters. Inherited from [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0). |
| employeeHireDate | DateTimeOffset | The date and time when the user was hired or will start work if there is a future hire. Inherited from [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0). |
| employeeId | String | The employee identifier assigned to the user by the organization. The maximum length is 16 characters. Inherited from [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0). |
| employeeLeaveDateTime | DateTimeOffset | The date and time when the user left or will leave the organization. To read this property, the calling app must be assigned the *User-LifeCycleInfo.Read.All* permission. To write this property, the calling app must be assigned the *User.Read.All* and *User-LifeCycleInfo.ReadWrite.All* permissions. To read this property in delegated scenarios, the admin needs at least one of the following Microsoft Entra roles: *Lifecycle Workflows Administrator* \(least privilege\), *Global Reader*. To write this property in delegated scenarios, the admin needs the *Global Administrator* role. For more information, see [Configure the employeeLeaveDateTime property for a user](https://learn.microsoft.com/en-us/graph/tutorial-lifecycle-workflows-set-employeeleavedatetime). Inherited from [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0). |
| employeeOrgData | [employeeOrgData](https://learn.microsoft.com/en-us/graph/api/resources/employeeorgdata?view=graph-rest-1.0) | Represents organization data \(for example, division and costCenter\) associated with a user. Inherited from [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0). |
| employeeType | String | Captures enterprise worker type. For example, `Employee`, `Contractor`, `Consultant`, or `Vendor`. Inherited from [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0). |
| faxNumber | String | The fax number of the user. Inherited from [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0). |
| givenName | String | The given name \(first name\) of the user. Maximum length is 64 characters. Inherited from [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0). |
| id | String | The unique identifier for the user. It should be treated as an opaque identifier. Inherited from [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0). Not nullable. Read-only. Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0) |
| identityParentId | String | References the object ID of the associated [agent identity](https://learn.microsoft.com/en-us/graph/api/resources/agentidentity?view=graph-rest-1.0). This property is required when creating the object, and it can't be cleared during updates. Inherited from [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0). |
| imAddresses | String collection | The instant message voice-over IP \(VOIP\) session initiation protocol \(SIP\) addresses for the user. Read-only. Inherited from [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0). |
| infoCatalogs | String collection | Identifies the info segments assigned to the user. Inherited from [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0). |
| isLicenseReconciliationNeeded | Boolean | Indicates whether the user is pending an exchange mailbox license assignment. Read-only. Inherited from [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0). |
| isManagementRestricted | Boolean | `true` if the user is a member of a restricted management administrative unit. If not set, the default value is `null` and the default behavior is false. Read-only. To manage a user who is a member of a restricted management administrative unit, the administrator or calling app must be assigned a Microsoft Entra role at the scope of the restricted management administrative unit. Inherited from [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0). |
| isResourceAccount | Boolean | Do not use – reserved for future use. Inherited from [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0). |
| jobTitle | String | The user's job title. Maximum length is 128 characters. Inherited from [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0). |
| licenseAssignmentStates | [licenseAssignmentState](https://learn.microsoft.com/en-us/graph/api/resources/licenseassignmentstate?view=graph-rest-1.0) collection | State of license assignments for this user. It also indicates licenses that are directly assigned and the ones the user inherited through group memberships. Read-only. Inherited from [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0). |
| mail | String | The SMTP address for the user, for example, `admin@contoso.com`. Changes to this property also update the user's **proxyAddresses** collection to include the value as an SMTP address. This property can't contain accent characters. NOTE: We don't recommend updating this property for Azure AD B2C user profiles. Use the **otherMails** property instead. Inherited from [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0). |
| mailNickname | String | The mail alias for the user. This property must be specified when a user is created. Maximum length is 64 characters. Inherited from [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0). |
| mobilePhone | String | The primary cellular telephone number for the user. Read-only for users synced from the on-premises directory. Inherited from [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0). |
| officeLocation | String | The office location in the user's place of business. Maximum length is 128 characters. Inherited from [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0). |
| otherMails | String collection | A list of additional email addresses for the user; for example: `["bob@contoso.com", "Robert@fabrikam.com"]`. Can store up to 250 values, each with a limit of 250 characters. NOTE: This property can't contain accent characters. Inherited from [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0). |
| postalCode | String | The postal code for the user's postal address. The postal code is specific to the user's country/region. In the United States of America, this attribute contains the ZIP code. Maximum length is 40 characters. Inherited from [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0). |
| preferredDataLocation | String | The preferred data location for the user. For more information, see [OneDrive Online Multi-Geo](https://learn.microsoft.com/en-us/sharepoint/dev/solution-guidance/multigeo-introduction). Inherited from [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0). |
| preferredLanguage | String | The preferred language for the user. The preferred language format is based on RFC 4646. The name combines an ISO 639 two-letter lowercase culture code associated with the language and an ISO 3166 two-letter uppercase subculture code associated with the country or region. Example: "en-US", or "es-ES". Inherited from [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0). |
| provisionedPlans | [provisionedPlan](https://learn.microsoft.com/en-us/graph/api/resources/provisionedplan?view=graph-rest-1.0) collection | The plans that are provisioned for the user. Read-only. Not nullable. Inherited from [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0). |
| proxyAddresses | String collection | For example: `["SMTP: bob@contoso.com", "smtp: bob@sales.contoso.com"]`. Changes to the **mail** property also update this collection to include the value as an SMTP address. For more information, see [mail and proxyAddresses properties](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0#mail-and-proxyaddresses-properties). The proxy address prefixed with `SMTP` \(capitalized\) is the primary proxy address, while the ones prefixed with `smtp` are the secondary proxy addresses. For Azure AD B2C accounts, this property has a limit of 10 unique addresses. Read-only in Microsoft Graph; you can update this property only through the [Microsoft 365 admin center](https://learn.microsoft.com/en-us/exchange/recipients-in-exchange-online/manage-user-mailboxes/add-or-remove-email-addresses). Not nullable. Inherited from [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0). |
| refreshTokensValidFromDateTime | DateTimeOffset | Any refresh tokens or sessions tokens \(session cookies\) issued before this time are invalid, and applications get an error when using an invalid refresh or sessions token to acquire a delegated access token \(to access APIs such as Microsoft Graph\). If it happens, the application must acquire a new refresh token by requesting the authorized endpoint. Read-only. Inherited from [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0). |
| securityIdentifier | String | Security identifier \(SID\) of the user, used in Windows scenarios. Read-only. Returned by default. Inherited from [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0). |
| showInAddressList | Boolean | **Do not use in Microsoft Graph. Manage this property through the Microsoft 365 admin center instead.** Represents whether the agent user should be included in the Outlook global address list. See [Known issue](https://learn.microsoft.com/en-us/graph/known-issues#showinaddresslist-property-is-out-of-sync-with-microsoft-exchange). Inherited from [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0). |
| signInSessionsValidFromDateTime | DateTimeOffset | Any refresh tokens or sessions tokens \(session cookies\) issued before this time are invalid, and applications get an error when using an invalid refresh or sessions token to acquire a delegated access token \(to access APIs such as Microsoft Graph\). If this happens, the application must acquire a new refresh token by requesting the authorized endpoint. Read-only. Use [revokeSignInSessions](https://learn.microsoft.com/en-us/graph/api/user-revokesigninsessions?view=graph-rest-1.0) to reset. Inherited from [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0). |
| state | String | The state or province in the agent user's address. Maximum length is 128 characters. Inherited from [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0). |
| streetAddress | String | The street address of the agent user's place of business. Maximum length is 1024 characters. Inherited from [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0). |
| surname | String | The user's surname \(family name or last name\). Maximum length is 64 characters. Inherited from [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0). |
| usageLocation | String | A two-letter country code \(ISO standard 3166\). Required for agent users that are assigned licenses due to legal requirements to check for availability of services in countries. Examples include: `US`, `JP`, and `GB`. Not nullable. Inherited from [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0). |
| userPrincipalName | String | The user principal name \(UPN\) of the agent user. The UPN is an Internet-style sign-in name for the user based on the Internet standard RFC 822. By convention, this should map to the agent user's email name. The general format is alias@domain, where the domain must be present in the tenant's verified domain collection. This property is required when a user is created. The verified domains for the tenant can be accessed from the **verifiedDomains** property of [organization](https://learn.microsoft.com/en-us/graph/api/resources/organization?view=graph-rest-1.0). NOTE: This property can't contain accent characters. Only the following characters are allowed `A - Z`, `a - z`, `0 - 9`, `' . - _ ! # ^ ~`. For the complete list of allowed characters, see [username policies](https://learn.microsoft.com/en-us/azure/active-directory/authentication/concept-sspr-policy#userprincipalname-policies-that-apply-to-all-user-accounts). Inherited from [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0). |
| userType | String | A String value that can be used to classify agent user types in your directory. The possible values are `Member` and `Guest`. **NOTE:** For more information about the permissions for member and guest users, see [What are the default user permissions in Microsoft Entra ID?](https://learn.microsoft.com/en-us/azure/active-directory/fundamentals/users-default-permissions?context=graph/context#member-and-guest-users) Inherited from [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0). |

## Relationships

Important

While this resource type inherits all relationships from the **user** resource type, some relationships are not applicable to agent users and will always return `null` or default values. These relationships are excluded from the table below for clarity.

| Relationship | Type | Description |
| :--- | :--- | :--- |
| appRoleAssignments | [appRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/approleassignment?view=graph-rest-1.0) collection | Represents the app roles an agent user has been granted for an application. Inherited from [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) |
| directReports | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | The users and contacts that report to the agent user. \(The users and contacts with their manager property set to this user.\) Read-only. Nullable. Inherited from [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) |
| manager | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) | The user or contact that is this agent user's manager. Read-only. Inherited from [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) |
| memberOf | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | The groups, directory roles, and administrative units that the agent user is a member of. Read-only. Nullable. Inherited from [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) |
| ownedObjects | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Directory objects owned by the agent user. Read-only. Nullable. Inherited from [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) |
| sponsors | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | The [users](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) and [groups](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0) responsible for this agent user's privileges in the tenant and keep the agent user's information and access updated. \(HTTP Methods: GET, POST, DELETE.\). Inherited from [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) |
| transitiveMemberOf | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | The groups, including nested groups and directory roles that the agent user is a member of. Nullable. Inherited from [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) |
| transitiveReports | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | The transitive reports for an agent user. Read-only. Inherited from [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.agentUser",
  "id": "String (identifier)",
  "deletedDateTime": "String (timestamp)",
  "accountEnabled": "Boolean",
  "assignedLicenses": [
    {
      "@odata.type": "microsoft.graph.assignedLicense"
    }
  ],
  "assignedPlans": [
    {
      "@odata.type": "microsoft.graph.assignedPlan"
    }
  ],
  "businessPhones": [
    "String"
  ],
  "city": "String",
  "companyName": "String",
  "country": "String",
  "countryCode": "Integer",
  "createdDateTime": "String (timestamp)",
  "creationType": "String",
  "customSecurityAttributes": {
    "@odata.type": "microsoft.graph.customSecurityAttributeValue"
  },
  "department": "String",
  "displayName": "String",
  "employeeHireDate": "String (timestamp)",
  "employeeId": "String",
  "employeeOrgData": {
    "@odata.type": "microsoft.graph.employeeOrgData"
  },
  "employeeType": "String",
  "employeeLeaveDateTime": "String (timestamp)",
  "faxNumber": "String",
  "givenName": "String",
  "imAddresses": [
    "String"
  ],
  "infoCatalogs": [
    "String"
  ],
  "isLicenseReconciliationNeeded": "Boolean",
  "isManagementRestricted": "Boolean",
  "isResourceAccount": "Boolean",
  "jobTitle": "String",
  "licenseAssignmentStates": [
    {
      "@odata.type": "microsoft.graph.licenseAssignmentState"
    }
  ],
  "mail": "String",
  "mailNickname": "String",
  "mobilePhone": "String",
  "otherMails": [
    "String"
  ],
  "officeLocation": "String",
  "postalCode": "String",
  "preferredDataLocation": "String",
  "preferredLanguage": "String",
  "provisionedPlans": [
    {
      "@odata.type": "microsoft.graph.provisionedPlan"
    }
  ],
  "proxyAddresses": [
    "String"
  ],
  "refreshTokensValidFromDateTime": "String (timestamp)",
  "securityIdentifier": "String",
  "showInAddressList": "Boolean",
  "signInSessionsValidFromDateTime": "String (timestamp)",
  "state": "String",
  "streetAddress": "String",
  "surname": "String",
  "usageLocation": "String",
  "userPrincipalName": "String",
  "userType": "String",
  "identityParentId": "String"
}
```
