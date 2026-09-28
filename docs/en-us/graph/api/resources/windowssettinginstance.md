<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowssettinginstance?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# windowsSettingInstance resource type

Namespace: microsoft.graph

Represents a setting instance from the Windows operating system that is stored in the cloud for a given user.

A **windowsSettingInstance** belongs to a [**windowsSetting**](https://learn.microsoft.com/en-us/graph/api/resources/windowssetting?view=graph-rest-1.0).

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/windowssetting-list-instances?view=graph-rest-1.0) | [windowsSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/windowssettinginstance?view=graph-rest-1.0) collection | Get a list of [windowsSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/windowssettinginstance?view=graph-rest-1.0) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/windowssettinginstance-get?view=graph-rest-1.0) | [windowsSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/windowssettinginstance?view=graph-rest-1.0) | Read the properties and relationships of a [windowsSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/windowssettinginstance?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | Set by the server. Represents the dateTime in UTC when the object was created on the server. |
| expirationDateTime | DateTimeOffset | Set by the server. The object expires at the specified dateTime in UTC, making it unavailable after that time. |
| id | String | The unique identifier of the object. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| lastModifiedDateTime | DateTimeOffset | Set by the server if not provided in the request from the Windows client device. Refers to the user's Windows device that modified the object at the specified dateTime in UTC. |
| payload | String | Base64-encoded JSON setting value. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.windowsSettingInstance",
  "id": "6984732f-86b0-8e31-dc02-37fce0df6d61",
  "payload": "VGhpcyBpcyBhbm90aGVyIGp1c3QgYW4gZXhhbXBsZSE=",
  "lastModifiedDateTime": "2024-10-31T23:30:41Z",
  "createdDateTime": "2024-02-12T19:34:35.223Z",
  "expirationDateTime": "2034-02-09T19:34:33.771Z"
}
```
