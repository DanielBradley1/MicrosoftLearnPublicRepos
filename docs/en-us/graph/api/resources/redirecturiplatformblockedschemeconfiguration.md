<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/redirecturiplatformblockedschemeconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-17 -->

# redirectUriPlatformBlockedSchemeConfiguration resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Platform-specific configuration that specifies blocked URI schemes for redirect URIs. This configuration applies to a specific platform type \(web, SPA, or public client\) and is combined with global blocked scheme settings. Configured for properties defined on the [redirectUriBlockedSchemeConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/redirecturiblockedschemeconfiguration?view=graph-rest-beta) resource.

**Applies to:** [redirectUriBlockedSchemeConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/redirecturiblockedschemeconfiguration?view=graph-rest-beta) \(**web**, **spa**, **publicClient**\)

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| blockedSchemes | String collection | Collection of URI schemes that are blocked for this specific platform. Schemes refer to URI schemes as defined in [RFC 3986 §3.1](https://datatracker.ietf.org/doc/html/rfc3986#section-3.1). |
| exemptFormats | String collection | Collection of URI patterns that are exempt from the blocked scheme restrictions for this platform. Patterns must follow specific validation rules for standard URI formats or URN formats. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.redirectUriPlatformBlockedSchemeConfiguration",
  "blockedSchemes": [
    "String"
  ],
  "exemptFormats": [
    "String"
  ]
}
```

## Related content

- [redirectUriBlockedSchemeConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/redirecturiblockedschemeconfiguration?view=graph-rest-beta)
