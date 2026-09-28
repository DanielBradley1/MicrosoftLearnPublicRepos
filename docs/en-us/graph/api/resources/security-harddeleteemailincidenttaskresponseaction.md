<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-harddeleteemailincidenttaskresponseaction?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-28 -->

# hardDeleteEmailIncidentTaskResponseAction resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an action to permanently delete an email message in Microsoft Defender XDR. This action is used when a malicious or compromised email needs to be completely removed from the system, with no possibility of recovery.

Inherits from [microsoft.graph.security.incidentTaskResponseAction](https://learn.microsoft.com/en-us/graph/api/resources/security-incidenttaskresponseaction?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| identifierValue | String | Required. The identifier of the email message to be permanently deleted \(such as the message ID or network message ID\). Inherited from [microsoft.graph.security.incidentTaskResponseAction](https://learn.microsoft.com/en-us/graph/api/resources/security-incidenttaskresponseaction?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.hardDeleteEmailIncidentTaskResponseAction",
  "identifierValue": "String"
}
```
