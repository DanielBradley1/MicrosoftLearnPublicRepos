<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamstemplate?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# teamsTemplate resource type

Namespace: microsoft.graph

A team template is a blueprint for creating a [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0) in Microsoft Teams. A template specifies the structure, settings, and even content that should be provisioned in a new team created using the template. Microsoft provides a suite of base templates and customers can save their own custom templates.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier of the template. Cannot be null. |

## JSON representation

```json
{
  "id": "string"
}
```

## Related content

- [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0)
