<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/educationassignmentindividualrecipient?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-09 -->

# educationAssignmentIndividualRecipient resource type

Namespace: microsoft.graph

Used inside the [assignment.assignTo](https://learn.microsoft.com/en-us/graph/api/resources/educationassignment?view=graph-rest-1.0) property. When set to individual recipient list, selected students in the class will receive a submission object when the assignment is published.

This resource is a subclass of [educationAssignmentRecipient](https://learn.microsoft.com/en-us/graph/api/resources/educationassignmentrecipient?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| recipients | String collection | A collection of IDs of the recipients. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "recipients": ["String"]
}
```
