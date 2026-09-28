<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-user?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-03-12 -->

# user resource type \(Global Secure Access user\)

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Unique Microsoft Entra ID user identified by the Global Secure Access services.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | User display Name. |
| lastAccessDateTime | DateTimeOffset | The date and time of the most recent access. |
| trafficType | microsoft.graph.networkaccess.trafficType | The traffic classification. The possible values are `internet`, `private`, `microsoft365`, and `all`. |
| userId | String | The ID for the user. |
| userPrincipalName | String | A unique identifier that is associated with a user in a system or directory. Typically, this value is an email address that is used for user authentication and identification. |
| userType | microsoft.graph.networkaccess.userType | The user type. The possible values are `member`, `guest`, and `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.user",
  "displayName": "String",
  "userPrincipalName": "String",
  "userId": "String",
  "userType": "String",
  "trafficType": "String",
  "lastAccessDateTime": "String (timestamp)"
}
```
