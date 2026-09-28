<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/applicationriskfactors?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-04 -->

# applicationRiskFactors resource type

Namespace: microsoft.graph

Represents a collection of risk factor categories that describe different aspects of an application's trust and compliance posture. These factors are used to evaluate the overall security, operational, and legal risk level of the application. The **riskFactors** property of the [applicationTemplate](https://learn.microsoft.com/en-us/graph/api/resources/applicationtemplate?view=graph-rest-1.0) resource is an **applicationRiskFactors** object.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| compliance | [applicationSecurityCompliance](https://learn.microsoft.com/en-us/graph/api/resources/applicationsecuritycompliance?view=graph-rest-1.0) | Provides information about the application's adherence to security frameworks, certifications, and industry compliance standards. |
| general | [applicationRiskFactorGeneralInfo](https://learn.microsoft.com/en-us/graph/api/resources/applicationriskfactorgeneralinfo?view=graph-rest-1.0) | Contains general business, operational, and data handling details that influence the application's risk assessment. |
| legal | [applicationRiskFactorLegalInfo](https://learn.microsoft.com/en-us/graph/api/resources/applicationriskfactorlegalinfo?view=graph-rest-1.0) | Provides legal and regulatory compliance information, including data ownership, retention, and GDPR adherence. |
| security | [applicationRiskFactorSecurityInfo](https://learn.microsoft.com/en-us/graph/api/resources/applicationriskfactorsecurityinfo?view=graph-rest-1.0) | Contains information related to the application's security posture, such as encryption, authentication, and vulnerability management practices. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.applicationRiskFactors",
  "general": {
    "@odata.type": "microsoft.graph.applicationRiskFactorGeneralInfo"
  },
  "security": {
    "@odata.type": "microsoft.graph.applicationRiskFactorSecurityInfo"
  },
  "compliance": {
    "@odata.type": "microsoft.graph.applicationSecurityCompliance"
  },
  "legal": {
    "@odata.type": "microsoft.graph.applicationRiskFactorLegalInfo"
  }
}
```
