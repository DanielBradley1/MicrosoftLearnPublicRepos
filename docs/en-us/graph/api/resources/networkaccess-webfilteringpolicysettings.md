<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webfilteringpolicysettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-13 -->

# webFilteringPolicySettings resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the default behavior for traffic that does not match a rule in a [webFilteringPolicy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webfilteringpolicy?view=graph-rest-beta).

This type is used by the **settings** property of [webFilteringPolicy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webfilteringpolicy?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| defaultAction | [microsoft.graph.networkaccess.webFilteringAction](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webfilteringaction?view=graph-rest-beta) | The action to apply to web traffic that does not match any rule in the policy. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.webFilteringPolicySettings",
  "defaultAction": {
    "@odata.type": "microsoft.graph.networkaccess.webFilteringAction"
  }
}
```
