<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/classificationrequestcontentmetadata?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# classificationRequestContentMetaData resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Metadata that describes the content being classified. Pass this optional metadata in the [textClassificationRequest](https://learn.microsoft.com/en-us/graph/api/resources/textclassificationrequest?view=graph-rest-beta) **contentMetaData** property to give the service additional context about the source of the content.

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| sourceId | String | An identifier for the source of the content being classified. |
| workloadType | [mipWorkloads](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-beta#mipworkloads-values) | The type of workload the content belongs to. The possible values are: `endpointDevices`, `exchange`, `oneDriveForBusiness`, `sharePoint`, `teams`, `coldCrawl`, `applications`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.classificationRequestContentMetaData",
  "sourceId": "String",
  "workloadType": "String"
}
```
