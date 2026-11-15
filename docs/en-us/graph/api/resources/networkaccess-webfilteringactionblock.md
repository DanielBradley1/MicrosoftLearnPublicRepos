<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webfilteringactionblock?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-13 -->

# webFilteringActionBlock resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an action that blocks web traffic when a [webFilteringRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webfilteringrule?view=graph-rest-beta) matches.

Inherits from [microsoft.graph.networkaccess.webFilteringAction](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webfilteringaction?view=graph-rest-beta).

Instances of this type can be used by the **action** property of [webFilteringRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webfilteringrule?view=graph-rest-beta) and the **defaultAction** property of [webFilteringPolicySettings](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webfilteringpolicysettings?view=graph-rest-beta), both of which have type [webFilteringAction](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webfilteringaction?view=graph-rest-beta).

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
  "@odata.type": "#microsoft.graph.networkaccess.webFilteringActionBlock"
}
```
