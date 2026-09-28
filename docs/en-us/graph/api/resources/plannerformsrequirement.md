<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/plannerformsrequirement?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-06-10 -->

# plannerFormsRequirement resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a form completion requirement on a [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| requiredForms | String collection | Read-only. A collection of keys from the [plannerFormsDictionary](https://learn.microsoft.com/en-us/graph/api/resources/plannerformsdictionary?view=graph-rest-beta) that identify the [plannerFormReference](https://learn.microsoft.com/en-us/graph/api/resources/plannerformreference?view=graph-rest-beta) objects that specify the requirements to complete the [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.plannerFormsRequirement",
  "requiredForms": ["String"]
}
```
