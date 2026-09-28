<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/applicationriskfactorgeneralinfo?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-04 -->

# applicationRiskFactorGeneralInfo resource type

Namespace: microsoft.graph

Represents general information about an application that contributes to its overall risk profile, including its business background, operational resilience, and data handling practices. The **general** property of the [applicationRiskFactors](https://learn.microsoft.com/en-us/graph/api/resources/applicationriskfactors?view=graph-rest-1.0) resource is an **applicationRiskFactorGeneralInfo** object.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| consumerPopularity | Int32 | Indicates the relative popularity or adoption of the application based on the user or tenant usage metrics. |
| domainRegistrationDate | Date | Specifies the date when the application's primary domain was registered, used to assess domain maturity and legitimacy. |
| founded | Int32 | Year the company or organization behind the application was founded. |
| hasDisasterRecoveryPlan | Boolean | Indicates whether the application provider maintains a disaster recovery or business continuity plan. |
| hold | holdType | Specifies whether the application is publicly available, privately distributed, or in restricted status. The possible values are: `none`, `private`, `public`, `unknownFutureValue`. |
| hostingCompanyName | String | Specifies the name of the company or provider that hosts the application's infrastructure. |
| location | [applicationLocation](https://learn.microsoft.com/en-us/graph/api/resources/applicationlocation?view=graph-rest-1.0) | Provides the geographical and operational location information for the application, including data center and headquarters regions. |
| privacyPolicy | String | Specifies the URL of the application's privacy policy. |
| processedDataTypes | applicationDataType | Specifies the types of data the application processes. The possible values are: `none`, `codingFiles`, `creditCards`, `databaseFiles`, `documents`, `mediaFiles`, `unknownFutureValue`. This is a multi-value flags enum. |
| termsOfService | String | Specifies the URL of the application's terms of service. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.applicationRiskFactorGeneralInfo",
  "hasDisasterRecoveryPlan": "Boolean",
  "founded": "Integer",
  "domainRegistrationDate": "Date",
  "hold": "String",
  "consumerPopularity": "Integer",
  "location": {
    "@odata.type": "microsoft.graph.applicationLocation"
  },
  "hostingCompanyName": "String",
  "termsOfService": "String",
  "privacyPolicy": "String",
  "processedDataTypes": "String"
}
```
