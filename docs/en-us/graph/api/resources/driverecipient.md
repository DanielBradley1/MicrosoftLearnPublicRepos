<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/driverecipient?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-09 -->

# driveRecipient resource type

Namespace: microsoft.graph

Represents a person, group, or other recipient to share a drive item with using the [invite](https://learn.microsoft.com/en-us/graph/api/driveitem-invite?view=graph-rest-1.0) action.

When using [invite](https://learn.microsoft.com/en-us/graph/api/driveitem-invite?view=graph-rest-1.0) to add permissions, the **driveRecipient** object would specify the **email**, **alias**, or **objectId** of the recipient. Only one of these values is required; multiple values are not accepted.

## Properties

The recipients resource has these properties.

| Property name | Type | Description |
| :--- | :--- | :--- |
| alias | String | The alias of the domain object, for cases where an email address is unavailable \(for example, security groups\). |
| email | String | The email address for the recipient, if the recipient has an associated email address. |
| objectId | String | The unique identifier for the recipient in the directory. |

## JSON representation

```json
{
  "alias": "string",
  "email": "string",
  "objectId": "string",
}
```
