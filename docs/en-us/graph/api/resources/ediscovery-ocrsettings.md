<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-ocrsettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-10 -->

# ocrSettings resource type

Namespace: microsoft.graph.ediscovery

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

The eDiscovery APIs in the microsoft.graph.eDiscovery subnamespace are deprecated. Use the new [eDiscovery APIs under microsoft.graph.security subnamespace](https://learn.microsoft.com/en-us/graph/api/resources/security-api-overview#ediscovery).

The OCR \(Optical Character Recognition\) settings for the eDiscovery case.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| isEnabled | Boolean | Indicates whether or not OCR is enabled for the case. |
| maxImageSize | Int32 | Maximum image size that will be processed in KB\). |
| timeout | Duration | The timeout duration for the OCR engine. A longer timeout may increase success of OCR, but may add to the total processing time. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.ediscovery.ocrSettings",
  "isEnabled": "Boolean",
  "maxImageSize": "Integer",
  "timeout": "String (duration)"
}
```
