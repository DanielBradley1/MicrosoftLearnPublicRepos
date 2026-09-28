<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/signinactivity?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-05 -->

# signInActivity resource type

Namespace: microsoft.graph

Provides the last interactive or non-interactive sign-in *attempt* time for a specific [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0). Because **signInActivity** describes a property of the user object, Microsoft Entra ID stores sign-in activity for your users for as long as the user object exists.

Effective December 1, 2023, the **lastSuccessfulSignInDateTime** property is available to provide the last *successful* sign-in time for a specific user, regardless of whether the sign-in was interactive or non-interactive. The data isn't backfilled for this property.

See an example of [getting the **signInActivity** details](https://learn.microsoft.com/en-us/graph/api/user-list?view=graph-rest-1.0#example-11-get-users-including-their-last-sign-in-time).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| lastNonInteractiveSignInDateTime | DateTimeOffset | The last non-interactive sign-in date for a specific user. You can use this field to calculate the last time a client attempted \(either successfully or unsuccessfully\) to sign in to the directory on behalf of a user. Because some users may use clients to access tenant resources rather than signing into your tenant directly, you can use the non-interactive sign-in date to along with lastSignInDateTime to identify inactive users. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Microsoft Entra ID maintains non-interactive sign-ins going back to May 2020. For more information about using the value of this property, see [Manage inactive user accounts in Microsoft Entra ID](https://learn.microsoft.com/en-us/azure/active-directory/reports-monitoring/howto-manage-inactive-user-accounts). |
| lastNonInteractiveSignInRequestId | String | Request identifier of the last non-interactive sign-in performed by this user. |
| lastSignInDateTime | DateTimeOffset | The last interactive sign-in date and time for a specific user. This property records the last time a user attempted an interactive sign-in to the directory—whether the attempt was successful or not. Note: Since unsuccessful attempts are also logged, this value might not accurately reflect actual system usage. For tracking actual account access, please use the lastSuccessfulSignInDateTime property. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| lastSignInRequestId | String | Request identifier of the last interactive sign-in performed by this user. |
| lastSuccessfulSignInDateTime | DateTimeOffset | The date and time of the user's most recent successful interactive or non-interactive sign-in. Use this property if you need to determine when the account was truly accessed. This field can be used to build reports, such as inactive users. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Microsoft Entra ID maintains interactive sign-ins going back to April 2020. For more information about using the value of this property, see [Manage inactive user accounts in Microsoft Entra ID](https://learn.microsoft.com/en-us/azure/active-directory/reports-monitoring/howto-manage-inactive-user-accounts). |
| lastSuccessfulSignInRequestId | String | The request ID of the last successful sign-in. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.signInActivity",
  "lastNonInteractiveSignInDateTime": "String (timestamp)",
  "lastNonInteractiveSignInRequestId": "String",
  "lastSignInDateTime": "String (timestamp)",
  "lastSignInRequestId": "String",
  "lastSuccessfulSignInDateTime": "String (timestamp)",
  "lastSuccessfulSignInRequestId": "String"
}
```
