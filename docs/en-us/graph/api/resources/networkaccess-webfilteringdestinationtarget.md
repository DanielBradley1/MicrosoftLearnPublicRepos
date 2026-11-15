<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webfilteringdestinationtarget?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-13 -->

# webFilteringDestinationTarget resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a destination target used to match web traffic. This is an abstract type that can't be instantiated directly.

The following types derive from this resource:

- [webFilteringUrlDestination](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webfilteringurldestination?view=graph-rest-beta)
- [webFilteringWebCategoryDestination](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webfilteringwebcategorydestination?view=graph-rest-beta)

Instances are differentiated by the `@odata.type` property.

This type is used by the **targets** collection property of [webFilteringDestinationMatching](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webfilteringdestinationmatching?view=graph-rest-beta).

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
  "@odata.type": "#microsoft.graph.networkaccess.webFilteringDestinationTarget"
}
```
