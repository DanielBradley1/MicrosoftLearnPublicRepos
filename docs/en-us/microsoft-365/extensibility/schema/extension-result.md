<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-result?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# extensionResult object

Object that defines the type of information that is returned by the function.

Properties that reference this object type:

- [root.extensions.runtimes.customFunctions.functions.result](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-function?view=m365-app-1.30#result-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "dimensionality": "scalar | matrix"
}
```

```json
{
  "type": "object",
  "description": "Object that defines the type of information that is returned by the function.",
  "properties": {
    "dimensionality": {
      "type": "string",
      "enum": [
        "scalar",
        "matrix"
      ],
      "default": "scalar",
      "description": "Must be either scalar (a non-array value) or matrix (a 2-dimensional array). Default: scalar."
    }
  }
}
```

## Properties

#### dimensionality

Must be either scalar \(a non-array value\) or matrix \(a 2-dimensional array\). Default: scalar.

**Type**  
string

**Required**  
—

**Constraints**  


**Supported values**  
Allowed values: `scalar`, `matrix`.
