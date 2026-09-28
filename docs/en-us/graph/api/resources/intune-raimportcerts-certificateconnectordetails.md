<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-raimportcerts-certificateconnectordetails?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# certificateConnectorDetails resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Entity used to retrieve information about Intune Certificate Connectors.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List certificateConnectorDetailses](https://learn.microsoft.com/en-us/graph/api/intune-raimportcerts-certificateconnectordetails-list?view=graph-rest-beta) | [certificateConnectorDetails](https://learn.microsoft.com/en-us/graph/api/resources/intune-raimportcerts-certificateconnectordetails?view=graph-rest-beta) collection | List properties and relationships of the [certificateConnectorDetails](https://learn.microsoft.com/en-us/graph/api/resources/intune-raimportcerts-certificateconnectordetails?view=graph-rest-beta) objects. |
| [Get certificateConnectorDetails](https://learn.microsoft.com/en-us/graph/api/intune-raimportcerts-certificateconnectordetails-get?view=graph-rest-beta) | [certificateConnectorDetails](https://learn.microsoft.com/en-us/graph/api/resources/intune-raimportcerts-certificateconnectordetails?view=graph-rest-beta) | Read properties and relationships of the [certificateConnectorDetails](https://learn.microsoft.com/en-us/graph/api/resources/intune-raimportcerts-certificateconnectordetails?view=graph-rest-beta) object. |
| [Create certificateConnectorDetails](https://learn.microsoft.com/en-us/graph/api/intune-raimportcerts-certificateconnectordetails-create?view=graph-rest-beta) | [certificateConnectorDetails](https://learn.microsoft.com/en-us/graph/api/resources/intune-raimportcerts-certificateconnectordetails?view=graph-rest-beta) | Create a new [certificateConnectorDetails](https://learn.microsoft.com/en-us/graph/api/resources/intune-raimportcerts-certificateconnectordetails?view=graph-rest-beta) object. |
| [Delete certificateConnectorDetails](https://learn.microsoft.com/en-us/graph/api/intune-raimportcerts-certificateconnectordetails-delete?view=graph-rest-beta) | None | Deletes a [certificateConnectorDetails](https://learn.microsoft.com/en-us/graph/api/resources/intune-raimportcerts-certificateconnectordetails?view=graph-rest-beta). |
| [Update certificateConnectorDetails](https://learn.microsoft.com/en-us/graph/api/intune-raimportcerts-certificateconnectordetails-update?view=graph-rest-beta) | [certificateConnectorDetails](https://learn.microsoft.com/en-us/graph/api/resources/intune-raimportcerts-certificateconnectordetails?view=graph-rest-beta) | Update the properties of a [certificateConnectorDetails](https://learn.microsoft.com/en-us/graph/api/resources/intune-raimportcerts-certificateconnectordetails?view=graph-rest-beta) object. |
| [getHealthMetrics action](https://learn.microsoft.com/en-us/graph/api/intune-raimportcerts-certificateconnectordetails-gethealthmetrics?view=graph-rest-beta) | [keyLongValuePair](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-keylongvaluepair?view=graph-rest-beta) collection |  |
| [getHealthMetricTimeSeries action](https://learn.microsoft.com/en-us/graph/api/intune-raimportcerts-certificateconnectordetails-gethealthmetrictimeseries?view=graph-rest-beta) | [certificateConnectorHealthMetricValue](https://learn.microsoft.com/en-us/graph/api/resources/intune-raimportcerts-certificateconnectorhealthmetricvalue?view=graph-rest-beta) collection |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier for this set of ConnectorDetails. |
| connectorName | String | Connector name \(set during enrollment\). |
| machineName | String | Name of the machine hosting this connector service. |
| enrollmentDateTime | DateTimeOffset | Date/time when this connector was enrolled. |
| lastCheckinDateTime | DateTimeOffset | Date/time when this connector last connected to the service. |
| connectorVersion | String | Version of the connector installed. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.certificateConnectorDetails",
  "id": "String (identifier)",
  "connectorName": "String",
  "machineName": "String",
  "enrollmentDateTime": "String (timestamp)",
  "lastCheckinDateTime": "String (timestamp)",
  "connectorVersion": "String"
}
```
