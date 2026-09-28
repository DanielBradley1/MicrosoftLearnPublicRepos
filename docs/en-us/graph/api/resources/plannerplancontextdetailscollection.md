<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/plannerplancontextdetailscollection?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-11 -->

# plannerPlanContextDetailsCollection resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

The **plannerPlanContextDetailsCollection** resource represents the collection of external contexts to which a plan is linked. This resource is an open type that allows additional properties beyond those documented here and is part of the [plannerPlanDetails](https://learn.microsoft.com/en-us/graph/api/resources/plannerplandetails?view=graph-rest-beta) object. The property name in the property-value pair is an app-specific identifier of the context; the value is the [plannerPlanContextDetails](https://learn.microsoft.com/en-us/graph/api/resources/plannerplancontextdetails?view=graph-rest-beta) object.

## Properties

Properties of an open type can be defined by the client. In this case, the client should use a distinctive identifier that represents the external context as the property name. The property values must be [plannerPlanContextDetails](https://learn.microsoft.com/en-us/graph/api/resources/plannerplancontextdetails?view=graph-rest-beta) objects. Based on OData, property names in open types cannot contain the following characters: `.`, `:`, `@`, `%`. These characters need to be encoded with URL encoding format. To remove an item in the favorites list, the value needs to be removed from the [plannerPlanContextCollection](https://learn.microsoft.com/en-us/graph/api/resources/plannerplancontextcollection?view=graph-rest-beta) collection instead, which will automatically remove the entry in this object.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
}
```
