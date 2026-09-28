<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-developer?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# root.developer object

Specifies information about your company. For apps submitted to the Teams Store, these values must match the information in your Teams Store listing. For more information, see the [Teams Store publishing guidelines](https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/deploy-and-publish/appsource/publish). Developer name helps improve your app discoverability in the Teams Store.

Specifies information about the developer and their business. For Teams Store apps, the value must match the values that you provide in the Partner Center app submission form.

Properties that reference this object type:

- [root.developer](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root?view=m365-app-1.30#developer-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "name": "{string}",
  "mpnId": "{string}",
  "websiteUrl": "{string}",
  "privacyUrl": "{string}",
  "termsOfUseUrl": "{string}",
  "contactInfo": {
    "defaultSupport": {
      defaultSupport object
    }
  }
}
```

```json
{
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "name": {
      "type": "string",
      "description": "The display name for the developer.",
      "maxLength": 32
    },
    "mpnId": {
      "type": "string",
      "description": "The Microsoft Partner Network ID that identifies the partner organization building the app. This field is not required, and should only be used if you are already part of the Microsoft Partner Network. More info at https://aka.ms/partner",
      "maxLength": 10
    },
    "websiteUrl": {
      "$ref": "#/definitions/anyHttpUrl",
      "description": "The url to the page that provides support information for the app."
    },
    "privacyUrl": {
      "$ref": "#/definitions/anyHttpUrl",
      "description": "The url to the page that provides privacy information for the app."
    },
    "termsOfUseUrl": {
      "$ref": "#/definitions/anyHttpUrl",
      "description": "The url to the page that provides the terms of use for the app."
    },
    "contactInfo": {
      "type": "object",
      "description": "App developer contact information.",
      "properties": {
        "defaultSupport": {
          "type": "object",
          "description": "Support configuration.",
          "properties": {
            "userEmailsForChatSupport": {
              "type": "array",
              "description": "User email for chat support contacts.",
              "maxItems": 10,
              "minItems": 1,
              "items": {
                "type": "string",
                "maxLength": 80
              }
            },
            "emailsForEmailSupport": {
              "type": "array",
              "description": "Email address for email support.",
              "maxItems": 1,
              "minItems": 1,
              "items": {
                "type": "string",
                "maxLength": 80
              }
            }
          },
          "required": [
            "emailsForEmailSupport",
            "userEmailsForChatSupport"
          ]
        }
      },
      "required": [
        "defaultSupport"
      ]
    }
  },
  "required": [
    "name",
    "websiteUrl",
    "privacyUrl",
    "termsOfUseUrl"
  ]
}
```

- [Syntax](#tabpanel_2_syntax)
- [Schema](#tabpanel_2_schema)

```json
{
  "name": "{string}",
  "mpnId": "{string}",
  "websiteUrl": "{string}",
  "privacyUrl": "{string}",
  "termsOfUseUrl": "{string}"
}
```

```json
{
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "name": {
      "type": "string",
      "description": "The display name for the developer.",
      "maxLength": 32
    },
    "mpnId": {
      "type": "string",
      "description": "The Microsoft Partner Network ID that identifies the partner organization building the app. This field is not required, and should only be used if you are already part of the Microsoft Partner Network. More info at https://aka.ms/partner",
      "maxLength": 10
    },
    "websiteUrl": {
      "$ref": "#/definitions/anyHttpUrl",
      "description": "The url to the page that provides support information for the app."
    },
    "privacyUrl": {
      "$ref": "#/definitions/anyHttpUrl",
      "description": "The url to the page that provides privacy information for the app."
    },
    "termsOfUseUrl": {
      "$ref": "#/definitions/anyHttpUrl",
      "description": "The url to the page that provides the terms of use for the app."
    }
  },
  "required": [
    "name",
    "websiteUrl",
    "privacyUrl",
    "termsOfUseUrl"
  ]
}
```

- [Syntax](#tabpanel_3_syntax)
- [Schema](#tabpanel_3_schema)

```json
{
  "name": "{string}",
  "mpnId": "{string}",
  "websiteUrl": "{string}",
  "privacyUrl": "{string}",
  "termsOfUseUrl": "{string}"
}
```

```json
{
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "name": {
      "type": "string",
      "description": "The display name for the developer.",
      "maxLength": 32
    },
    "mpnId": {
      "type": "string",
      "description": "The Microsoft Partner Network ID that identifies the partner organization building the app. This field is not required, and should only be used if you are already part of the Microsoft Partner Network. More info at https://aka.ms/partner",
      "maxLength": 10
    },
    "websiteUrl": {
      "$ref": "#/definitions/httpsUrl",
      "description": "The url to the page that provides support information for the app."
    },
    "privacyUrl": {
      "$ref": "#/definitions/httpsUrl",
      "description": "The url to the page that provides privacy information for the app."
    },
    "termsOfUseUrl": {
      "$ref": "#/definitions/httpsUrl",
      "description": "The url to the page that provides the terms of use for the app."
    }
  },
  "required": [
    "name",
    "websiteUrl",
    "privacyUrl",
    "termsOfUseUrl"
  ]
}
```

## Properties

#### name

The display name for the developer.

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 32.

**Supported values**  


#### mpnId

The Microsoft Cloud Partner Program ID \(formerly known as Microsoft Partner Network \(MPN\) ID\) that identifies the partner organization building the app.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 10.

**Supported values**  


#### websiteUrl

The https:// URL to the developer's website. This link must take users to your company or product-specific landing page.

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 2048.

**Supported values**  
The string must start with `http://` or `https://`.

#### privacyUrl

The https:// URL to the developer's privacy policy.

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 2048.

**Supported values**  
The string must start with `http://` or `https://`.

#### termsOfUseUrl

The https:// URL to the developer's terms of use.

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 2048.

**Supported values**  
The string must start with `http://` or `https://`.

#### contactInfo

App developer's contact information.

**Type**  
[contactInfo](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-developer-contact-info?view=m365-app-1.30)

**Required**  
—

**Constraints**  


**Supported values**  


## Examples

```json
{
    "developer": {
        "name": "Publisher Name",
        "websiteUrl": "https://example.com/",
        "privacyUrl": "https://example.com/privacy",
        "termsOfUseUrl": "https://example.com/app-tos",
        "mpnId": "1234567890"
    }
}
```
