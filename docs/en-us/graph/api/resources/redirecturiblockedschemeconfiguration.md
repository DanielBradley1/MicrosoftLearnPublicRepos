<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/redirecturiblockedschemeconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-17 -->

# redirectUriBlockedSchemeConfiguration resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Configuration object that specifies blocked URI schemes for redirect URIs with global and platform-specific settings and exempt format patterns. Blocked schemes prevent applications from using specific URI schemes \(such as `http`, `urn`, or custom schemes\) in their redirect URIs.

**Applies to:** [redirectUriConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/redirecturiconfiguration?view=graph-rest-beta) \(**uriWithBlockedScheme**\)

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| blockedSchemes | String collection | Collection of URI schemes that are blocked globally across all platforms. Schemes refer to URI schemes as defined in [RFC 3986 §3.1](https://datatracker.ietf.org/doc/html/rfc3986#section-3.1). |
| excludeActors | [appManagementPolicyActorExemptions](https://learn.microsoft.com/en-us/graph/api/resources/appmanagementpolicyactorexemptions?view=graph-rest-beta) | Applications or service principals that are exempt from this restriction. |
| exemptFormats | String collection | Collection of URI patterns that are exempt from the blocked scheme restrictions. Patterns must follow specific validation rules for standard URI formats or URN formats. |
| isStateSetByMicrosoft | Boolean | Indicates whether the restriction state was set by Microsoft. |
| publicClient | [redirectUriPlatformBlockedSchemeConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/redirecturiplatformblockedschemeconfiguration?view=graph-rest-beta) | Platform-specific blocked scheme configuration for public client applications \(native/mobile apps\). |
| restrictForAppsCreatedAfterDateTime | DateTimeOffset | Date and time when this restriction starts applying to newly created applications. Applications created before this date are not affected. |
| spa | [redirectUriPlatformBlockedSchemeConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/redirecturiplatformblockedschemeconfiguration?view=graph-rest-beta) | Platform-specific blocked scheme configuration for single-page applications \(SPAs\). |
| state | appManagementRestrictionState | Indicates whether the restriction is enabled or disabled. The possible values are: `enabled`, `disabled`, `unknownFutureValue`. |
| web | [redirectUriPlatformBlockedSchemeConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/redirecturiplatformblockedschemeconfiguration?view=graph-rest-beta) | Platform-specific blocked scheme configuration for web applications. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.redirectUriBlockedSchemeConfiguration",
  "state": "String",
  "isStateSetByMicrosoft": "Boolean",
  "restrictForAppsCreatedAfterDateTime": "String (timestamp)",
  "blockedSchemes": [
    "String"
  ],
  "exemptFormats": [
    "String"
  ],
  "web": {
    "@odata.type": "microsoft.graph.redirectUriPlatformBlockedSchemeConfiguration"
  },
  "spa": {
    "@odata.type": "microsoft.graph.redirectUriPlatformBlockedSchemeConfiguration"
  },
  "publicClient": {
    "@odata.type": "microsoft.graph.redirectUriPlatformBlockedSchemeConfiguration"
  },
  "excludeActors": {
    "@odata.type": "microsoft.graph.appManagementPolicyActorExemptions"
  }
}
```

## Related content

- [redirectUriConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/redirecturiconfiguration?view=graph-rest-beta)
