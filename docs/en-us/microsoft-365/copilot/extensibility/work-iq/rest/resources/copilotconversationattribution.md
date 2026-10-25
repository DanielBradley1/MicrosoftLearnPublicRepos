<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/work-iq/rest/resources/copilotconversationattribution -->
<!-- Sitemap-Last-Modified: 2026-10-19 -->

# Work IQ - copilotConversationAttribution resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications isn't supported.

Describes a citation or annotation in a [copilotConversationResponseMessage](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/work-iq/rest/resources/copilotconversationresponsemessage) from the Work IQ Chat API.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `attributionSource` | [copilotConversationAttributionSource](#copilotconversationattributionsource-enumeration) | The source of the attribution. |
| `attributionType` | [copilotConversationAttributionType](#copilotconversationattributiontype-enumeration) | The type of attribution. |
| `imageFavIcon` | String | The base64-encoded favicon image URL for the attribution. |
| `imageHeight` | Int32 | The height of the image, if included. |
| `imageWebUrl` | String | The URL for the attribution image, if included. |
| `imageWidth` | Int32 | The width of the image, if included. |
| `providerDisplayName` | String | Display text for the provider of the attribution. |
| `seeMoreWebUrl` | String | The destination URL for the attribution. |

### copilotConversationAttributionType enumeration

An [evolvable enumeration](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations) with the following possible values.

| Value |
| :--- |
| `citation` |
| `annotation` |

### copilotConversationAttributionSource enumeration

An [evolvable enumeration](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations) with the following possible values.

| Value |
| :--- |
| `grounding` |
| `model` |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.copilotConversationAttribution",
  "attributionType": "String",
  "providerDisplayName": "String",
  "attributionSource": "String",
  "seeMoreWebUrl": "String",
  "imageWebUrl": "String",
  "imageFavIcon": "String",
  "imageWidth": "Int32",
  "imageHeight": "Int32"
}
```
