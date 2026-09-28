<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/credential?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# credential resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Indicates a single credential used for sign-in to an application. For example, username is one credential, password is another credential.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| fieldId | String | The name of the field for this credential. e.g, username or password or phoneNumber. This is defined by the application. Must match what is in the html field on singleSignOnSettings/password object. |
| type | String | The type for this credential. Valid values: username, password, or other. |
| value | String | The value for this credential. e.g, mysuperhiddenpassword. Note the value for passwords is write-only, the value can never be read back. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.credential",
  "fieldId": "param_username",
  "value": "myusername",
  "type": "username"
}
```
