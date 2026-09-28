<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-organizationalscope?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-20 -->

# organizationalScope resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a scope that specifies which devices are covered by a [custom detection rule's](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionrule?view=graph-rest-beta) [detection action](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionaction?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| deviceGroups | String collection | List of device groups to which the custom detection rule applies. |
| scopeNames \(deprecated\) | String collection | List of groups to which the custom detection rule applies. **Deprecated.** Use **deviceGroups** instead. This property will be removed from this resource on October 1, 2026. |
| scopeType \(deprecated\) | [microsoft.graph.security.scopeType](https://learn.microsoft.com/en-us/graph/api/resources/enums-security?view=graph-rest-beta#scopetype-values) | The type of the organizational scope. The possible values are: `deviceGroup`, `unknownFutureValue`. **Deprecated.** Use **deviceGroups** instead. This property will be removed from this resource on October 1, 2026. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.organizationalScope",
  "deviceGroups": [
    "String"
  ],
  "scopeType": "String",
  "scopeNames": [
    "String"
  ]
}
```
