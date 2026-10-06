<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-web-application-info-nested-app-auth-info?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-10-01 -->

# root.webApplicationInfo.nestedAppAuthInfo object

By including this property, an NAA token based on its contents will be prefetched when the tab is loaded.

Properties that reference this object type:

- [root.webApplicationInfo.nestedAppAuthInfo](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-web-application-info?view=m365-app-1.30#nestedAppAuthInfo-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "redirectUri": "{string}",
  "scopes": [
    "{string}"
  ],
  "claims": "{string}",
  "clientId": "{string}"
}
```

```json
{
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
    },
    "clientId": {
      "type": "string",
      "description": "Optional Microsoft Entra ID application (client) ID to use for Nested App Authentication (NAA) for this specific manifest entry. If specified, this value overrides the client ID defined in webApplicationInfo.id. If omitted, webApplicationInfo.id is used as the default client ID.",
      "minLength": 1
    }
  },
  "required": [
    "redirectUri",
    "scopes"
  ],
  "additionalProperties": false
}
```

- [Syntax](#tabpanel_2_syntax)
- [Schema](#tabpanel_2_schema)

```json
{
  "redirectUri": "{string}",
  "scopes": [
    "{string}"
  ],
  "claims": "{string}"
}
```

```json
{
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
```

## Properties

#### redirectUri

Represents the nested app's valid redirect URI \(always a base origin\).

**Type**  
string

**Required**  
✅

**Constraints**  


**Supported values**  


#### scopes

Represents the stringified list of scopes the access token requested requires. Order must match that of the proceeding NAA request in the app.

**Type**  
Array of string

**Required**  
✅

**Constraints**  
Maximum array items: 20.

**Supported values**  


#### claims

An optional JSON formatted object of client capabilities that represents if the resource server is CAE capable. Do not use an empty string for this value. If unsupported, keep the field undefined. If supported, use the following string exactly: `{"access_token":{"xms_cc":{"values":["CP1"]}}}`. For more information on client capabilities, see [How to communicate client capabilities to Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity-platform/claims-challenge?tabs=dotnet#how-to-communicate-client-capabilities-to-microsoft-entra-id).

**Type**  
string

**Required**  
—

**Constraints**  
Minimum string length: 1.

**Supported values**  


#### clientId

Optional Microsoft Entra ID application \(client\) ID to use for Nested App Authentication \(NAA\) for this specific manifest entry. If specified, this value overrides the client ID defined in webApplicationInfo.id. If omitted, webApplicationInfo.id is used as the default client ID.

**Type**  
string

**Required**  
—

**Constraints**  
Minimum string length: 1.

**Supported values**
