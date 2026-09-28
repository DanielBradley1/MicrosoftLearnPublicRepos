<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-elicitation-forms -->
<!-- Sitemap-Last-Modified: 2026-06-16 -->

# Collect structured input with elicitation forms in Copilot Cowork

When an MCP server needs structured input from the user mid-tool-call—a confirmation, a picked option, a few form fields—it can use *elicitation* to pause execution and present a native form. The user fills it out, submits, and tool execution resumes with the data.

Elicitation is part of the *MCP Specification: Elicitation*. Copilot Cowork supports form-mode elicitation, so any compliant MCP server works automatically. Find protocol details such as schema rules, response model, and capability negotiation in the [MCP Specification: Elicitation](https://modelcontextprotocol.io/specification/latest/client/elicitation). For specific details, select a category in the left panel.

## When to use elicitation

Use elicitation when your tool needs to:

- Collect a small set of fields \(name, email, environment selection\)
- Disambiguate between options \("Which of these three \(3\) matching accounts?"\)
- Confirm a destructive action \("Delete all 47 contacts?"\).

  Annotations can be used for up-front confirmation. Elicitations allow for last-minute confirmation. Learn more in [MCP annotation and confirmation management](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-plugin-development#mcp-annotation-and-confirmation-management).

Elicitation is designed for simple, short forms. If your input needs are more complex \(for example, nested data, searchable lists, visual previews\), elicitation might not be the correct fit.

## How elicitation works

During a `tools/call`, your MCP server sends an `elicitation/create` JSON-RPC request. Cowork renders the form, collects the user's response, and returns it so tool execution can continue.

### Server request

The server sends an `elicitation/create` request with a message and a JSON Schema describing the form:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "elicitation/create",
  "params": {
    "message": "Enter the new contact's details.",
    "requestedSchema": {
      "type": "object",
      "properties": {
        "first_name": { "type": "string", "title": "First Name" },
        "last_name": { "type": "string", "title": "Last Name" },
        "email": { "type": "string", "format": "email", "title": "Email Address" },
        "role": { "type": "string", "title": "Role", "enum": ["Engineering", "Sales", "Support"] }
      },
      "required": ["first_name", "last_name", "email"]
    }
  }
}
```

### User response

Cowork returns the user's response as a JSON-RPC result:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "action": "accept",
    "content": {
      "first_name": "Jane",
      "last_name": "Smith",
      "email": "jane.smith@example.com",
      "role": "Engineering"
    }
  }
}
```

The `action` field indicates how the user responded:

| Action | Meaning | `content` present? |
| --- | --- | --- |
| `accept` | User submitted the form | Yes |
| `decline` | User explicitly refused | No |
| `cancel` | User dismissed the form \(Escape, navigated away\) | No |

Cowork auto-cancels pending forms if the user sends a new message, or the session connection drops.

## Schema constraints

Schemas must be *flat objects with primitive properties only*—no nesting, no arrays of objects.

| Supported types | Notes |
| --- | --- |
| `string` | Formats: `email`, `uri`, `date`, `date-time` |
| `number`, `integer` | Numeric input |
| `boolean` | Checkbox / toggle |
| `enum` | Dropdown picker \(`"enum": ["A", "B", "C"]` on a string property\) |

Use `title` and `description` on properties. They become form labels and help text. Learn about the schema rules in the [MCP Specification: Elicitation](https://modelcontextprotocol.io/specification/latest/client/elicitation).

## Capability negotiation

Not all MCP hosts support elicitation yet. Your server should check the client's advertised capabilities before sending an `elicitation/create` request, and provide a conversational fallback when elicitation isn't available. Learn more in [MCP Specification: Capability negotiation](https://modelcontextprotocol.io/seps/2577-deprecate-roots-sampling-and-logging#capability-negotiation).

## Guidelines

- **No secrets in forms.** Never request passwords, API keys, or tokens via elicitation.
- **Keep forms short.** More than five to seven \(5–7\) fields usually means the interaction needs a richer UI.
- **One at a time.** Only one elicitation can be pending per session. Sequential forms work; parallel forms don't.

## Common questions

**Does my connector need special configuration?**

No. Cowork advertises elicitation support during the MCP handshake automatically.

**Is URL-mode elicitation supported?**

Not yet. Cowork supports form mode only.

**Can I customize the form's appearance?**

No. Cowork renders forms using native UI components. You control content \(fields, types, help text\) but not styling.
