<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-xll-custom-functions?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# extensionXllCustomFunctions object

Represents an [XLL-based add-ins custom function](https://learn.microsoft.com/en-us/office/dev/add-ins/excel/make-custom-functions-compatible-with-xll-udf).

Properties that reference this object type:

- [root.extensions.alternates.prefer.xllCustomFunctions](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-alternate-versions-array-prefer?view=m365-app-1.30#xllCustomFunctions-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "fileName": "{string}"
}
```

```json
{
  "type": "object",
  "properties": {
    "fileName": {
      "type": "string",
      "pattern": "^(?!.*[\\r\\n\\f\\b\\v\\u0007\\t])[\\S]*\\.xll$",
      "minLength": 4,
      "maxLength": 254
    }
  }
}
```

- [Syntax](#tabpanel_2_syntax)
- [Schema](#tabpanel_2_schema)

```json
{
  "fileName": "{string}"
}
```

```json
{
  "type": "object",
  "properties": {
    "fileName": {
      "type": "string",
      "description": "File name for the XLL extension. Maximum length is 254 characters.",
      "pattern": "^(?!.*[\\r\\n\\f\\b\\v\\u0007\\t])[\\S]*\\.xll$",
      "minLength": 4,
      "maxLength": 254
    }
  }
}
```

- [Syntax](#tabpanel_3_syntax)
- [Schema](#tabpanel_3_schema)

```json
{
  "fileName": "{string}"
}
```

```json
{
  "type": "object",
  "properties": {
    "fileName": {
      "type": "string",
      "description": "File name for the XLL extension. Maximum length is 254 characters.",
      "pattern": "^(?!.*[\\r\\n\\f\\b\\v\\a\\t])[\\S]*\\.xll$",
      "minLength": 4,
      "maxLength": 254
    }
  }
}
```

- [Syntax](#tabpanel_4_syntax)
- [Schema](#tabpanel_4_schema)

```json
{
  "fileName": "{string}"
}
```

```json
{
  "type": "object",
  "properties": {
    "fileName": {
      "type": "string",
      "pattern": "^(?!.*[\\r\\n\\f\\b\\v\\a\\t])[\\S]*\\.xll$",
      "minLength": 1,
      "maxLength": 64
    }
  }
}
```

## Properties

#### fileName

Name of Excel add-in file with the file extension *.xll*.

**Type**  
string

**Required**  
—

**Constraints**  
Minimum string length: 4. Maximum string length: 254.

**Supported values**  
The string value must not contain any whitespace characters and must end with `.xll`.

#### fileName

Name of Excel add-in file with the file extension *.xll*.

**Type**  
string

**Required**  
—

**Constraints**  
Minimum string length: 1. Maximum string length: 64.

**Supported values**  
The string value must not contain any whitespace characters and must end with `.xll`.
