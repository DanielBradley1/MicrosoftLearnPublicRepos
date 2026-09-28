<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/userregistrationmethodsummary?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# userRegistrationMethodSummary resource type

Namespace: microsoft.graph

Represents the summary of number of users registered for each authentication method. For more information about license requirements for this feature, see [Authentication Methods Activity: Permissions and licenses](https://learn.microsoft.com/en-us/entra/identity/authentication/howto-authentication-methods-activity#permissions-and-licenses).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/authenticationmethodsroot-usersregisteredbymethod?view=graph-rest-1.0) | [userRegistrationMethodSummary](https://learn.microsoft.com/en-us/graph/api/resources/userregistrationmethodsummary?view=graph-rest-1.0) | Get the number of users registered for each authentication method. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| totalUserCount | Int64 | Total number of users in the tenant. |
| userRegistrationMethodCounts | [userRegistrationMethodCount](https://learn.microsoft.com/en-us/graph/api/resources/userregistrationmethodcount?view=graph-rest-1.0) collection | Number of users registered for each authentication method. |
| userRoles | includedUserRoles | The role type of the user. The possible values are: `all`, `privilegedAdmin`, `admin`, `user`, `unknownFutureValue`. |
| userTypes | includedUserTypes | User type. The possible values are: `all`, `member`, `guest`, `unknownFutureValue`. |

The value `privilegedAdmin` consists of the following [Microsoft Entra roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json).

- Global Administrator
- Security Administrator
- Conditional Access Administrator
- Exchange Administrator
- SharePoint Administrator
- Helpdesk Administrator
- Billing Administrator
- User Administrator
- Authentication Administrator

The value `admin` includes all Microsoft Entra admin roles.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.userRegistrationMethodSummary",
  "totalUserCount": "Int64",
  "userRegistrationMethodCounts": [{"@odata.type": "microsoft.graph.userRegistrationMethodCount"}],
  "userRoles": "String",
  "userTypes": "String"
}
```
