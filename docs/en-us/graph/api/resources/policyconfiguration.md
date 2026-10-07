<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/policyconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-09-29 -->

# policyConfiguration resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the effective configuration that applies to policy evaluation scenarios. This type is used by the **policyConfiguration** property of [policyScopeBase](https://learn.microsoft.com/en-us/graph/api/resources/policyscopebase?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| errorSettings | [errorSettings](https://learn.microsoft.com/en-us/graph/api/resources/errorsettings?view=graph-rest-beta) | Settings that control enforcement behavior when policy evaluation can't be completed. |
| lastModifiedDateTime | DateTimeOffset | The date and time when the effective policy configuration was last modified. The timestamp is always in UTC. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.policyConfiguration",
  "errorSettings": {
    "@odata.type": "#microsoft.graph.errorSettings"
  },
  "lastModifiedDateTime": "DateTimeOffset"
}
```
