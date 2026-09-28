<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-restrictappexecutionincidenttaskresponseaction?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-28 -->

# restrictAppExecutionIncidentTaskResponseAction resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an action to restrict application execution on a device in Microsoft Defender XDR. This action configures the device to allow only executables that are signed with a Microsoft-issued certificate to run, helping prevent the execution of potentially malicious software.

Inherits from [microsoft.graph.security.incidentTaskResponseAction](https://learn.microsoft.com/en-us/graph/api/resources/security-incidenttaskresponseaction?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| identifierValue | String | Required. The identifier of the device on which to restrict application execution. Inherited from [microsoft.graph.security.incidentTaskResponseAction](https://learn.microsoft.com/en-us/graph/api/resources/security-incidenttaskresponseaction?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.restrictAppExecutionIncidentTaskResponseAction",
  "identifierValue": "String"
}
```
