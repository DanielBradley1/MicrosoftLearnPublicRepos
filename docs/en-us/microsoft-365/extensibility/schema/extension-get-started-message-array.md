<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-get-started-message-array?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# extensionGetStartedMessageArray object

Provides [information used by the callout](https://learn.microsoft.com/en-us/office/dev/add-ins/develop/requirements-property-unified-manifest#extensionsgetstartedmessagesrequirements) that appears when the add-in is installed in Excel, PowerPoint, or Word.

Properties that reference this object type:

- [root.extensions.getStartedMessages](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/element-extensions?view=m365-app-1.30#getStartedMessages-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "requirements": {
    "capabilities": [
      {
        capabilities object
      }
    ],
    "scopes": [
      "mail | workbook | document | presentation"
    ],
    "formFactors": [
      "desktop | mobile"
    ]
  },
  "title": "{string}",
  "description": "{string}",
  "learnMoreUrl": "{string}"
}
```

```json
{
  "type": "object",
  "properties": {
    "requirements": {
      "type": "object",
      "$ref": "#/definitions/requirementsExtensionElement"
    },
    "title": {
      "type": "string",
      "description": "The title used for the top of the callout.",
      "maxLength": 125
    },
    "description": {
      "type": "string",
      "description": "The description/body content for the callout.",
      "maxLength": 250
    },
    "learnMoreUrl": {
      "$ref": "#/definitions/anyHttpUrl",
      "description": "A URL to a page that explains the add-in in detail."
    }
  },
  "additionalProperties": false,
  "required": [
    "title",
    "description",
    "learnMoreUrl"
  ]
}
```

- [Syntax](#tabpanel_2_syntax)
- [Schema](#tabpanel_2_schema)

```json
{
  "requirements": {
    "capabilities": [
      {
        capabilities object
      }
    ],
    "scopes": [
      "mail | workbook | document | presentation"
    ],
    "formFactors": [
      "desktop | mobile"
    ]
  },
  "title": "{string}",
  "description": "{string}",
  "learnMoreUrl": "{string}"
}
```

```json
{
  "type": "object",
  "properties": {
    "requirements": {
      "type": "object",
      "$ref": "#/definitions/requirementsExtensionElement"
    },
    "title": {
      "type": "string",
      "description": "The title used for the top of the callout.",
      "maxLength": 125
    },
    "description": {
      "type": "string",
      "description": "The description/body content for the callout.",
      "maxLength": 250
    },
    "learnMoreUrl": {
      "$ref": "#/definitions/httpsUrl",
      "description": "A URL to a page that explains the add-in in detail."
    }
  },
  "additionalProperties": false,
  "required": [
    "title",
    "description",
    "learnMoreUrl"
  ]
}
```

## Properties

#### requirements

Used when there are multiple get started messages to ensure that only one object is used in any given Office client.

**Type**  
[requirementsExtensionElement](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/requirements-extension-element?view=m365-app-1.30)

**Required**  
—

**Constraints**  


**Supported values**  


#### title

The title used for the top of the callout.

This property is localizable. For more information, see the [localization schema](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/loc-schema/root?view=m365-app-1.30).

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 125.

**Supported values**  


#### description

The description/body content for the callout.

This property is localizable. For more information, see the [localization schema](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/loc-schema/root?view=m365-app-1.30).

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 250.

**Supported values**  


#### learnMoreUrl

A URL to a page that explains the add-in in detail.

Note

Currently, a bug prevents this property from rendering in the callout. However, it is still required to ensure the URL will render correctly once the issue is resolved.

This property is localizable. For more information, see the [localization schema](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/loc-schema/root?view=m365-app-1.30).

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 2048.

**Supported values**  
The string must start with `http://` or `https://`.

If the `getStartedMessages` property isn't used, the callout is populated with the [`name.short`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-name?view=m365-app-1.30) and [`description.short`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-description?view=m365-app-1.30) values.
