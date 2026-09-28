<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-compose-extensions-authorization-o-auth-configuration?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# root.composeExtensions.authorization.oAuthConfiguration object

Object capturing details needed to match the application's OAuth configuration for the app. This should be and must be populated only when `authType` is set to *oAuth2.0*. See [Enable OAuth authentication for API-based message extension](https://learn.microsoft.com/en-us/microsoftteams/platform/messaging-extensions/api-based-oauth) for details.

Properties that reference this object type:

- [root.composeExtensions.authorization.oAuthConfiguration](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-compose-extensions-authorization?view=m365-app-1.30#oAuthConfiguration-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "oAuthConfigurationId": "{string}"
}
```

```json
{
  "type": "object",
  "description": "Object capturing details needed to match the application\u0027s OAuth configuration for the app. This should be and must be populated only when authType is set to oAuth2.0r",
  "properties": {
    "oAuthConfigurationId": {
      "type": "string",
      "description": "The oAuth configuration id obtained by the Developer when registering their configuration in Developer Portal.",
      "maxLength": 128
    }
  },
  "additionalProperties": false
}
```

## Properties

#### oAuthConfigurationId

The oAuth configuration id obtained by the Developer when registering their configuration in Developer Portal.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 128.

**Supported values**
