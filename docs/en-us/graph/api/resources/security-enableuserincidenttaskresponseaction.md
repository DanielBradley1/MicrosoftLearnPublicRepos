<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-enableuserincidenttaskresponseaction?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-28 -->

# enableUserIncidentTaskResponseAction resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an action to re-enable a previously disabled user account in Microsoft Defender XDR. This action restores the user's ability to log in after their account was disabled due to a security incident.

Inherits from [microsoft.graph.security.incidentTaskResponseAction](https://learn.microsoft.com/en-us/graph/api/resources/security-incidenttaskresponseaction?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| identifierValue | String | Required. The identifier \(such as userPrincipalName or object ID\) of the user account to enable. Inherited from [microsoft.graph.security.incidentTaskResponseAction](https://learn.microsoft.com/en-us/graph/api/resources/security-incidenttaskresponseaction?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.enableUserIncidentTaskResponseAction",
  "identifierValue": "String"
}
```
