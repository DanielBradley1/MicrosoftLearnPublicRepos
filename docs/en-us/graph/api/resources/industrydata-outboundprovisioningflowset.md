<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/industrydata-outboundprovisioningflowset?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# outboundProvisioningFlowSet resource type

Namespace: microsoft.graph.industryData

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a collection of outbound provisioning flows used to configure how school data sync populates data in Microsoft 365 and Microsoft Entra ID. A flow set may specify a filter based on a subset of available organizations \(schools\) or may include all of the organizations in the inbound data. There may be multiple outboundProvisioningFlowSets, allowing different configurations for different organizations. Each outbound provisioning flow set doesn't need to include every provisioning flow type.

Outbound provisioning flow set may contain no more than one \(1\) of each provisioning flow configuration that is being configured: [userProvisioningFlow](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-userprovisioningflow?view=graph-rest-beta), [classGroupProvisioingFlow](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-classgroupprovisioningflow?view=graph-rest-beta), [securityGroupProvisioingFlow](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-securitygroupprovisioningflow?view=graph-rest-beta), [administrativeUnitProvisioingFlow](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-administrativeunitprovisioningflow?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List outboundProvisioningFlowSet objects](https://learn.microsoft.com/en-us/graph/api/industrydata-industrydataroot-list-outboundprovisioningflowsets?view=graph-rest-beta) | [microsoft.graph.industryData.outboundProvisioningFlowSet](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-outboundprovisioningflowset?view=graph-rest-beta) collection | Get a list of outboundprovisioningflowset objects and their properties. |
| [Create outboundProvisioningFlowSet](https://learn.microsoft.com/en-us/graph/api/industrydata-industrydataroot-post-outboundprovisioningflowsets?view=graph-rest-beta) | [microsoft.graph.industryData.outboundProvisioningFlowSet](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-outboundprovisioningflowset?view=graph-rest-beta) | Create a new outboundprovisioningflowset object. |
| [Get outboundProvisioningFlowSet](https://learn.microsoft.com/en-us/graph/api/industrydata-outboundprovisioningflowset-get?view=graph-rest-beta) | [microsoft.graph.industryData.outboundProvisioningFlowSet](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-outboundprovisioningflowset?view=graph-rest-beta) | Read the properties and relationships of an outboundprovisioningflowset object. |
| [Update outboundProvisioningFlowSet](https://learn.microsoft.com/en-us/graph/api/industrydata-outboundprovisioningflowset-update?view=graph-rest-beta) | [microsoft.graph.industryData.outboundProvisioningFlowSet](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-outboundprovisioningflowset?view=graph-rest-beta) | Update the properties of an outboundprovisioningflowset object. |
| [Delete outboundProvisioningFlowSet](https://learn.microsoft.com/en-us/graph/api/industrydata-industrydataroot-delete-outboundprovisioningflowsets?view=graph-rest-beta) | None | Delete an outboundprovisioningflowset object. |
| [List provisioningFlows](https://learn.microsoft.com/en-us/graph/api/industrydata-outboundprovisioningflowset-list-provisioningflows?view=graph-rest-beta) | [microsoft.graph.industryData.provisioningFlow](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-provisioningflow?view=graph-rest-beta) collection | Get the provisioningFlow resources from the provisioningFlows navigation property. |
| [Create provisioningFlow](https://learn.microsoft.com/en-us/graph/api/industrydata-outboundprovisioningflowset-post-provisioningflows?view=graph-rest-beta) | [microsoft.graph.industryData.provisioningFlow](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-provisioningflow?view=graph-rest-beta) | Create a new provisioningFlow object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | The date and time when the flowSet was created. The timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| displayName | String | The display name of the flowSet provided by the caller. |
| filter | [microsoft.graph.industryData.filter](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-filter?view=graph-rest-beta) | The collection of provisioning filters applicable to all the flows under the given flowSet. |
| id | String | The unique identifier for the flowSet. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| lastModifiedDateTime | DateTimeOffset | The date and time when the flowSet was most recently changed. The timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| provisioningFlows | [microsoft.graph.industryData.provisioningFlow](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-provisioningflow?view=graph-rest-beta) collection | A flow that provisions relevant records of a given entity type in the Microsoft 365 tenant. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.industryData.outboundProvisioningFlowSet",
  "displayName": "String",
  "createdDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "filter": {
    "@odata.type": "microsoft.graph.industryData.filter"
  }
}
```
