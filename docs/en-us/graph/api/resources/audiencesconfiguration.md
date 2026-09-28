<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/audiencesconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-03-17 -->

# audiencesConfiguration resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Contains settings to block specific **signInAudience** types in an [application management policy](https://learn.microsoft.com/en-us/graph/api/resources/applicationauthenticationmethodpolicy?view=graph-rest-beta). Only restrictions for `azureAdMultipleOrgs` and `personalMicrosoftAccount` **signInAudience** types are available.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| azureAdMultipleOrgs | [audienceRestriction](https://learn.microsoft.com/en-us/graph/api/resources/audiencerestriction?view=graph-rest-beta) | Setting to allow or disallow creation of apps with multitenant **signInAudience**. |
| personalMicrosoftAccount | [audienceRestriction](https://learn.microsoft.com/en-us/graph/api/resources/audiencerestriction?view=graph-rest-beta) | Setting to allow or disallow creation of apps with personal Microsoft account **signInAudience**. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.audiencesConfiguration",
  "azureAdMultipleOrgs": {
    "@odata.type": "microsoft.graph.audienceRestriction"
  },
  "personalMicrosoftAccount": {
    "@odata.type": "microsoft.graph.audienceRestriction"
  }
}
```
