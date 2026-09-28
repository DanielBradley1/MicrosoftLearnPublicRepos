<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/workforceintegrationencryption?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-09 -->

# workforceIntegrationEncryption resource type

Namespace: microsoft.graph

An encryption entity defining the protocol and secret for a [workforceintegration](https://learn.microsoft.com/en-us/graph/api/resources/workforceintegration?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| protocol | String | The possible values are: `sharedSecret`, `unknownFutureValue`. |
| secret | String | Encryption shared secret. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "protocol": "String",
  "secret": "String"
}
```
