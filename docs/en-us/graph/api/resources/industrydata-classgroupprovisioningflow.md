<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/industrydata-classgroupprovisioningflow?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# classGroupProvisioningFlow resource type

Namespace: microsoft.graph.industryData

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the parameters that school data sync uses to create class groups and teams in Microsoft 365 from your inbound data. Class groups allow users to connect, communicate, and collaborate across various Microsoft 365 applications including Teams.

classGroupProvisioningFlow is defined within an [outboundProvisioningFlowSet](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-outboundprovisioningflowset?view=graph-rest-beta) that may specify a filter based on a subset of available organizations \(schools\) or may include all of the organizations in the inbound data.

There may be multiple classGroupProvisioningFlows, defined within separate OutboundProvsioningFlowSets \(editor note, hyperlink to related docs\) allowing different configurations for different organizations.

Inherits from [microsoft.graph.industryData.provisioningFlow](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-provisioningflow?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/industrydata-classgroupprovisioningflow-get?view=graph-rest-beta) | [microsoft.graph.industryData.classGroupProvisioningFlow](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-classgroupprovisioningflow?view=graph-rest-beta) | Read the properties and relationships of a classgroupprovisioningflow object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/industrydata-classgroupprovisioningflow-update?view=graph-rest-beta) | [microsoft.graph.industryData.classGroupProvisioningFlow](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-classgroupprovisioningflow?view=graph-rest-beta) | Update the properties of a classgroupprovisioningflow object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/industrydata-classgroupprovisioningflow-delete?view=graph-rest-beta) | None. | Delete a classgroupprovisioningflow object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| configuration | [microsoft.graph.industryData.classGroupConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-classgroupconfiguration?view=graph-rest-beta) | The different attribute choices for the class groups to be provisioned. |
| createdDateTime | DateTimeOffset | Inherited from [microsoft.graph.industryData.provisioningFlow](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-provisioningflow?view=graph-rest-beta). |
| id | String | Inherited from [microsoft.graph.industryData.provisioningFlow](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-provisioningflow?view=graph-rest-beta). |
| lastModifiedDateTime | DateTimeOffset | Inherited from [microsoft.graph.industryData.provisioningFlow](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-provisioningflow?view=graph-rest-beta). |
| readinessStatus | microsoft.graph.industryData.readinessStatus | Inherited from [microsoft.graph.industryData.provisioningFlow](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-provisioningflow?view=graph-rest-beta). The possible values are: `notReady`, `ready`, `failed`, `disabled`, `expired`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.industryData.classGroupProvisioningFlow",
  "createdDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)",
  "readinessStatus": "String",
  "id": "String (identifier)",
  "configuration": {
    "@odata.type": "microsoft.graph.industryData.classGroupConfiguration"
  }
}
```
