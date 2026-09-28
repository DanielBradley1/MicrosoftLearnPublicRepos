<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-connectors?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# root.connectors object

The set of Office365 connectors for this app. The object is an array \(maximum of one element\) with all elements of type `object`. Currently only one connector per app is supported.

Properties that reference this object type:

- [root.connectors](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root?view=m365-app-1.30#connectors-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "connectorId": "{string}",
  "configurationUrl": "{string}",
  "scopes": [
    "team"
  ]
}
```

```json
{
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "connectorId": {
      "type": "string",
      "description": "A unique identifier for the connector which matches its ID in the Connectors Developer Portal.",
      "maxLength": 64
    },
    "configurationUrl": {
      "$ref": "#/definitions/anyHttpUrl",
      "description": "The url to use for configuring the connector using the inline configuration experience."
    },
    "scopes": {
      "type": "array",
      "description": "Specifies whether the connector offers an experience in the context of a channel in a team, or an experience scoped to an individual user alone. Currently, only the team scope is supported.",
      "maxItems": 1,
      "items": {
        "enum": [
          "team"
        ]
      }
    }
  },
  "required": [
    "connectorId",
    "scopes"
  ]
}
```

- [Syntax](#tabpanel_2_syntax)
- [Schema](#tabpanel_2_schema)

```json
{
  "connectorId": "{string}",
  "configurationUrl": "{string}",
  "scopes": [
    "team"
  ]
}
```

```json
{
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "connectorId": {
      "type": "string",
      "description": "A unique identifier for the connector which matches its ID in the Connectors Developer Portal.",
      "maxLength": 64
    },
    "configurationUrl": {
      "$ref": "#/definitions/httpsUrl",
      "description": "The url to use for configuring the connector using the inline configuration experience."
    },
    "scopes": {
      "type": "array",
      "description": "Specifies whether the connector offers an experience in the context of a channel in a team, or an experience scoped to an individual user alone. Currently, only the team scope is supported.",
      "maxItems": 1,
      "items": {
        "enum": [
          "team"
        ]
      }
    }
  },
  "required": [
    "connectorId",
    "scopes"
  ]
}
```

## Properties

#### connectorId

A unique identifier for the Connector that matches its ID in the [Connectors Developer Dashboard](https://aka.ms/connectorsdashboard).

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 64.

**Supported values**  


#### configurationUrl

The https:// URL to use when configuring the connector using the inline configuration experience.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 2048.

**Supported values**  
The string must start with `http://` or `https://`.

#### scopes

Specifies whether the connector offers an experience in the context of a channel in a `team`, or an experience scoped to an individual user alone.

**Type**  
Array of enum

**Required**  
✅

**Constraints**  
Maximum array items: 1.

**Supported values**  
Allowed values: `team`.

## Examples

```json
{
    "connectors": [
        {
            "connectorId": "GUID-FROM-CONNECTOR-DEV-PORTAL%",
            "configurationUrl": "https://contoso.com/teamsconnector/configure",
            "scopes": [
                "team"
            ]
        }
    ]
}
```
