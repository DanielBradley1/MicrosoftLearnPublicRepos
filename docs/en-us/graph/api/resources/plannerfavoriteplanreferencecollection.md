<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/plannerfavoriteplanreferencecollection?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-11 -->

# plannerFavoritePlanReferenceCollection resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

The **plannerFavoritePlanReferenceCollection** resource represents the collection of references to plans that are marked as a favorite by a user. This resource is an open type that allows additional properties beyond those documented here and is part of the [plannerUser](https://learn.microsoft.com/en-us/graph/api/resources/planneruser?view=graph-rest-beta) object. The property name in the property-value pair is the ID of the corresponding plan; the value is the [plannerFavoritePlanReference](https://learn.microsoft.com/en-us/graph/api/resources/plannerfavoriteplanreference?view=graph-rest-beta) object.

## Properties

You can define the properties of this open type. The property names are `id` values of [plannerPlan](https://learn.microsoft.com/en-us/graph/api/resources/plannerplan?view=graph-rest-beta) resources and their values must be [plannerFavoritePlanReference](https://learn.microsoft.com/en-us/graph/api/resources/plannerfavoriteplanreference?view=graph-rest-beta) objects. To remove an item in the favorites list, set the value of the property to `null`.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "jd8S5gOaFk2S8aWCIAJz42QAAxtD": {
    "@odata.type": "microsoft.graph.plannerFavoritePlanReference",
    "orderHint": "8586866870001551087",
    "planTitle": "Customer reviews"
  },
  "uZWtCtli30CGoWLIWSat1mQAC0ai": {
    "@odata.type": "microsoft.graph.plannerFavoritePlanReference",
    "orderHint": "8586848705198093378",
    "planTitle": "Order Management (December 2017)"
  }
}
```
