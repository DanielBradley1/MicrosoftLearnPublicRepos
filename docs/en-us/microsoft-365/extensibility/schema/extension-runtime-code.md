<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-runtime-code?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# extensionRuntimeCode object

Specifies the location of code for the runtime. Based on `runtime.type`, add-ins can use either a JavaScript file or an HTML page with an embedded `script` tag that specifies the URL of a JavaScript file. Both URLs are necessary in situations where the `runtime.type` is uncertain.

Properties that reference this object type:

- [root.extensions.contentRuntimes.code](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-content-runtime-array?view=m365-app-1.30#code-property)
- [root.extensions.runtimes.code](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-runtimes-array?view=m365-app-1.30#code-property)

Properties that reference this object type:

- [root.extensions.runtimes.code](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-runtimes-array?view=m365-app-1.30#code-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "page": "{string}",
  "script": "{string}"
}
```

```json
{
  "type": "object",
  "properties": {
    "page": {
      "$ref": "#/definitions/secureHttpUrl",
      "description": "URL of the .html page to be loaded in browser-based runtimes."
    },
    "script": {
      "$ref": "#/definitions/secureHttpUrl",
      "description": "URL of the .js script file to be loaded in UI-less runtimes."
    }
  },
  "additionalProperties": false,
  "required": [
    "page"
  ]
}
```

- [Syntax](#tabpanel_2_syntax)
- [Schema](#tabpanel_2_schema)

```json
{
  "page": "{string}",
  "script": "{string}"
}
```

```json
{
  "type": "object",
  "properties": {
    "page": {
      "$ref": "#/definitions/httpsUrl",
      "description": "URL of the .html page to be loaded in browser-based runtimes."
    },
    "script": {
      "$ref": "#/definitions/httpsUrl",
      "description": "URL of the .js script file to be loaded in UI-less runtimes."
    }
  },
  "additionalProperties": false,
  "required": [
    "page"
  ]
}
```

## Properties

#### page

Specifies the URL of the web page that contains an embedded `script` tag, which specifies the URL of a JavaScript file \(to be loaded in a [browser-based runtime](https://learn.microsoft.com/en-us/office/dev/add-ins/testing/runtimes#browser-runtime)\).

This property is localizable. For more information, see the [localization schema](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/loc-schema/root?view=m365-app-1.30).

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 2048.

**Supported values**  
The string must start with `https://`.

#### page

Specifies the URL of the web page that contains an embedded `script` tag, which specifies the URL of a JavaScript file \(to be loaded in a [browser-based runtime](https://learn.microsoft.com/en-us/office/dev/add-ins/testing/runtimes#browser-runtime)\).

This property is localizable. For more information, see the [localization schema](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/loc-schema/root?view=m365-app-1.30).

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 2048.

**Supported values**  
The string must start with `http://` or `https://`.

#### script

Specifies the URL of the JavaScript file to be loaded in [JavaScript-only runtime](https://learn.microsoft.com/en-us/office/dev/add-ins/testing/runtimes#javascript-only-runtime).

This property is localizable. For more information, see the [localization schema](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/loc-schema/root?view=m365-app-1.30).

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 2048.

**Supported values**  
The string must start with `https://`.

#### script

Specifies the URL of the JavaScript file to be loaded in [JavaScript-only runtime](https://learn.microsoft.com/en-us/office/dev/add-ins/testing/runtimes#javascript-only-runtime).

This property is localizable. For more information, see the [localization schema](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/loc-schema/root?view=m365-app-1.30).

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 2048.

**Supported values**  
The string must start with `http://` or `https://`.

## Remarks

For more information about the use of this property, see [Add-in commands](https://learn.microsoft.com/en-us/office/dev/add-ins/design/add-in-commands), [Event-based add-in activation](https://learn.microsoft.com/en-us/office/dev/add-ins/outlook/autolaunch), and [Copilot agents](https://learn.microsoft.com/en-us/office/dev/add-ins/design/agent-and-add-in-overview).

## Examples

```json
{
    "extensions": [
        {
          "runtimes": [
              "code": {
                "page": "https://contoso.com/events.html",
                "script": "https://contoso.com/events.js"
              }
          ]
        }
    ]
}
```
