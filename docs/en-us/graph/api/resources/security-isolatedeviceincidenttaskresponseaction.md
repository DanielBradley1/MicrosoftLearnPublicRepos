<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-isolatedeviceincidenttaskresponseaction?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-28 -->

# isolateDeviceIncidentTaskResponseAction resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an action to isolate a device from the network in Microsoft Defender XDR. This action restricts a potentially compromised device's network connectivity to prevent lateral movement or data exfiltration while allowing for investigation and remediation.

Inherits from [microsoft.graph.security.incidentTaskResponseAction](https://learn.microsoft.com/en-us/graph/api/resources/security-incidenttaskresponseaction?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| identifierValue | String | Required. The identifier of the device to isolate \(such as device ID or computer name\). Inherited from [microsoft.graph.security.incidentTaskResponseAction](https://learn.microsoft.com/en-us/graph/api/resources/security-incidenttaskresponseaction?view=graph-rest-beta). |
| isolationType | microsoft.graph.security.isolationType | Required. The type of network isolation to apply. The possible values are: `full` \(complete network isolation\), `selective` \(allows access to specific network resources\), `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.isolateDeviceIncidentTaskResponseAction",
  "identifierValue": "String",
  "isolationType": "String"
}
```
