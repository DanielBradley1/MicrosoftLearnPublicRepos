<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-skills?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# root.agentSkills object

An agent skill declaration. References a folder containing a SKILL.md file.

Properties that reference this object type:

- [root.agentSkills](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root?view=m365-app-1.30#agentSkills-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "folder": "{string}"
}
```

```json
{
  "type": "object",
  "description": "An agent skill declaration. References a folder containing a SKILL.md file.",
  "properties": {
    "folder": {
      "type": "string",
      "description": "Path to the folder within the app package that contains the SKILL.md file.",
      "maxLength": 256
    }
  },
  "required": [
    "folder"
  ],
  "additionalProperties": false
}
```

## Properties

#### folder

Path to the folder within the app package that contains the SKILL.md file.

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 256.

**Supported values**
