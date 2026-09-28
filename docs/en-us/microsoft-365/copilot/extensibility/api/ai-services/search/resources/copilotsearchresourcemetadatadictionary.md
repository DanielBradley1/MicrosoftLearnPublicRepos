<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/search/resources/copilotsearchresourcemetadatadictionary -->
<!-- Sitemap-Last-Modified: 2025-10-20 -->

# copilotSearchResourceMetadataDictionary resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Represents a dictionary of metadata properties for a search result.

## Properties

This resource is a dictionary with string keys and string values. The property names in the dictionary correspond to the list of metadata fields requested in the `resourceMetadataNames` parameter to the [search API](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/search/copilotroot-search). The property values are string representations of the value of the corresponding metadata fields.

Supported field names include: `path`, `author`, `fileName`, `fileType`, `title`, `id`, `driveId`, `siteId`, `listId`, `createdBy`, `lastModifiedTime`, and `modifiedBy`.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "title": "String",
  "author": "String",
  "lastModifiedTime": "String",
  "fileType": "String"
}
```
