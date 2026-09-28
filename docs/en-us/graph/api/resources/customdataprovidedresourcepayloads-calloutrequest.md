<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/customdataprovidedresourcepayloads-calloutrequest?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-25 -->

# calloutRequest resource type

Namespace: microsoft.graph.customDataProvidedResourcePayloads

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the payload sent to a customer-managed Logic App workflow when a [customDataProvidedResource](https://learn.microsoft.com/en-us/graph/api/resources/customdataprovidedresource?view=graph-rest-beta) upload is triggered. The envelope includes identifiers for the source, catalog, and resource, along with a data payload that provides the context for the callout.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| catalogId | String | The unique identifier of the catalog that contains the custom data provided resource. |
| data | [microsoft.graph.customDataProvidedResourcePayloads.data](https://learn.microsoft.com/en-us/graph/api/resources/customdataprovidedresourcepayloads-data?view=graph-rest-beta) | An object containing the context data for the callout, such as access review identifiers. |
| resourceId | String | The unique identifier of the custom data provided resource that the callout is for. |
| source | String | The source of the callout request, for example, `/identityGovernance/accessReviews`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.customDataProvidedResourcePayloads.calloutRequest",
  "source": "String",
  "catalogId": "String",
  "resourceId": "String",
  "data": {
    "@odata.type": "microsoft.graph.customDataProvidedResourcePayloads.data"
  }
}
```
