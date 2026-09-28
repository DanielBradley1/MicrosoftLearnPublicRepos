<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/callrecords-clientuseragent?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# clientUserAgent resource type

Namespace: microsoft.graph.callRecords

Represents a client user agent of an endpoint in a call. Inherits from the [userAgent](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-useragent?view=graph-rest-1.0) type.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| applicationVersion | String | Identifies the version of application software used by this endpoint. |
| azureADAppId | String | The unique identifier of the Microsoft Entra application used by this endpoint. |
| communicationServiceId | String | Immutable resource identifier of the Azure Communication Service associated with this endpoint based on [Communication Services APIs](https://azure.microsoft.com/services/communication-services/). |
| headerValue | String | User-agent header value reported by this endpoint. |
| platform | microsoft.graph.callRecords.clientPlatform | Identifies the platform used by this endpoint. The possible values are: `unknown`, `windows`, `macOS`, `iOS`, `android`, `web`, `ipPhone`, `roomSystem`, `surfaceHub`, `holoLens`, `unknownFutureValue`. |
| productFamily | microsoft.graph.callRecords.productFamily | Identifies the family of application software used by this endpoint. The possible values are: `unknown`, `teams`, `skypeForBusiness`, `lync`, `unknownFutureValue`, `azureCommunicationServices`. Use the `Prefer: include-unknown-enum-members` request header to get the following members in this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `azureCommunicationServices`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "applicationVersion": "String",
  "azureADAppId": "String",
  "communicationServiceId": "String",
  "headerValue": "String",
  "platform": "String",
  "productFamily": "String"
}
```
