<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-web-application-info?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# root.webApplicationInfo object

Specifies information about the app's Microsoft Entra ID application registration.

Properties that reference this object type:

- [root.webApplicationInfo](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root?view=m365-app-1.30#webApplicationInfo-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "id": "{string}",
  "resource": "{string}",
  "nestedAppAuthInfo": [
    {
      "redirectUri": "{string}",
      "scopes": [
        "{string}"
      ],
      "claims": "{string}"
    }
  ]
}
```

```json
{
  "type": "object",
  "description": "Specify your AAD App ID and Graph information to help users seamlessly sign into your AAD app.",
  "properties": {
    "id": {
      "$ref": "#/definitions/guid",
      "description": "AAD application id of the app. This id must be a GUID."
    },
    "resource": {
      "type": "string",
      "description": "Resource url of app for acquiring auth token for SSO.",
      "maxLength": 2048
    },
    "nestedAppAuthInfo": {
      "type": "array",
      "maxItems": 5,
      "description": "By including this property, an NAA token based on its contents will be prefetched when the tab is loaded.",
      "items": {
        "type": "object",
        "properties": {
          "redirectUri": {
            "type": "string",
            "description": "Represents the nested app\u0027s valid redirect URI (always a base origin)."
          },
          "scopes": {
            "type": "array",
            "description": "Represents the stringified list of scopes the access token requested requires. Order must match that of the proceeding NAA request in the app.",
            "maxItems": 20,
            "items": {
              "type": "string"
            }
          },
          "claims": {
            "type": "string",
            "description": "An optional JSON formatted object of client capabilities that represents if the resource server is CAE capable. Do not use an empty string for this value. If unsupported, keep the field undefined. If supported, use the following string exactly: \u0027{\u0022access_token\u0022:{\u0022xms_cc\u0022:{\u0022values\u0022:[\u0022CP1\u0022]}}}\u0027. More info on client capabilities here: https://learn.microsoft.com/en-us/entra/identity-platform/claims-challenge?tabs=dotnet#how-to-communicate-client-capabilities-to-microsoft-entra-id ",
            "minLength": 1
          }
        },
        "required": [
          "redirectUri",
          "scopes"
        ],
        "additionalProperties": false
      }
    }
  },
  "required": [
    "id"
  ],
  "additionalProperties": false
}
```

- [Syntax](#tabpanel_2_syntax)
- [Schema](#tabpanel_2_schema)

```json
{
  "id": "{string}",
  "resource": "{string}"
}
```

```json
{
  "type": "object",
  "description": "Specify your AAD App ID and Graph information to help users seamlessly sign into your AAD app.",
  "properties": {
    "id": {
      "$ref": "#/definitions/guid",
      "description": "AAD application id of the app. This id must be a GUID."
    },
    "resource": {
      "type": "string",
      "description": "Resource url of app for acquiring auth token for SSO.",
      "maxLength": 2048
    }
  },
  "required": [
    "id"
  ],
  "additionalProperties": false
}
```

## Properties

#### id

Microsoft Entra application ID of the app. This ID must be a GUID.

**Type**  
string

**Required**  
✅

**Constraints**  


**Supported values**  
The string value must be a [guid](https://en.wikipedia.org/wiki/Universally_unique_identifier).

#### resource

Resource URL of app for acquiring auth token for SSO.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 2048.

**Supported values**  


#### nestedAppAuthInfo

By including this property, an NAA token based on its contents will be prefetched when the tab is loaded.

**Type**  
Array of [nestedAppAuthInfo](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-web-application-info-nested-app-auth-info?view=m365-app-1.30)

**Required**  
—

**Constraints**  
Maximum array items: 5.

**Supported values**  


## Remarks

If you aren't using SSO, ensure that you enter a dummy string value for the `resource` value to avoid an error response, for example *https://example*. The dummy URL string value must not contain domains or URLs that aren't in your control, either directly or through wildcards. For example, `yourapp.onmicrosoft.com` is valid, but `*.onmicrosoft.com` isn't valid. Top-level domains, such as `*.com` and `*.org`, are prohibited.

Note

- If your app includes an Office Add-in, be sure you're familiar with where the single sign-on API in the Office JavaScript Library is currently supported. See [Identity API requirement sets](https://learn.microsoft.com/en-us/javascript/api/requirement-sets/common/identity-api-requirement-sets).
- If you're working with an Outlook add-in, be sure to enable Modern Authentication for the Microsoft 365 tenancy. To learn how to do this, see [Enable or disable modern authentication for Outlook in Exchange Online](https://learn.microsoft.com/en-us/exchange/clients-and-mobile-in-exchange-online/enable-or-disable-modern-authentication-in-exchange-online).

## Examples

```json
{
    "webApplicationInfo": {
        "id": "12345678-abcd-1234-efab-123456789abc",
        "resource": "api://contoso.com/12345678-abcd-1234-efab-123456789abc"
    }
}
```
