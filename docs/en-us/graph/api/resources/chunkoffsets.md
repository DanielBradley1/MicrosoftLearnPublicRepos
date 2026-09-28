<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/chunkoffsets?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-09-09 -->

# chunkOffsets resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Provides positional offset metadata for the text chunks that produced caller-supplied embedding data. This type is used by the **chunkOffsets** property of [embeddingInput](https://learn.microsoft.com/en-us/graph/api/resources/embeddinginput?view=graph-rest-beta) and uses base64-encoded integer values instead of floats.

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| lengths | String | An optional base64 string that encodes a packed sequence of little-endian signed 32-bit integers. Decoded values represent chunk lengths and must be nonnegative. The decoded byte count must be divisible by 4. When supplied, the decoded element count must match **starts**, and elements pair by index. |
| starts | String | A base64 string that encodes a packed sequence of little-endian signed 64-bit integers. Decoded values represent chunk start positions and must be nonnegative and in ascending order. The decoded byte count must be divisible by 8. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.chunkOffsets",
  "starts": "String",
  "lengths": "String"
}
```
