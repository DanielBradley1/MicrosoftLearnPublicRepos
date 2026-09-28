<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-function?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# extensionFunction object

Array of function object which defines [custom function](https://learn.microsoft.com/en-us/office/dev/add-ins/excel/custom-functions-overview) metadata.

Properties that reference this object type:

- [root.extensions.runtimes.customFunctions.functions](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-custom-functions?view=m365-app-1.30#functions-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "id": "{string}",
  "name": "{string}",
  "description": "{string}",
  "helpUrl": "{string}",
  "parameters": [
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
  ],
  "result": {
    "dimensionality": "scalar | matrix"
  },
  "stream": {boolean},
  "volatile": {boolean},
  "cancelable": {boolean},
  "requiresAddress": {boolean},
  "requiresParameterAddress": {boolean},
  "requiresStreamAddress": {boolean},
  "requiresStreamParameterAddresses": {boolean},
  "capturesCallingObject": {boolean},
  "excludeFromAutoComplete": {boolean},
  "linkedEntityLoadService": {boolean}
}
```

```json
{
  "type": "object",
  "properties": {
    "id": {
      "type": "string",
      "pattern": "^[a-zA-Z][a-zA-Z0-9._]*$",
      "description": "A unique ID for the function.",
      "minLength": 3,
      "maxLength": 64
    },
    "name": {
      "type": "string",
      "pattern": "^[\\p{L}][\\p{L}0-9._]*$",
      "description": "The name of the function that end users see in Excel. In Excel, this function name is prefixed by the custom functions namespace that\u0027s specified in the manifest file.",
      "minLength": 3,
      "maxLength": 64
    },
    "description": {
      "type": "string",
      "description": "The description of the function that end users see in Excel.",
      "minLength": 1,
      "maxLength": 1024
    },
    "helpUrl": {
      "description": "URL that provides information about the function. (It is displayed in a task pane.)",
      "$ref": "#/definitions/secureHttpUrl"
    },
    "parameters": {
      "type": "array",
      "description": "Array that defines the input parameters for the function.",
      "items": {
        "$ref": "#/definitions/extensionFunctionParameter"
      },
      "minItems": 0,
      "maxItems": 128
    },
    "result": {
      "$ref": "#/definitions/extensionResult"
    },
    "stream": {
      "type": "boolean",
      "description": "If true, the function can output repeatedly to the cell even when invoked only once. This option is useful for rapidly-changing data sources, such as a stock price. The function should have no return statement. Instead, the result value is passed as the argument of the StreamingInvocation.setResult callback function.",
      "default": false
    },
    "volatile": {
      "type": "boolean",
      "description": "If true, the function recalculates each time Excel recalculates, instead of only when the formula\u0027s dependent values have changed. A function can\u0027t use both the stream and volatile properties. If the stream and volatile properties are both set to true, the volatile property will be ignored.",
      "default": false
    },
    "cancelable": {
      "type": "boolean",
      "description": "If true, Excel calls the CancelableInvocation handler whenever the user takes an action that has the effect of canceling the function; for example, manually triggering recalculation or editing a cell that is referenced by the function. Cancelable functions are typically only used for asynchronous functions that return a single result and need to handle the cancellation of a request for data. A function can\u0027t use both the stream and cancelable properties.",
      "default": false
    },
    "requiresAddress": {
      "type": "boolean",
      "description": "If true, your custom function can access the address of the cell that invoked it. The address property of the invocation parameter contains the address of the cell that invoked your custom function. A function can\u0027t use both the stream and requiresAddress properties.",
      "default": false
    },
    "requiresParameterAddress": {
      "type": "boolean",
      "description": "If true, your custom function can access the addresses of the function\u0027s input parameters. This property must be used in combination with the dimensionality property of the result object, and dimensionality must be set to matrix.",
      "default": false
    },
    "requiresStreamAddress": {
      "type": "boolean",
      "default": false,
      "description": "If \u0060true\u0060, the function can access the address of the cell calling the streaming function. The \u0060address\u0060 property of the invocation parameter contains the address of the cell that invoked your streaming function. "
    },
    "requiresStreamParameterAddresses": {
      "type": "boolean",
      "description": "If \u0060true\u0060, the function can access the parameter addresses of the cell calling the streaming function. The \u0060parameterAddresses\u0060 property of the invocation parameter contains the parameter addresses for your streaming function.",
      "default": false
    },
    "capturesCallingObject": {
      "type": "boolean",
      "description": "If \u0060true\u0060, the data type being referenced by the custom function is passed as the first argument to the custom function.",
      "default": false
    },
    "excludeFromAutoComplete": {
      "type": "boolean",
      "description": "If \u0060true\u0060, the custom function will not appear in the formula AutoComplete menu in Excel.",
      "default": false
    },
    "linkedEntityLoadService": {
      "type": "boolean",
      "description": "If \u0060true\u0060, it designates that the function is a linked entity load service that returns linked entity cell values for linked entity IDs requested by Excel.",
      "default": false
    }
  },
  "required": [
    "id",
    "name",
    "parameters",
    "result"
  ]
}
```

- [Syntax](#tabpanel_2_syntax)
- [Schema](#tabpanel_2_schema)

```json
{
  "id": "{string}",
  "name": "{string}",
  "description": "{string}",
  "helpUrl": "{string}",
  "parameters": [
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
  ],
  "result": {
    "dimensionality": "scalar | matrix"
  },
  "stream": {boolean},
  "volatile": {boolean},
  "cancelable": {boolean},
  "requiresAddress": {boolean},
  "requiresParameterAddress": {boolean},
  "requiresStreamAddress": {boolean},
  "requiresStreamParameterAddresses": {boolean},
  "capturesCallingObject": {boolean},
  "excludeFromAutoComplete": {boolean},
  "linkedEntityLoadService": {boolean}
}
```

```json
{
  "type": "object",
  "properties": {
    "id": {
      "type": "string",
      "pattern": "^[a-zA-Z][a-zA-Z0-9._]*$",
      "description": "A unique ID for the function.",
      "minLength": 3,
      "maxLength": 64
    },
    "name": {
      "type": "string",
      "pattern": "^[\\p{L}][\\p{L}0-9._]*$",
      "description": "The name of the function that end users see in Excel. In Excel, this function name is prefixed by the custom functions namespace that\u0027s specified in the manifest file.",
      "minLength": 3,
      "maxLength": 64
    },
    "description": {
      "type": "string",
      "description": "The description of the function that end users see in Excel.",
      "minLength": 1,
      "maxLength": 1024
    },
    "helpUrl": {
      "description": "URL that provides information about the function. (It is displayed in a task pane.)",
      "$ref": "#/definitions/secureHttpUrl"
    },
    "parameters": {
      "type": "array",
      "description": "Array that defines the input parameters for the function.",
      "items": {
        "$ref": "#/definitions/extensionFunctionParameter"
      },
      "minItems": 0,
      "maxItems": 128
    },
    "result": {
      "$ref": "#/definitions/extensionResult"
    },
    "stream": {
      "type": "boolean",
      "description": "If true, the function can output repeatedly to the cell even when invoked only once. This option is useful for rapidly-changing data sources, such as a stock price. The function should have no return statement. Instead, the result value is passed as the argument of the StreamingInvocation.setResult callback function.",
      "default": false
    },
    "volatile": {
      "type": "boolean",
      "description": "If true, the function recalculates each time Excel recalculates, instead of only when the formula\u0027s dependent values have changed. A function can\u0027t use both the stream and volatile properties. If the stream and volatile properties are both set to true, the volatile property will be ignored.",
      "default": false
    },
    "cancelable": {
      "type": "boolean",
      "description": "If true, Excel calls the CancelableInvocation handler whenever the user takes an action that has the effect of canceling the function; for example, manually triggering recalculation or editing a cell that is referenced by the function. Cancelable functions are typically only used for asynchronous functions that return a single result and need to handle the cancellation of a request for data. A function can\u0027t use both the stream and cancelable properties.",
      "default": false
    },
    "requiresAddress": {
      "type": "boolean",
      "description": "If true, your custom function can access the address of the cell that invoked it. The address property of the invocation parameter contains the address of the cell that invoked your custom function. A function can\u0027t use both the stream and requiresAddress properties.",
      "default": false
    },
    "requiresParameterAddress": {
      "type": "boolean",
      "description": "If true, your custom function can access the addresses of the function\u0027s input parameters. This property must be used in combination with the dimensionality property of the result object, and dimensionality must be set to matrix.",
      "default": false
    },
    "requiresStreamAddress": {
      "type": "boolean",
      "default": false,
      "description": "If \u0060true\u0060, the function can access the address of the cell calling the streaming function. The \u0060address\u0060 property of the invocation parameter contains the address of the cell that invoked your streaming function. "
    },
    "requiresStreamParameterAddresses": {
      "type": "boolean",
      "description": "If \u0060true\u0060, the function can access the parameter addresses of the cell calling the streaming function. The \u0060parameterAddresses\u0060 property of the invocation parameter contains the parameter addresses for your streaming function.",
      "default": false
    },
    "capturesCallingObject": {
      "type": "boolean",
      "description": "If \u0060true\u0060, the data type being referenced by the custom function is passed as the first argument to the custom function.",
      "default": false
    },
    "excludeFromAutoComplete": {
      "type": "boolean",
      "description": "If \u0060true\u0060, the custom function will not appear in the formula AutoComplete menu in Excel.",
      "default": false
    },
    "linkedEntityLoadService": {
      "type": "boolean",
      "description": "If \u0060true\u0060, it designates that the function is a linked entity load service that returns linked entity cell values for linked entity IDs requested by Excel.",
      "default": false
    }
  },
  "required": [
    "id",
    "name",
    "parameters",
    "result"
  ]
}
```

- [Syntax](#tabpanel_3_syntax)
- [Schema](#tabpanel_3_schema)

```json
{
  "id": "{string}",
  "name": "{string}",
  "description": "{string}",
  "helpUrl": "{string}",
  "parameters": [
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
  ],
  "result": {
    "dimensionality": "scalar | matrix"
  },
  "stream": {boolean},
  "volatile": {boolean},
  "cancelable": {boolean},
  "requiresAddress": {boolean},
  "requiresParameterAddress": {boolean},
  "requiresStreamAddress": {boolean},
  "requiresStreamParameterAddresses": {boolean},
  "capturesCallingObject": {boolean},
  "excludeFromAutoComplete": {boolean},
  "linkedEntityLoadService": {boolean}
}
```

```json
{
  "type": "object",
  "properties": {
    "id": {
      "type": "string",
      "pattern": "^[a-zA-Z][a-zA-Z0-9._]*$",
      "description": "A unique ID for the function.",
      "minLength": 3,
      "maxLength": 64
    },
    "name": {
      "type": "string",
      "pattern": "^[\\p{L}][\\p{L}0-9._]*$",
      "description": "The name of the function that end users see in Excel. In Excel, this function name is prefixed by the custom functions namespace that\u0027s specified in the manifest file.",
      "minLength": 3,
      "maxLength": 64
    },
    "description": {
      "type": "string",
      "description": "The description of the function that end users see in Excel.",
      "minLength": 1,
      "maxLength": 1024
    },
    "helpUrl": {
      "type": "string",
      "format": "uri",
      "description": "URL that provides information about the function. (It is displayed in a task pane.)",
      "minLength": 1,
      "maxLength": 2048
    },
    "parameters": {
      "type": "array",
      "description": "Array that defines the input parameters for the function.",
      "items": {
        "$ref": "#/definitions/extensionFunctionParameter"
      },
      "minItems": 0,
      "maxItems": 128
    },
    "result": {
      "$ref": "#/definitions/extensionResult"
    },
    "stream": {
      "type": "boolean",
      "description": "If true, the function can output repeatedly to the cell even when invoked only once. This option is useful for rapidly-changing data sources, such as a stock price. The function should have no return statement. Instead, the result value is passed as the argument of the StreamingInvocation.setResult callback function.",
      "default": false
    },
    "volatile": {
      "type": "boolean",
      "description": "If true, the function recalculates each time Excel recalculates, instead of only when the formula\u0027s dependent values have changed. A function can\u0027t use both the stream and volatile properties. If the stream and volatile properties are both set to true, the volatile property will be ignored.",
      "default": false
    },
    "cancelable": {
      "type": "boolean",
      "description": "If true, Excel calls the CancelableInvocation handler whenever the user takes an action that has the effect of canceling the function; for example, manually triggering recalculation or editing a cell that is referenced by the function. Cancelable functions are typically only used for asynchronous functions that return a single result and need to handle the cancellation of a request for data. A function can\u0027t use both the stream and cancelable properties.",
      "default": false
    },
    "requiresAddress": {
      "type": "boolean",
      "description": "If true, your custom function can access the address of the cell that invoked it. The address property of the invocation parameter contains the address of the cell that invoked your custom function. A function can\u0027t use both the stream and requiresAddress properties.",
      "default": false
    },
    "requiresParameterAddress": {
      "type": "boolean",
      "description": "If true, your custom function can access the addresses of the function\u0027s input parameters. This property must be used in combination with the dimensionality property of the result object, and dimensionality must be set to matrix.",
      "default": false
    },
    "requiresStreamAddress": {
      "type": "boolean",
      "default": false,
      "description": "If \u0060true\u0060, the function can access the address of the cell calling the streaming function. The \u0060address\u0060 property of the invocation parameter contains the address of the cell that invoked your streaming function. "
    },
    "requiresStreamParameterAddresses": {
      "type": "boolean",
      "description": "If \u0060true\u0060, the function can access the parameter addresses of the cell calling the streaming function. The \u0060parameterAddresses\u0060 property of the invocation parameter contains the parameter addresses for your streaming function.",
      "default": false
    },
    "capturesCallingObject": {
      "type": "boolean",
      "description": "If \u0060true\u0060, the data type being referenced by the custom function is passed as the first argument to the custom function.",
      "default": false
    },
    "excludeFromAutoComplete": {
      "type": "boolean",
      "description": "If \u0060true\u0060, the custom function will not appear in the formula AutoComplete menu in Excel.",
      "default": false
    },
    "linkedEntityLoadService": {
      "type": "boolean",
      "description": "If \u0060true\u0060, it designates that the function is a linked entity load service that returns linked entity cell values for linked entity IDs requested by Excel.",
      "default": false
    }
  },
  "required": [
    "id",
    "name",
    "parameters",
    "result"
  ]
}
```

- [Syntax](#tabpanel_4_syntax)
- [Schema](#tabpanel_4_schema)

```json
{
  "id": "{string}",
  "name": "{string}",
  "description": "{string}",
  "helpUrl": "{string}",
  "parameters": [
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
  ],
  "result": {
    "dimensionality": "scalar | matrix"
  },
  "stream": {boolean},
  "volatile": {boolean},
  "cancelable": {boolean},
  "requiresAddress": {boolean},
  "requiresParameterAddress": {boolean},
  "requiresStreamAddress": {boolean},
  "requiresStreamParameterAddresses": {boolean},
  "capturesCallingObject": {boolean},
  "excludeFromAutoComplete": {boolean},
  "linkedEntityLoadService": {boolean}
}
```

```json
{
  "type": "object",
  "properties": {
    "id": {
      "type": "string",
      "pattern": "^[a-zA-Z][a-zA-Z0-9._]*$",
      "description": "A unique ID for the function.",
      "minLength": 3,
      "maxLength": 64
    },
    "name": {
      "type": "string",
      "pattern": "^[\\p{L}][\\p{L}0-9._]*$",
      "description": "The name of the function that end users see in Excel. In Excel, this function name is prefixed by the custom functions namespace that\u0027s specified in the manifest file.",
      "minLength": 3,
      "maxLength": 64
    },
    "description": {
      "type": "string",
      "description": "The description of the function that end users see in Excel.",
      "minLength": 1,
      "maxLength": 128
    },
    "helpUrl": {
      "type": "string",
      "format": "uri",
      "description": "URL that provides information about the function. (It is displayed in a task pane.)",
      "minLength": 1,
      "maxLength": 2048
    },
    "parameters": {
      "type": "array",
      "description": "Array that defines the input parameters for the function.",
      "items": {
        "$ref": "#/definitions/extensionFunctionParameter"
      },
      "minItems": 0,
      "maxItems": 128
    },
    "result": {
      "$ref": "#/definitions/extensionResult"
    },
    "stream": {
      "type": "boolean",
      "description": "If true, the function can output repeatedly to the cell even when invoked only once. This option is useful for rapidly-changing data sources, such as a stock price. The function should have no return statement. Instead, the result value is passed as the argument of the StreamingInvocation.setResult callback function.",
      "default": false
    },
    "volatile": {
      "type": "boolean",
      "description": "If true, the function recalculates each time Excel recalculates, instead of only when the formula\u0027s dependent values have changed. A function can\u0027t use both the stream and volatile properties. If the stream and volatile properties are both set to true, the volatile property will be ignored.",
      "default": false
    },
    "cancelable": {
      "type": "boolean",
      "description": "If true, Excel calls the CancelableInvocation handler whenever the user takes an action that has the effect of canceling the function; for example, manually triggering recalculation or editing a cell that is referenced by the function. Cancelable functions are typically only used for asynchronous functions that return a single result and need to handle the cancellation of a request for data. A function can\u0027t use both the stream and cancelable properties.",
      "default": false
    },
    "requiresAddress": {
      "type": "boolean",
      "description": "If true, your custom function can access the address of the cell that invoked it. The address property of the invocation parameter contains the address of the cell that invoked your custom function. A function can\u0027t use both the stream and requiresAddress properties.",
      "default": false
    },
    "requiresParameterAddress": {
      "type": "boolean",
      "description": "If true, your custom function can access the addresses of the function\u0027s input parameters. This property must be used in combination with the dimensionality property of the result object, and dimensionality must be set to matrix.",
      "default": false
    },
    "requiresStreamAddress": {
      "type": "boolean",
      "default": false,
      "description": "If \u0060true\u0060, the function can access the address of the cell calling the streaming function. The \u0060address\u0060 property of the invocation parameter contains the address of the cell that invoked your streaming function. "
    },
    "requiresStreamParameterAddresses": {
      "type": "boolean",
      "description": "If \u0060true\u0060, the function can access the parameter addresses of the cell calling the streaming function. The \u0060parameterAddresses\u0060 property of the invocation parameter contains the parameter addresses for your streaming function.",
      "default": false
    },
    "capturesCallingObject": {
      "type": "boolean",
      "description": "If \u0060true\u0060, the data type being referenced by the custom function is passed as the first argument to the custom function.",
      "default": false
    },
    "excludeFromAutoComplete": {
      "type": "boolean",
      "description": "If \u0060true\u0060, the custom function will not appear in the formula AutoComplete menu in Excel.",
      "default": false
    },
    "linkedEntityLoadService": {
      "type": "boolean",
      "description": "If \u0060true\u0060, it designates that the function is a linked entity load service that returns linked entity cell values for linked entity IDs requested by Excel.",
      "default": false
    }
  },
  "required": [
    "id",
    "name",
    "parameters",
    "result"
  ]
}
```

- [Syntax](#tabpanel_5_syntax)
- [Schema](#tabpanel_5_schema)

```json
{
  "id": "{string}",
  "name": "{string}",
  "description": "{string}",
  "helpUrl": "{string}",
  "parameters": [
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
  ],
  "result": {
    "dimensionality": "scalar | matrix"
  },
  "stream": {boolean},
  "volatile": {boolean},
  "cancelable": {boolean},
  "requiresAddress": {boolean},
  "requiresParameterAddress": {boolean},
  "requiresStreamAddress": {boolean},
  "requiresStreamParameterAddresses": {boolean},
  "capturesCallingObject": {boolean},
  "excludeFromAutoComplete": {boolean},
  "linkedEntityLoadService": {boolean}
}
```

```json
{
  "type": "object",
  "properties": {
    "id": {
      "type": "string",
      "description": "A unique ID for the function.",
      "pattern": "^[a-zA-Z][a-zA-Z0-9._]*$",
      "minLength": 3,
      "maxLength": 64
    },
    "name": {
      "type": "string",
      "description": "The name of the function that end users see in Excel. In Excel, this function name is prefixed by the custom functions namespace that\u0027s specified in the manifest file.",
      "pattern": "^[\\p{L}][\\p{L}0-9._]*$",
      "minLength": 3,
      "maxLength": 64
    },
    "description": {
      "type": "string",
      "description": "The description of the function that end users see in Excel.",
      "minLength": 1,
      "maxLength": 128
    },
    "helpUrl": {
      "type": "string",
      "description": "URL that provides information about the function. (It is displayed in a task pane.)",
      "format": "uri",
      "minLength": 1,
      "maxLength": 2048
    },
    "parameters": {
      "type": "array",
      "description": "Array that defines the input parameters for the function.",
      "items": {
        "$ref": "#/definitions/extensionFunctionParameter"
      },
      "minItems": 0,
      "maxItems": 128
    },
    "result": {
      "$ref": "#/definitions/extensionResult"
    },
    "stream": {
      "type": "boolean",
      "description": "If true, the function can output repeatedly to the cell even when invoked only once. This option is useful for rapidly-changing data sources, such as a stock price. The function should have no return statement. Instead, the result value is passed as the argument of the StreamingInvocation.setResult callback function.",
      "default": false
    },
    "volatile": {
      "type": "boolean",
      "description": "If true, the function recalculates each time Excel recalculates, instead of only when the formula\u0027s dependent values have changed. A function can\u0027t use both the stream and volatile properties. If the stream and volatile properties are both set to true, the volatile property will be ignored.",
      "default": false
    },
    "cancelable": {
      "type": "boolean",
      "description": "If true, Excel calls the CancelableInvocation handler whenever the user takes an action that has the effect of canceling the function; for example, manually triggering recalculation or editing a cell that is referenced by the function. Cancelable functions are typically only used for asynchronous functions that return a single result and need to handle the cancellation of a request for data. A function can\u0027t use both the stream and cancelable properties.",
      "default": false
    },
    "requiresAddress": {
      "type": "boolean",
      "description": "If true, your custom function can access the address of the cell that invoked it. The address property of the invocation parameter contains the address of the cell that invoked your custom function. A function can\u0027t use both the stream and requiresAddress properties.",
      "default": false
    },
    "requiresParameterAddress": {
      "type": "boolean",
      "description": "If true, your custom function can access the addresses of the function\u0027s input parameters. This property must be used in combination with the dimensionality property of the result object, and dimensionality must be set to matrix.",
      "default": false
    },
    "requiresStreamAddress": {
      "type": "boolean",
      "default": false,
      "description": "If \u0060true\u0060, the function can access the address of the cell calling the streaming function. The \u0060address\u0060 property of the invocation parameter contains the address of the cell that invoked your streaming function. "
    },
    "requiresStreamParameterAddresses": {
      "type": "boolean",
      "description": "If \u0060true\u0060, the function can access the parameter addresses of the cell calling the streaming function. The \u0060parameterAddresses\u0060 property of the invocation parameter contains the parameter addresses for your streaming function.",
      "default": false
    },
    "capturesCallingObject": {
      "type": "boolean",
      "description": "If \u0060true\u0060, the data type being referenced by the custom function is passed as the first argument to the custom function.",
      "default": false
    },
    "excludeFromAutoComplete": {
      "type": "boolean",
      "description": "If \u0060true\u0060, the custom function will not appear in the formula AutoComplete menu in Excel.",
      "default": false
    },
    "linkedEntityLoadService": {
      "type": "boolean",
      "description": "If \u0060true\u0060, it designates that the function is a linked entity load service that returns linked entity cell values for linked entity IDs requested by Excel.",
      "default": false
    }
  },
  "required": [
    "id",
    "name",
    "parameters",
    "result"
  ]
}
```

- [Syntax](#tabpanel_6_syntax)
- [Schema](#tabpanel_6_schema)

```json
{
  "id": "{string}",
  "name": "{string}",
  "description": "{string}",
  "helpUrl": "{string}",
  "parameters": [
    {
      "name": "{string}",
      "description": "{string}",
      "type": "{string}",
      "cellValueType": "cellvalue | booleancellvalue | doublecellvalue | entitycellvalue | errorcellvalue | formattednumbercellvalue | linkedentitycellvalue | localimagecellvalue | stringcellvalue | webimagecellvalue | ",
      "dimensionality": "scalar | matrix",
      "optional": boolean | null,
      "repeating": {boolean}
    }
  ],
  "result": {
    "dimensionality": "scalar | matrix"
  },
  "stream": {boolean},
  "volatile": {boolean},
  "cancelable": {boolean},
  "requiresAddress": {boolean},
  "requiresParameterAddress": {boolean}
}
```

```json
{
  "type": "object",
  "properties": {
    "id": {
      "type": "string",
      "description": "A unique ID for the function.",
      "pattern": "^[a-zA-Z][a-zA-Z0-9._]*$",
      "minLength": 3,
      "maxLength": 64
    },
    "name": {
      "type": "string",
      "description": "The name of the function that end users see in Excel. In Excel, this function name is prefixed by the custom functions namespace that\u0027s specified in the manifest file.",
      "pattern": "^[\\p{L}][\\p{L}0-9._]*$",
      "minLength": 3,
      "maxLength": 64
    },
    "description": {
      "type": "string",
      "description": "The description of the function that end users see in Excel.",
      "minLength": 1,
      "maxLength": 128
    },
    "helpUrl": {
      "type": "string",
      "description": "URL that provides information about the function. (It is displayed in a task pane.)",
      "format": "uri",
      "minLength": 1,
      "maxLength": 2048
    },
    "parameters": {
      "type": "array",
      "description": "Array that defines the input parameters for the function.",
      "items": {
        "$ref": "#/definitions/extensionFunctionParameter"
      },
      "minItems": 0,
      "maxItems": 128
    },
    "result": {
      "$ref": "#/definitions/extensionResult"
    },
    "stream": {
      "type": "boolean",
      "description": "If true, the function can output repeatedly to the cell even when invoked only once. This option is useful for rapidly-changing data sources, such as a stock price. The function should have no return statement. Instead, the result value is passed as the argument of the StreamingInvocation.setResult callback function.",
      "default": false
    },
    "volatile": {
      "type": "boolean",
      "description": "If true, the function recalculates each time Excel recalculates, instead of only when the formula\u0027s dependent values have changed. A function can\u0027t use both the stream and volatile properties. If the stream and volatile properties are both set to true, the volatile property will be ignored.",
      "default": false
    },
    "cancelable": {
      "type": "boolean",
      "description": "If true, Excel calls the CancelableInvocation handler whenever the user takes an action that has the effect of canceling the function; for example, manually triggering recalculation or editing a cell that is referenced by the function. Cancelable functions are typically only used for asynchronous functions that return a single result and need to handle the cancellation of a request for data. A function can\u0027t use both the stream and cancelable properties.",
      "default": false
    },
    "requiresAddress": {
      "type": "boolean",
      "description": "If true, your custom function can access the address of the cell that invoked it. The address property of the invocation parameter contains the address of the cell that invoked your custom function. A function can\u0027t use both the stream and requiresAddress properties.",
      "default": false
    },
    "requiresParameterAddress": {
      "type": "boolean",
      "description": "If true, your custom function can access the addresses of the function\u0027s input parameters. This property must be used in combination with the dimensionality property of the result object, and dimensionality must be set to matrix.",
      "default": false
    }
  },
  "required": [
    "id",
    "name",
    "parameters",
    "result"
  ]
}
```

## Properties

#### id

A unique ID for the function.

**Type**  
string

**Required**  
✅

**Constraints**  
Minimum string length: 3. Maximum string length: 64.

**Supported values**  
The string value must start with a letter and can contain only letters, numbers, periods, and underscores.

#### name

The name of the function that end users see in Excel. In Excel, this function name is prefixed by the custom functions namespace that's specified in the manifest file.

This property is localizable. For more information, see the [localization schema](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/loc-schema/root?view=m365-app-1.30).

**Type**  
string

**Required**  
✅

**Constraints**  
Minimum string length: 3. Maximum string length: 64.

**Supported values**  
The string value must start with a letter and can contain only letters, numbers, periods, and underscores.

#### description

The description of the function that end users see in Excel.

This property is localizable. For more information, see the [localization schema](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/loc-schema/root?view=m365-app-1.30).

**Type**  
string

**Required**  
—

**Constraints**  
Minimum string length: 1. Maximum string length: 1024.

**Supported values**  


#### description

The description of the function that end users see in Excel.

This property is localizable. For more information, see the [localization schema](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/loc-schema/root?view=m365-app-1.30).

**Type**  
string

**Required**  
—

**Constraints**  
Minimum string length: 1. Maximum string length: 128.

**Supported values**  


#### helpUrl

URL that provides information about the function. \(It is displayed in a task pane.\)

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 2048.

**Supported values**  
The string must start with `https://`.

#### helpUrl

URL that provides information about the function. \(It is displayed in a task pane.\)

**Type**  
string

**Required**  
—

**Constraints**  
Minimum string length: 1. Maximum string length: 2048.

**Supported values**  


#### parameters

Array that defines the input parameters for the function.

**Type**  
Array of [extensionFunctionParameter](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-function-parameter?view=m365-app-1.30)

**Required**  
✅

**Constraints**  
Maximum array items: 128.

**Supported values**  


#### result

**Type**  
[extensionResult](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-result?view=m365-app-1.30)

**Required**  
✅

**Constraints**  


**Supported values**  


#### stream

If true, the function can output repeatedly to the cell even when invoked only once. This option is useful for rapidly-changing data sources, such as a stock price. The function should have no return statement. Instead, the result value is passed as the argument of the StreamingInvocation.setResult callback function.

**Type**  
boolean

**Required**  
—

**Constraints**  


**Supported values**  
Default value: `False`.

#### volatile

If true, the function recalculates each time Excel recalculates, instead of only when the formula's dependent values have changed. A function can't use both the stream and volatile properties. If the stream and volatile properties are both set to true, the volatile property will be ignored.

**Type**  
boolean

**Required**  
—

**Constraints**  


**Supported values**  
Default value: `False`.

#### cancelable

If true, Excel calls the CancelableInvocation handler whenever the user takes an action that has the effect of canceling the function; for example, manually triggering recalculation or editing a cell that is referenced by the function. Cancelable functions are typically only used for asynchronous functions that return a single result and need to handle the cancellation of a request for data. A function can't use both the stream and cancelable properties.

**Type**  
boolean

**Required**  
—

**Constraints**  


**Supported values**  
Default value: `False`.

#### requiresAddress

If true, your custom function can access the address of the cell that invoked it. The address property of the invocation parameter contains the address of the cell that invoked your custom function. A function can't use both the stream and requiresAddress properties.

**Type**  
boolean

**Required**  
—

**Constraints**  


**Supported values**  
Default value: `False`.

#### requiresParameterAddress

If true, your custom function can access the addresses of the function's input parameters. This property must be used in combination with the dimensionality property of the result object, and dimensionality must be set to matrix.

**Type**  
boolean

**Required**  
—

**Constraints**  


**Supported values**  
Default value: `False`.

#### requiresStreamAddress

If `true`, the function can access the address of the cell calling the streaming function. The `address` property of the invocation parameter contains the address of the cell that invoked your streaming function.

**Type**  
boolean

**Required**  
—

**Constraints**  


**Supported values**  
Default value: `False`.

#### requiresStreamParameterAddresses

If `true`, the function can access the parameter addresses of the cell calling the streaming function. The `parameterAddresses` property of the invocation parameter contains the parameter addresses for your streaming function.

**Type**  
boolean

**Required**  
—

**Constraints**  


**Supported values**  
Default value: `False`.

#### capturesCallingObject

If `true`, the data type being referenced by the custom function is passed as the first argument to the custom function.

**Type**  
boolean

**Required**  
—

**Constraints**  


**Supported values**  
Default value: `False`.

#### excludeFromAutoComplete

If `true`, the custom function will not appear in the formula AutoComplete menu in Excel.

**Type**  
boolean

**Required**  
—

**Constraints**  


**Supported values**  
Default value: `False`.

#### linkedEntityLoadService

If `true`, it designates that the function is a linked entity load service that returns linked entity cell values for linked entity IDs requested by Excel.

**Type**  
boolean

**Required**  
—

**Constraints**  


**Supported values**  
Default value: `False`.
