<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-catalogcontent?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-27 -->

# catalogContent resource type

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents content that can be deployed from the catalog.

The catalog keeps an inventory of available updates identified by a [microsoft.graph.windowsUpdates.catalogEntry](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-catalogentry?view=graph-rest-beta). The entry, in addition to an **id**, might contain other properties to describe the content. Different categories of content have different entry types and properties, such as `feature`, `quality`, and `driver`.

The typical workflow is to [list entries](https://learn.microsoft.com/en-us/graph/api/windowsupdates-catalog-list-entries?view=graph-rest-beta) of the catalog filtered by specific search criteria until the desired updates to be deployed are identified. Relevant entries can then be wrapped by the **catalogContent** resource type and passed as [deployableContent](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-deployablecontent?view=graph-rest-beta) input to either a [deployment](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-deployment?view=graph-rest-beta) or [contentApproval](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-contentapproval?view=graph-rest-beta) to initiate offering the content to a [deploymentAudience](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-deploymentaudience?view=graph-rest-beta).

Inherits from [deployableContent](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-deployablecontent?view=graph-rest-beta).

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| catalogEntry | [microsoft.graph.windowsUpdates.catalogEntry](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-catalogentry?view=graph-rest-beta) | Metadata for a piece of content that you can approve for deployment. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.windowsUpdates.catalogContent"
}
```
