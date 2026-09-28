<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-compose-extensions-authorization?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# root.composeExtensions.authorization object

The authorization property represents authorization info for API-based message extensions. For more, see [Enable authentication for API-based message extensions](https://learn.microsoft.com/en-us/microsoftteams/platform/messaging-extensions/build-api-based-message-extension).

Properties that reference this object type:

- [root.composeExtensions.authorization](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-compose-extensions?view=m365-app-1.30#authorization-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "authType": "none | apiSecretServiceAuth | microsoftEntra | oAuth2.0",
  "microsoftEntraConfiguration": {
    "supportsSingleSignOn": {boolean}
  },
  "apiSecretServiceAuthConfiguration": {
    "apiSecretRegistrationId": "{string}"
  },
  "oAuthConfiguration": {
    "oAuthConfigurationId": "{string}"
  }
}
```

```json
{
  "type": "object",
  "description": "Object capturing authorization information.",
  "properties": {
    "authType": {
      "type": "string",
      "enum": [
        "none",
        "apiSecretServiceAuth",
        "microsoftEntra",
        "oAuth2.0"
      ],
      "description": "Enum of possible authorization types."
    },
    "microsoftEntraConfiguration": {
      "type": "object",
      "description": "Object capturing details needed to do microsoftEntra auth flow. It will be only present when auth type is microsoftEntra.",
      "properties": {
        "supportsSingleSignOn": {
          "type": "boolean",
          "default": false,
          "description": "Boolean indicating whether single sign on is configured for the app."
        }
      },
      "additionalProperties": false
    },
    "apiSecretServiceAuthConfiguration": {
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
    },
    "oAuthConfiguration": {
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
  },
  "additionalProperties": false
}
```

- [Syntax](#tabpanel_2_syntax)
- [Schema](#tabpanel_2_schema)

```json
{
  "authType": "none | apiSecretServiceAuth | microsoftEntra | oAuth2.0",
  "microsoftEntraConfiguration": {
    "supportsSingleSignOn": {boolean}
  },
  "apiSecretServiceAuthConfiguration": {
    "apiSecretRegistrationId": "{string}"
  },
  "oAuthConfiguration": {
    "oAuthConfigurationId": "{string}"
  }
}
```

```json
{
  "type": "object",
  "description": "Object capturing authorization information.",
  "properties": {
    "authType": {
      "type": "string",
      "enum": [
        "none",
        "apiSecretServiceAuth",
        "microsoftEntra",
        "oAuth2.0"
      ],
      "description": "Enum of possible authentication types."
    },
    "microsoftEntraConfiguration": {
      "type": "object",
      "description": "Object capturing details needed to do single aad auth flow. It will be only present when auth type is entraId.",
      "properties": {
        "supportsSingleSignOn": {
          "type": "boolean",
          "default": false,
          "description": "Boolean indicating whether single sign on is configured for the app."
        }
      },
      "additionalProperties": false
    },
    "apiSecretServiceAuthConfiguration": {
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
    },
    "oAuthConfiguration": {
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
  },
  "additionalProperties": false
}
```

- [Syntax](#tabpanel_3_syntax)
- [Schema](#tabpanel_3_schema)

```json
{
  "authType": "none | apiSecretServiceAuth | microsoftEntra",
  "microsoftEntraConfiguration": {
    "supportsSingleSignOn": {boolean}
  },
  "apiSecretServiceAuthConfiguration": {
    "apiSecretRegistrationId": "{string}"
  }
}
```

```json
{
  "type": "object",
  "description": "Object capturing authorization information.",
  "properties": {
    "authType": {
      "type": "string",
      "enum": [
        "none",
        "apiSecretServiceAuth",
        "microsoftEntra"
      ],
      "description": "Enum of possible authentication types."
    },
    "microsoftEntraConfiguration": {
      "type": "object",
      "description": "Object capturing details needed to do single aad auth flow. It will be only present when auth type is entraId.",
      "properties": {
        "supportsSingleSignOn": {
          "type": "boolean",
          "default": false,
          "description": "Boolean indicating whether single sign on is configured for the app."
        }
      },
      "additionalProperties": false
    },
    "apiSecretServiceAuthConfiguration": {
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
  },
  "additionalProperties": false
}
```

## Properties

#### authType

Enum of possible authorization types.

**Type**  
string

**Required**  
—

**Constraints**  


**Supported values**  
Allowed values: `none`, `apiSecretServiceAuth`, `microsoftEntra`, `oAuth2.0`.

#### authType

Enum of possible authorization types.

**Type**  
string

**Required**  
—

**Constraints**  


**Supported values**  
Allowed values: `none`, `apiSecretServiceAuth`, `microsoftEntra`.

#### microsoftEntraConfiguration

Object capturing details needed to do microsoftEntra auth flow. Applicable only when auth type is `microsoftEntra`.

**Type**  
[microsoftEntraConfiguration](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-compose-extensions-authorization-microsoft-entra-configuration?view=m365-app-1.30)

**Required**  
—

**Constraints**  


**Supported values**  


#### apiSecretServiceAuthConfiguration

Object capturing details needed to do service auth. Applicable only when auth type is `apiSecretServiceAuth`.

**Type**  
[apiSecretServiceAuthConfiguration](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-compose-extensions-authorization-api-secret-service-auth-configuration?view=m365-app-1.30)

**Required**  
—

**Constraints**  


**Supported values**  


#### oAuthConfiguration

Object capturing details needed to match the application's OAuth configuration for the app. This should be and must be populated only when `authType` is set to *oAuth2.0*.

**Type**  
[oAuthConfiguration](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-compose-extensions-authorization-o-auth-configuration?view=m365-app-1.30)

**Required**  
—

**Constraints**  


**Supported values**
