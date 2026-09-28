<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/workbookcommentmention?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-09-20 -->

# workbookCommentMention resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the person mentioned in a workbook comment.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| email | String | Represents the email address of the person that is mentioned in a comment. |
| id | Int32 | Represents the ID of the person that is mentioned in a comment. |
| name | String | Represents the display name of the person that is mentioned in a comment. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "email": "String",
  "id": "Int32",
  "name": "String"
}
```
