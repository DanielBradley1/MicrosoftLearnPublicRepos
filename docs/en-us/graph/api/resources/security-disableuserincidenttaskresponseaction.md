<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-disableuserincidenttaskresponseaction?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-28 -->

# disableUserIncidentTaskResponseAction resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an action to temporarily disable a user account in response to a security incident in Microsoft Defender XDR. This action prevents the user from logging in to prevent potential unauthorized access.

Inherits from [microsoft.graph.security.incidentTaskResponseAction](https://learn.microsoft.com/en-us/graph/api/resources/security-incidenttaskresponseaction?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| identifierValue | String | Required. The identifier \(such as userPrincipalName or object ID\) of the user account to disable. Inherited from [microsoft.graph.security.incidentTaskResponseAction](https://learn.microsoft.com/en-us/graph/api/resources/security-incidenttaskresponseaction?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.disableUserIncidentTaskResponseAction",
  "identifierValue": "String"
}
```
