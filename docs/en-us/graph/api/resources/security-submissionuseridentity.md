<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-submissionuseridentity?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# submissionUserIdentity resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the identity of the user who sends the threat submission.

Inherits from [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Inherited from **identity**. |
| email | String | The email of user who is making the submission when logged in \(delegated token case\). |
| id | String | Inherited from **identity**. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.submissionUserIdentity",
  "displayName": "String",
  "id": "String (identifier)",
  "email": "String"
}
```
