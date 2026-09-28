<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/applicationtemplate?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-26 -->

# applicationTemplate resource type

Namespace: microsoft.graph

Represents an application in the [Microsoft Entra application gallery](https://learn.microsoft.com/en-us/azure/active-directory/saas-apps/tutorial-list).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/applicationtemplate-list?view=graph-rest-1.0) | [applicationTemplate](https://learn.microsoft.com/en-us/graph/api/resources/applicationtemplate?view=graph-rest-1.0) | Retrieve a list of applicationTemplate objects. |
| [Get](https://learn.microsoft.com/en-us/graph/api/applicationtemplate-get?view=graph-rest-1.0) | [applicationTemplate](https://learn.microsoft.com/en-us/graph/api/resources/applicationtemplate?view=graph-rest-1.0) | Read properties and relationships of applicationTemplate object. |
| [Instantiate](https://learn.microsoft.com/en-us/graph/api/applicationtemplate-instantiate?view=graph-rest-1.0) | [applicationServicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/applicationserviceprincipal?view=graph-rest-1.0) | Add an instance of an application from the Microsoft Entra application gallery into your directory. The application template with ID `8adf8e6e-67b2-4cf2-a259-e3dc5476c621` can be used to add a non-gallery app that you can configure different single-sign on \(SSO\) modes like SAML SSO and password-based SSO. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| categories | String collection | The list of categories for the application. Supported values can be: `Collaboration`, `Business Management`, `Consumer`, `Content management`, `CRM`, `Data services`, `Developer services`, `E-commerce`, `Education`, `ERP`, `Finance`, `Health`, `Human resources`, `IT infrastructure`, `Mail`, `Management`, `Marketing`, `Media`, `Productivity`, `Project management`, `Telecommunications`, `Tools`, `Travel`, and `Web design & hosting`.  <br>  <br>Supports `$filter` \(`contains`\). |
| deprecationDate | Date | Deprecation date for this application. If specified, the application will be removed from the Microsoft Entra application gallery on this date. |
| description | String | A description of the application. |
| displayName | String | The name of the application. Supports `$filter` \(`contains`\). |
| endpoints | String collection | A collection of string URLs representing various domains that are used by this application. |
| homePageUrl | String | The home page URL of the application. |
| id | String | Unique identifier for the application. Read-only. |
| isEntraIntegrated | Boolean | Indicates whether the application is integrated with Entra ID \(for example, through single sign-on or user provisioning\). |
| lastModifiedDateTime | DateTimeOffset | The date and time when the data for the application was last updated, represented using ISO 8601 format and always in UTC time. |
| logoUrl | String | The URL to get the logo for this application. |
| publisher | String | The name of the publisher for this application. |
| riskFactors | [applicationRiskFactors](https://learn.microsoft.com/en-us/graph/api/resources/applicationriskfactors?view=graph-rest-1.0) | A comprehensive set of risk assessment data for the application, including general, security, compliance, and legal dimensions. Returned only when `$select` is used. |
| riskScore | [applicationRiskScore](https://learn.microsoft.com/en-us/graph/api/resources/applicationriskscore?view=graph-rest-1.0) | Represents the Microsoft-generated numerical risk score assessment for the application. Supported `$orderby` on **total** \(for example, `$orderby=riskScore/total desc`\). Returned only when `$select` is used. |
| supportedProvisioningTypes | String collection | The list of provisioning modes supported by this application. The only valid value is `sync`. |
| supportedSingleSignOnModes | String collection | The list of single sign-on modes supported by this application. The supported values are `oidc`, `password`, `saml`, and `notSupported`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "categories": ["categories-value"],
  "deprecationDate": "String (Date)",
  "description": "description-value",
  "displayName": "displayName-value",
  "endpoints": ["String"],
  "homePageUrl": "homePageUrl-value",
  "id": "id-value",
  "isEntraIntegrated": "Boolean",
  "lastModifiedDateTime": "String (timestamp)",
  "logoUrl": "logoUrl-value",
  "publisher": "publisher-value",
  "riskFactors": {"@odata.type": "microsoft.graph.applicationRiskFactors"},
  "riskScore": {"@odata.type": "microsoft.graph.applicationRiskScore"},
  "supportedSingleSignOnModes": ["supportedSingleSignOnModes-value"]
}
```

## Related content

[Quickstart: Add an enterprise application from the Microsoft Entra gallery](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal)
