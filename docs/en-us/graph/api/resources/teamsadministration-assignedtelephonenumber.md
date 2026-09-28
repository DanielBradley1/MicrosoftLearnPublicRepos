<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamsadministration-assignedtelephonenumber?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-19 -->

# assignedTelephoneNumber resource type

Namespace: microsoft.graph.teamsAdministration

Represents details about the phone number and its corresponding assignment category. The assignment category can include values such as `primary`, `private`, and `alternate`.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| assignmentCategory | microsoft.graph.teamsAdministration.assignmentCategory | The category of the assigned phone number. The possible values are: `primary`, `private`, `alternate`, `unknownFutureValue`. |
| telephoneNumber | String | The assigned phone number. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.teamsAdministration.assignedTelephoneNumber",
  "assignmentCategory": "String",
  "telephoneNumber": "String"
}
```
