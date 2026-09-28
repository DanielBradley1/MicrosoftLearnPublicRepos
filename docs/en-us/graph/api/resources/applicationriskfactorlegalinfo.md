<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/applicationriskfactorlegalinfo?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-04 -->

# applicationRiskFactorLegalInfo resource type

Namespace: microsoft.graph

Represents legal compliance information and data management policies for an application, including data retention practices, GDPR alignment, ownership rights, and DMCA adherence. The **legal** property of the [applicationRiskFactors](https://learn.microsoft.com/en-us/graph/api/resources/applicationriskfactors?view=graph-rest-1.0) resource is an **applicationRiskFactorLegalInfo** object.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| dataRetention | dataRetentionLevel | Specifies how long the application retains user or customer data after account deletion or contract termination. The possible values are: `none`, `dataRetained`, `deletedImmediately`, `deletedWithin1Month`, `deletedWithin2Weeks`, `deletedWithin3Months`, `deletedWithinMoreThan3Months`, `unknownFutureValue`. |
| gdpr | [applicationRiskFactorLegalInfoGdpr](https://learn.microsoft.com/en-us/graph/api/resources/applicationriskfactorlegalinfogdpr?view=graph-rest-1.0) | Provides details on the application's compliance with the General Data Protection Regulation \(GDPR\), including data subject rights and lawful processing bases. |
| hasDataOwnership | Boolean | Indicates whether customers maintain ownership and control of their data processed or stored by the application. |
| hasDmca | Boolean | Indicates whether the application or organization complies with the Digital Millennium Copyright Act \(DMCA\) or equivalent copyright protection frameworks. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.applicationRiskFactorLegalInfo",
  "hasDmca": "Boolean",
  "hasDataOwnership": "Boolean",
  "dataRetention": "String",
  "gdpr": {
    "@odata.type": "microsoft.graph.applicationRiskFactorLegalInfoGdpr"
  }
}
```
