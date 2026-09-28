<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/mediainfo?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# mediaInfo resource type

Namespace: microsoft.graph

The media information used in actions for prompts.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| resourceId | String | Optional. Used to uniquely identity the resource. If passed in, the prompt uri is against this resourceId as a key. |
| uri | String | Path to the prompt that will be played. Currently supports only Wave file \(.wav\) format, single-channel, 16-bit samples with a 16,000 \(16 KHz\) sampling rate. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "resourceId": "String",
  "uri": "String"
}
```
