<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-manifest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-06 -->

# Declarative agent schema 1.0 for Microsoft 365 Copilot

This article describes the 1.0 schema used by the declarative agent manifest. The manifest is a machine-readable document that provides a Large Language Model \(LLM\) with the necessary instructions, knowledge, and actions to specialize in addressing a select set of user problems. Microsoft 365 app manifest references declarative agent manifests inside an [app package](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agents-are-apps#app-package). For details, see the [Microsoft 365 app manifest reference](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/declarative-agent-ref).

Important

The latest version of the declarative agent manifest schema is [version 1.8](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-manifest-1.8). Use the latest schema version for new agents.

Declarative agents are valuable in understanding and generating human-like text, making them versatile for tasks like writing and answering questions. This specification focuses on the declarative agent manifest that acts as a structured framework to specialize and enhance functionalities a specific user needs.

## JSON schema

You can find the schema described in this document in [JSON Schema](https://json-schema.org/) format [here](https://aka.ms/json-schemas/copilot/declarative-agent/v1.0/schema.json).

## Conventions

### Relative references in URLs

Unless specified otherwise, all properties that are URLs can be relative references. Relative references in the manifest document are relative to the location of the manifest document.

### String length

Unless specified otherwise, limit all string properties to 4,000 characters. This string length doesn't set an acceptable size for all string properties in the document. Implementations can set their own practical limits on manifest length.

### Unrecognized properties

JSON objects defined in this document support only the described properties. Unrecognized or extraneous properties in any JSON object make the entire document invalid.

### String localization

Localizable strings can use a localization key instead of a literal value. The syntax is `[[key_name]]`, where `key_name` is the key name in the `localizationKeys` property in your localization files. For details on localization, see [Localize your agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/localize-agents).

## Declarative agent manifest object

The root of the manifest document is a JSON object that covers required fields, capabilities, conversation starters, and actions.

The declarative agent manifest object contains the following properties.

| Property | Type | Description |
| --- | --- | --- |
| `version` | String | Required. The schema version. Set to `v1.0`. |
| `id` | String | Optional. |
| `name` | String | Required. Localizable. The name of the declarative agent. It must contain at least one nonwhitespace character and be 100 characters or less. |
| `description` | String | Required. Localizable. The description of the declarative agent. It must contain at least one nonwhitespace character and be 1,000 characters or less. |
| `instructions` | String | Required. The detailed instructions or guidelines on how the declarative agent should behave, its functions, and any behaviors to avoid. It must contain at least one nonwhitespace character and be 8,000 characters or less. |
| `capabilities` | Array of [Capabilities object](#capabilities-object) | Optional. Contains an array of objects that define capabilities of the declarative agent. The array can't contain more than one of each derived type of [Capabilities object](#capabilities-object). |
| `conversation_starters` | Array of [Conversation starter object](#conversation-starters-object) | Optional. Title and Text are localizable. A list of examples of questions that the declarative agent can answer. The array can't contain more than 12 objects. |
| `actions` | Array of [Action object](#actions-object) | Optional. A list of objects that identify [plugins](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/plugin-manifest-2.4) that provide actions accessible to the declarative agent. |

### Declarative agent manifest object example

The following code shows an example of the required fields in a declarative agent manifest.

- [JSON](#tabpanel_1_json)
- [TypeSpec](#tabpanel_1_tsp)

```json
{
  "name" : "Repairs agent",
  "description": "This declarative agent is meant to help track any tickets and repairs",
  "instructions": "This declarative agent needs to look at my Service Now and Jira tickets/instances to help me keep track of open items"
}
```

```typescript
@agent(
  "Repairs agent",
  "This declarative agent needs to look at my Service Now and Jira tickets/instances to help me keep track of open items"
)
@instructions(
  "This declarative agent needs to look at my Service Now and Jira tickets/instances to help me keep track of open items"
)
namespace MyAgent {

}
```

### Capabilities object

The capabilities object is the base type for objects in the `capabilities` property of the declarative agent manifest object. The possible object types are:

- [Web search object](#web-search-object)
- [OneDrive and SharePoint object](#onedrive-and-sharepoint-object)
- [Copilot connectors object](#copilot-connectors-object)

Note

Users can access declarative agents with any capabilities other than Web search only if their tenants allow metered usage or if they have a Microsoft 365 Copilot license.

#### Capabilities object example

- [JSON](#tabpanel_2_json)
- [TypeSpec](#tabpanel_2_tsp)

```json
{
  "capabilities": [
    {
      "name": "WebSearch"
    },
    {
      "name": "OneDriveAndSharePoint",
      "items_by_sharepoint_ids": [
        {
          "site_id": "bc54a8cc-8c2e-4e62-99cf-660b3594bbfd",
          "web_id": "a5377427-f041-49b5-a2e9-0d58f4343939",
          "list_id": "78A4158C-D2E0-4708-A07D-EE751111E462",
          "unique_id": "304fcfdf-8842-434d-a56f-44a1e54fbed2"
        }
      ],
      "items_by_url": [
        {
          "url": "https://contoso.sharepoint.com/teams/admins/Documents/Folders1"
        }
      ]
    },
    {
      "name": "GraphConnectors",
      "connections": [
        {
          "connection_id": "jiraTickets"
        }
      ]
    }
  ]
}
```

```typescript
namespace MyAgent {
  op webSearch is AgentCapabilities.WebSearch;

  op od_sp is AgentCapabilities.OneDriveAndSharePoint<
    ItemsBySharePointIds = [
      {
        siteId: "bc54a8cc-8c2e-4e62-99cf-660b3594bbfd";
        webId: "a5377427-f041-49b5-a2e9-0d58f4343939";
        listId: "78A4158C-D2E0-4708-A07D-EE751111E462";
        itemId: "304fcfdf-8842-434d-a56f-44a1e54fbed2";
      }
    ],
    ItemsByUrl = [
      {
        url: "https://contoso.sharepoint.com/teams/admins/Documents/Folders1"
      }
    ]
  >;

  op copilotConnectors is AgentCapabilities.CopilotConnectors<Connections = [
    {
        connectionId: "jiraTickets"
    }
  ]>;
}
```

#### Web search object

Indicates that the declarative agent can search the web for grounding information.

The web search object contains the following property.

| Property | Type | Description |
| --- | --- | --- |
| `name` | String | Required. Must be set to `WebSearch`. |

Note

For details about data, privacy, and security for web search in Microsoft 365 Copilot Chat and Microsoft 365 Copilot, see [Data, privacy, and security for web search](https://learn.microsoft.com/en-us/copilot/microsoft-365/manage-public-web-access).

#### OneDrive and SharePoint object

Indicates that the declarative agent can search a user's SharePoint and OneDrive for grounding information.

The OneDrive and SharePoint object contains the following properties.

| Property | Type | Description |
| --- | --- | --- |
| `name` | String | Required. Must be set to `OneDriveAndSharePoint`. |
| `items_by_sharepoint_ids` | Array of [Items by SharePoint IDs object](#items-by-sharepoint-ids-object) | Optional. An array of objects that identify SharePoint or OneDrive sources using IDs. If you omit both the `items_by_sharepoint_ids` and the `items_by_url` properties, the declarative agent can access all OneDrive and SharePoint sources in the organization. |
| `items_by_url` | Array of [Items by URL object](#items-by-url-object) | Optional. An array of objects that identify SharePoint or OneDrive sources by URL. If you omit both the `items_by_sharepoint_ids` and the `items_by_url` properties, the declarative agent can access all OneDrive and SharePoint sources in the organization. |

For information about how to optimize SharePoint content for Copilot, see [Optimize content retrieval](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/optimize-content-retrieval).

##### Items by SharePoint IDs object

The items by SharePoint IDs object contains the following properties.

| Property | Type | Description |
| --- | --- | --- |
| `site_id` | String | Optional. A unique GUID identifier for a SharePoint or OneDrive site. |
| `web_id` | String | Optional. A unique GUID identifier for a specific web within a SharePoint or OneDrive site. |
| `list_id` | String | Optional. A unique GUID identifier for a document library within a SharePoint site. |
| `unique_id` | String | Optional. A unique GUID identifier used to scope a folder or file in the document library specified by the `list_id` property. |

Tip

For information about how to get the unique identifiers for a SharePoint or OneDrive resource, see [Retrieving capabilities IDs for declarative agent manifest](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-capabilities-ids).

##### Items by URL object

The items by URL object contains the following property.

| Property | Type | Description |
| --- | --- | --- |
| `url` | String | Optional. An absolute URL to a SharePoint or OneDrive resource. |

#### Copilot connectors object

Indicates that the declarative agent can search selected Copilot connectors for grounding information.

The Copilot connectors object contains the following properties.

| Property | Type | Description |
| --- | --- | --- |
| `name` | String | Required. Must be set to `GraphConnectors`. |
| `connections` | Array of [Connection object](#connection-object) | Optional. An array of objects that identify the Copilot connectors available to the declarative agent. If you omit this property, the declarative agent can access all Copilot connectors in the organization. |

##### Connection object

Identifies a Copilot connector.

The connection object contains the following property.

| Property | Type | Description |
| --- | --- | --- |
| `connection_id` | String | Required. The unique identifier of the Copilot connector. |

Tip

For instructions on getting the unique identifier for a Copilot connector, see [Retrieving capabilities IDs for declarative agent manifest](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-capabilities-ids).

### Conversation starters object

The conversation starters object is optional in the manifest. It contains hints that the agent displays to the user to show how they can get started with the declarative agent.

The conversation starter object contains the following properties:

| Property | Type | Description |
| --- | --- | --- |
| `text` | String | Required. Localizable. A suggestion that the user can use to get the desired result from the declarative agent. It must contain at least one nonwhitespace character. |
| `title` | String | Optional. Localizable. A unique title for the conversation starter. It must contain at least one nonwhitespace character. |

#### Conversation starters object example

- [JSON](#tabpanel_3_json)
- [TypeSpec](#tabpanel_3_tsp)

```json
{
  "conversation_starters": [
    {
      "title": "My Open Repairs",
      "text": "What open repairs are assigned to me?"
    }
  ]
}
```

```typescript
@conversationStarter(#{
  title: "My Open Repairs",
  text: "What open repairs are assigned to me?"
)}
```

### Actions object

Actions are an optional JSON object in the manifest. They act as developer input and can be considered as plugins.

The action object contains the following properties.

| Property | Type | Description |
| --- | --- | --- |
| `id` | String | Required. A unique identifier for the action. It can be a GUID. |
| `file` | String | Required. A path to the API plugin manifest for this action. |

#### Actions object example

- [JSON](#tabpanel_4_json)
- [TypeSpec](#tabpanel_4_tsp)

```json
{
  "actions": [
    {
      "id": "repairsPlugin",
      "file": "plugin.json"
    }
  ]
}
```

```typescript
@service
@server("https://jsonplaceholder.typicode.com")
@actions(#{
  nameForHuman: "Posts APIs",
  descriptionForHuman: "Manage blog post items on JSON Placeholder APIs.",
  descriptionForModel: "Read, create, update and delete blog post items on the JSON Placeholder APIs."
})
namespace PostsAPI {
  // All operations from the actions
}
```

## Declarative agent manifest example

The following example shows a declarative agent manifest file that uses most of the manifest properties described in this article.

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/copilot/declarative-agent/v1.0/schema.json",
  "version": "v1.0",
  "name": "Microsoft 365 Agents Toolkit declarative copilot",
  "description": "Declarative copilot created with Agents Toolkit",
  "instructions": "You are a repairs expert copilot. With the response from the listRepairs function, you **must** create a poem out of the repairs listed and always include their title and the assigned person. The poem **must** not use the quote markdown and use regular text. If the user is asking to create a new repair, use the createRepair function and do not add poems.",
  "conversation_starters": [
    {
      "title": "Getting Started",
      "text": "How can I get started with Agents Toolkit?"
    },
    {
      "title": "Getting Help",
      "text": "How can I get help with Agents Toolkit?"
    }
  ],
  "actions": [
    {
      "id": "repairsPlugin",
      "file": "repairs-hub-api-plugin.json"
    }
  ],
  "capabilities": [
    {
      "name": "WebSearch"
    },
    {
      "name": "OneDriveAndSharePoint",
      "items_by_url": [
        {
          "url": "https://contoso.sharepoint.com/sites/ProductSupport"
        }
      ]
    },
    {
      "name": "GraphConnectors",
      "connections": [
        {
          "connection_id": "foodStore"
        }
      ]
    }
  ]
}
```

## Related content

- [Write effective instructions for declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-instructions)
- [Microsoft 365 app manifest reference](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema)
