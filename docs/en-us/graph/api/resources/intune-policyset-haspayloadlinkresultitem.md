<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-haspayloadlinkresultitem?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# hasPayloadLinkResultItem resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

A class containing the result of HasPayloadLinks action.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| payloadId | String | Key of the Payload, In the format of Guid. |
| hasLink | Boolean | Indicate whether a payload has any link or not. |
| error | String | Exception information indicates if check for this item was successful or not.Empty string for no error. |
| sources | [deviceAndAppManagementAssignmentSource](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceandappmanagementassignmentsource?view=graph-rest-beta) collection | The reason where the link comes from. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.hasPayloadLinkResultItem",
  "payloadId": "String",
  "hasLink": true,
  "error": "String",
  "sources": [
    "String"
  ]
}
```
