<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/redirecturiwildcardexcludeformats?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-17 -->

# redirectUriWildcardExcludeFormats resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Configuration object that specifies exceptions to wildcard restrictions in redirect URIs, allowing specific trusted scenarios while maintaining overall security. Configured on the **excludeFormats** property of [redirectUriWildcardConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/redirecturiwildcardconfiguration?view=graph-rest-beta) resource.

**Applies to:** [redirectUriWildcardConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/redirecturiwildcardconfiguration?view=graph-rest-beta) \(**excludeFormats**\)

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| excludeWildcardsInPath | Boolean | When `true`, blocks the use of wildcards in the path portion of redirect URIs. When `false`, allows wildcards in paths. |
| excludeWildcardsInPathWithDomains | String collection | Collection of domain names where wildcards in the path portion of redirect URIs are blocked. Accepts only valid host names \(no wildcards\) as defined in [RFC 3986 §3.2.2](https://datatracker.ietf.org/doc/html/rfc3986#section-3.2.2). For example, `login.microsoft.com` or `contoso.com`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.redirectUriWildcardExcludeFormats",
  "excludeWildcardsInPath": "Boolean",
  "excludeWildcardsInPathWithDomains": [
    "String"
  ]
}
```

## Related content

- [redirectUriWildcardConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/redirecturiwildcardconfiguration?view=graph-rest-beta)
