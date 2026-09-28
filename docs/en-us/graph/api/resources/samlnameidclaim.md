<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/samlnameidclaim?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-06-10 -->

# samlNameIdClaim resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

A nameID claim included in the SAML tokens affected by this policy.

Inherits from [customClaimBase](https://learn.microsoft.com/en-us/graph/api/resources/customclaimbase?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| configurations | [customClaimConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/customclaimconfiguration?view=graph-rest-beta) collection | One or more configurations that describe how the claim is sourced and under what conditions. Inherited from [customClaimBase](https://learn.microsoft.com/en-us/graph/api/resources/customclaimbase?view=graph-rest-beta). |
| nameIdFormat | samlNameIDFormat | Allows to specify the format of the saml nameID claim value. The possible values are: `default`, `unspecified`, `emailAddress`, `windowsDomainQualifiedName`, `persistent`, `unknownFutureValue`. |
| serviceProviderNameQualifier | String | Allows the specification of a service provider name qualifier reflected in the sAML response. The value provided must match one of the service provider names configured for the application and is only applicable for IdP-initiated applications \(the sign-on URL should be empty for the IdP-initiated applications\), in all other cases this value is ignored. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.samlNameIdClaim",
  "configurations": [
    {
      "@odata.type": "microsoft.graph.customClaimConfiguration"
    }
  ],
  "serviceProviderNameQualifier": "String",
  "nameIdFormat": "String"
}
```
