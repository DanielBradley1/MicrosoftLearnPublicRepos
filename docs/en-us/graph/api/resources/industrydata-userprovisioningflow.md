<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/industrydata-userprovisioningflow?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-08-01 -->

# userProvisioningFlow resource type

Namespace: microsoft.graph.industryData

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the configuration parameters that allow you to automate creation and matching to Microsoft 365 users from your inbound data.

userProvisioningFlow is defined within an [outboundProvisioningFlowSet](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-outboundprovisioningflowset?view=graph-rest-beta) that may specify a filter based on a subset of available organizations \(schools\) or may include all of the organizations in the inbound data.

There may be multiple userProvisioningFlows, defined within separate outboundProvsioningFlowSets allowing different configurations for different organizations.

Inherits from [microsoft.graph.industryData.provisioningFlow](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-provisioningflow?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/industrydata-userprovisioningflow-get?view=graph-rest-beta) | [microsoft.graph.industryData.userProvisioningFlow](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-userprovisioningflow?view=graph-rest-beta) | Read the properties and relationships of a userprovisioningflow object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/industrydata-userprovisioningflow-update?view=graph-rest-beta) | [microsoft.graph.industryData.userProvisioningFlow](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-userprovisioningflow?view=graph-rest-beta) | Update the properties of a userprovisioningflow object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/industrydata-userprovisioningflow-delete?view=graph-rest-beta) | None | Delete a userprovisioningflow object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | Inherited from [microsoft.graph.industryData.provisioningFlow](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-provisioningflow?view=graph-rest-beta). |
| createUnmatchedUsers | Boolean | A Boolean choice indicating whether unmatched users should be created or ignored. |
| creationOptions | [microsoft.graph.industryData.userCreationOptions](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-usercreationoptions?view=graph-rest-beta) | The different management choices for the new users to be provisioned. |
| id | String | Inherited from [microsoft.graph.industryData.provisioningFlow](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-provisioningflow?view=graph-rest-beta). |
| lastModifiedDateTime | DateTimeOffset | Inherited from [microsoft.graph.industryData.provisioningFlow](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-provisioningflow?view=graph-rest-beta). |
| managementOptions | [microsoft.graph.industryData.userManagementOptions](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-usermanagementoptions?view=graph-rest-beta) | The different attribute choices for all the users to be considered. |
| readinessStatus | microsoft.graph.industryData.readinessStatus | Inherited from [microsoft.graph.industryData.provisioningFlow](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-provisioningflow?view=graph-rest-beta). The possible values are: `notReady`, `ready`, `failed`, `disabled`, `expired`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.industryData.userProvisioningFlow",
  "createdDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)",
  "readinessStatus": "String",
  "id": "String (identifier)",
  "createUnmatchedUsers": "Boolean",
  "managementOptions": {
    "@odata.type": "microsoft.graph.industryData.userManagementOptions"
  },
  "creationOptions": {
    "@odata.type": "microsoft.graph.industryData.userCreationOptions"
  }
}
```
