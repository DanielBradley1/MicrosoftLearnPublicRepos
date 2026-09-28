<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-markuserascompromisedincidenttaskresponseaction?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-28 -->

# markUserAsCompromisedIncidentTaskResponseAction resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an action to mark a user account as compromised in Microsoft Defender XDR. This action sets the user's risk level to "high" in Microsoft Entra ID Protection, which can trigger conditional access policies and additional security measures.

Inherits from [microsoft.graph.security.incidentTaskResponseAction](https://learn.microsoft.com/en-us/graph/api/resources/security-incidenttaskresponseaction?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| identifierValue | String | Required. The identifier \(such as userPrincipalName or object ID\) of the user account to mark as compromised. Inherited from [microsoft.graph.security.incidentTaskResponseAction](https://learn.microsoft.com/en-us/graph/api/resources/security-incidenttaskresponseaction?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.markUserAsCompromisedIncidentTaskResponseAction",
  "identifierValue": "String"
}
```
