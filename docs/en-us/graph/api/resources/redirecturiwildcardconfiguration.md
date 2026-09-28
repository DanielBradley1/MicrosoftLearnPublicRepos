<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/redirecturiwildcardconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-17 -->

# redirectUriWildcardConfiguration resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Configuration object that controls the use of wildcard patterns in redirect URIs with configurable exceptions. When enabled, applications are restricted from using wildcard patterns in their redirect URIs, improving security by preventing overly permissive redirect configurations.

**Applies to:** [redirectUriConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/redirecturiconfiguration?view=graph-rest-beta) \(**uriWithWildcard**\)

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| excludeActors | [appManagementPolicyActorExemptions](https://learn.microsoft.com/en-us/graph/api/resources/appmanagementpolicyactorexemptions?view=graph-rest-beta) | Applications or service principals that are exempt from this restriction. |
| excludeFormats | [redirectUriWildcardExcludeFormats](https://learn.microsoft.com/en-us/graph/api/resources/redirecturiwildcardexcludeformats?view=graph-rest-beta) | Configuration that specifies exceptions to the wildcard restriction, such as allowing wildcards for specific trusted domains. |
| isStateSetByMicrosoft | Boolean | Indicates whether the restriction state was set by Microsoft. |
| restrictForAppsCreatedAfterDateTime | DateTimeOffset | Date and time when this restriction starts applying to newly created applications. Applications created before this date are not affected. |
| state | appManagementRestrictionState | Indicates whether the restriction is enabled or disabled. The possible values are: `enabled`, `disabled`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.redirectUriWildcardConfiguration",
  "state": "String",
  "isStateSetByMicrosoft": "Boolean",
  "restrictForAppsCreatedAfterDateTime": "String (timestamp)",
  "excludeFormats": {
    "@odata.type": "microsoft.graph.redirectUriWildcardExcludeFormats"
  },
  "excludeActors": {
    "@odata.type": "microsoft.graph.appManagementPolicyActorExemptions"
  }
}
```

## Related content

- [redirectUriConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/redirecturiconfiguration?view=graph-rest-beta)
- [redirectUriWildcardExcludeFormats](https://learn.microsoft.com/en-us/graph/api/resources/redirecturiwildcardexcludeformats?view=graph-rest-beta)
