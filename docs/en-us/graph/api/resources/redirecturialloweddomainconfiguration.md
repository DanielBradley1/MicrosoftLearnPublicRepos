<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/redirecturialloweddomainconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-17 -->

# redirectUriAllowedDomainConfiguration resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Configuration object that specifies allowed domains for redirect URIs with global and platform-specific settings. When enabled, only redirect URIs using the specified domains are permitted, creating a positive list of approved domains for enhanced security.

**Applies to:** [redirectUriConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/redirecturiconfiguration?view=graph-rest-beta) \(**uriWithoutAllowedDomain**\)

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| allowedDomains | String collection | Collection of domain names that are allowed globally across all platforms. Domain validation follows [RFC 3986](https://datatracker.ietf.org/doc/html/rfc3986) \(URI syntax, section 3.2.2 for the host component\). Domain matching is case-insensitive and exact; wildcards are not supported. |
| excludeActors | [appManagementPolicyActorExemptions](https://learn.microsoft.com/en-us/graph/api/resources/appmanagementpolicyactorexemptions?view=graph-rest-beta) | Applications or service principals that are exempt from this restriction. |
| isStateSetByMicrosoft | Boolean | Indicates whether the restriction state was set by Microsoft. |
| publicClient | [redirectUriPlatformAllowedDomainConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/redirecturiplatformalloweddomainconfiguration?view=graph-rest-beta) | Platform-specific allowed domain configuration for public client applications \(native/mobile apps\). |
| restrictForAppsCreatedAfterDateTime | DateTimeOffset | Date and time when this restriction starts applying to newly created applications. Applications created before this date are not affected. |
| spa | [redirectUriPlatformAllowedDomainConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/redirecturiplatformalloweddomainconfiguration?view=graph-rest-beta) | Platform-specific allowed domain configuration for single-page applications \(SPAs\). |
| state | appManagementRestrictionState | Indicates whether the restriction is enabled or disabled. The possible values are: `enabled`, `disabled`, `unknownFutureValue`. |
| web | [redirectUriPlatformAllowedDomainConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/redirecturiplatformalloweddomainconfiguration?view=graph-rest-beta) | Platform-specific allowed domain configuration for web applications. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.redirectUriAllowedDomainConfiguration",
  "state": "String",
  "isStateSetByMicrosoft": "Boolean",
  "restrictForAppsCreatedAfterDateTime": "String (timestamp)",
  "allowedDomains": [
    "String"
  ],
  "web": {
    "@odata.type": "microsoft.graph.redirectUriPlatformAllowedDomainConfiguration"
  },
  "spa": {
    "@odata.type": "microsoft.graph.redirectUriPlatformAllowedDomainConfiguration"
  },
  "publicClient": {
    "@odata.type": "microsoft.graph.redirectUriPlatformAllowedDomainConfiguration"
  },
  "excludeActors": {
    "@odata.type": "microsoft.graph.appManagementPolicyActorExemptions"
  }
}
```

## Related content

- [redirectUriConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/redirecturiconfiguration?view=graph-rest-beta)
