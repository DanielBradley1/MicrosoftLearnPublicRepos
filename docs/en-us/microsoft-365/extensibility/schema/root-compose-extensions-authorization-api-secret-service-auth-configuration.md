<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-compose-extensions-authorization-api-secret-service-auth-configuration?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# root.composeExtensions.authorization.apiSecretServiceAuthConfiguration object

Object capturing details needed to do service auth. Applicable only when auth type is `apiSecretServiceAuth`.

Properties that reference this object type:

- [root.composeExtensions.authorization.apiSecretServiceAuthConfiguration](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-compose-extensions-authorization?view=m365-app-1.30#apiSecretServiceAuthConfiguration-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "apiSecretRegistrationId": "{string}"
}
```

```json
{
  "type": "object",
  "description": "Object capturing details needed to do service auth. It will be only present when auth type is apiSecretServiceAuth.",
  "properties": {
    "apiSecretRegistrationId": {
      "type": "string",
      "description": "Registration id returned when developer submits the api key through Developer Portal.",
      "maxLength": 128
    }
  },
  "additionalProperties": false
}
```

## Properties

#### apiSecretRegistrationId

Registration ID returned when developer submits the API key through Developer Portal.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 128.

**Supported values**
