<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/customclaim?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-06-10 -->

# customClaim resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an individual claim included in the tokens affected by this policy. It consists of a configurable name, namespace, token format, and claim name format. The claim name format is applicable only for SAML tokens.

Inherits from [customClaimBase](https://learn.microsoft.com/en-us/graph/api/resources/customclaimbase?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| configurations | [customClaimConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/customclaimconfiguration?view=graph-rest-beta) collection | One or more configurations that describe how the claim is sourced and under what conditions. Inherited from [customClaimBase](https://learn.microsoft.com/en-us/graph/api/resources/customclaimbase?view=graph-rest-beta). |
| name | String | The name of the claim to be emitted. |
| namespace | String | An optional namespace to be included as part of the claim name. |
| samlAttributeNameFormat | samlAttributeNameFormat | If specified, it sets the `nameFormat` attribute associated with the claim in the SAML response. The possible values are: `unspecified`, `uri`, `basic`, `unknownFutureValue`. |
| tokenFormat | tokenFormat collection | List of token formats for which this claim should be emitted. The possible values are: `saml`,`jwt`, `unknownFutureValue` |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.customClaim",
  "configurations": [
    {
      "@odata.type": "microsoft.graph.customClaimConfiguration"
    }
  ],
  "name": "String",
  "namespace": "String",
  "tokenFormat": [
    "String"
  ],
  "samlAttributeNameFormat": "String"
}
```
