<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networklocationdetail?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# networkLocationDetail resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Provides the name and type of network from which the user signed in. This object is configured in the **networkLocationDetails** property of [signIn](https://learn.microsoft.com/en-us/graph/api/resources/signin?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| networkNames | String collection | Provides the name of the network used when signing in. |
| networkType | networkType | Provides the type of network used when signing in. The possible values are: `intranet`, `extranet`, `namedNetwork`, `trusted`, `unknownFutureValue`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "networkNames": ["String"],
  "networkType": "String"
}
```
