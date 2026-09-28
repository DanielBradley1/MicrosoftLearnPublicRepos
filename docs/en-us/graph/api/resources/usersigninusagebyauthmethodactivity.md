<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/usersigninusagebyauthmethodactivity?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-12 -->

# userSignInUsageByAuthMethodActivity resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the summary of the number of successful sign-ins for each authentication method enabled on the tenant.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/authenticationmethodsroot-usersigninsbyauthmethodsummary?view=graph-rest-beta) | [userSignInUsageByAuthMethodActivity](https://learn.microsoft.com/en-us/graph/api/resources/usersigninusagebyauthmethodactivity?view=graph-rest-beta) collection | Get the number of successful sign ins for each authentication method. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| authenticationMethod | String | The authentication method for the given summary. |
| successActivityCount | Int64 | The total number of successful sign in events for the given authentication method. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.userSignInUsageByAuthMethodActivity",
  "authenticationMethod": "String (identifier)",
  "successActivityCount": "Int64"
}
```
