<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/industrydata-securitygroupprovisioningflow?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# securityGroupProvisioningFlow resource type

Namespace: microsoft.graph.industryData

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the parameters that school data sync uses to create security groups and teams in Microsoft 365 from your inbound data. Security groups provide a grouping construct for use within various identity management, application management, and device management scenarios in Microsoft 365.

securityGroupProvisioningFlow is defined within an [outboundProvisioningFlowSet](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-outboundprovisioningflowset?view=graph-rest-beta) that may specify a filter based on a subset of available organizations \(schools\) or may include all of the organizations in the inbound data.

There may be multiple securityGroupProvisioningFlows, defined within separate outboundProvsioningFlowSets allowing different configurations for different organizations.

Inherits from [microsoft.graph.industryData.provisioningFlow](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-provisioningflow?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/industrydata-securitygroupprovisioningflow-get?view=graph-rest-beta) | [microsoft.graph.industryData.securityGroupProvisioningFlow](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-securitygroupprovisioningflow?view=graph-rest-beta) | Read the properties and relationships of a securitygroupprovisioningflow object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/industrydata-securitygroupprovisioningflow-update?view=graph-rest-beta) | [microsoft.graph.industryData.securityGroupProvisioningFlow](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-securitygroupprovisioningflow?view=graph-rest-beta) | Update the properties of a securitygroupprovisioningflow object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/industrydata-securitygroupprovisioningflow-delete?view=graph-rest-beta) | None | Delete a securitygroupprovisioningflow object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | Inherited from [microsoft.graph.industryData.provisioningFlow](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-provisioningflow?view=graph-rest-beta). |
| creationOptions | [microsoft.graph.industryData.securityGroupCreationOptions](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-securitygroupcreationoptions?view=graph-rest-beta) | The different attribute choices for the class groups to be provisioned. |
| id | String | Inherited from [microsoft.graph.industryData.provisioningFlow](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-provisioningflow?view=graph-rest-beta). |
| lastModifiedDateTime | DateTimeOffset | Inherited from [microsoft.graph.industryData.provisioningFlow](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-provisioningflow?view=graph-rest-beta). |
| readinessStatus | microsoft.graph.industryData.readinessStatus | Inherited from [microsoft.graph.industryData.provisioningFlow](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-provisioningflow?view=graph-rest-beta). The possible values are: `notReady`, `ready`, `failed`, `disabled`, `expired`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.industryData.securityGroupProvisioningFlow",
  "createdDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)",
  "readinessStatus": "String",
  "id": "String (identifier)",
  "creationOptions": {
    "@odata.type": "microsoft.graph.industryData.securityGroupCreationOptions"
  }
}
```
