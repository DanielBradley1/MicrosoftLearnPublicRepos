<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/typedemailaddress?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# typedEmailAddress resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the name, email addresses, and their corresponding email address type of a [contact](https://learn.microsoft.com/en-us/graph/api/resources/contact?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| address | String | The email address of a contact. |
| name | String | The display name of a contact. |
| type | String | The type of email address. The possible values are: `unknown`, `work`, `personal`, `main`, `other`. The default value is `unknown`, which means **address** has not been set as a specific type. |
| otherLabel | String | To specify a custom type of email address, set **type** to `other`, and assign **otherLabel** to a custom string. For example, you may use a specific email address for your volunteer activities. Set **type** to `other`, and set **otherLabel** to a custom string such as `Volunteer work`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "address": "string",
  "name": "string",
  "type": "string",
  "otherLabel": "string"
}
```
