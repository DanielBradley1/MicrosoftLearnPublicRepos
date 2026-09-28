<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-unrestrictappexecutionincidenttaskresponseaction?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-28 -->

# unRestrictAppExecutionIncidentTaskResponseAction resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an action to remove application execution restrictions from a device in Microsoft Defender XDR. This action reverts previous restrictions that limited application execution to only Microsoft-signed executables, restoring normal application execution capabilities on the device.

Inherits from [microsoft.graph.security.incidentTaskResponseAction](https://learn.microsoft.com/en-us/graph/api/resources/security-incidenttaskresponseaction?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| identifierValue | String | Required. The identifier of the device from which to remove application execution restrictions. Inherited from [microsoft.graph.security.incidentTaskResponseAction](https://learn.microsoft.com/en-us/graph/api/resources/security-incidenttaskresponseaction?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.unRestrictAppExecutionIncidentTaskResponseAction",
  "identifierValue": "String"
}
```
