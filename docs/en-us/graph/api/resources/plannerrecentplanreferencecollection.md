<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/plannerrecentplanreferencecollection?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-11 -->

# plannerRecentPlanReferenceCollection resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

The **plannerRecentPlanReferenceCollection** resource represents the collection of references to plans that were recently viewed by a user. This resource is an open type that allows additional properties beyond those documented here and is part of the [plannerUser](https://learn.microsoft.com/en-us/graph/api/resources/planneruser?view=graph-rest-beta) object. The property name is the ID of the corresponding plan. The value in the property-value pair is the [plannerRecentPlanReference](https://learn.microsoft.com/en-us/graph/api/resources/plannerrecentplanreference?view=graph-rest-beta) object. Adding new references to this collection will automatically remove the oldest entries when the size of the collection exceeds a predetermined maximum value.

## Properties

You can define the properties of this open type. The property names are `id` values of [plannerPlan](https://learn.microsoft.com/en-us/graph/api/resources/plannerplan?view=graph-rest-beta) resources and their values must be [plannerRecentPlanReference](https://learn.microsoft.com/en-us/graph/api/resources/plannerrecentplanreference?view=graph-rest-beta) objects. To remove an item in the favorites list, set the value of the property to `null`.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "7oTB5aMIAE2rVo-1N-L7RmQAGX2q": {
    "@odata.type": "microsoft.graph.plannerRecentPlanReference",
    "lastAccessedDateTime": "2017-12-02T22:49:46.155Z",
    "planTitle": "Purchase Workflow"
  },
  "iKNMHkk3vEWpSF7F7iZWIGQAAMMw": {
    "@odata.type": "microsoft.graph.plannerRecentPlanReference",
    "lastAccessedDateTime": "2017-12-03T21:59:28.975Z",
    "planTitle": "New Year's Office Party"
  }
}
```
