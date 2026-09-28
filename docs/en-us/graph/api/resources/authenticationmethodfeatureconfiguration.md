<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodfeatureconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# authenticationMethodFeatureConfiguration resource type

Namespace: microsoft.graph

Defines the features that are allowed for different authentication methods. For each authentication method, defines the users who are enabled or excluded from using the feature.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| excludeTarget | [featureTarget](https://learn.microsoft.com/en-us/graph/api/resources/featuretarget?view=graph-rest-1.0) | A single entity that is excluded from this feature. |
| includeTarget | [featureTarget](https://learn.microsoft.com/en-us/graph/api/resources/featuretarget?view=graph-rest-1.0) | A single entity that is included in this feature. |
| state | advancedConfigState | Enable or disable the feature. The possible values are: `default`, `enabled`, `disabled`, `unknownFutureValue`. The `default` value is used when the configuration hasn't been explicitly set and uses the default behavior of Microsoft Entra ID for the setting. The default value is `disabled`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.authenticationMethodFeatureConfiguration",
  "excludeTarget": {
    "@odata.type": "microsoft.graph.featureTarget"
  },
  "includeTarget": {
    "@odata.type": "microsoft.graph.featureTarget"
  },
  "state": "String"
}
```
