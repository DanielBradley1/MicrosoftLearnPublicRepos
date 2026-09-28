<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-function-parameter?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# extensionFunctionParameter object

Array that defines the input parameters for the function.

Properties that reference this object type:

- [root.extensions.runtimes.customFunctions.functions.parameters](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-function?view=m365-app-1.30#parameters-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "name": "{string}",
  "description": "{string}",
  "type": "{string}",
  "cellValueType": "cellvalue | booleancellvalue | doublecellvalue | entitycellvalue | errorcellvalue | linkedentitycellvalue | localimagecellvalue | stringcellvalue | webimagecellvalue | ",
  "dimensionality": "scalar | matrix",
  "optional": boolean | null,
  "repeating": {boolean},
  "customEnumId": "{string}"
}
```

```json
{
  "type": "object",
  "properties": {
    "name": {
      "type": "string",
      "description": "The name of the parameter. This name is displayed in Excel\u0027s IntelliSense.",
      "minLength": 1,
      "maxLength": 64
    },
    "description": {
      "type": "string",
      "description": "A description of the parameter. This is displayed in Excel\u0027s IntelliSense.",
      "minLength": 1,
      "maxLength": 512
    },
    "type": {
      "type": "string",
      "minLength": 1,
      "maxLength": 128,
      "description": "The data type of the parameter. It can only be boolean, number, string, any, CustomFunctions.Invocation, CustomFunctions.StreamingInvocation or CustomFunctions.CancelableInvocation, any allows you to use any of other types.",
      "default": "any"
    },
    "cellValueType": {
      "type": "string",
      "enum": [
        "cellvalue",
        "booleancellvalue",
        "doublecellvalue",
        "entitycellvalue",
        "errorcellvalue",
        "linkedentitycellvalue",
        "localimagecellvalue",
        "stringcellvalue",
        "webimagecellvalue",
        null
      ],
      "description": "A subfield of the type property. Specifies the Excel data types accepted by the custom function. Accepts the values cellvalue, booleancellvalue, doublecellvalue, entitycellvalue, errorcellvalue, linkedentitycellvalue, localimagecellvalue, stringcellvalue, webimagecellvalue"
    },
    "dimensionality": {
      "type": "string",
      "enum": [
        "scalar",
        "matrix"
      ],
      "default": "scalar",
      "description": "Must be either scalar (a non-array value) or matrix (a 2-dimensional array)."
    },
    "optional": {
      "type": [
        "boolean",
        "null"
      ],
      "default": false,
      "description": "If true, the parameter is optional."
    },
    "repeating": {
      "type": "boolean",
      "default": false,
      "description": "If true, parameters populate from a specified array. Note that functions all repeating parameters are considered optional parameters by definition."
    },
    "customEnumId": {
      "type": "string",
      "description": "|The \u0060id\u0060 of the enum in the \u0060enums\u0060 array. This associates the custom enum with the function and enables Excel to display the enum members in the formula AutoComplete menu.",
      "maxLength": 64
    }
  },
  "required": [
    "name"
  ]
}
```

- [Syntax](#tabpanel_2_syntax)
- [Schema](#tabpanel_2_schema)

```json
{
  "name": "{string}",
  "description": "{string}",
  "type": "{string}",
  "cellValueType": "cellvalue | booleancellvalue | doublecellvalue | entitycellvalue | errorcellvalue | linkedentitycellvalue | localimagecellvalue | stringcellvalue | webimagecellvalue | ",
  "dimensionality": "scalar | matrix",
  "customEnumId": "{string}",
  "optional": boolean | null,
  "repeating": {boolean}
}
```

```json
{
  "type": "object",
  "properties": {
    "name": {
      "type": "string",
      "description": "The name of the parameter. This name is displayed in Excel\u0027s IntelliSense.",
      "minLength": 1,
      "maxLength": 64
    },
    "description": {
      "type": "string",
      "description": "A description of the parameter. This is displayed in Excel\u0027s IntelliSense.",
      "minLength": 1,
      "maxLength": 512
    },
    "type": {
      "type": "string",
      "minLength": 1,
      "maxLength": 128,
      "description": "The data type of the parameter. It can only be \u0027boolean\u0027, \u0027number\u0027, \u0027string\u0027, \u0027any\u0027, \u0027CustomFunctions.Invocation\u0027, \u0027CustomFunctions.StreamingInvocation\u0027 or \u0027CustomFunctions.CancelableInvocation\u0027, \u0027any\u0027 allows you to use any of other types.",
      "default": "any"
    },
    "cellValueType": {
      "type": "string",
      "enum": [
        "cellvalue",
        "booleancellvalue",
        "doublecellvalue",
        "entitycellvalue",
        "errorcellvalue",
        "linkedentitycellvalue",
        "localimagecellvalue",
        "stringcellvalue",
        "webimagecellvalue",
        null
      ],
      "description": "A subfield of the type property. Specifies the Excel data types accepted by the custom function. Accepts the values cellvalue, booleancellvalue, doublecellvalue, entitycellvalue, errorcellvalue, linkedentitycellvalue, localimagecellvalue, stringcellvalue, webimagecellvalue"
    },
    "dimensionality": {
      "type": "string",
      "enum": [
        "scalar",
        "matrix"
      ],
      "default": "scalar",
      "description": "Must be either scalar (a non-array value) or matrix (a 2-dimensional array)."
    },
    "customEnumId": {
      "type": "string",
      "maxLength": 64,
      "description": "|The \u0060id\u0060 of the enum in the \u0060enums\u0060 array. This associates the custom enum with the function and enables Excel to display the enum members in the formula AutoComplete menu."
    },
    "optional": {
      "type": [
        "boolean",
        "null"
      ],
      "description": "If true, the parameter is optional."
    },
    "repeating": {
      "type": "boolean",
      "default": false,
      "description": "If true, parameters populate from a specified array. Note that functions all repeating parameters are considered optional parameters by definition."
    }
  },
  "required": [
    "name"
  ]
}
```

- [Syntax](#tabpanel_3_syntax)
- [Schema](#tabpanel_3_schema)

```json
{
  "name": "{string}",
  "description": "{string}",
  "type": "{string}",
  "cellValueType": "cellvalue | booleancellvalue | doublecellvalue | entitycellvalue | errorcellvalue | linkedentitycellvalue | localimagecellvalue | stringcellvalue | webimagecellvalue | ",
  "dimensionality": "scalar | matrix",
  "customEnumId": "{string}",
  "optional": boolean | null,
  "repeating": {boolean}
}
```

```json
{
  "type": "object",
  "properties": {
    "name": {
      "type": "string",
      "description": "The name of the parameter. This name is displayed in Excel\u0027s IntelliSense.",
      "minLength": 1,
      "maxLength": 64
    },
    "description": {
      "type": "string",
      "description": "A description of the parameter. This is displayed in Excel\u0027s IntelliSense.",
      "minLength": 1,
      "maxLength": 128
    },
    "type": {
      "type": "string",
      "minLength": 1,
      "maxLength": 128,
      "description": "The data type of the parameter. It can only be \u0027boolean\u0027, \u0027number\u0027, \u0027string\u0027, \u0027any\u0027, \u0027CustomFunctions.Invocation\u0027, \u0027CustomFunctions.StreamingInvocation\u0027 or \u0027CustomFunctions.CancelableInvocation\u0027, \u0027any\u0027 allows you to use any of other types.",
      "default": "any"
    },
    "cellValueType": {
      "type": "string",
      "enum": [
        "cellvalue",
        "booleancellvalue",
        "doublecellvalue",
        "entitycellvalue",
        "errorcellvalue",
        "linkedentitycellvalue",
        "localimagecellvalue",
        "stringcellvalue",
        "webimagecellvalue",
        null
      ],
      "description": "A subfield of the type property. Specifies the Excel data types accepted by the custom function. Accepts the values cellvalue, booleancellvalue, doublecellvalue, entitycellvalue, errorcellvalue, linkedentitycellvalue, localimagecellvalue, stringcellvalue, webimagecellvalue"
    },
    "dimensionality": {
      "type": "string",
      "enum": [
        "scalar",
        "matrix"
      ],
      "default": "scalar",
      "description": "Must be either scalar (a non-array value) or matrix (a 2-dimensional array)."
    },
    "customEnumId": {
      "type": "string",
      "maxLength": 64,
      "description": "|The \u0060id\u0060 of the enum in the \u0060enums\u0060 array. This associates the custom enum with the function and enables Excel to display the enum members in the formula AutoComplete menu."
    },
    "optional": {
      "type": [
        "boolean",
        "null"
      ],
      "description": "If true, the parameter is optional."
    },
    "repeating": {
      "type": "boolean",
      "default": false,
      "description": "If true, parameters populate from a specified array. Note that functions all repeating parameters are considered optional parameters by definition."
    }
  },
  "required": [
    "name"
  ]
}
```

- [Syntax](#tabpanel_4_syntax)
- [Schema](#tabpanel_4_schema)

```json
{
  "name": "{string}",
  "description": "{string}",
  "type": "{string}",
  "cellValueType": "cellvalue | booleancellvalue | doublecellvalue | entitycellvalue | errorcellvalue | linkedentitycellvalue | localimagecellvalue | stringcellvalue | webimagecellvalue | ",
  "dimensionality": "scalar | matrix",
  "optional": boolean | null,
  "repeating": {boolean},
  "customEnumId": "{string}"
}
```

```json
{
  "type": "object",
  "properties": {
    "name": {
      "type": "string",
      "description": "The name of the parameter. This name is displayed in Excel\u0027s IntelliSense.",
      "minLength": 1,
      "maxLength": 64
    },
    "description": {
      "type": "string",
      "description": "A description of the parameter. This is displayed in Excel\u0027s IntelliSense.",
      "minLength": 1,
      "maxLength": 128
    },
    "type": {
      "type": "string",
      "minLength": 1,
      "maxLength": 128,
      "description": "The data type of the parameter. It can only be \u0027boolean\u0027, \u0027number\u0027, \u0027string\u0027, \u0027any\u0027, \u0027CustomFunctions.Invocation\u0027, \u0027CustomFunctions.StreamingInvocation\u0027 or \u0027CustomFunctions.CancelableInvocation\u0027, \u0027any\u0027 allows you to use any of other types.",
      "default": "any"
    },
    "cellValueType": {
      "type": "string",
      "enum": [
        "cellvalue",
        "booleancellvalue",
        "doublecellvalue",
        "entitycellvalue",
        "errorcellvalue",
        "linkedentitycellvalue",
        "localimagecellvalue",
        "stringcellvalue",
        "webimagecellvalue",
        null
      ],
      "description": "A subfield of the type property. Specifies the Excel data types accepted by the custom function. Accepts the values cellvalue, booleancellvalue, doublecellvalue, entitycellvalue, errorcellvalue, linkedentitycellvalue, localimagecellvalue, stringcellvalue, webimagecellvalue"
    },
    "dimensionality": {
      "type": "string",
      "enum": [
        "scalar",
        "matrix"
      ],
      "default": "scalar",
      "description": "Must be either scalar (a non-array value) or matrix (a 2-dimensional array)."
    },
    "optional": {
      "type": [
        "boolean",
        "null"
      ],
      "description": "If true, the parameter is optional."
    },
    "repeating": {
      "type": "boolean",
      "default": false,
      "description": "If true, parameters populate from a specified array. Note that functions all repeating parameters are considered optional parameters by definition."
    },
    "customEnumId": {
      "type": "string",
      "description": "|The \u0060id\u0060 of the enum in the \u0060enums\u0060 array. This associates the custom enum with the function and enables Excel to display the enum members in the formula AutoComplete menu.",
      "maxLength": 64
    }
  },
  "required": [
    "name"
  ]
}
```

- [Syntax](#tabpanel_5_syntax)
- [Schema](#tabpanel_5_schema)

```json
{
  "name": "{string}",
  "description": "{string}",
  "type": "{string}",
  "cellValueType": "cellvalue | booleancellvalue | doublecellvalue | entitycellvalue | errorcellvalue | formattednumbercellvalue | linkedentitycellvalue | localimagecellvalue | stringcellvalue | webimagecellvalue | ",
  "dimensionality": "scalar | matrix",
  "optional": boolean | null,
  "repeating": {boolean}
}
```

```json
{
  "type": "object",
  "properties": {
    "name": {
      "type": "string",
      "description": "The name of the parameter. This name is displayed in Excel\u0027s IntelliSense.",
      "minLength": 1,
      "maxLength": 64
    },
    "description": {
      "type": "string",
      "description": "A description of the parameter. This is displayed in Excel\u0027s IntelliSense.",
      "minLength": 1,
      "maxLength": 128
    },
    "type": {
      "type": "string",
      "minLength": 1,
      "maxLength": 128,
      "description": "The data type of the parameter. It can only be \u0027boolean\u0027, \u0027number\u0027, \u0027string\u0027, \u0027any\u0027, \u0027CustomFunctions.Invocation\u0027, \u0027CustomFunctions.StreamingInvocation\u0027 or \u0027CustomFunctions.CancelableInvocation\u0027, \u0027any\u0027 allows you to use any of other types.",
      "default": "any"
    },
    "cellValueType": {
      "type": "string",
      "enum": [
        "cellvalue",
        "booleancellvalue",
        "doublecellvalue",
        "entitycellvalue",
        "errorcellvalue",
        "formattednumbercellvalue",
        "linkedentitycellvalue",
        "localimagecellvalue",
        "stringcellvalue",
        "webimagecellvalue",
        null
      ],
      "description": "A subfield of the type property. Specifies the Excel data types accepted by the custom function. Accepts the values \u0027cellvalue\u0027, \u0027booleancellvalue\u0027, \u0027doublecellvalue\u0027, \u0027entitycellvalue\u0027, \u0027errorcellvalue\u0027, \u0027formattednumbercellvalue\u0027, \u0027linkedentitycellvalue\u0027, \u0027localimagecellvalue\u0027, \u0027stringcellvalue\u0027, \u0027webimagecellvalue\u0027"
    },
    "dimensionality": {
      "type": "string",
      "enum": [
        "scalar",
        "matrix"
      ],
      "default": "scalar",
      "description": "Must be either scalar (a non-array value) or matrix (a 2-dimensional array)."
    },
    "optional": {
      "type": [
        "boolean",
        "null"
      ],
      "description": "If true, the parameter is optional."
    },
    "repeating": {
      "type": "boolean",
      "default": false,
      "description": "If true, parameters populate from a specified array. Note that functions all repeating parameters are considered optional parameters by definition."
    }
  },
  "required": [
    "name"
  ]
}
```

## Properties

#### name

The name of the parameter. This name is displayed in Excel's IntelliSense.

This property is localizable. For more information, see the [localization schema](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/loc-schema/root?view=m365-app-1.30).

**Type**  
string

**Required**  
✅

**Constraints**  
Minimum string length: 1. Maximum string length: 64.

**Supported values**  


#### description

A description of the parameter. This is displayed in Excel's IntelliSense.

This property is localizable. For more information, see the [localization schema](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/loc-schema/root?view=m365-app-1.30).

**Type**  
string

**Required**  
—

**Constraints**  
Minimum string length: 1. Maximum string length: 512.

**Supported values**  


#### description

A description of the parameter. This is displayed in Excel's IntelliSense.

This property is localizable. For more information, see the [localization schema](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/loc-schema/root?view=m365-app-1.30).

**Type**  
string

**Required**  
—

**Constraints**  
Minimum string length: 1. Maximum string length: 128.

**Supported values**  


#### type

The data type of the parameter. It can only be boolean, number, string, any, CustomFunctions.Invocation, CustomFunctions.StreamingInvocation or CustomFunctions.CancelableInvocation, any allows you to use any of other types.

**Type**  
string

**Required**  
—

**Constraints**  
Minimum string length: 1. Maximum string length: 128.

**Supported values**  


#### cellValueType

A subfield of the type property. Specifies the Excel data types accepted by the custom function. Accepts the values cellvalue, booleancellvalue, doublecellvalue, entitycellvalue, errorcellvalue, formattednumbercellvalue, linkedentitycellvalue, localimagecellvalue, stringcellvalue, webimagecellvalue

**Type**  
string

**Required**  
—

**Constraints**  


**Supported values**  
Allowed values: `cellvalue`, `booleancellvalue`, `doublecellvalue`, `entitycellvalue`, `errorcellvalue`, `linkedentitycellvalue`, `localimagecellvalue`, `stringcellvalue`, `webimagecellvalue`, ``.

#### cellValueType

A subfield of the type property. Specifies the Excel data types accepted by the custom function. Accepts the values cellvalue, booleancellvalue, doublecellvalue, entitycellvalue, errorcellvalue, formattednumbercellvalue, linkedentitycellvalue, localimagecellvalue, stringcellvalue, webimagecellvalue

**Type**  
string

**Required**  
—

**Constraints**  


**Supported values**  
Allowed values: `cellvalue`, `booleancellvalue`, `doublecellvalue`, `entitycellvalue`, `errorcellvalue`, `formattednumbercellvalue`, `linkedentitycellvalue`, `localimagecellvalue`, `stringcellvalue`, `webimagecellvalue`, ``.

#### dimensionality

Must be either scalar \(a non-array value\) or matrix \(a 2-dimensional array\).

**Type**  
string

**Required**  
—

**Constraints**  


**Supported values**  
Allowed values: `scalar`, `matrix`.

#### optional

If true, the parameter is optional.

**Type**  
boolean \| null

**Required**  
—

**Constraints**  


**Supported values**  


#### repeating

If true, parameters populate from a specified array. Note that functions all repeating parameters are considered optional parameters by definition.

**Type**  
boolean

**Required**  
—

**Constraints**  


**Supported values**  
Default value: `False`.

#### customEnumId

\|The `id` of the enum in the `enums` array. This associates the custom enum with the function and enables Excel to display the enum members in the formula AutoComplete menu.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 64.

**Supported values**
