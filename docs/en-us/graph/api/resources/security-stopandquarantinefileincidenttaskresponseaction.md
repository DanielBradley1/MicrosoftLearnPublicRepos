<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-stopandquarantinefileincidenttaskresponseaction?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-28 -->

# stopAndQuarantineFileIncidentTaskResponseAction resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an action to stop and quarantine a potentially malicious file in Microsoft Defender XDR. This action halts any running instances of the file and moves it to a secure location where it cannot harm the system, allowing for further investigation of the threat.

Inherits from [microsoft.graph.security.incidentTaskResponseAction](https://learn.microsoft.com/en-us/graph/api/resources/security-incidenttaskresponseaction?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| deviceId | String | Optional. The identifier of the device where the file is located. This property allows targeting the action to a specific device when the same file exists on multiple devices. |
| identifierValue | String | Required. The identifier \(such as SHA1 hash\) of the file to be stopped and quarantined. Inherited from [microsoft.graph.security.incidentTaskResponseAction](https://learn.microsoft.com/en-us/graph/api/resources/security-incidenttaskresponseaction?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.stopAndQuarantineFileIncidentTaskResponseAction",
  "identifierValue": "String",
  "deviceId": "String"
}
```
