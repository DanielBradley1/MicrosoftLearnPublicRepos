<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/applicationriskfactorlegalinfogdpr?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-04 -->

# applicationRiskFactorLegalInfoGdpr resource type

Namespace: microsoft.graph

Represents information about how an application complies with the General Data Protection Regulation \(GDPR\), focusing on user data rights, protection mechanisms, and transparency obligations. The **gdpr** property of the [applicationRiskFactorLegalInfo](https://learn.microsoft.com/en-us/graph/api/resources/applicationriskfactorlegalinfo?view=graph-rest-1.0) resource is an **applicationRiskFactorLegalInfoGdpr** object.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| dataProtection | dataProtection | Specifies the data protection mechanisms implemented by the application to comply with GDPR. The possible values are: `none`, `impactAssessments`, `officers`, `secureCrossBorderDataTransfer`, `unknownFutureValue`. This is a multi-value flags enum. |
| hasRightToErasure | Boolean | Indicates whether the application provides users with the ability to request deletion of their personal data \(the right to be forgotten\). |
| isReportingDataBreaches | Boolean | Indicates whether the organization reports personal data breaches to authorities and affected users in accordance with GDPR requirements. |
| statementUrl | String | Specifies the URL of the application's GDPR or privacy compliance statement, outlining how user data is handled. |
| userOwnership | userOwnership | Specifies the GDPR data subject rights supported by the application. The possible values are: `none`, `lawfulBasisForProcessing`, `rightToAccess`, `rightToBeInformed`, `rightToDataPortability`, `rightToObject`, `rightToRectification`, `rightToRestrictionOfProcessing`, `rightsRelatedToAutomatedDecisionMaking`, `unknownFutureValue`. This is a multi-value flags enum. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.applicationRiskFactorLegalInfoGdpr",
  "statementUrl": "String",
  "hasRightToErasure": "Boolean",
  "isReportingDataBreaches": "Boolean",
  "dataProtection": "String",
  "userOwnership": "String"
}
```
