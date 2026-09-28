<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/plannerplancontextcollection?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-11 -->

# plannerPlanContextCollection resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

The **plannerPlanContextCollection** resource represents the collection of external contexts to which a plan is linked. This resource is an open type that allows additional properties beyond those documented here and is part of the [plannerPlan](https://learn.microsoft.com/en-us/graph/api/resources/plannerplan?view=graph-rest-beta) object. The value in the property-value pair is the [plannerPlanContext](https://learn.microsoft.com/en-us/graph/api/resources/plannerplancontext?view=graph-rest-beta) object.

## Properties

You can define the properties of this open type. The property values should be distinctive identifier that represents the external context as the property name. The property values must be [plannerPlanContext](https://learn.microsoft.com/en-us/graph/api/resources/plannerplancontext?view=graph-rest-beta) objects. Based on OData requirements, property names in open types cannot contain the following characters: `.`, `:`, `%`, `@`, `#`. These characters need to be encoded using URL encoding. To remove an item in the favorites list, set the value of the property to `null`.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "48#19%3Ad128c63941b24733951ea7defd81e550%40thread%2Eskype19%3Ad128c63941b24733951ea7defd81e550%40thread%2Eskype": {
    "@odata.type": "#microsoft.graph.plannerPlanContext",
    "associationType": "Board",
    "createdDateTime": "2015-10-14T00:57:28.4698344Z",
    "displayNameSegments": [
        "Finance Team",
        "Budget Plans"
    ],
    "ownerAppId": "5e3ce6c0-2b1f-4285-8d4b-75ee78787346"
  }
}
```
