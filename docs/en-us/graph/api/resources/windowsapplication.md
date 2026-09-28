<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowsapplication?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# windowsApplication resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents settings for apps running Microsoft Windows and published in the Microsoft Store or Xbox games store.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| packageSid | String | The package security identifier that Microsoft has assigned the application. Optional. Read-only. |
| redirectUris | String collection | Specifies the URLs where user tokens are sent for sign-in or the redirect URIs where OAuth 2.0 authorization codes and access tokens are sent. Only available for applications that support the `PersonalMicrosoftAccount` **signInAudience**. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "packageSid": "String",
  "redirectUris": ["String"]
}
```
