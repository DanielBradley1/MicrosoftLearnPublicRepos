<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/sensitivitylabelassignment?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# sensitivityLabelAssignment resource type

Namespace: microsoft.graph

Provides details about a sensitivity label assigned to a [file](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0) in SharePoint or OneDrive for Business.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| assignmentMethod | sensitivityLabelAssignmentMethod | Indicates whether the label assignment is done automatically, as a standard, or a privileged operation. The possible values are: `standard`, `privileged`, `auto`, `unknownFutureValue`. |
| sensitivityLabelId | String | The unique identifier for the sensitivity label assigned to the file. |
| tenantId | String | The unique identifier for the tenant that hosts the file when this label is applied. |

### sensitivityLabelAssignmentMethod values

| Member | Description |
| :--- | :--- |
| standard | The assignment method for the label is standard. |
| privileged | The assignment method for the label is privileged. Indicates that the label is applied manually by a user or by an admin. |
| auto | Indicates that the label is applied automatically by the system due to a configured policy, such as default label or autoclassification of sensitive content. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| labels | [extractSensitivityLabelsResult](https://learn.microsoft.com/en-us/graph/api/resources/extractsensitivitylabelsresult?view=graph-rest-1.0) | List of sensitivity labels assigned to a file. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.sensitivityLabelAssignment",
  "assignmentMethod": "String",
  "sensitivityLabelId": "String",
  "tenantId": "String"
}
```
