<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/verifiedpublisher?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# verifiedPublisher resource type

Namespace: microsoft.graph

Represents the verified publisher of the [application](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-1.0). For more information, see [Publisher verification](https://learn.microsoft.com/en-us/azure/active-directory/develop/publisher-verification-overview). Verified publishers are set using [setVerifiedPublisher](https://learn.microsoft.com/en-us/graph/api/application-setverifiedpublisher?view=graph-rest-1.0) and can only be removed using [unsetVerifiedPublisher](https://learn.microsoft.com/en-us/graph/api/application-unsetverifiedpublisher?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| addedDateTime | DateTimeOffSet | The timestamp when the verified publisher was first added or most recently updated. |
| displayName | String | The verified publisher name from the app publisher's Partner Center account. |
| verifiedPublisherId | String | The ID of the verified publisher from the app publisher's Partner Center account. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "displayName": "String",
  "verifiedPublisherId": "String",
  "addedDateTime": "DateTimeOffSet"
}
```
