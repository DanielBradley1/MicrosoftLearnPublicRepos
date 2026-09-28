<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/redirecturiplatformallowedschemeconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-17 -->

# redirectUriPlatformAllowedSchemeConfiguration resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Platform-specific configuration that specifies allowed URI schemes for redirect URIs. This configuration applies to a specific platform type \(web, SPA, or public client\) and is combined with global allowed scheme settings. The `allowedSchemes` property accepts `"*"` as a special value to allow any URI scheme for the platform. Configured for properties defined on the [redirectUriAllowedSchemeConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/redirecturiallowedschemeconfiguration?view=graph-rest-beta) resource.

**Applies to:** [redirectUriAllowedSchemeConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/redirecturiallowedschemeconfiguration?view=graph-rest-beta) \(**web**, **spa**, **publicClient**\)

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| allowedSchemes | String collection | Collection of URI schemes that are allowed for this specific platform. Schemes refer to URI schemes as defined in [RFC 3986 §3.1](https://datatracker.ietf.org/doc/html/rfc3986#section-3.1). The value `"*"` can be used to allow any scheme for this platform. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.redirectUriPlatformAllowedSchemeConfiguration",
  "allowedSchemes": [
    "String"
  ]
}
```

## Related content

- [redirectUriAllowedSchemeConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/redirecturiallowedschemeconfiguration?view=graph-rest-beta)
