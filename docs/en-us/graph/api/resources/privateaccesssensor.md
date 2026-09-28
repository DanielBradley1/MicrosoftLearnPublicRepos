<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/privateaccesssensor?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-06 -->

# privateAccessSensor resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

A lightweight agent installed on domain controllers that helps secure access and enforce MFA to on-premise resources. For more information, see [Configure Microsoft Entra Private Access for Active Directory domain controllers \(preview\)](https://learn.microsoft.com/en-us/entra/global-secure-access/how-to-configure-domain-controllers).

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/onpremisespublishingprofile-list-sensors?view=graph-rest-beta) | [privateAccessSensor](https://learn.microsoft.com/en-us/graph/api/resources/privateaccesssensor?view=graph-rest-beta) collection | Get a list of the privateAccessSensor objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/privateaccesssensor-get?view=graph-rest-beta) | [privateAccessSensor](https://learn.microsoft.com/en-us/graph/api/resources/privateaccesssensor?view=graph-rest-beta) | Read the properties and relationships of a privateAccessSensor object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| externalIp | String | External IP of sensor. |
| id | String | Unique ID of the sensor. Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta) |
| isAuditMode | Boolean | Not Implementated. |
| isBreakglassEnabled | Boolean | Not Implemented. |
| machineName | String | Machine name of sensor. |
| version | String | Version of sensor. |
| status | microsoft.graph.sensorStatus | The possible values are: `active`, `inactive`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.privateAccessSensor",
  "id": "String (identifier)",
  "machineName": "String",
  "externalIp": "String",
  "version": "String",
  "status": "String",
  "isBreakglassEnabled": "Boolean",
  "isAuditMode": "Boolean"
}
```
