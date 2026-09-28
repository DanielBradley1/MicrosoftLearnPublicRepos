<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/securescorecontrolprofiles?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# secureScoreControlProfile resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a tenant's secure score per control data. By default, it returns all controls for a tenant and can explicitly pull individual controls.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List secure score control profiles](https://learn.microsoft.com/en-us/graph/api/securescorecontrolprofiles-list?view=graph-rest-beta) | [secureScoreControlProfile](https://learn.microsoft.com/en-us/graph/api/resources/securescorecontrolprofiles?view=graph-rest-beta) collection | Get a collection of secureScoreControlProfile objects. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| actionType | String | Control action type \(Config, Review, Behavior\). |
| actionUrl | String | URL to where the control can be actioned. |
| azureTenantId | String | GUID string for tenant ID. |
| complianceInformation | [complianceInformation](https://learn.microsoft.com/en-us/graph/api/resources/complianceinformation?view=graph-rest-beta) collection | The collection of compliance information associated with secure score control. **Not implemented. Currently returns `null`.** |
| controlCategory | String | Control action category \(Account, Data, Device, Apps, Infrastructure\). |
| controlName | String | Name of the control. |
| controlStateUpdates | [secureScoreControlStateUpdate](https://learn.microsoft.com/en-us/graph/api/resources/securescorecontrolstateupdate?view=graph-rest-beta) collection | Flag to indicate where the tenant has marked a control \(ignored, thirdParty, reviewed\) \(supports [update](https://learn.microsoft.com/en-us/graph/api/securescorecontrolprofiles-update?view=graph-rest-beta)\). |
| deprecated | Boolean | Flag to indicate if a control is depreciated. |
| id | String | Provider-generated GUID/unique identifier. Read-only. Required. |
| implementationCost | String | Resource cost of implemmentating control \(low, moderate, high\). |
| lastModifiedDateTime | DateTimeOffset | Time at which the control profile entity was last modified. The Timestamp type represents date and time |
| maxScore | String | Current obtained max score on specified date. |
| rank | Int32 | Microsoft's stack ranking of control. |
| remediation | String | Description of what the control will help remediate. |
| remediationImpact | String | Description of the impact on users of the remediation. |
| service | String | Service that owns the control \(Exchange, Sharepoint, Microsoft Entra ID\). |
| threats | String collection | List of threats the control mitigates \(accountBreach, dataDeletion, dataExfiltration, dataSpillage, elevationOfPrivilege, maliciousInsider, passwordCracking, phishingOrWhaling, spoofing\). |
| tier | String | Control tier \(Core, Defense in Depth, Advanced.\) |
| title | String | Title of the control. |
| userImpact | String | User impact of implementing control \(low, moderate, high\). |
| vendorInformation | [securityVendorInformation](https://learn.microsoft.com/en-us/graph/api/resources/securityvendorinformation?view=graph-rest-beta) | Complex type containing details about the security product/service vendor, provider, and subprovider \(for example, vendor=Microsoft; provider=SecureScore\). Required. |

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
  "deprecated": false,
  "id": "String (identifier)",
  "implementationCost": "String",
  "lastModifiedDateTime": "String (timestamp)",
  "maxScore": 1024.13,
  "rank": 100,
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
