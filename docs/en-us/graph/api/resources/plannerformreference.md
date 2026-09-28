<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/plannerformreference?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-26 -->

# plannerFormReference resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents complete details about a form, including the form's display name, URL, and the response data. This object is typically used as a value in the [plannerFormsDictionary](https://learn.microsoft.com/en-us/graph/api/resources/plannerformsdictionary?view=graph-rest-beta) object.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The display name of the form. |
| formWebUrl | String | The URL of the form associated with the **plannerFormReference** object. |
| formResponse | String | The unique identifier of the response. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
    "displayName": "String-value",
    "formWebUrl": "String-value",
    "formResponse": "String-value"
}
```
