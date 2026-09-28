<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/contentcustomization?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# contentCustomization resource type

Namespace: microsoft.graph

Contains details of the various content options to be customized in the authentication flow for a tenant.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| attributeCollection | [keyValue](https://learn.microsoft.com/en-us/graph/api/resources/keyvalue?view=graph-rest-1.0) collection | Represents the content options of External Identities to be customized throughout the authentication flow for a tenant. |
| attributeCollectionRelativeUrl | String | A relative URL for the content options of External Identities to be customized throughout the authentication flow for a tenant. |
| registrationCampaign | [keyValue](https://learn.microsoft.com/en-us/graph/api/resources/keyvalue?view=graph-rest-1.0) collection | Represents content options to customize during MFA proofup interruptions. |
| registrationCampaignRelativeUrl | String | The relative URL of the content options to customize during MFA proofup interruptions. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.contentCustomization",
  "attributeCollection": [
    {
      "@odata.type": "microsoft.graph.keyValue"
    }
  ],
  "attributeCollectionRelativeUrl": "String",
   "registrationCampaign": [
    {
      "@odata.type": "microsoft.graph.keyValue"
    }
  ],
  "registrationCampaignRelativeUrl": "String"
}
```
