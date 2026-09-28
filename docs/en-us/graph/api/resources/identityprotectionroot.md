<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identityprotectionroot?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# identityProtectionRoot resource type

Namespace: microsoft.graph

Container for the navigation properties for [Microsoft Graph identity protection](https://learn.microsoft.com/en-us/graph/api/resources/identityprotection-overview?view=graph-rest-1.0) resources.

## Methods

None.

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| riskDetections | [riskDetection](https://learn.microsoft.com/en-us/graph/api/resources/riskdetection?view=graph-rest-1.0) collection | Risk detection in Microsoft Entra ID Protection and the associated information about the detection. |
| riskyUsers | [riskyUser](https://learn.microsoft.com/en-us/graph/api/resources/riskyuser?view=graph-rest-1.0) collection | Users that are flagged as at-risk by Microsoft Entra ID Protection. |
| riskyServicePrincipals | [riskyServicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/riskyserviceprincipal?view=graph-rest-1.0) collection | Microsoft Entra service principals that are at risk. |
| servicePrincipalRiskDetections | [servicePrincipalRiskDetection](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipalriskdetection?view=graph-rest-1.0) collection | Represents information about detected at-risk service principals in a Microsoft Entra tenant. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityProtectionRoot"
}
```
