<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-custom-functions-namespace?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# extensionCustomFunctionsNamespace object

Defines the namespace for your custom functions. A namespace prepends itself to your custom functions to help customers identify your functions as part of your add-in.

Properties that reference this object type:

- [root.extensions.runtimes.customFunctions.namespace](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-custom-functions?view=m365-app-1.30#namespace-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "id": "{string}",
  "name": "{string}"
}
```

```json
{
  "type": "object",
  "description": "Defines the namespace for your custom functions. A namespace prepends itself to your custom functions to help customers identify your functions as part of your add-in.",
  "properties": {
    "id": {
      "type": "string",
      "description": "Non-localizeable version of the namespace.",
      "pattern": "^[A-Za-z][A-Za-z0-9._]*$",
      "minLength": 1,
      "maxLength": 32
    },
    "name": {
      "type": "string",
      "description": "Localizeable version of the namespace.",
      "pattern": "^[A-Za-z][A-Za-z0-9._]*$",
      "minLength": 1,
      "maxLength": 32
    }
  },
  "required": [
    "id",
    "name"
  ]
}
```

- [Syntax](#tabpanel_2_syntax)
- [Schema](#tabpanel_2_schema)

```json
{
  "id": "{string}",
  "name": "{string}"
}
```

```json
{
  "type": "object",
  "description": "Defines the namespace for your custom functions. A namespace prepends itself to your custom functions to help customers identify your functions as part of your add-in.",
  "properties": {
    "id": {
      "type": "string",
      "pattern": "^[A-Za-z][A-Za-z0-9._]*$",
      "description": "Non-localizable version of the namespace.",
      "minLength": 1,
      "maxLength": 32
    },
    "name": {
      "type": "string",
      "description": "Localizable version of the namespace.",
      "pattern": "^[A-Za-z][A-Za-z0-9._]*$",
      "minLength": 1,
      "maxLength": 32
    }
  },
  "required": [
    "id",
    "name"
  ]
}
```

- [Syntax](#tabpanel_3_syntax)
- [Schema](#tabpanel_3_schema)

```json
{
  "id": "{string}",
  "name": "{string}"
}
```

```json
{
  "type": "object",
  "description": "Defines the namespace for your custom functions. A namespace prepends itself to your custom functions to help customers identify your functions as part of your add-in.",
  "properties": {
    "id": {
      "type": "string",
      "description": "Non-localizable version of the namespace.",
      "pattern": "^[A-Za-z][A-Za-z0-9._]*$",
      "minLength": 1,
      "maxLength": 32
    },
    "name": {
      "type": "string",
      "description": "Localizable version of the namespace.",
      "pattern": "^[A-Za-z][A-Za-z0-9._]*$",
      "minLength": 1,
      "maxLength": 32
    }
  },
  "required": [
    "id",
    "name"
  ]
}
```

## Properties

#### id

Non-localizeable version of the namespace.

**Type**  
string

**Required**  
✅

**Constraints**  
Minimum string length: 1. Maximum string length: 32.

**Supported values**  
The string value must start with a letter and can contain only letters, numbers, periods, and underscores.

#### name

Localizeable version of the namespace.

This property is localizable. For more information, see the [localization schema](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/loc-schema/root?view=m365-app-1.30).

**Type**  
string

**Required**  
✅

**Constraints**  
Minimum string length: 1. Maximum string length: 32.

**Supported values**  
The string value must start with a letter and can contain only letters, numbers, periods, and underscores.
