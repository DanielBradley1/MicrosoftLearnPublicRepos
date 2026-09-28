<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/redirecturiconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-17 -->

# redirectUriConfiguration resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Configuration object that contains redirect URI validation rules and restrictions for applications. This object is configured on the **redirectUris** property of the [appManagementApplicationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/appmanagementapplicationconfiguration?view=graph-rest-beta&preserve-view=true) and [customAppManagementApplicationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/customappmanagementapplicationconfiguration?view=graph-rest-beta&preserve-view=true) resources.

**Applies to:** [appManagementApplicationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/appmanagementapplicationconfiguration?view=graph-rest-beta), [customAppManagementApplicationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/customappmanagementapplicationconfiguration?view=graph-rest-beta), [tenantAppManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/tenantappmanagementpolicy?view=graph-rest-beta) \(**applicationRestrictions**\)

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| uriWithBlockedDomain | [redirectUriBlockedDomainConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/redirecturiblockeddomainconfiguration?view=graph-rest-beta) | Configuration that specifies blocked domains for redirect URIs with global and platform-specific settings. |
| uriWithBlockedScheme | [redirectUriBlockedSchemeConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/redirecturiblockedschemeconfiguration?view=graph-rest-beta) | Configuration that specifies blocked URI schemes for redirect URIs with global and platform-specific settings and exempt format patterns. |
| uriWithWildcard | [redirectUriWildcardConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/redirecturiwildcardconfiguration?view=graph-rest-beta) | Configuration that controls the use of wildcard patterns in redirect URIs with configurable exceptions. |
| uriWithoutAllowedDomain | [redirectUriAllowedDomainConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/redirecturialloweddomainconfiguration?view=graph-rest-beta) | Configuration that specifies allowed domains for redirect URIs with global and platform-specific settings. |
| uriWithoutAllowedScheme | [redirectUriAllowedSchemeConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/redirecturiallowedschemeconfiguration?view=graph-rest-beta) | Configuration that specifies allowed URI schemes for redirect URIs with global and platform-specific settings. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.redirectUriConfiguration",
  "uriWithBlockedScheme": {
    "@odata.type": "microsoft.graph.redirectUriBlockedSchemeConfiguration"
  },
  "uriWithoutAllowedScheme": {
    "@odata.type": "microsoft.graph.redirectUriAllowedSchemeConfiguration"
  },
  "uriWithWildcard": {
    "@odata.type": "microsoft.graph.redirectUriWildcardConfiguration"
  },
  "uriWithoutAllowedDomain": {
    "@odata.type": "microsoft.graph.redirectUriAllowedDomainConfiguration"
  },
  "uriWithBlockedDomain": {
    "@odata.type": "microsoft.graph.redirectUriBlockedDomainConfiguration"
  }
}
```

## Related content

- [appManagementApplicationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/appmanagementapplicationconfiguration?view=graph-rest-beta)
- [customAppManagementApplicationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/customappmanagementapplicationconfiguration?view=graph-rest-beta)
- [tenantAppManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/tenantappmanagementpolicy?view=graph-rest-beta)
