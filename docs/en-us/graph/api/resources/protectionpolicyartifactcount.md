<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/protectionpolicyartifactcount?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-08-21 -->

# protectionPolicyArtifactCount resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the count of artifacts protected as part of a [protection policy](https://learn.microsoft.com/en-us/graph/api/resources/protectionpolicybase?view=graph-rest-beta) by status.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| completed | Int32 | The number of artifacts whose protection is completed. |
| failed | Int32 | The number of artifacts whose protection failed. |
| inProgress | Int32 | The number of artifacts whose protection is in progress. |
| total | Int32 | The number of artifacts present in the protection policy. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.protectionPolicyArtifactCount",
  "completed": "Int32",
  "failed": "Int32",
  "inProgress": "Int32",
  "total": "Int32"
}
```
