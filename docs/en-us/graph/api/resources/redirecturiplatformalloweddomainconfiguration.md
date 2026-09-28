<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/redirecturiplatformalloweddomainconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-17 -->

# redirectUriPlatformAllowedDomainConfiguration resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Platform-specific configuration that specifies allowed domains for redirect URIs. This configuration applies to a specific platform type \(web, SPA, or public client\) and is combined with global allowed domain settings. Configured for properties defined on the [redirectUriAllowedDomainConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/redirecturialloweddomainconfiguration?view=graph-rest-beta) resource.

**Applies to:** [redirectUriAllowedDomainConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/redirecturialloweddomainconfiguration?view=graph-rest-beta) \(**web**, **spa**, **publicClient**\)

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| allowedDomains | String collection | Collection of domain names that are allowed for this specific platform. Domain validation follows [RFC 3986](https://datatracker.ietf.org/doc/html/rfc3986) \(URI syntax, section 3.2.2 for the host component\). Domain matching is case-insensitive and exact; wildcards are not supported. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.redirectUriPlatformAllowedDomainConfiguration",
  "allowedDomains": [
    "String"
  ]
}
```

## Related content

- [redirectUriAllowedDomainConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/redirecturialloweddomainconfiguration?view=graph-rest-beta)
