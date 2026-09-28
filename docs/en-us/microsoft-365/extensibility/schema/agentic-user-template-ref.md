<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/agentic-user-template-ref?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# agenticUserTemplateRef object

An array of agentic user templates references.

Properties that reference this object type:

- [root.agenticUserTemplates](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root?view=m365-app-1.30#agenticUserTemplates-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "id": "{string}",
  "file": "{string}"
}
```

```json
{
  "type": "object",
  "properties": {
    "id": {
      "type": "string",
      "description": "Unique identifier for the agentic user template. Must contain only alphanumeric characters, dots, underscores, and hyphens.",
      "pattern": "^[a-zA-Z0-9._-]\u002B$",
      "minLength": 1,
      "maxLength": 64
    },
    "file": {
      "$ref": "#/definitions/relativePath",
      "description": "Relative file path to this agentic user template element file in the application package."
    }
  },
  "required": [
    "id",
    "file"
  ],
  "additionalProperties": false
}
```

## Properties

#### id

Unique identifier for the agentic user template. Must contain only alphanumeric characters, dots, underscores, and hyphens.

**Type**  
string

**Required**  
✅

**Constraints**  
Minimum string length: 1. Maximum string length: 64.

**Supported values**  
The string must match the following regular expression: `^[a-zA-Z0-9._-]+$`.

#### file

Relative file path to this agentic user template element file in the application package. This file is generated for you when using [Agent 365 CLI](https://learn.microsoft.com/en-us/microsoft-agent-365/developer/reference/cli/setup) or [Developer Portal](https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/build-and-test/manage-your-apps-in-developer-portal#agent-identity-blueprint) to create agent blueprint templates.

The agent is based on the public schema:

```
https://developer.microsoft.com/json-schemas/teams/vDevPreview/MicrosoftTeams.AgenticUser.schema.json
```

And includes the following properties:

| Property | Type | Definition |
| --- | --- | --- |
| `id` | string | Required. Unique identifier for the agentic user template. Must contain only alphanumeric characters, dots, underscores, and hyphens. |
| `schemaVersion` | string | Required. Version of the agentic user template schema. |
| `agentIdentityBlueprintId` | string | Required. Agent Identity Blueprint ID registered in Azure AD portal. The string value must be a [guid](https://en.wikipedia.org/wiki/Universally_unique_identifier) |
| `communicationProtocol` | string | Protocol used for communicating with the agentic user. Default value is `activityProtocol`. See [Understanding the Activity Protocol](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/activity-protocol) in Microsoft 365 Agents SDK documentation to learn more. |

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 2048.

**Supported values**
