<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-default-group-capability?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# root.defaultGroupCapability object

When a group install scope is selected, it defines the default capability when the user installs the app. Options are: `team`,`groupchat`, `meetings`.

Properties that reference this object type:

- [root.defaultGroupCapability](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root?view=m365-app-1.30#defaultGroupCapability-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "team": "tab | bot | connector",
  "groupchat": "tab | bot | connector",
  "meetings": "tab | bot | connector"
}
```

```json
{
  "type": "object",
  "properties": {
    "team": {
      "type": "string",
      "enum": [
        "tab",
        "bot",
        "connector"
      ],
      "description": "When the install scope selected is Team, this field specifies the default capability available"
    },
    "groupchat": {
      "type": "string",
      "enum": [
        "tab",
        "bot",
        "connector"
      ],
      "description": "When the install scope selected is GroupChat, this field specifies the default capability available"
    },
    "meetings": {
      "type": "string",
      "enum": [
        "tab",
        "bot",
        "connector"
      ],
      "description": "When the install scope selected is Meetings, this field specifies the default capability available"
    }
  },
  "description": "When a group install scope is selected, this will define the default capability when the user installs the app",
  "additionalProperties": false
}
```

## Properties

#### team

When the install scope selected is `team`, this field specifies the default capability available.

**Type**  
string

**Required**  
—

**Constraints**  


**Supported values**  
Allowed values: `tab`, `bot`, `connector`.

#### groupchat

When the install scope selected is `groupChat`, this field specifies the default capability available.

**Type**  
string

**Required**  
—

**Constraints**  


**Supported values**  
Allowed values: `tab`, `bot`, `connector`.

#### meetings

When the install scope selected is `meetings`, this field specifies the default capability available.

**Type**  
string

**Required**  
—

**Constraints**  


**Supported values**  
Allowed values: `tab`, `bot`, `connector`.

## Examples

```json
{
    "defaultGroupCapability": {
        "meetings": "tab",
        "team": "bot",
        "groupChat": "bot"
    }
}
```
