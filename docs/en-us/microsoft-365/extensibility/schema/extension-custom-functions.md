<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-custom-functions?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# extensionCustomFunctions object

[Custom function](https://learn.microsoft.com/en-us/office/dev/add-ins/excel/custom-functions-overview) enable developers to add new functions to Excel by defining those functions in JavaScript as part of an Add-in. Users within Excel can access custom functions just as they would any native function in Excel, such as SUM\(\).

Properties that reference this object type:

- [root.extensions.runtimes.customFunctions](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-runtimes-array?view=m365-app-1.30#customFunctions-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "functions": [
    {
      "id": "{string}",
      "name": "{string}",
      "description": "{string}",
      "helpUrl": "{string}",
      "parameters": [
        {
          extensionFunctionParameter object
        }
      ],
      "result": {
        extensionResult object
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
  ],
  "namespace": {
    "id": "{string}",
    "name": "{string}"
  },
  "allowCustomDataForDataTypeAny": {boolean},
  "metadataUrl": "{string}",
  "enums": [
    {
      "id": "{string}",
      "type": "number | string",
      "values": [
        {
          values object
        }
      ]
    }
  ]
}
```

```json
{
  "type": "object",
  "description": "Custom function enable developers to add new functions to Excel by defining those functions in JavaScript as part of an add-in. Users within Excel can access custom functions just as they would any native function in Excel, such as SUM().",
  "properties": {
    "functions": {
      "description": "Array of function object which defines function metadata.",
      "items": {
        "$ref": "#/definitions/extensionFunction"
      },
      "maxItems": 20000,
      "minItems": 1,
      "type": "array"
    },
    "namespace": {
      "$ref": "#/definitions/extensionCustomFunctionsNamespace"
    },
    "allowCustomDataForDataTypeAny": {
      "type": "boolean",
      "description": "Allows a custom function to accept Excel data types as parameters and return values.",
      "default": false
    },
    "metadataUrl": {
      "$ref": "#/definitions/secureHttpUrl",
      "description": "The full URL of a metadata json file. If \u0060functions\u0060 is not empty, the Office client will install CustomFunctions based on \u0060functions\u0060. Any definitions in \u0060metadataUrl\u0060 will be ignored."
    },
    "enums": {
      "type": "array",
      "description": "Array of custom defined enum objects.",
      "items": {
        "$ref": "#/definitions/enum"
      },
      "maxItems": 20000
    }
  },
  "additionalProperties": false
}
```

- [Syntax](#tabpanel_2_syntax)
- [Schema](#tabpanel_2_schema)

```json
{
  "functions": [
    {
      "id": "{string}",
      "name": "{string}",
      "description": "{string}",
      "helpUrl": "{string}",
      "parameters": [
        {
          extensionFunctionParameter object
        }
      ],
      "result": {
        extensionResult object
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
  ],
  "namespace": {
    "id": "{string}",
    "name": "{string}"
  },
  "allowCustomDataForDataTypeAny": {boolean},
  "metadataUrl": "{string}",
  "enums": [
    {
      "id": "{string}",
      "type": "number | string",
      "values": [
        {
          values object
        }
      ]
    }
  ]
}
```

```json
{
  "type": "object",
  "description": "Custom function enable developers to add new functions to Excel by defining those functions in JavaScript as part of an add-in. Users within Excel can access custom functions just as they would any native function in Excel, such as SUM().",
  "properties": {
    "functions": {
      "description": "Array of function object which defines function metadata.",
      "items": {
        "$ref": "#/definitions/extensionFunction"
      },
      "maxItems": 20000,
      "minItems": 1,
      "type": "array"
    },
    "namespace": {
      "$ref": "#/definitions/extensionCustomFunctionsNamespace"
    },
    "allowCustomDataForDataTypeAny": {
      "type": "boolean",
      "description": "Allows a custom function to accept Excel data types as parameters and return values.",
      "default": false
    },
    "metadataUrl": {
      "$ref": "#/definitions/secureHttpUrl",
      "description": "The full URL of a metadata json file with default locale."
    },
    "enums": {
      "type": "array",
      "items": {
        "$ref": "#/definitions/enum"
      },
      "maxItems": 256
    }
  },
  "additionalProperties": false
}
```

- [Syntax](#tabpanel_3_syntax)
- [Schema](#tabpanel_3_schema)

```json
{
  "functions": [
    {
      "id": "{string}",
      "name": "{string}",
      "description": "{string}",
      "helpUrl": "{string}",
      "parameters": [
        {
          extensionFunctionParameter object
        }
      ],
      "result": {
        extensionResult object
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
  ],
  "namespace": {
    "id": "{string}",
    "name": "{string}"
  },
  "allowCustomDataForDataTypeAny": {boolean},
  "metadataUrl": "{string}",
  "enums": [
    {
      "id": "{string}",
      "type": "number | string",
      "values": [
        {
          values object
        }
      ]
    }
  ]
}
```

```json
{
  "type": "object",
  "description": "Custom function enable developers to add new functions to Excel by defining those functions in JavaScript as part of an add-in. Users within Excel can access custom functions just as they would any native function in Excel, such as SUM().",
  "properties": {
    "functions": {
      "description": "Array of function object which defines function metadata.",
      "items": {
        "$ref": "#/definitions/extensionFunction"
      },
      "maxItems": 20000,
      "minItems": 1,
      "type": "array"
    },
    "namespace": {
      "$ref": "#/definitions/extensionCustomFunctionsNamespace"
    },
    "allowCustomDataForDataTypeAny": {
      "type": "boolean",
      "description": "Allows a custom function to accept Excel data types as parameters and return values.",
      "default": false
    },
    "metadataUrl": {
      "$ref": "#/definitions/httpsUrl",
      "description": "The full URL of a metadata json file with default locale."
    },
    "enums": {
      "type": "array",
      "items": {
        "$ref": "#/definitions/enum"
      },
      "maxItems": 256
    }
  },
  "additionalProperties": false
}
```

- [Syntax](#tabpanel_4_syntax)
- [Schema](#tabpanel_4_schema)

```json
{
  "functions": [
    {
      "id": "{string}",
      "name": "{string}",
      "description": "{string}",
      "helpUrl": "{string}",
      "parameters": [
        {
          extensionFunctionParameter object
        }
      ],
      "result": {
        extensionResult object
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
  ],
  "namespace": {
    "id": "{string}",
    "name": "{string}"
  },
  "allowCustomDataForDataTypeAny": {boolean},
  "metadataUrl": "{string}",
  "enums": [
    {
      "id": "{string}",
      "type": "number | string",
      "values": [
        {
          values object
        }
      ]
    }
  ]
}
```

```json
{
  "type": "object",
  "description": "Custom function enable developers to add new functions to Excel by defining those functions in JavaScript as part of an add-in. Users within Excel can access custom functions just as they would any native function in Excel, such as SUM().",
  "properties": {
    "functions": {
      "description": "Array of function object which defines function metadata.",
      "items": {
        "$ref": "#/definitions/extensionFunction"
      },
      "maxItems": 20000,
      "minItems": 1,
      "type": "array"
    },
    "namespace": {
      "$ref": "#/definitions/extensionCustomFunctionsNamespace"
    },
    "allowCustomDataForDataTypeAny": {
      "type": "boolean",
      "description": "Allows a custom function to accept Excel data types as parameters and return values.",
      "default": false
    },
    "metadataUrl": {
      "$ref": "#/definitions/httpsUrl",
      "description": "The full URL of a metadata json file with default locale."
    },
    "enums": {
      "type": "array",
      "description": "Array of custom defined enum objects.",
      "items": {
        "$ref": "#/definitions/enum"
      },
      "maxItems": 20000
    }
  },
  "additionalProperties": false
}
```

- [Syntax](#tabpanel_5_syntax)
- [Schema](#tabpanel_5_schema)

```json
{
  "functions": [
    {
      "id": "{string}",
      "name": "{string}",
      "description": "{string}",
      "helpUrl": "{string}",
      "parameters": [
        {
          extensionFunctionParameter object
        }
      ],
      "result": {
        extensionResult object
      },
      "stream": {boolean},
      "volatile": {boolean},
      "cancelable": {boolean},
      "requiresAddress": {boolean},
      "requiresParameterAddress": {boolean}
    }
  ],
  "namespace": {
    "id": "{string}",
    "name": "{string}"
  },
  "allowCustomDataForDataTypeAny": {boolean},
  "metadataUrl": "{string}"
}
```

```json
{
  "type": "object",
  "description": "Custom function enable developers to add new functions to Excel by defining those functions in JavaScript as part of an add-in. Users within Excel can access custom functions just as they would any native function in Excel, such as SUM().",
  "properties": {
    "functions": {
      "description": "Array of function object which defines function metadata.",
      "items": {
        "$ref": "#/definitions/extensionFunction"
      },
      "maxItems": 20000,
      "minItems": 1,
      "type": "array"
    },
    "namespace": {
      "$ref": "#/definitions/extensionCustomFunctionsNamespace"
    },
    "allowCustomDataForDataTypeAny": {
      "type": "boolean",
      "description": "Allows a custom function to accept Excel data types as parameters and return values.",
      "default": false
    },
    "metadataUrl": {
      "$ref": "#/definitions/httpsUrl",
      "description": "The full URL of a metadata json file with default locale."
    }
  },
  "additionalProperties": false
}
```

- [Syntax](#tabpanel_6_syntax)
- [Schema](#tabpanel_6_schema)

```json
{
  "functions": [
    {
      "id": "{string}",
      "name": "{string}",
      "description": "{string}",
      "helpUrl": "{string}",
      "parameters": [
        {
          extensionFunctionParameter object
        }
      ],
      "result": {
        extensionResult object
      },
      "stream": {boolean},
      "volatile": {boolean},
      "cancelable": {boolean},
      "requiresAddress": {boolean},
      "requiresParameterAddress": {boolean}
    }
  ],
  "namespace": {
    "id": "{string}",
    "name": "{string}"
  },
  "allowCustomDataForDataTypeAny": {boolean}
}
```

```json
{
  "type": "object",
  "description": "Custom function enable developers to add new functions to Excel by defining those functions in JavaScript as part of an add-in. Users within Excel can access custom functions just as they would any native function in Excel, such as SUM().",
  "properties": {
    "functions": {
      "description": "Array of function object which defines function metadata.",
      "items": {
        "$ref": "#/definitions/extensionFunction"
      },
      "maxItems": 20000,
      "minItems": 1,
      "type": "array"
    },
    "namespace": {
      "$ref": "#/definitions/extensionCustomFunctionsNamespace"
    },
    "allowCustomDataForDataTypeAny": {
      "type": "boolean",
      "description": "Allows a custom function to accept Excel data types as parameters and return values.",
      "default": false
    }
  },
  "required": [
    "functions",
    "namespace"
  ]
}
```

## Properties

#### functions

Array of function object which defines function metadata.

**Type**  
Array of [extensionFunction](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-function?view=m365-app-1.30)

**Required**  
—

**Constraints**  
Minimum array items: 1. Maximum array items: 20000.

**Supported values**  


#### functions

Array of function object which defines function metadata.

**Type**  
Array of [extensionFunction](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-function?view=m365-app-1.30)

**Required**  
✅

**Constraints**  
Minimum array items: 1. Maximum array items: 20000.

**Supported values**  


#### namespace

A unique identifier for your custom functions.

**Type**  
[extensionCustomFunctionsNamespace](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-custom-functions-namespace?view=m365-app-1.30)

**Required**  
—

**Constraints**  


**Supported values**  


#### namespace

**Type**  
[extensionCustomFunctionsNamespace](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-custom-functions-namespace?view=m365-app-1.30)

**Required**  
✅

**Constraints**  


**Supported values**  


#### allowCustomDataForDataTypeAny

Allows a custom function to accept Excel data types as parameters and return values.

**Type**  
boolean

**Required**  
—

**Constraints**  


**Supported values**  
Default value: `False`.

#### metadataUrl

The full URL of a metadata json file with default locale.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 2048.

**Supported values**  
The string must start with `https://`.

#### metadataUrl

The full URL of a metadata json file with default locale.

This property is localizable. For more information, see the [localization schema](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/loc-schema/root?view=m365-app-1.30).

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 2048.

**Supported values**  
The string must start with `https://`.

#### metadataUrl

The full URL of a metadata json file with default locale.

This property is localizable. For more information, see the [localization schema](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/loc-schema/root?view=m365-app-1.30).

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 2048.

**Supported values**  
The string must start with `http://` or `https://`.

#### enums

**Type**  
Array of [enum](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/enum?view=m365-app-1.30)

**Required**  
—

**Constraints**  
Maximum array items: 256.

**Supported values**  


#### enums

Array of custom defined enum objects.

**Type**  
Array of [enum](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/enum?view=m365-app-1.30)

**Required**  
—

**Constraints**  
Maximum array items: 256.

**Supported values**  


#### enums

Array of custom defined enum objects.

**Type**  
Array of [enum](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/enum?view=m365-app-1.30)

**Required**  
—

**Constraints**  
Maximum array items: 20000.

**Supported values**
