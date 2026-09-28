<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/customextensioncalloutresult?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# customExtensionCalloutResult resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Indicates the result of an API request to the [custom authentication extension](https://learn.microsoft.com/en-us/graph/api/resources/customauthenticationextension?view=graph-rest-beta) endpoint. This object is used by the **appliedEventListeners** object of [sign-ins](https://learn.microsoft.com/en-us/graph/api/resources/signin?view=graph-rest-beta).

Inherits from [authenticationEventHandlerResult](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventhandlerresult?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| calloutDateTime | DateTimeOffset | When the API transaction was initiated, the date and time information uses ISO 8601 format and is always in UTC time. Example: midnight on Jan 1, 2014, is reported as `2014-01-01T00:00:00Z`. |
| customExtensionId | String | Identifier of the custom extension that was called. |
| errorCode | Int32 | Error code that was returned when the last API attempt failed. |
| httpStatus | Int32 | The HTTP status code that was returned by the target API endpoint after the last API attempt. |
| numberOfAttempts | Int32 | The number of API calls to the customer's API. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.customExtensionCalloutResult",
  "customExtensionId": "String",
  "calloutDateTime": "String (timestamp)",
  "numberOfAttempts": "Integer",
  "httpStatus": "Integer",
  "errorCode": "Integer"
}
```
