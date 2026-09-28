<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/passwordresetresponse?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-09-11 -->

# passwordResetResponse resource type

Namespace: microsoft.graph

Represents the new system-generated password after a [password reset operation](https://learn.microsoft.com/en-us/graph/api/authenticationmethod-resetpassword?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| newPassword | String | The Microsoft Entra ID-generated password. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.passwordResetResponse",
  "newPassword": "String"
}
```
