<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-content-runtime-array?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# extensionContentRuntimeArray object

Defines the configuration for embedded content runtimes in Excel or PowerPoint documents. Content runtimes are either a [JavaScript-only runtime](https://learn.microsoft.com/en-us/office/dev/add-ins/testing/runtimes#javascript-only-runtime), which supports features like WebSockets and CORS\(Cross-Origin Resource Sharing\), or a [Browser runtime](https://learn.microsoft.com/en-us/office/dev/add-ins/testing/runtimes#browser-runtime), which includes all JavaScript runtime features plus additional support for local storage and cookies. For more details, see [Runtimes in Office Add-ins](https://learn.microsoft.com/en-us/office/dev/add-ins/testing/runtimes).

Properties that reference this object type:

- [root.extensions.contentRuntimes](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/element-extensions?view=m365-app-1.30#contentRuntimes-property)

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
  "id": "{string}",
  "code": {
    "page": "{string}",
    "script": "{string}"
  },
  "requestedHeight": {number},
  "requestedWidth": {number},
  "disableSnapshot": {boolean}
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
    "id": {
      "type": "string",
      "description": "A unique identifier for this runtime within the app. This is developer specified.",
      "maxLength": 64
    },
    "code": {
      "$ref": "#/definitions/extensionRuntimeCode"
    },
    "requestedHeight": {
      "type": "number",
      "description": "The desired height in pixels for the initial content placeholder. This value MUST be between 32 and 1000 pixels. Default value will be determined by host.",
      "minimum": 32,
      "maximum": 1000
    },
    "requestedWidth": {
      "type": "number",
      "description": "The desired width in pixels for the initial content placeholder. This value MUST be between 32 and 1000 pixels. Default value will be determined by host.",
      "minimum": 32,
      "maximum": 1000
    },
    "disableSnapshot": {
      "type": "boolean",
      "description": "Specifies whether a snapshot image of your content add-in is saved with the host document. Default value is false. Set true to disable.",
      "default": false
    }
  },
  "additionalProperties": false,
  "required": [
    "id",
    "code"
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
  "id": "{string}",
  "code": {
    "page": "{string}",
    "script": "{string}"
  },
  "requestedHeight": {number},
  "requestedWidth": {number},
  "disableSnapshot": {boolean}
}
```

```json
{
  "type": "object",
  "properties": {
    "requirements": {
      "type": "object",
      "$ref": "#/definitions/requirementsExtensionElement",
      "description": "Specifies the Office requirement sets for content add-in runtime. If the user\u0027s Office version doesn\u0027t support the specified requirements, the component will not be available in that client."
    },
    "id": {
      "type": "string",
      "description": "A unique identifier for this runtime within the app. This is developer specified.",
      "maxLength": 64
    },
    "code": {
      "$ref": "#/definitions/extensionRuntimeCode",
      "description": "Specifies the location of code for this runtime. Depending on the runtime.type, add-ins use either a JavaScript file or an HTML page with an embedded \u003Cscript\u003E tag that specifies the URL of a JavaScript file."
    },
    "requestedHeight": {
      "type": "number",
      "description": "The desired height in pixels for the initial content placeholder. This value MUST be between 32 and 1000 pixels. Default value will be determined by host.",
      "minimum": 32,
      "maximum": 1000
    },
    "requestedWidth": {
      "type": "number",
      "description": "The desired width in pixels for the initial content placeholder. This value MUST be between 32 and 1000 pixels. Default value will be determined by host.",
      "minimum": 32,
      "maximum": 1000
    },
    "disableSnapshot": {
      "type": "boolean",
      "description": "Specifies whether a snapshot image of your content add-in is saved with the host document. Default value is false. Set true to disable.",
      "default": false
    }
  },
  "additionalProperties": false,
  "required": [
    "id",
    "code"
  ]
}
```

## Properties

#### requirements

**Type**  
[requirementsExtensionElement](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/requirements-extension-element?view=m365-app-1.30)

**Required**  
—

**Constraints**  


**Supported values**  


#### requirements

Specifies the Office requirement sets for content add-in runtime. If the user's Office version doesn't support the specified requirements, the component will not be available in that client.

**Type**  
[requirementsExtensionElement](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/requirements-extension-element?view=m365-app-1.30)

**Required**  
—

**Constraints**  


**Supported values**  


#### id

A unique identifier for this runtime within the app. This is developer specified.

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 64.

**Supported values**  


#### code

**Type**  
[extensionRuntimeCode](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-runtime-code?view=m365-app-1.30)

**Required**  
✅

**Constraints**  


**Supported values**  


#### code

Specifies the location of code for this runtime. Depending on the runtime.type, add-ins use either a JavaScript file or an HTML page with an embedded <script> tag that specifies the URL of a JavaScript file.

**Type**  
[extensionRuntimeCode](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-runtime-code?view=m365-app-1.30)

**Required**  
✅

**Constraints**  


**Supported values**  


#### requestedHeight

The desired height in pixels for the initial content placeholder. This value MUST be between 32 and 1000 pixels. Default value will be determined by host.

**Type**  
number

**Required**  
—

**Constraints**  
Maximum number value: 1000.

**Supported values**  


#### requestedWidth

The desired width in pixels for the initial content placeholder. This value MUST be between 32 and 1000 pixels. Default value will be determined by host.

**Type**  
number

**Required**  
—

**Constraints**  
Maximum number value: 1000.

**Supported values**  


#### disableSnapshot

Specifies whether a snapshot image of your content add-in is saved with the host document. Default value is false. Set true to disable.

Important

Leaving this property with its default value of false makes an image of the add-in visible for users that open the document in a version of the Office application that doesn't support Office Add-ins, or provides a static image of the add-in if the application can't connect to the server hosting the add-in. However, this also means that potentially sensitive information displayed in the add-in can be accessed directly from the document hosting the add-in.

**Type**  
boolean

**Required**  
—

**Constraints**  


**Supported values**  
Default value: `False`.

## Remarks

Note

An object in the `extensions` array may not have both a `runtimes` and a `contentRuntimes` property.

## Examples

```json
{
 "extensions": [
    {
      "contentRuntimes": [
        {
          "id": "ContentRuntime",
          "code": {
            "page": "https://localhost:3000/content.html"
          },
          "requestedWidth": 100,
          "requestedHeight": 100,
          "disableSnapshot": true,
        }
      ]
    }
  ]
}
```
