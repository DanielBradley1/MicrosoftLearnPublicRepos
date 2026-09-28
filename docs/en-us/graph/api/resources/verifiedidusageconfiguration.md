<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/verifiedidusageconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-04 -->

# verifiedIdUsageConfiguration resource type

Namespace: microsoft.graph

Configuration defining the usage capability of a [Verified ID credential](https://learn.microsoft.com/en-us/graph/api/resources/verifiedidprofile?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| isEnabledForTestOnly | Boolean | Sets profile usage for evaluation \(test-only\) or production. |
| purpose | verifiedIdUsageConfigurationPurpose | Sets the supported scenarios for a Verified ID profile. Currently only `recovery` is supported. The possible values are: `recovery`, `onboarding`, `all`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.verifiedIdUsageConfiguration",
  "isEnabledForTestOnly": "Boolean",
  "purpose": "String"
}
```
