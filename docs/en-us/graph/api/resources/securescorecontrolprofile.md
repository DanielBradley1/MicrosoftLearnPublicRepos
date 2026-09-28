<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/securescorecontrolprofile?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# secureScoreControlProfile resource type

Namespace: microsoft.graph

Represents a tenant's secure score per control data. By default, this resource returns all controls for a tenant and can explicitly pull individual controls.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List secure score control profiles](https://learn.microsoft.com/en-us/graph/api/security-list-securescorecontrolprofiles?view=graph-rest-1.0) | [secureScoreControlProfile](https://learn.microsoft.com/en-us/graph/api/resources/securescorecontrolprofile?view=graph-rest-1.0) | Read properties and metadata of a secureScoreControlProfiles object. |
| [Get secure score control profile](https://learn.microsoft.com/en-us/graph/api/securescorecontrolprofile-get?view=graph-rest-1.0) | [securescorecontrolprofile](https://learn.microsoft.com/en-us/graph/api/resources/securescorecontrolprofile?view=graph-rest-1.0) | Read properties and metadata of a secureScoreControlProfiles object. |
| [Update secure score control profiles](https://learn.microsoft.com/en-us/graph/api/securescorecontrolprofile-update?view=graph-rest-1.0) | [securescorecontrolprofile](https://learn.microsoft.com/en-us/graph/api/resources/securescorecontrolprofile?view=graph-rest-1.0) | Update an securescorecontrolprofile object. |

## Properties

| Name | Type | Description |
| :--- | :--- | :--- |
| actionType | String | Control action type \(Config, Review, Behavior\). |
| actionUrl | String | URL to where the control can be actioned. |
| azureTenantId | String | GUID string for tenant ID. |
| complianceInformation | [complianceInformation](https://learn.microsoft.com/en-us/graph/api/resources/complianceinformation?view=graph-rest-1.0) collection | The collection of compliance information associated with secure score control. **Not implemented. Currently returns `null`.** |
| controlCategory | String | Control action category \(Identity, Data, Device, Apps, Infrastructure\). |
| controlStateUpdates | [secureScoreControlStateUpdate](https://learn.microsoft.com/en-us/graph/api/resources/securescorecontrolstateupdate?view=graph-rest-1.0) collection | Flag to indicate where the tenant has marked a control \(ignored, thirdParty, reviewed\) \(supports [update](https://learn.microsoft.com/en-us/graph/api/securescorecontrolprofile-update?view=graph-rest-1.0)\). |
| deprecated | Boolean | Flag to indicate if a control is depreciated. |
| id | String | Provider-generated GUID/unique identifier. Read-only. Required. |
| implementationCost | String | Resource cost of implemmentating control \(low, moderate, high\). |
| lastModifiedDateTime | DateTimeOffset | Time at which the control profile entity was last modified. The Timestamp type represents date and time |
| maxScore | Double | max attainable score for the control. |
| rank | Int32 | Microsoft's stack ranking of control. |
| remediation | String | Description of what the control will help remediate. |
| remediationImpact | String | Description of the impact on users of the remediation. |
| service | String | Service that owns the control \(Exchange, Sharepoint, Microsoft Entra ID\). |
| threats | String collection | List of threats the control mitigates \(accountBreach, dataDeletion, dataExfiltration, dataSpillage, elevationOfPrivilege, maliciousInsider, passwordCracking, phishingOrWhaling, spoofing\). |
| tier | String | Control tier \(Core, Defense in Depth, Advanced.\) |
| title | String | Title of the control. |
| userImpact | String | User impact of implementing control \(low, moderate, high\). |
| vendorInformation | [securityVendorInformation](https://learn.microsoft.com/en-us/graph/api/resources/securityvendorinformation?view=graph-rest-1.0) | Complex type containing details about the security product/service vendor, provider, and subprovider \(for example, vendor=Microsoft; provider=SecureScore\). Required. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "actionType": "String",
  "actionUrl": "String",
  "azureTenantId": "String",
  "complianceInformation": [{"@odata.type": "microsoft.graph.complianceInformation"}],
  "controlCategory": "String",
  "controlStateUpdates": [{"@odata.type": "microsoft.graph.secureScoreControlStateUpdate"}],
  "deprecated": "Boolean",
  "id": "String (identifier)",
  "implementationCost": "String",
  "lastModifiedDateTime": "String (timestamp)",
  "maxScore": "Double",
  "rank": "Int32",
  "remediation": "String",
  "remediationImpact": "String",
  "service": "String",
  "threats": ["String"],
  "tier": "String",
  "title": "String",
  "userImpact": "String",
  "vendorInformation": {"@odata.type": "microsoft.graph.securityVendorInformation"}
}
```
