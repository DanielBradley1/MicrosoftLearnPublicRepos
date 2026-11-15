<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webfilteringaction?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-13 -->

# webFilteringAction resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the action to apply when a web filtering rule matches traffic. This is an abstract type that can't be instantiated directly.

The following types derive from this resource:

- [webFilteringActionAllow](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webfilteringactionallow?view=graph-rest-beta)
- [webFilteringActionBlock](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webfilteringactionblock?view=graph-rest-beta)

Instances are differentiated by the `@odata.type` property.

This type is used by the **action** property of [webFilteringRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webfilteringrule?view=graph-rest-beta) and the **defaultAction** property of [webFilteringPolicySettings](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webfilteringpolicysettings?view=graph-rest-beta).

## Methods

None.

## Properties

None.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.webFilteringAction"
}
```
