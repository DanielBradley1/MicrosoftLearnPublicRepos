<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/conversionuserdetails?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-31 -->

# conversionUserDetails resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents information that the API returns after a user is [converted from external to internal](https://learn.microsoft.com/en-us/graph/api/user-convertexternaltointernalmemberuser?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| convertedToInternalDateTime | DateTimeOffset | The date and time the user was converted from external to internal. |
| displayName | String | Name displayed for the user. |
| mail | String | The SMTP address for the user. |
| userPrincipalName | String | The user principal name \(UPN\) of the user. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
    "@odata.type": "#microsoft.graph.conversionUserDetails",
    "displayName": "String",
    "userPrincipalName": "String",
    "convertedToInternalUserDateTime": "String (timestamp)",
    "mail": "String"
}
```
