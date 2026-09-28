<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/redirecturiallowedschemeconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-17 -->

# redirectUriAllowedSchemeConfiguration resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Configuration object that specifies allowed URI schemes for redirect URIs with global and platform-specific settings. When enabled, only redirect URIs using the specified schemes are permitted. The `allowedSchemes` property accepts `"*"` as a special value to allow any URI scheme for a specific platform.

**Applies to:** [redirectUriConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/redirecturiconfiguration?view=graph-rest-beta) \(**uriWithoutAllowedScheme**\)

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| allowedSchemes | String collection | Collection of URI schemes that are allowed globally across all platforms. Schemes refer to URI schemes as defined in [RFC 3986 §3.1](https://datatracker.ietf.org/doc/html/rfc3986#section-3.1). The value `"*"` can be used to allow any scheme. |
| excludeActors | [appManagementPolicyActorExemptions](https://learn.microsoft.com/en-us/graph/api/resources/appmanagementpolicyactorexemptions?view=graph-rest-beta) | Applications or service principals that are exempt from this restriction. |
| isStateSetByMicrosoft | Boolean | Indicates whether the restriction state was set by Microsoft. |
| publicClient | [redirectUriPlatformAllowedSchemeConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/redirecturiplatformallowedschemeconfiguration?view=graph-rest-beta) | Platform-specific allowed scheme configuration for public client applications \(native/mobile apps\). |
| restrictForAppsCreatedAfterDateTime | DateTimeOffset | Date and time when this restriction starts applying to newly created applications. Applications created before this date are not affected. |
| spa | [redirectUriPlatformAllowedSchemeConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/redirecturiplatformallowedschemeconfiguration?view=graph-rest-beta) | Platform-specific allowed scheme configuration for single-page applications \(SPAs\). |
| state | appManagementRestrictionState | Indicates whether the restriction is enabled or disabled. The possible values are: `enabled`, `disabled`, `unknownFutureValue`. |
| web | [redirectUriPlatformAllowedSchemeConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/redirecturiplatformallowedschemeconfiguration?view=graph-rest-beta) | Platform-specific allowed scheme configuration for web applications. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.redirectUriAllowedSchemeConfiguration",
  "state": "String",
  "isStateSetByMicrosoft": "Boolean",
  "restrictForAppsCreatedAfterDateTime": "String (timestamp)",
  "allowedSchemes": [
    "String"
  ],
  "web": {
    "@odata.type": "microsoft.graph.redirectUriPlatformAllowedSchemeConfiguration"
  },
  "spa": {
    "@odata.type": "microsoft.graph.redirectUriPlatformAllowedSchemeConfiguration"
  },
  "publicClient": {
    "@odata.type": "microsoft.graph.redirectUriPlatformAllowedSchemeConfiguration"
  },
  "excludeActors": {
    "@odata.type": "microsoft.graph.appManagementPolicyActorExemptions"
  }
}
```

## Related content

- [redirectUriConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/redirecturiconfiguration?view=graph-rest-beta)
