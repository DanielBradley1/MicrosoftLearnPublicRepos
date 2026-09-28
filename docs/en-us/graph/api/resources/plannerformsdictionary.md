<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/plannerformsdictionary?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-26 -->

# plannerFormsDictionary resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

An open type that represents a dictionary of data about the forms associated with a task. This resource is a part of the [plannerTaskDetails](https://learn.microsoft.com/en-us/graph/api/resources/plannertaskdetails?view=graph-rest-beta) object. Each entry in the dictionary is a key-value pair, where the value is a [plannerFormReference](https://learn.microsoft.com/en-us/graph/api/resources/plannerformreference?view=graph-rest-beta) object.

## Properties

You can add and remove values from open type properties. Provide GUID values as keys, and [plannerFormReference](https://learn.microsoft.com/en-us/graph/api/resources/plannerformreference?view=graph-rest-beta) objects as values. To remove an item in the forms, set its value to `null`.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "String-value":
  {
    "displayName": "String-value",
    "formWebUrl": "String-value",
    "formResponse": "String-value"
  }
}
```
