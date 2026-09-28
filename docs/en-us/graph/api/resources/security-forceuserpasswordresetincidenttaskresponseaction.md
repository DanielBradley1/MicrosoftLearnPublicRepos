<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-forceuserpasswordresetincidenttaskresponseaction?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-28 -->

# forceUserPasswordResetIncidentTaskResponseAction resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an action to force a user to reset their password in Microsoft Defender XDR. This action is typically used when there's a suspicion that a user's credentials have been compromised, requiring them to create a new password at their next sign-in attempt.

Inherits from [microsoft.graph.security.incidentTaskResponseAction](https://learn.microsoft.com/en-us/graph/api/resources/security-incidenttaskresponseaction?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| identifierValue | String | Required. The identifier \(such as userPrincipalName or object ID\) of the user who will be required to reset their password. Inherited from [microsoft.graph.security.incidentTaskResponseAction](https://learn.microsoft.com/en-us/graph/api/resources/security-incidenttaskresponseaction?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.forceUserPasswordResetIncidentTaskResponseAction",
  "identifierValue": "String"
}
```
