<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/industrydata-administrativeunitprovisioningflow?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# administrativeUnitProvisioningFlow resource type

Namespace: microsoft.graph.industryData

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the parameters that school data sync uses to create administrative units from your inbound data. Administrative units provide a grouping construct for delegated IT administration and scoped role assignments. Scoped role assignments allow admins to manage a subset of the broader Microsoft 365 directory.

administrativeUnitProvisioningFlow is defined within an [outboundProvisioningFlowSet](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-outboundprovisioningflowset?view=graph-rest-beta) that may specify a filter based on a subset of available organizations \(schools\) or may include all of the organizations in the inbound data.

There may be multiple administrativeUnitProvisioningFlows, defined within separate outboundProvsioningFlowSets allowing different configurations for different organizations.

Inherits from [microsoft.graph.industryData.provisioningFlow](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-provisioningflow?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/industrydata-administrativeunitprovisioningflow-get?view=graph-rest-beta) | [microsoft.graph.industryData.administrativeUnitProvisioningFlow](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-administrativeunitprovisioningflow?view=graph-rest-beta) | Read the properties and relationships of an administrativeunitprovisioningflow object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/industrydata-administrativeunitprovisioningflow-update?view=graph-rest-beta) | [microsoft.graph.industryData.administrativeUnitProvisioningFlow](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-administrativeunitprovisioningflow?view=graph-rest-beta) | Update the properties of an administrativeunitprovisioningflow object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/industrydata-administrativeunitprovisioningflow-delete?view=graph-rest-beta) | None | Delete an administrativeunitprovisioningflow object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | Inherited from [microsoft.graph.industryData.provisioningFlow](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-provisioningflow?view=graph-rest-beta). |
| creationOptions | [microsoft.graph.industryData.adminUnitCreationOptions](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-adminunitcreationoptions?view=graph-rest-beta) | The different attribute choices for the administrative units to be provisioned. |
| id | String | Inherited from [microsoft.graph.industryData.provisioningFlow](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-provisioningflow?view=graph-rest-beta). |
| lastModifiedDateTime | DateTimeOffset | Inherited from [microsoft.graph.industryData.provisioningFlow](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-provisioningflow?view=graph-rest-beta). |
| readinessStatus | microsoft.graph.industryData.readinessStatus | Inherited from [microsoft.graph.industryData.provisioningFlow](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-provisioningflow?view=graph-rest-beta). The possible values are: `notReady`, `ready`, `failed`, `disabled`, `expired`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.industryData.administrativeUnitProvisioningFlow",
  "createdDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)",
  "readinessStatus": "String",
  "id": "String (identifier)",
  "creationOptions": {
    "@odata.type": "microsoft.graph.industryData.adminUnitCreationOptions"
  }
}
```
