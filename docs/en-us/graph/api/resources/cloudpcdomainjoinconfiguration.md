<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcdomainjoinconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-01-21 -->

# cloudPcDomainJoinConfiguration resource type

Namespace: microsoft.graph

Represents a defined configuration of how a provisioned Cloud PC device joins to Microsoft Entra ID.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| domainJoinType | [cloudPcDomainJoinType](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcdomainjoinconfiguration?view=graph-rest-1.0#cloudpcdomainjointype-values) | Specifies the method by which the provisioned Cloud PC joins Microsoft Entra ID. If you choose the `hybridAzureADJoin` type, only provide a value for the **onPremisesConnectionId** property and leave the **regionName** property empty. If you choose the `azureADJoin` type, provide a value for either the **onPremisesConnectionId** or the **regionName** property. The possible values are: `azureADJoin`, `hybridAzureADJoin`, `unknownFutureValue`. |
| onPremisesConnectionId | String | The Azure network connection ID that matches the virtual network IT admins want the provisioning policy to use when they create Cloud PCs. You can use this property in both domain join types: *Azure AD joined* or *Hybrid Microsoft Entra joined*. If you enter an **onPremisesConnectionId**, leave the **regionName** property empty. |
| regionGroup | [cloudPcRegionGroup](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcregiongroup?view=graph-rest-1.0) | The logical geographic group this region belongs to. Multiple regions can belong to one region group. A customer can select a **regionGroup** when they provision a Cloud PC, and the Cloud PC is put in one of the regions in the group based on resource status. For example, the Europe region group contains the Northern Europe and Western Europe regions. Read-only. |
| regionName | String | The supported Azure region where the IT admin wants the provisioning policy to create Cloud PCs. Within this region, the Windows 365 service creates and manages the underlying virtual network. This option is available only when the IT admin selects *Microsoft Entra joined* as the domain join type. If you enter a **regionName**, leave the **onPremisesConnectionId** property empty. |

### cloudPcDomainJoinType values

| Member | Description |
| :--- | :--- |
| azureADJoin | Joined only to Microsoft Entra ID. Cloud-only and hybrid users can be assigned and sign into the Cloud PC. |
| hybridAzureADJoin | Joined to on-premises Active Directory and Microsoft Entra ID. Only hybrid users can be assigned and sign into the Cloud PC. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcDomainJoinConfiguration",
  "domainJoinType": "String",
  "onPremisesConnectionId": "String",
  "regionGroup": "String",
  "regionName": "String"
}
```
