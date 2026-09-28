<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/redirecturisettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# redirectUriSettings resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Specifies the index of the URLs where user tokens are sent for sign-in. This is only valid for applications using SAML.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| uri | String | Specifies the URI that tokens are sent to. |
| index | Int32 | Identifies the specific URI within the redirectURIs collection in SAML SSO flows. Defaults to `null`. The index is unique across all the redirectUris for the application. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.redirectUriSettings",
  "uri": "String",
  "index": "Integer"
}
```
