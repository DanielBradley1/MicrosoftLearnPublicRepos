<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/mcp-apps-support -->
<!-- Sitemap-Last-Modified: 2026-09-10 -->

# MCP apps plugin author guide for Cowork

Cowork can render *interactive UI widgets* delivered by your MCP server, following the [MCP Apps Extension \(SEP-1865\)](https://github.com/modelcontextprotocol/ext-apps/blob/main/specification/2026-01-26/apps.mdx).

A widget is an HTML/JS view that Cowork renders inline in the conversation inside a sandboxed iframe, and wires up to your server so it can show data, take input, and call your tools back.

This article describes what Cowork supports, what parts of the protocol it does and doesn't implement, and the contract and limits your server must respect. It's intended for authors of MCP servers, including those published through the marketplace and built-in connectors. It doesn't assume any particular SDK—if you use the official `@modelcontextprotocol/ext-apps` server/client helpers, everything below still applies because those helpers emit the same wire protocol.

Note

If you're new to building widgets, the official Apps SDK and the SEP-1865 spec are the right starting points. This article focuses specifically on Cowork's behavior.

Note

This article covers interactive UI widgets. To let a tool accept a file from the user's workspace as input, you don't need a widget—declare the tool parameter with `contentEncoding: base64`. Learn more in [Accept files from the Cowork workspace](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-plugin-development#accept-files-from-the-cowork-workspace).

## How widget rendering works in Cowork

Cowork follows the spec's *template/data separation* model. A widget is delivered in three steps:

1. **You declare a UI resource on the tool**: In your `tools/list` definition, a widget-enabled tool carries `_meta.ui.resourceUri` pointing at a `ui://` resource. The tool handler itself returns ordinary data \(text or `structuredContent`\)—*not* HTML.
2. **Cowork detects the widget after the tool runs**: When that tool completes a `tools/call`, Cowork knows \(from the declaration in the previous step\) that the result has an associated UI resource, and mounts a widget for that tool invocation. The tool's result data is delivered alongside so the widget can render immediately.
3. **Cowork fetches the HTML and renders it**: Cowork requests the HTML template from your server via `resources/read` for the declared `ui://` URI, then renders the returned HTML in a sandboxed iframe.

This process means two registrations per widget-enabled tool, exactly as in the spec: the tool \(returns data, declares the URI\), and the resource \(serves the HTML\).

```
  Agent calls your tool ──► tools/call ──► your MCP server
                                             returns DATA (+ tool declared ui://…)
  Cowork mounts widget  ◄── notify + data
  Cowork fetches HTML   ──► resources/read(ui://…) ──► your MCP server
                                             returns HTML (text/html;profile=mcp-app)
  Cowork renders iframe ◄── HTML
```

### Declare a widget tool

The tool definition must include `_meta.ui.resourceUri` \(SEP-1865 [§Resource Discovery](https://github.com/modelcontextprotocol/ext-apps/blob/main/specification/2026-01-26/apps.mdx#resource-discovery)\):

```jsonc
// tools/list — tool definition
{
  "name": "show_claims_dashboard",
  "description": "Open an interactive claims dashboard.",
  "inputSchema": { /* … */ },
  "_meta": {
    "ui": { "resourceUri": "ui://your-app/claims-dashboard.html" }
  }
}
```

Requirements Cowork enforces on the declared URI:

- It *must* use the `ui://` scheme. Other schemes are ignored \(no widget is rendered\).
- It must be at most 1024 characters.

### Serve the HTML resource

When Cowork issues `resources/read` for the `ui://` URI, your server must return the HTML with the MCP Apps mime type:

```jsonc
// resources/read response
{
  "contents": [
    {
      "uri": "ui://your-app/claims-dashboard.html",
      "mimeType": "text/html;profile=mcp-app",
      "text": "<!doctype html> … </html>"
    }
  ]
}
```

SEP-1865 [§UI Resource Format](https://github.com/modelcontextprotocol/ext-apps/blob/main/specification/2026-01-26/apps.mdx#ui-resource-format) defines this mime type and allows the body as base64 `blob` instead of `text`.

There are two caveats about Cowork:

- **Cowork reads only the `text` field**: A base64 `blob` body isn't decoded. Serve your HTML as `text`.
- **The mime type matters**: Always set `text/html;profile=mcp-app`.

Treat your HTML as self-contained: inline your scripts and styles, and embed assets as `data:` URLs where practical. Cowork doesn't host, transform, or supply your assets. For anything your widget needs from the network at runtime, declare the origins in `_meta.ui.csp` \(learn more in [Content Security Policy](#content-security-policy)\), or route the request through a widget `tools/call` to your server—the better choice when the request needs credentials or tokens, which then stay server-side.

## Honored `_meta.ui` fields

`_meta.ui` appears in two places—on the tool and on the UI resource—and Cowork reads a specific set of fields from each place, listed in the following sections. Other fields are ignored.

### On the tool \(`tools/list` definition\)

| Field | Type | Effect in Cowork |
| --- | --- | --- |
| `resourceUri` | string \(`ui://…`\) | Required for a widget. Identifies the HTML resource Cowork fetches via `resources/read`. |
| `visibility` | array of `"model"` / `"app"` | Controls whether the tool is exposed to the agent and/or callable from a widget. More information: [Tool visibility](#tool-visibility) |

### On the UI resource \(`resources/read` response - `contents[]._meta.ui`\)

| Field | Type | Effect in Cowork |
| --- | --- | --- |
| `csp` | object | Content security policy domain declarations for the widget. More information: [Content Security Policy](#content-security-policy) |
| `permissions` | object \(feature name → options map\) | Browser feature permissions your widget requests, from a fixed allow list. More information: [Iframe permissions](#iframe-permissions) |

Note

- Declare `csp` and `permissions` on the **UI resource's** `_meta.ui` \(the `resources/read` response\), where the spec defines them.
- `_meta.ui.domain` is parsed \(maximum 256 characters\) and, for a marketplace package, must be covered by your `validDomains[]` like any other declared domain.

### Tool visibility

`_meta.ui.visibility` \(SEP-1865 [§Resource Discovery → Visibility](https://github.com/modelcontextprotocol/ext-apps/blob/main/specification/2026-01-26/apps.mdx#resource-discovery)\) declares who can invoke a tool:

- `"model"`: The agent \(LLM\) can call the tool.
- `"app"`: A rendered widget can call the tool \(via widget callbacks, described later\).

Cowork's behavior:

- If you omit `visibility`, the tool defaults to both `model` and `app`—the agent can call it and widgets can call it.
- If you include `visibility` but it doesn't include `"model"`, Cowork hides the tool from the agent's tool list \(per the spec's RFC 2119 MUST\). App-only tools are still callable from your widget.
- If you include `visibility` but it contains no recognized values \(empty, or only unknown strings\), Cowork treats it as fail-closed: the tool is hidden from the agent.

This behavior lets you ship "app-only" tools \(for example, a `refresh_data` tool that the widget calls on a button selection\) that the agent never sees, while keeping data tools visible to the agent.

### Content security policy

SEP-1865's [`McpUiResourceCsp`](https://github.com/modelcontextprotocol/ext-apps/blob/main/specification/2026-01-26/apps.mdx#ui-resource-format) defines four keys \(`connectDomains`, `resourceDomains`, `frameDomains`, `baseUriDomains`\). Cowork validates your declared `_meta.ui.csp` domains, filters them against your package's `validDomains[]` \(see the important note that follows\), and builds the widget iframe's CSP from the result. `baseUriDomains` isn't applied:

| Key | Status | Behavior |
| --- | --- | --- |
| `connectDomains` | ✅ honored | Origins your widget can make outbound connections to. Declare this key whenever you declare any CSP—it's what anchors policy building. |
| `resourceDomains` | ✅ honored | Origins your widget can load resources from \(images, styles, media\). Takes effect only when `connectDomains` is also declared. |
| `frameDomains` | ✅ honored | Origins the widget can embed as nested iframes \(maps to CSP `frame-src`\). |
| `baseUriDomains` | ⚠️ not honored | Never applied. |

How Cowork builds the policy:

- Entries must be `https://` \(or `wss://`\) origins, with at most one leading `*.` wildcard label. Malformed entries are dropped.
- At most 16 origins per directive are applied.

Important

`validDomains` gates your declared domains. For a server published through a marketplace package, every domain you declare in `csp.connectDomains`, `csp.resourceDomains`, or `_meta.ui.domain` must also be listed in your package manifest's `validDomains[]`. The check is strictly per-package and fail-closed: declared entries that aren't authorized by `validDomains` are stripped before they reach the rendering layer, and a package that declares no `validDomains` at all has *every* declared domain stripped. When domains are stripped, the user sees a "widget network blocked" warning card that names your app—an empty `validDomains` doesn't just degrade the widget, it visibly blames it. List every domain your widget declares.

### Iframe permissions

The `_meta.ui.permissions` property \([§UI Resource Format](https://github.com/modelcontextprotocol/ext-apps/blob/main/specification/2026-01-26/apps.mdx#ui-resource-format)\) lets a widget request browser feature access. Declare it as an **object map** keyed by feature name, with empty objects as values—*not* an array of strings. An array is silently ignored and grants nothing:

```jsonc
"_meta": {
  "ui": {
    "permissions": {
      "camera": {},
      "clipboardWrite": {}
    }
  }
}
```

Cowork honors only a fixed allow list of features, using the SEP-1865 spellings:

- `camera`
- `microphone`
- `geolocation`
- `clipboardWrite`

These map to W3C Permissions-Policy features applied via the inner iframe's `allow="…"` attribute—they aren't iframe `sandbox` tokens.

## Widget-to-server communication

After rendering a widget, it can call back through Cowork to your MCP server. Cowork proxies a *bounded set* of JSON-RPC methods from the widget to the originating server:

| Method | Behavior | Purpose |
| --- | --- | --- |
| `resources/read` | ✅ forwarded to your server | Fetch the widget's HTML template \(Cowork does this to mount the widget\) and any additional resources. |
| `tools/call` | ✅ forwarded to your server | The widget invokes a tool on your server - for example, refresh data on a user action. |
| `ui/message` | ✅ to the conversation \(not your server\) | Cowork injects the message as a **user turn into the conversation \(to the agent\)**. Use it to drive the conversation, not to call your server. |

Any other method—including `initialize`, `tools/list`, `sampling/*`, `elicitation/*`, and `notifications/*`—isn't forwarded and is rejected. This approach provides a least-authority boundary: a widget can't enumerate tools, re-initialize the connection, or drive sampling and elicitation from inside the iframe.

Note

`ui/message` goes to the agent, not your server. Only `resources/read` and `tools/call` reach your MCP server. If a widget button should hand work back to your server, use `tools/call`. If it should say something to the agent on the user's behalf, use `ui/message`.

For `tools/call` from a widget, Cowork additionally enforces visibility at call time: if the target tool's declared `visibility` excludes `"app"`, the call is refused. \(A tool with no `visibility` declaration is allowed, matching the default.\)

To protect your server and the user's session, Cowork rate-limits widget-initiated calls to 60 requests per minute per conversation.

### Display mode

A widget can request a display-mode change at runtime through `ui/request-display-mode` \([§Display Modes](https://github.com/modelcontextprotocol/ext-apps/blob/main/specification/2026-01-26/apps.mdx#display-modes)\): Cowork supports switching between **`inline`** and **`fullscreen`**. `pip` \(picture-in-picture\) isn't available and such a request is rejected. Design your widget to work in both inline and fullscreen modes. Don't depend on `pip`.

### Widget sizing

Cowork honors the spec's `ui/notifications/size-changed`: as your widget reports its rendered size, Cowork resizes the inline frame to match, clamped to a width between 200 and 720 pixels and a height of up to 640 pixels \(resize reports are debounced\). Design your inline layout for those bounds, and use fullscreen mode for larger surfaces.

### Opening links

A widget can ask Cowork to open an external URL through `ui/open-link` \([§Requests \(View → Host\)](https://github.com/modelcontextprotocol/ext-apps/blob/main/specification/2026-01-26/apps.mdx#requests-view--host)\). Cowork supports it with two guardrails: only `https://` URLs are accepted, and the user sees a confirmation dialog before the link opens. Design for the user declining—don't make navigation the only way to complete a flow.

### Host context

At initialization, Cowork pushes host context to your widget—theme, locale, time zone, text direction, and style variables—and sends updates through `ui/notifications/host-context-changed`. Read it instead of hardcoding: it's how your widget matches Cowork's theme and locale.

## Tool result delivery to the widget

When a widget-enabled tool finishes, Cowork sends that tool's full result to the widget—the `content`, `structuredContent`, and `_meta` of the `CallToolResult`—through the spec's `ui/notifications/tool-result` \([§Notifications \(Host → View\)](https://github.com/modelcontextprotocol/ext-apps/blob/main/specification/2026-01-26/apps.mdx#notifications-host--view)\). By using the official Apps SDK, your widget's tool-result handler \(such as `app.ontoolresult`\) receives this data.

Before the result, Cowork also sends the tool's *arguments* to the widget through the spec's `ui/notifications/tool-input`. Partial argument streaming \(`tool-input-partial`\) isn't delivered—the widget receives the full arguments once.

Constraints:

- The inlined result is limited to 64 KiB \(serialized\). If your result is larger, the result data is omitted. The widget still mounts and you can fetch data on demand via a widget-initiated `tools/call`. Design large payloads to be pulled rather than pushed.
- If the tool returns an error result, the result data isn't inlined.

Keep `structuredContent` compact. Put bulk or large data behind an app-callable `tools/call` the widget fetches when needed.

## Stateful servers and sessions

\(Go to SEP-1865 [§Lifecycle](https://github.com/modelcontextprotocol/ext-apps/blob/main/specification/2026-01-26/apps.mdx#lifecycle) for the connection, initialization, interactive, and cleanup phases.\)

If your server returns an `Mcp-Session-Id` during `initialize`, Cowork captures it and includes it with the widget. When the widget later calls back \(`resources/read`, `tools/call`, `ui/message`\), Cowork re-attaches that session ID as the `Mcp-Session-Id` header on the upstream request. This process means *stateful MCP servers work*—the widget's follow-up calls land in the same session as the original handshake. You don't need to do anything beyond following the standard MCP session-id contract.

## Sandbox and security model

Widgets render in a *sandboxed iframe*. Design your widget accordingly:

- Your widget loads inside a *sandboxed, cross-origin iframe* isolated from Cowork: it can't read the Cowork page's DOM, cookies, or storage.
- Widgets are hosted on a *per-server origin*: widgets from the same MCP server share an origin—and therefore cookies and storage—while widgets from different servers are fully isolated from each other. Don't put anything in widget storage that another widget from your own server shouldn't see.
- Declared `_meta.ui.csp` domains are validated and, for marketplace packages, filtered against your package's `validDomains[]` before a CSP is built from them \(more information: [Content Security Policy](#content-security-policy)\).
- Cowork brokers all widget-to-server traffic through an authenticated, per-session channel. User credentials are never exposed to the iframe—Cowork attaches the appropriate auth to the upstream request on the widget's behalf.
- Ship a self-contained widget: inline scripts and styles, and assets as `data:` URLs where practical.

Because your server is the trust boundary for the content it serves, return only HTML you control, and treat any data rendered in the widget as you would any other untrusted input.

## Limitations

The following parts of the broader MCP / MCP Apps surface aren't implemented by Cowork. Plan around them:

- **`ui/update-model-context`**: \([§Requests \(View → Host\)](https://github.com/modelcontextprotocol/ext-apps/blob/main/specification/2026-01-26/apps.mdx#requests-view--host)\)—widgets can't silently update the agent's context. \(The Apps SDK exposes this; Cowork rejects it. Use a widget `tools/call` or `ui/message`, or have the user-visible result drive the conversation.\)
- **`pip` \(picture-in-picture\) display mode**: Cowork presents widgets `inline` and `fullscreen` and does honor `ui/request-display-mode` switches between those two \(more information: [Display mode](#display-mode)\), but `pip` isn't offered and a `pip` request is rejected.
- **Server-pushed / streaming widget updates**: Cowork delivers data with the tool result \(and on widget-initiated `tools/call`\). It doesn't support a server pushing new widget state without a corresponding call \(the spec's `ui/notifications/tool-input-partial` streaming path isn't delivered\).
- **`resources/list`**: Cowork proxies `resources/read` for MCP apps \(a widget might read any URI on its own server\), but doesn't expose `resources/list` to widgets, and doesn't bridge reads to other servers.
- **MCP sampling and prompts**: `sampling/*` and prompt features aren't exposed to widgets.
- **Inline HTML in tool results**: Cowork follows the spec's predeclared-resource model. Returning HTML directly in a tool result \(the older MCP-UI style\) isn't honored; declare `_meta.ui.resourceUri` and serve the HTML via `resources/read`.
- **Large inlined results**: `CallToolResult` payloads over 64 KiB aren't pushed to the widget.

If you need one of these, fetch-on-demand patterns \(`resources/read` / app-callable `tools/call`\) cover most cases.

## Graceful degradation

Widgets are *additive*. A widget-enabled tool should return meaningful text or `structuredContent` from its handler regardless of whether a widget renders:

- If widget rendering is unavailable for a session, or your `resourceUri` or MIME type is malformed, the tool still runs, and its data still flows to the agent. The user sees only the data without the custom UI.
- Initialize promptly: a widget that doesn't complete the `ui/initialize` handshake within 10 seconds is replaced with an error card.
- Always make the tool's return value self-sufficient for the agent to reason about.

This condition is also why "display" widgets \(charts, previews\) should return a text summary in the same result: the agent keeps working whether or not the widget mounts.

## When to use a widget vs. elicitation

Cowork already supports *MCP elicitation* \(structured input requests mid-conversation\). For simple confirmations, short enum choices, or flat forms, elicitation is the lighter option—no UI code, and it works without the widget pipeline. Reach for a widget when you need a rich, interactive, or visual surface: searchable pickers, dashboards, charts, previews, or live status.

## Quick checklist

- Tool declares `_meta.ui.resourceUri` with a `ui://` URI \(≤ 1024 characters\).
- Tool handler returns data \(text or compact `structuredContent`\), not HTML.
- A matching resource serves the HTML with mime type `text/html;profile=mcp-app`.
- `structuredContent` \(or whatever the widget needs at mount\) stays under the 64 KiB inline cap; bulk data is fetched via an app-callable `tools/call`.
- `csp` and `permissions` \(an object map, not an array\) declared on the **UI resource's** `_meta.ui`.
- Every domain declared in `csp` or `domain` also listed in your package manifest's `validDomains[]` \(marketplace packages — unauthorized domains are stripped, with a user-visible warning\).
- Inline layout works within 200–720 px width and up to 640 px height; the widget completes `ui/initialize` within 10 seconds.
- App-only tools marked `"visibility": ["app"]`; agent-facing tools include `"model"`.
- Widget callbacks restricted to `resources/read`, `tools/call` \(forwarded to your server\) and `ui/message` \(posts to the conversation, not your server\).
- Tool returns useful data even when no widget renders \(graceful degradation\).

## Related content

- **Spec**: [MCP Apps Extension \(SEP-1865\), 2026-01-26](https://github.com/modelcontextprotocol/ext-apps/blob/main/specification/2026-01-26/apps.mdx)

  Relevant sections:

  - [Resource Discovery](https://github.com/modelcontextprotocol/ext-apps/blob/main/specification/2026-01-26/apps.mdx#resource-discovery)
  - [Visibility](https://github.com/modelcontextprotocol/ext-apps/blob/main/specification/2026-01-26/apps.mdx#resource-discovery)
  - [UI Resource Format](https://github.com/modelcontextprotocol/ext-apps/blob/main/specification/2026-01-26/apps.mdx#ui-resource-format)
  - [Display Modes](https://github.com/modelcontextprotocol/ext-apps/blob/main/specification/2026-01-26/apps.mdx#display-modes)
  - [Notifications \(Host → View\)](https://github.com/modelcontextprotocol/ext-apps/blob/main/specification/2026-01-26/apps.mdx#notifications-host--view)
  - [Requests \(View → Host\)](https://github.com/modelcontextprotocol/ext-apps/blob/main/specification/2026-01-26/apps.mdx#requests-view--host)
  - [Lifecycle](https://github.com/modelcontextprotocol/ext-apps/blob/main/specification/2026-01-26/apps.mdx#lifecycle)

- **Apps SDK**: `@modelcontextprotocol/ext-apps`

Note

The section anchors in the preceding list following GitHub's heading-slug scheme for the `.mdx` source. If an anchor doesn't resolve in your viewer, it lands at the top of the spec. Scroll to the named section.
