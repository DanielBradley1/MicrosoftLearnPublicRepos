<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/redirecturiblockeddomainconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-17 -->

# redirectUriBlockedDomainConfiguration resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Configuration object that specifies blocked domains for redirect URIs with global and platform-specific settings. Blocked domains prevent applications from using specific domains \(such as URL shorteners or cloud-hosted domains\) in their redirect URIs to improve security. Configured on the [redirectUriConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/redirecturiconfiguration?view=graph-rest-beta) resource.

**Applies to:** [redirectUriConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/redirecturiconfiguration?view=graph-rest-beta) \(**uriWithBlockedDomain**\)

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| blockedDomains | String collection | Collection of domain names that are blocked globally across all platforms. Domain validation follows [RFC 3986](https://datatracker.ietf.org/doc/html/rfc3986) \(URI syntax, section 3.2.2 for the host component\). Domain matching is case-insensitive and exact; wildcards are not supported. |
| excludeActors | [appManagementPolicyActorExemptions](https://learn.microsoft.com/en-us/graph/api/resources/appmanagementpolicyactorexemptions?view=graph-rest-beta) | Applications or service principals that are exempt from this restriction. |
| isStateSetByMicrosoft | Boolean | Indicates whether the restriction state was set by Microsoft. |
| publicClient | [redirectUriPlatformBlockedDomainConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/redirecturiplatformblockeddomainconfiguration?view=graph-rest-beta) | Platform-specific blocked domain configuration for public client applications \(native/mobile apps\). |
| restrictForAppsCreatedAfterDateTime | DateTimeOffset | Date and time when this restriction starts applying to newly created applications. Applications created before this date are not affected. |
| spa | [redirectUriPlatformBlockedDomainConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/redirecturiplatformblockeddomainconfiguration?view=graph-rest-beta) | Platform-specific blocked domain configuration for single-page applications \(SPAs\). |
| state | appManagementRestrictionState | Indicates whether the restriction is enabled or disabled. The possible values are: `enabled`, `disabled`, `unknownFutureValue`. |
| web | [redirectUriPlatformBlockedDomainConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/redirecturiplatformblockeddomainconfiguration?view=graph-rest-beta) | Platform-specific blocked domain configuration for web applications. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.redirectUriBlockedDomainConfiguration",
  "state": "String",
  "isStateSetByMicrosoft": "Boolean",
  "restrictForAppsCreatedAfterDateTime": "String (timestamp)",
  "blockedDomains": [
    "String"
  ],
  "web": {
    "@odata.type": "microsoft.graph.redirectUriPlatformBlockedDomainConfiguration"
  },
  "spa": {
    "@odata.type": "microsoft.graph.redirectUriPlatformBlockedDomainConfiguration"
  },
  "publicClient": {
    "@odata.type": "microsoft.graph.redirectUriPlatformBlockedDomainConfiguration"
  },
  "excludeActors": {
    "@odata.type": "microsoft.graph.appManagementPolicyActorExemptions"
  }
}
```

## Related content

- [redirectUriConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/redirecturiconfiguration?view=graph-rest-beta)
