<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-alternate-versions-array?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# extensionAlternateVersionsArray object

The `extensions.alternates` property is used to hide or prioritize specific in-market add-ins when you've published multiple add-ins with overlapping functionality.

Properties that reference this object type:

- [root.extensions.alternates](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/element-extensions?view=m365-app-1.30#alternates-property)

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
  "prefer": {
    "comAddin": {
      comAddin object
    },
    "xllCustomFunctions": {
      extensionXllCustomFunctions object
    }
  },
  "hide": {
    "storeOfficeAddin": {
      storeOfficeAddin object
    },
    "customOfficeAddin": {
      customOfficeAddin object
    },
    "windowsExtensions": {
      windowsExtensions object
    }
  },
  "alternateIcons": {
    "icon": {
      extensionCommonIcon object
    },
    "highResolutionIcon": {
      extensionCommonIcon object
    }
  }
}
```

```json
{
  "type": "object",
  "properties": {
    "requirements": {
      "$ref": "#/definitions/requirementsExtensionElement"
    },
    "prefer": {
      "type": "object",
      "properties": {
        "comAddin": {
          "type": "object",
          "properties": {
            "progId": {
              "type": "string",
              "description": "Program ID of the alternate com extension. Maximum length is 64 characters.",
              "maxLength": 64
            }
          },
          "additionalProperties": false,
          "required": [
            "progId"
          ]
        },
        "xllCustomFunctions": {
          "$ref": "#/definitions/extensionXllCustomFunctions"
        }
      },
      "minProperties": 1
    },
    "hide": {
      "type": "object",
      "properties": {
        "storeOfficeAddin": {
          "type": "object",
          "properties": {
            "officeAddinId": {
              "type": "string",
              "description": "Solution ID of an in-market add-in to hide. Maximum length is 64 characters.",
              "maxLength": 64
            },
            "assetId": {
              "type": "string",
              "description": "Asset ID of the in-market add-in to hide. Maximum length is 64 characters.",
              "maxLength": 64
            }
          },
          "additionalProperties": false,
          "required": [
            "officeAddinId",
            "assetId"
          ]
        },
        "customOfficeAddin": {
          "type": "object",
          "properties": {
            "officeAddinId": {
              "type": "string",
              "description": "Solution ID of the in-market add-in to hide. Maximum length is 64 characters.",
              "maxLength": 64
            }
          },
          "additionalProperties": false,
          "required": [
            "officeAddinId"
          ]
        },
        "windowsExtensions": {
          "type": "object",
          "description": "Configures how to hide windows native extensions",
          "properties": {
            "effect": {
              "type": "string",
              "description": "Specifies the effect to take while installing the web add-in if the equivalent add-in is installed.",
              "enum": [
                "userOptionToDisable",
                "disableWithNotification"
              ]
            },
            "comAddin": {
              "type": "object",
              "description": "Specifies the equivalent COM or VSTO add-ins",
              "properties": {
                "progIds": {
                  "type": "array",
                  "description": "Specifies the program Ids of the equivalent COM add-ins and the names of equivalent VSTO add-ins",
                  "minItems": 1,
                  "maxItems": 5,
                  "items": {
                    "type": "string",
                    "minLength": 1,
                    "maxLength": 64
                  }
                }
              },
              "additionalProperties": false,
              "required": [
                "progIds"
              ]
            },
            "automationAddin": {
              "type": "object",
              "description": "Specifies the equivalent automation add-ins",
              "properties": {
                "progIds": {
                  "type": "array",
                  "description": "Specifies the program Ids of the equivalent automation add-ins",
                  "minItems": 1,
                  "maxItems": 5,
                  "items": {
                    "type": "string",
                    "minLength": 1,
                    "maxLength": 64
                  }
                }
              },
              "additionalProperties": false,
              "required": [
                "progIds"
              ]
            },
            "xllCustomFunctions": {
              "type": "object",
              "description": "Specifies the XLL-based add-ins custom function",
              "properties": {
                "fileNames": {
                  "type": "array",
                  "description": "Specifies the file names of the XLL-based add-ins custom function",
                  "minItems": 1,
                  "maxItems": 5,
                  "items": {
                    "type": "string",
                    "minLength": 1,
                    "maxLength": 64
                  }
                }
              },
              "additionalProperties": false,
              "required": [
                "fileNames"
              ]
            }
          },
          "additionalProperties": false,
          "anyOf": [
            {
              "required": [
                "effect",
                "comAddin"
              ]
            },
            {
              "required": [
                "effect",
                "automationAddin"
              ]
            },
            {
              "required": [
                "effect",
                "xllCustomFunctions"
              ]
            }
          ]
        }
      },
      "minProperties": 1
    },
    "alternateIcons": {
      "type": "object",
      "additionalProperties": false,
      "properties": {
        "icon": {
          "$ref": "#/definitions/extensionCommonIcon"
        },
        "highResolutionIcon": {
          "$ref": "#/definitions/extensionCommonIcon"
        }
      },
      "required": [
        "icon",
        "highResolutionIcon"
      ]
    }
  },
  "minProperties": 1,
  "additionalProperties": false,
  "required": [
    "alternateIcons"
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
  "prefer": {
    "comAddin": {
      comAddin object
    },
    "xllCustomFunctions": {
      extensionXllCustomFunctions object
    }
  },
  "hide": {
    "storeOfficeAddin": {
      storeOfficeAddin object
    },
    "customOfficeAddin": {
      customOfficeAddin object
    },
    "windowsExtensions": {
      windowsExtensions object
    }
  },
  "alternateIcons": {
    "icon": {
      extensionCommonIcon object
    },
    "highResolutionIcon": {
      extensionCommonIcon object
    }
  }
}
```

```json
{
  "type": "object",
  "properties": {
    "requirements": {
      "$ref": "#/definitions/requirementsExtensionElement"
    },
    "prefer": {
      "type": "object",
      "properties": {
        "comAddin": {
          "type": "object",
          "properties": {
            "progId": {
              "type": "string",
              "description": "Program ID of the alternate com extension. Maximum length is 64 characters.",
              "maxLength": 64
            }
          },
          "additionalProperties": false,
          "required": [
            "progId"
          ]
        },
        "xllCustomFunctions": {
          "$ref": "#/definitions/extensionXllCustomFunctions"
        }
      },
      "minProperties": 1
    },
    "hide": {
      "type": "object",
      "properties": {
        "storeOfficeAddin": {
          "type": "object",
          "properties": {
            "officeAddinId": {
              "type": "string",
              "description": "Solution ID of an in-market add-in to hide. Maximum length is 64 characters.",
              "maxLength": 64
            },
            "assetId": {
              "type": "string",
              "description": "Asset ID of the in-market add-in to hide. Maximum length is 64 characters.",
              "maxLength": 64
            }
          },
          "additionalProperties": false,
          "required": [
            "officeAddinId",
            "assetId"
          ]
        },
        "customOfficeAddin": {
          "type": "object",
          "properties": {
            "officeAddinId": {
              "type": "string",
              "description": "Solution ID of the in-market add-in to hide. Maximum length is 64 characters.",
              "maxLength": 64
            }
          },
          "additionalProperties": false,
          "required": [
            "officeAddinId"
          ]
        },
        "windowsExtensions": {
          "type": "object",
          "description": "Configures how to hide windows native extensions",
          "properties": {
            "effect": {
              "type": "string",
              "description": "Specifies the effect to take while installing the web add-in if the equivalent add-in is installed.",
              "enum": [
                "userOptionToDisable",
                "disableWithNotification"
              ]
            },
            "comAddin": {
              "type": "object",
              "description": "Specifies the equivalent COM add-ins",
              "properties": {
                "progIds": {
                  "type": "array",
                  "description": "Specifies the program Ids of the equivalent COM add-ins",
                  "minItems": 1,
                  "maxItems": 5,
                  "items": {
                    "type": "string",
                    "minLength": 1,
                    "maxLength": 64
                  }
                }
              },
              "additionalProperties": false,
              "required": [
                "progIds"
              ]
            },
            "automationAddin": {
              "type": "object",
              "description": "Specifies the equivalent automation add-ins",
              "properties": {
                "progIds": {
                  "type": "array",
                  "description": "Specifies the program Ids of the equivalent automation add-ins",
                  "minItems": 1,
                  "maxItems": 5,
                  "items": {
                    "type": "string",
                    "minLength": 1,
                    "maxLength": 64
                  }
                }
              },
              "additionalProperties": false,
              "required": [
                "progIds"
              ]
            },
            "xllCustomFunctions": {
              "type": "object",
              "description": "Specifies the XLL-based add-ins custom function",
              "properties": {
                "fileNames": {
                  "type": "array",
                  "description": "Specifies the file names of the XLL-based add-ins custom function",
                  "minItems": 1,
                  "maxItems": 5,
                  "items": {
                    "type": "string",
                    "minLength": 1,
                    "maxLength": 64
                  }
                }
              },
              "additionalProperties": false,
              "required": [
                "fileNames"
              ]
            }
          },
          "additionalProperties": false,
          "anyOf": [
            {
              "required": [
                "effect",
                "comAddin"
              ]
            },
            {
              "required": [
                "effect",
                "automationAddin"
              ]
            },
            {
              "required": [
                "effect",
                "xllCustomFunctions"
              ]
            }
          ]
        }
      },
      "minProperties": 1
    },
    "alternateIcons": {
      "type": "object",
      "additionalProperties": false,
      "properties": {
        "icon": {
          "$ref": "#/definitions/extensionCommonIcon"
        },
        "highResolutionIcon": {
          "$ref": "#/definitions/extensionCommonIcon"
        }
      },
      "required": [
        "icon",
        "highResolutionIcon"
      ]
    }
  },
  "minProperties": 1,
  "additionalProperties": false
}
```

- [Syntax](#tabpanel_3_syntax)
- [Schema](#tabpanel_3_schema)

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
  "prefer": {
    "comAddin": {
      comAddin object
    },
    "xllCustomFunctions": {
      extensionXllCustomFunctions object
    }
  },
  "hide": {
    "storeOfficeAddin": {
      storeOfficeAddin object
    },
    "customOfficeAddin": {
      customOfficeAddin object
    }
  },
  "alternateIcons": {
    "icon": {
      extensionCommonIcon object
    },
    "highResolutionIcon": {
      extensionCommonIcon object
    }
  }
}
```

```json
{
  "type": "object",
  "properties": {
    "requirements": {
      "$ref": "#/definitions/requirementsExtensionElement"
    },
    "prefer": {
      "type": "object",
      "properties": {
        "comAddin": {
          "type": "object",
          "properties": {
            "progId": {
              "type": "string",
              "description": "Program ID of the alternate com extension. Maximum length is 64 characters.",
              "maxLength": 64
            }
          },
          "additionalProperties": false,
          "required": [
            "progId"
          ]
        },
        "xllCustomFunctions": {
          "$ref": "#/definitions/extensionXllCustomFunctions"
        }
      },
      "minProperties": 1
    },
    "hide": {
      "type": "object",
      "properties": {
        "storeOfficeAddin": {
          "type": "object",
          "properties": {
            "officeAddinId": {
              "type": "string",
              "description": "Solution ID of an in-market add-in to hide. Maximum length is 64 characters.",
              "maxLength": 64
            },
            "assetId": {
              "type": "string",
              "description": "Asset ID of the in-market add-in to hide. Maximum length is 64 characters.",
              "maxLength": 64
            }
          },
          "additionalProperties": false,
          "required": [
            "officeAddinId",
            "assetId"
          ]
        },
        "customOfficeAddin": {
          "type": "object",
          "properties": {
            "officeAddinId": {
              "type": "string",
              "description": "Solution ID of the in-market add-in to hide. Maximum length is 64 characters.",
              "maxLength": 64
            }
          },
          "additionalProperties": false,
          "required": [
            "officeAddinId"
          ]
        }
      },
      "minProperties": 1
    },
    "alternateIcons": {
      "type": "object",
      "additionalProperties": false,
      "properties": {
        "icon": {
          "$ref": "#/definitions/extensionCommonIcon"
        },
        "highResolutionIcon": {
          "$ref": "#/definitions/extensionCommonIcon"
        }
      },
      "required": [
        "icon",
        "highResolutionIcon"
      ]
    }
  },
  "minProperties": 1,
  "additionalProperties": false
}
```

- [Syntax](#tabpanel_4_syntax)
- [Schema](#tabpanel_4_schema)

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
  "prefer": {
    "comAddin": {
      comAddin object
    }
  },
  "hide": {
    "storeOfficeAddin": {
      storeOfficeAddin object
    },
    "customOfficeAddin": {
      customOfficeAddin object
    }
  },
  "alternateIcons": {
    "icon": {
      extensionCommonIcon object
    },
    "highResolutionIcon": {
      extensionCommonIcon object
    }
  }
}
```

```json
{
  "type": "object",
  "properties": {
    "requirements": {
      "$ref": "#/definitions/requirementsExtensionElement"
    },
    "prefer": {
      "type": "object",
      "properties": {
        "comAddin": {
          "type": "object",
          "properties": {
            "progId": {
              "type": "string",
              "description": "Program ID of the alternate com extension. Maximum length is 64 characters.",
              "maxLength": 64
            }
          },
          "additionalProperties": false,
          "required": [
            "progId"
          ]
        }
      },
      "minProperties": 1
    },
    "hide": {
      "type": "object",
      "properties": {
        "storeOfficeAddin": {
          "type": "object",
          "properties": {
            "officeAddinId": {
              "type": "string",
              "description": "Solution ID of an in-market add-in to hide. Maximum length is 64 characters.",
              "maxLength": 64
            },
            "assetId": {
              "type": "string",
              "description": "Asset ID of the in-market add-in to hide. Maximum length is 64 characters.",
              "maxLength": 64
            }
          },
          "additionalProperties": false,
          "required": [
            "officeAddinId",
            "assetId"
          ]
        },
        "customOfficeAddin": {
          "type": "object",
          "properties": {
            "officeAddinId": {
              "type": "string",
              "description": "Solution ID of the in-market add-in to hide. Maximum length is 64 characters.",
              "maxLength": 64
            }
          },
          "additionalProperties": false,
          "required": [
            "officeAddinId"
          ]
        }
      },
      "minProperties": 1
    },
    "alternateIcons": {
      "type": "object",
      "additionalProperties": false,
      "properties": {
        "icon": {
          "$ref": "#/definitions/extensionCommonIcon"
        },
        "highResolutionIcon": {
          "$ref": "#/definitions/extensionCommonIcon"
        }
      },
      "required": [
        "icon",
        "highResolutionIcon"
      ]
    }
  },
  "minProperties": 1,
  "additionalProperties": false
}
```

## Properties

#### requirements

Specifies the scopes, formFactors, and Office JavaScript library requirement sets that must be supported on the Office client in order for the `hide`, `prefer`, or `alternateIcons` properties to take effect. For more information, see [Specify Office Add-in requirements in the unified manifest for Microsoft 365](https://learn.microsoft.com/en-us/office/dev/add-ins/develop/requirements-property-unified-manifest).

**Type**  
[requirementsExtensionElement](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/requirements-extension-element?view=m365-app-1.30)

**Required**  
—

**Constraints**  


**Supported values**  


#### prefer

Specifies an equivalent COM add-in or VSTO add-in that should be used in Office on Windows instead of the Office Web Add-in.

**Type**  
[prefer](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-alternate-versions-array-prefer?view=m365-app-1.30)

**Required**  
—

**Constraints**  


**Supported values**  


#### hide

Configures how to hide another add-in that you've published whenever the add-in is installed, so users don't see both in the Microsoft 365 UI. For example, use this property when you've previously published an add-in that uses the old XML app manifest and you're replacing it with a version that uses the new JSON app manifest.

**Type**  
[hide](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-alternate-versions-array-hide?view=m365-app-1.30)

**Required**  
—

**Constraints**  


**Supported values**  


#### alternateIcons

For future use. We are working on a system that will enable Office Add-ins that use the unified manifest for Microsoft 365 to be installable on older or non-subscription Office versions or platforms that do not directly support the unified manifest. That system will use this object to specify the icons that represent the add-in Office Add-in in the add-in insertion UX and the vertical task pane tab bar. For more information, see [Office Add-ins with the unified app manifest for Microsoft 365 - Client and platform support](https://learn.microsoft.com/en-us/office/dev/add-ins/develop/unified-manifest-overview#client-and-platform-support).

**Type**  
[alternateIcons](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-alternate-versions-array-alternate-icons?view=m365-app-1.30)

**Required**  
✅

**Constraints**  


**Supported values**  


#### alternateIcons

For future use. We are working on a system that will make Office Add-ins that use the unified manifest for Microsoft 365 installable on older or non-subscription Office versions or platforms that do not directly support the unified manifest. That system will use this object to specify the icons that represent the add-in Office Add-in in the add-in insertion UX and the vertical task pane tab bar. For more information, see [Office Add-ins with the unified app manifest for Microsoft 365 - Client and platform support](https://learn.microsoft.com/en-us/office/dev/add-ins/develop/unified-manifest-overview#client-and-platform-support).

**Type**  
[alternateIcons](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-alternate-versions-array-alternate-icons?view=m365-app-1.30)

**Required**  
—

**Constraints**  


**Supported values**  


## Examples

```json
{
  "alternates": [
    {
      "requirements": {
        "scopes": [ "mail" ]
      },
      "prefer": {
        "comAddin": {
          "progId": "ContosoExtension"
        }
      },
      "hide": {
        "storeOfficeAddin": {
          "officeAddinId": "00000000-0000-0000-0000-000000000000",
          "assetId": "WA000000000"
        }
      },
      "alternateIcons": {
        "icon": {
          "size": 64,
          "url": "https://contoso.com/assets/icon64x64.jpg"
        },
        "highResolutionIcon": {
          "size": 64,
          "url": "https://contoso.com/assets/icon128x128.jpg"
        }
      }
    }
  ]
}
```

## See also

- [Make your Office Add-in compatible with an existing COM or VSTO add-in](https://learn.microsoft.com/en-us/office/dev/add-ins/develop/make-office-add-in-compatible-with-existing-com-add-in)
