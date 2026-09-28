<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/declarative-agent-ref?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# declarativeAgentRef object

Declarative agents are customizations of Microsoft 365 Copilot that run on the same orchestrator and foundation models. The agents extend the capabilities of Microsoft 365 Copilot's through domain-specific customizations of knowledge and skills to fit the business needs of your users. The agent's behavior and configuration are defined in a [separate manifest file](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/declarative-agent-manifest) that specifies its capabilities. To learn more, see [Overview of declarative agents](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/overview-declarative-agent).

Properties that reference this object type:

- [root.copilotAgents.declarativeAgents](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-copilot-agents?view=m365-app-1.30#declarativeAgents-property)

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
      "description": "A unique identifier for this declarative agent element."
    },
    "file": {
      "$ref": "#/definitions/relativePath",
      "description": "Relative file path to this declarative agent element file in the application package."
    }
  },
  "description": "A reference to a declarative agent element. The element\u0027s definition is in a separate file.",
  "required": [
    "id",
    "file"
  ],
  "additionalProperties": false
}
```

## Properties

#### id

Unique identifier for the agent. When using Microsoft Copilot Studio to build agents, this is auto-generated. Otherwise, manually assign the value according to your own conventions or preference.

**Type**  
string

**Required**  
✅

**Constraints**  


**Supported values**  


#### file

Relative path within the app package to the [declarative agent manifest](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/declarative-agent-manifest) file.

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 2048.

**Supported values**  


## Examples

```json
{
    "copilotAgents": {
        "declarativeAgents": [
            {
                "id": "agent1",
                "file": "declarativeAgent1.json"
            }
        ]
    }
}
```
