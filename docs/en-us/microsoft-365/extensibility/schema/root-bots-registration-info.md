<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-registration-info?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# root.bots.registrationInfo object

System‑generated metadata. This information is maintained by Microsoft services and must not be modified manually.

Properties that reference this object type:

- [root.bots.registrationInfo](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots?view=m365-app-1.30#registrationInfo-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "source": "standard | microsoftCopilotStudio | onedriveSharepoint",
  "environment": "{string}",
  "schemaName": "{string}",
  "clusterCategory": "{string}"
}
```

```json
{
  "description": "System\u2011generated metadata. This information is maintained by Microsoft services and must not be modified manually.",
  "type": "object",
  "properties": {
    "source": {
      "type": "string",
      "enum": [
        "standard",
        "microsoftCopilotStudio",
        "onedriveSharepoint"
      ],
      "description": "The partner source through which the bot is registered. System\u2011generated metadata. This information is maintained by Microsoft services and must not be modified manually."
    },
    "environment": {
      "type": "string",
      "description": "A Power Platform environment that serves as a container for building apps under a Microsoft 365 tenant and can only be accessed by users within that tenant. System\u2011generated metadata. This information is maintained by Microsoft services and must not be modified manually.",
      "maxLength": 128
    },
    "schemaName": {
      "type": "string",
      "description": "The Copilot Studio copilot schema name. System\u2011generated metadata. This information is maintained by Microsoft services and must not be modified manually.",
      "maxLength": 128
    },
    "clusterCategory": {
      "type": "string",
      "description": "The core services cluster category for Copilot Studio copilots. System\u2011generated metadata. This information is maintained by Microsoft services and must not be modified manually.",
      "maxLength": 128
    }
  },
  "required": [
    "source"
  ],
  "additionalProperties": false
}
```

## Properties

#### source

The partner source through which the bot is registered. System‑generated metadata. This information is maintained by Microsoft services and must not be modified manually.

**Type**  
string

**Required**  
✅

**Constraints**  


**Supported values**  
Allowed values: `standard`, `microsoftCopilotStudio`, `onedriveSharepoint`.

#### environment

A Power Platform environment that serves as a container for building apps under a Microsoft 365 tenant and can only be accessed by users within that tenant. System‑generated metadata. This information is maintained by Microsoft services and must not be modified manually.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 128.

**Supported values**  


#### schemaName

The Copilot Studio copilot schema name. System‑generated metadata. This information is maintained by Microsoft services and must not be modified manually.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 128.

**Supported values**  


#### clusterCategory

The core services cluster category for Copilot Studio copilots. System‑generated metadata. This information is maintained by Microsoft services and must not be modified manually.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 128.

**Supported values**
