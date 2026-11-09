<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/agent-telemetry -->
<!-- Sitemap-Last-Modified: 2026-11-06 -->

# Microsoft 365 Agents SDK telemetry reference

The Microsoft 365 Agents SDK provides built-in instrumentation to help you monitor and debug your agent applications. Each SDK emits traces and metrics for key operations using the standard observability primitives of its runtime: `System.Diagnostics` in C#, and OpenTelemetry in Python and JavaScript. All signals are compatible with the OpenTelemetry ecosystem.

Use this reference to configure telemetry and look up span names, metric names, and attributes for your SDK language. Names and attribute types can differ between languages, so choose your development language before you build queries, dashboards, or alerts.

## Quick navigation

Use these links to find setup instructions and telemetry signals for your selected language.

### JavaScript

- [Setup](#javascript-setup)
- [Traces \(spans\)](#javascript-spans)

  - [CloudAdapter spans](#cloudadapter-spans)
  - [AgentApplication spans](#agentapplication-spans)
  - [TurnContext spans](#turncontext-spans)
  - [ConnectorClient spans](#connectorclient-spans)
  - [AgentClient spans](#agentclient-spans)
  - [Proactive spans](#proactive-spans)
  - [Storage spans](#storage-spans)
  - [Authentication spans](#authentication-spans)
  - [Authorization spans](#authorization-spans)
  - [UserTokenClient spans](#usertokenclient-spans)
  - [Dialog spans](#dialog-spans)
  - [Copilot Studio client spans](#copilot-studio-client-spans)
  - [Named pipe spans](#named-pipe-spans)
  - [Slack spans](#slack-spans)
  - [Error handling in spans](#error-handling-in-spans)
  - [Filter spans with a parent-based sampler](#filter-javascript-spans-with-a-parent-based-sampler)

- [Metrics](#javascript-metrics)

  - [Activity counters](#activity-counters)
  - [Request counters](#request-counters)
  - [Turn counters](#turn-counters)
  - [Duration histograms](#duration-histograms)
  - [Dialog metrics](#dialog-metrics)
  - [Proactive metrics](#proactive-metrics)
  - [Copilot Studio client metrics](#copilot-studio-client-metrics)
  - [Named pipe metrics](#named-pipe-metrics)
  - [Slack metrics](#slack-metrics)

- [Span constants reference](#javascript-span-constants-reference)
- [Metric constants reference](#javascript-metric-constants-reference)
- [Log records](#javascript-log-records)

### C#

- [System.Diagnostics integration](#systemdiagnostics-integration)
- [Setup](#c-setup)
- [Traces \(spans\)](#c-spans)

  - [CloudAdapter spans](#c-cloudadapter-spans)
  - [AgentApplication spans](#c-agentapplication-spans)
  - [TurnContext spans](#c-turncontext-spans)
  - [ConnectorClient spans](#c-connectorclient-spans)
  - [UserTokenClient spans](#c-usertokenclient-spans)
  - [Storage spans](#c-storage-spans)
  - [Authentication spans](#c-authentication-spans)
  - [Authorization spans](#c-authorization-spans)
  - [Proactive spans](#c-proactive-spans)
  - [Error handling in spans](#c-error-handling-in-spans)

- [Metrics](#c-metrics)

  - [Activity counters](#c-activity-counters)
  - [Turn metrics](#c-turn-metrics)
  - [Adapter metrics](#c-adapter-metrics)
  - [Connector metrics](#c-connector-metrics)
  - [UserTokenClient metrics](#c-usertokenclient-metrics)
  - [Storage metrics](#c-storage-metrics)
  - [Authentication metrics](#c-authentication-metrics)

- [Span constants reference](#c-span-constants-reference)
- [Attribute constants reference](#c-attribute-constants-reference)

### Python

- [Setup](#python-setup)
- [Traces \(spans\)](#python-spans)

  - [Adapter spans](#python-adapter-spans)
  - [AgentApplication spans](#python-agentapplication-spans)
  - [Proactive spans](#python-proactive-spans)
  - [TurnContext spans](#python-turncontext-spans)
  - [ConnectorClient spans](#python-connectorclient-spans)
  - [Storage spans](#python-storage-spans)
  - [UserTokenClient spans](#python-usertokenclient-spans)
  - [Authentication spans](#python-authentication-spans)
  - [Authorization spans](#python-authorization-spans)

- [Metrics](#python-metrics)

  - [Adapter metrics](#python-adapter-metrics)
  - [Turn metrics](#python-turn-metrics)
  - [Storage metrics](#python-storage-metrics)
  - [Connector metrics](#python-connector-metrics)
  - [UserTokenClient metrics](#python-usertokenclient-metrics)
  - [Authentication metrics](#python-authentication-metrics)

- [Filter spans](#filter-python-spans)
- [Error handling in spans](#python-error-handling-in-spans)
- [Span constants reference](#python-span-constants-reference)
- [Metric constants reference](#python-metric-constants-reference)

## Use this reference

Use the telemetry signals in this reference to:

- **Understand what data is collected**: Look up each span and metric by name, attributes, and purpose.
- **Build dashboards and alerts**: Use metric and span names in tools such as Azure Monitor, Jaeger, or Grafana.
- **Debug issues**: Use trace spans to identify where latency or errors occur in your agent's request processing pipeline.
- **Compare language implementations**: Check language-specific names and attributes before you reuse dashboards or queries.

## JavaScript telemetry

This section documents the OpenTelemetry spans, metrics, and log records emitted by the JavaScript and TypeScript Agents SDK.

### JavaScript setup

Install the OpenTelemetry packages used by the following tracing example:

```bash
npm install @opentelemetry/api @opentelemetry/sdk-node @opentelemetry/sdk-trace-node
```

Configure OpenTelemetry before your agent starts processing requests:

```typescript
import { NodeSDK } from '@opentelemetry/sdk-node';
import { ConsoleSpanExporter } from '@opentelemetry/sdk-trace-node';

const sdk = new NodeSDK({
  traceExporter: new ConsoleSpanExporter(),
  // Configure your exporters (Jaeger, Azure Monitor, etc.)
});

sdk.start();
```

The JavaScript telemetry package treats `@opentelemetry/api` as an optional peer dependency and uses no-op trace and metric helpers when it is unavailable. The example exports traces only. Configure a metric reader and exporter to export metrics. To mirror SDK logs into OpenTelemetry, also install `@opentelemetry/api-logs` and configure a logger provider and a processor and exporter; otherwise logs continue through the SDK's `debug` output only.

### JavaScript spans

Spans represent individual operations within your agent's request processing. Each span includes attributes that provide context about the operation.

The JavaScript trace helper does not set `SpanKind` explicitly, so these spans use OpenTelemetry's default `INTERNAL` kind.

#### CloudAdapter spans

The CloudAdapter is the main entry point for processing incoming activities from channels.

##### agents.adapter.process

Main processing span for incoming activities.

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.type` | string | The type of activity \(message, conversationUpdate, etc.\) |
| `activity.channel_id` | string | The channel the activity originated from \(msteams, webchat, etc.\) |
| `activity.delivery_mode` | string | The delivery mode of the activity |
| `activity.conversation_id` | string | The conversation identifier |
| `activity.is_agentic` | boolean | Whether this is an agentic \(agent-to-agent\) request |

##### agents.adapter.send\_activities

Span for sending one or more activities to a conversation.

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.count` | number | Number of activities being sent |

**`activity.sent` span event \(per activity\):**

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.id` | string | The activity identifier |
| `activity.type` | string | The type of activity |
| `activity.channel_id` | string | The channel identifier |
| `activity.conversation_id` | string | The conversation identifier |

##### agents.adapter.update\_activity

Span for updating an existing activity.

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.id` | string | The ID of the activity being updated |
| `activity.conversation_id` | string | The conversation identifier |

##### agents.adapter.delete\_activity

Span for deleting an activity from a conversation.

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.id` | string | The ID of the activity being deleted |
| `activity.conversation_id` | string | The conversation identifier |

##### agents.adapter.continue\_conversation

Span for continuing a conversation proactively.

| Attribute | Type | Description |
| --- | --- | --- |
| `bot.app_id` | string | The bot's application ID |
| `activity.conversation_id` | string | The conversation identifier |
| `activity.is_agentic` | boolean | Whether this is an agentic request |

##### agents.adapter.create\_connector\_client

Span for creating a connector client instance.

| Attribute | Type | Description |
| --- | --- | --- |
| `service_url` | string | The Bot Framework service URL |
| `auth.scopes` | string\[\] | The authentication scopes |
| `activity.is_agentic` | boolean | Whether this is for an agentic request \(when using identity variant\) |

##### agents.adapter.create\_user\_token\_client

Span for creating a user token client instance.

| Attribute | Type | Description |
| --- | --- | --- |
| `token.service.endpoint` | string | The token service endpoint URL |
| `auth.scope` | string | The authentication scope |

#### AgentApplication spans

The AgentApplication class provides a higher-level abstraction for building agents with routing and handlers.

##### agents.app.run

Main execution span for the AgentApplication.

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.type` | string | The type of activity being processed |
| `activity.channel_id` | string | The channel identifier |
| `activity.name` | string | The activity name |
| `route.authorized` | boolean | Whether the request was authorized |
| `route.matched` | boolean | Whether a route handler matched the activity |

Child spans:

- `agents.app.route_handler`: Includes `route.is_invoke` and `route.is_agentic` attributes
- `agents.app.download_files`: Includes the `agents.attachments.count` attribute
- `agents.app.typing_indicator`: Includes activity context and the typing notification sequence
- `agents.app.before_turn`: Runs before-turn handlers
- `agents.app.after_turn`: Runs after-turn handlers

##### agents.app.route\_handler

Child span for executing a matched route handler.

| Attribute | Type | Description |
| --- | --- | --- |
| `route.is_invoke` | boolean | Whether this is an invoke activity route |
| `route.is_agentic` | boolean | Whether this is an agentic route |

##### agents.app.before\_turn

Span for before-turn handlers execution.

*No specific attributes. Wraps the execution of registered before-turn event handlers.*

##### agents.app.after\_turn

Span for after-turn handlers execution.

*No specific attributes. Wraps the execution of registered after-turn event handlers.*

##### agents.app.download\_files

Span for downloading file attachments.

| Attribute | Type | Description |
| --- | --- | --- |
| `agents.attachments.count` | number | Number of attachments being downloaded |

##### agents.app.typing\_indicator

Span for sending a periodic typing activity while a turn is being processed. A new span is emitted for each typing notification.

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.type` | string | The activity type \(`typing`; defaults to `unknown` when unavailable\) |
| `activity.channel_id` | string | The channel identifier, or `unknown` when unavailable |
| `activity.conversation_id` | string | The conversation identifier, or `unknown` when unavailable |
| `typing.notification.sequence` | number | One-based sequence number of the typing notification for the current typing timer |

#### TurnContext spans

The TurnContext manages the current turn of conversation.

##### agents.turn.send\_activities

Span for sending activities through the turn context.

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.count` | number | Number of activities being sent |

**`activity.sent` span event \(per activity\):**

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.id` | string | The activity identifier |
| `activity.type` | string | The type of activity |
| `activity.delivery_mode` | string | The delivery mode of the activity |

#### ConnectorClient spans

The ConnectorClient handles HTTP communication with the Bot Framework Connector service.

##### agents.connector.reply\_to\_activity

Span for replying to a specific activity.

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.conversation_id` | string | The conversation identifier |
| `activity.id` | string | The activity being replied to |

##### agents.connector.send\_to\_conversation

Span for sending an activity to a conversation.

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.conversation_id` | string | The target conversation identifier |

##### agents.connector.update\_activity

Span for updating an activity via the connector.

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.conversation_id` | string | The conversation identifier |
| `activity.id` | string | The activity being updated |

##### agents.connector.delete\_activity

Span for deleting an activity via the connector.

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.conversation_id` | string | The conversation identifier |
| `activity.id` | string | The activity being deleted |

##### agents.connector.create\_conversation

Span for creating a new conversation.

*No span-level attributes. Metrics are recorded with operation, http.method, and http.status\_code.*

##### agents.connector.get\_conversations

Span for retrieving conversations.

*No span-level attributes. Metrics are recorded with operation, http.method, and http.status\_code.*

##### agents.connector.get\_conversation\_member

Span for retrieving a conversation member.

*No span-level attributes. Metrics are recorded with operation, http.method, and http.status\_code.*

##### agents.connector.upload\_attachment

Span for uploading an attachment.

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.conversation_id` | string | The conversation identifier |

##### agents.connector.get\_attachment\_info

Span for retrieving attachment information.

| Attribute | Type | Description |
| --- | --- | --- |
| `attachment.id` | string | The attachment identifier |

##### agents.connector.get\_attachment

Span for retrieving attachment content.

| Attribute | Type | Description |
| --- | --- | --- |
| `attachment.id` | string | The attachment identifier |
| `view.id` | string | The view identifier |

#### AgentClient spans

The AgentClient handles agent-to-agent communication.

##### agents.agent\_client.post\_activity

Span for posting an activity to another agent.

| Attribute | Type | Description |
| --- | --- | --- |
| `target.endpoint` | string | The target agent's endpoint URL |
| `target.client_id` | string | The target agent's client ID |
| `http.status_code` | string | HTTP response status code |

#### Storage spans

Storage spans are emitted by all storage implementations \(`MemoryStorage`, `FileStorage`, `BlobsStorage`, `CosmosDbPartitionedStorage`\).

##### agents.storage.read

Span for reading items from storage.

| Attribute | Type | Description |
| --- | --- | --- |
| `storage.operation` | string | Always `"read"` |
| `storage.key.count` | number | Number of keys being read |

##### agents.storage.write

Span for writing items to storage.

| Attribute | Type | Description |
| --- | --- | --- |
| `storage.operation` | string | Always `"write"` |
| `storage.key.count` | number | Number of keys being written |

##### agents.storage.delete

Span for deleting items from storage.

| Attribute | Type | Description |
| --- | --- | --- |
| `storage.operation` | string | Always `"delete"` |
| `storage.key.count` | number | Number of keys being deleted |

#### Authentication spans

Authentication spans cover token acquisition operations via the MSAL token provider.

##### agents.authentication.get\_access\_token

Span for acquiring an access token.

| Attribute | Type | Description |
| --- | --- | --- |
| `auth.scope` | string | The authentication scope requested |
| `auth.method` | string | The resolved `AuthType` value, such as `ClientSecret`, `Certificate`, `WorkloadIdentity`, or `FederatedCredentials` |

##### agents.authentication.acquire\_token\_on\_behalf\_of

Span for acquiring a token using the on-behalf-of flow.

| Attribute | Type | Description |
| --- | --- | --- |
| `auth.scopes` | string\[\] | The authentication scopes requested |

##### agents.authentication.get\_agentic\_instance\_token

Span for acquiring an agentic instance token.

| Attribute | Type | Description |
| --- | --- | --- |
| `agentic.instance_id` | string | The agentic application instance ID |

##### agents.authentication.get\_agentic\_user\_token

Span for acquiring an agentic user token.

| Attribute | Type | Description |
| --- | --- | --- |
| `agentic.instance_id` | string | The agentic application instance ID |
| `agentic.user_id` | string | The agentic user ID |
| `auth.scopes` | string\[\] | The authentication scopes requested |

#### Authorization spans

Authorization spans cover the authorization handlers used by AgentApplication.

##### agents.authorization.agentic\_token

Span for retrieving an agentic authorization token.

| Attribute | Type | Description |
| --- | --- | --- |
| `auth.handler.id` | string | The authorization handler identifier |
| `auth.connection.name` | string | The connection name used |
| `auth.scopes` | string\[\] | The authentication scopes requested |

##### agents.authorization.azure\_bot\_token

Span for retrieving an Azure Bot Service authorization token.

| Attribute | Type | Description |
| --- | --- | --- |
| `auth.handler.id` | string | The authorization handler identifier |
| `auth.connection.name` | string | The connection name used |

##### agents.authorization.azure\_bot\_obo\_token

Span for retrieving an Azure Bot Service token using the on-behalf-of flow.

| Attribute | Type | Description |
| --- | --- | --- |
| `auth.handler.id` | string | The authorization handler identifier |
| `auth.connection.name` | string | The connection name used |
| `auth.scopes` | string\[\] | The authentication scopes requested |

##### agents.authorization.azure\_bot\_signin

Span for the Azure Bot Service sign-in flow.

| Attribute | Type | Description |
| --- | --- | --- |
| `auth.handler.id` | string | The authorization handler identifier |
| `auth.handler.status` | string | The resulting sign-in status \(e.g., APPROVED, REJECTED, REVALIDATE\) |
| `auth.handler.status.reason` | string | The reason for the sign-in status |
| `auth.connection.name` | string | The connection name used |

##### agents.authorization.azure\_bot\_signout

Span for signing out a user via Azure Bot Service.

| Attribute | Type | Description |
| --- | --- | --- |
| `auth.handler.id` | string | The authorization handler identifier |
| `auth.connection.name` | string | The connection name used |
| `activity.channel_id` | string | The channel identifier |

#### UserTokenClient spans

The UserTokenClient handles user token operations against the Bot Framework Token Service.

##### agents.user\_token\_client.get\_user\_token

Span for getting a user token.

| Attribute | Type | Description |
| --- | --- | --- |
| `auth.connection.name` | string | The connection name |
| `activity.channel_id` | string | The channel identifier |
| `user.id` | string | The user identifier |

##### agents.user\_token\_client.sign\_out

Span for signing out a user.

| Attribute | Type | Description |
| --- | --- | --- |
| `user.id` | string | The user identifier |
| `auth.connection.name` | string | The connection name |
| `activity.channel_id` | string | The channel identifier |

##### agents.user\_token\_client.get\_sign\_in\_resource

Span for getting a sign-in resource URL.

| Attribute | Type | Description |
| --- | --- | --- |
| `auth.connection.name` | string | The connection name |

##### agents.user\_token\_client.exchange\_token

Span for exchanging a token.

| Attribute | Type | Description |
| --- | --- | --- |
| `user.id` | string | The user identifier |
| `auth.connection.name` | string | The connection name |
| `activity.channel_id` | string | The channel identifier |

##### agents.user\_token\_client.get\_token\_or\_sign\_in\_resource

Span for getting a token or sign-in resource.

| Attribute | Type | Description |
| --- | --- | --- |
| `user.id` | string | The user identifier |
| `auth.connection.name` | string | The connection name |
| `activity.channel_id` | string | The channel identifier |

##### agents.user\_token\_client.get\_token\_status

Span for getting the token status.

| Attribute | Type | Description |
| --- | --- | --- |
| `user.id` | string | The user identifier |
| `activity.channel_id` | string | The channel identifier |

##### agents.user\_token\_client.get\_aad\_tokens

Span for getting Microsoft Entra ID tokens.

| Attribute | Type | Description |
| --- | --- | --- |
| `user.id` | string | The user identifier |
| `auth.connection.name` | string | The connection name |
| `activity.channel_id` | string | The channel identifier |

#### Proactive spans

Proactive spans cover operations for sending messages and managing conversations outside of a user-initiated turn.

##### agents.proactive.store\_conversation

Span for storing a conversation reference for later proactive use.

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.conversation_id` | string | The conversation identifier |

##### agents.proactive.get\_conversation

Span for retrieving a stored conversation reference.

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.conversation_id` | string | The conversation identifier |
| `proactive.conversation_found` | boolean | Whether the conversation was found |

##### agents.proactive.get\_conversation\_or\_throw

Span for retrieving a stored conversation reference, throwing if not found.

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.conversation_id` | string | The conversation identifier |

##### agents.proactive.delete\_conversation

Span for deleting a stored conversation reference.

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.conversation_id` | string | The conversation identifier |

##### agents.proactive.send\_activity

Span for sending a proactive activity to a conversation.

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.channel_id` | string | The channel identifier |
| `activity.type` | string | The type of activity |
| `activity.conversation_id` | string | The conversation identifier |

##### agents.proactive.continue\_conversation

Span for continuing a conversation proactively with a callback.

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.channel_id` | string | The channel identifier |
| `proactive.has_auto_sign_in` | boolean | Whether auto sign-in is configured |
| `activity.conversation_id` | string | The conversation identifier |

##### agents.proactive.create\_conversation

Span for creating a new proactive conversation.

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.channel_id` | string | The channel identifier |
| `proactive.store_conversation` | boolean | Whether the conversation should be stored |
| `proactive.has_handler` | boolean | Whether a handler callback was provided |
| `proactive.members_count` | number | Number of members in the conversation |

#### Dialog spans

Dialog spans are emitted by the `@microsoft/agents-hosting-dialogs` package for dialog lifecycle operations.

##### agents.dialogs.run

Main execution span for running a dialog set.

| Attribute | Type | Description |
| --- | --- | --- |
| `dialog.root_id` | string | The root dialog identifier |
| `activity.type` | string | The type of activity being processed |
| `activity.channel_id` | string | The channel identifier |
| `activity.conversation_id` | string | The conversation identifier |
| `dialog.status` | string | The dialog turn status |
| `dialog.attempt_count` | number | Number of dialog attempts |

##### agents.dialogs.context.begin

Span for beginning a new dialog.

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.type` | string | The type of activity |
| `activity.conversation_id` | string | The conversation identifier |
| `dialog.id` | string | The dialog identifier |
| `dialog.name` | string | The dialog name |
| `dialog.parent_id` | string | The parent dialog identifier |
| `dialog.status` | string | The dialog turn status |

##### agents.dialogs.context.continue

Span for continuing an active dialog.

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.type` | string | The type of activity |
| `activity.conversation_id` | string | The conversation identifier |
| `dialog.id` | string | The dialog identifier |
| `dialog.name` | string | The dialog name |
| `dialog.status` | string | The dialog turn status |

##### agents.dialogs.context.end

Span for ending a dialog.

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.type` | string | The type of activity |
| `activity.conversation_id` | string | The conversation identifier |
| `dialog.id` | string | The dialog identifier |
| `dialog.name` | string | The dialog name |
| `dialog.status` | string | The dialog turn status |

##### agents.dialogs.context.replace

Span for replacing the current dialog with a new one.

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.type` | string | The type of activity |
| `activity.conversation_id` | string | The conversation identifier |
| `dialog.id` | string | The current dialog identifier |
| `dialog.name` | string | The current dialog name |
| `dialog.replacement_id` | string | The replacement dialog identifier |
| `dialog.replacement_name` | string | The replacement dialog name |
| `dialog.status` | string | The dialog turn status |

##### agents.dialogs.context.cancel\_all

Span for canceling all active dialogs.

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.type` | string | The type of activity |
| `activity.conversation_id` | string | The conversation identifier |
| `dialog.cancel_parents` | boolean | Whether parent dialogs should also be canceled |
| `dialog.event_name` | string | The cancellation event name |
| `dialog.id` | string | The dialog identifier |
| `dialog.name` | string | The dialog name |
| `dialog.status` | string | The dialog turn status |

#### Copilot Studio client spans

Copilot Studio Client spans are emitted by the `@microsoft/agents-copilotstudio-client` package for Direct-to-Engine communication.

##### agents.copilot\_client.start\_conversation

Span for starting a new conversation with a Copilot Studio agent.

| Attribute | Type | Description |
| --- | --- | --- |
| `copilot.emit_start_event` | boolean | Whether a start event was emitted \(conditional\) |
| `copilot.request` | boolean | `true` when the operation uses the request path instead of emitting a start event \(conditional\) |

##### agents.copilot\_client.send\_activity

Span for sending an activity to a Copilot Studio agent.

| Attribute | Type | Description |
| --- | --- | --- |
| `copilot.activity.type` | string | The type of activity |
| `copilot.activity.conversation_id` | string | The conversation identifier |

##### agents.copilot\_client.post\_request

Span for making an HTTP request to the Copilot Studio API.

| Attribute | Type | Description |
| --- | --- | --- |
| `copilot.post_request.url` | string | The request URL |
| `copilot.post_request.method` | string | The HTTP method |

**`activity.received` span event \(per response activity\):**

| Attribute | Type | Description |
| --- | --- | --- |
| `copilot.post_request.activity.type` | string | The type of response activity |
| `copilot.post_request.activity.conversation_id` | string | The conversation identifier |

##### agents.copilot\_client.webchat.create\_connection

Span for creating a WebChat connection to a Copilot Studio agent.

| Attribute | Type | Description |
| --- | --- | --- |
| `copilot.webchat.show_typing` | boolean | Whether typing indicators are shown |

##### agents.copilot\_client.webchat.start\_conversation

Span for starting a WebChat conversation and receiving its initial activities.

| Attribute | Type | Description |
| --- | --- | --- |
| `copilot.webchat.activity.received_count` | number | Number of initial activities received |
| `copilot.webchat.conversation_id` | string | The WebChat conversation identifier |

##### agents.copilot\_client.webchat.post\_activity

Span for posting an activity to a WebChat conversation and collecting response activities.

| Attribute | Type | Description |
| --- | --- | --- |
| `copilot.webchat.activity.id` | string | The posted activity identifier |
| `copilot.webchat.activity.type` | string | The posted activity type |
| `copilot.webchat.activity.received_count` | number | Number of response activities received |
| `copilot.webchat.conversation_id` | string | The WebChat conversation identifier |

**`activity.sent` span event:**

| Attribute | Type | Description |
| --- | --- | --- |
| `copilot.webchat.activity.id` | string | The sent activity identifier |
| `copilot.webchat.activity.type` | string | The sent activity type |
| `copilot.webchat.activity.conversation_id` | string | The WebChat conversation identifier |

##### agents.copilot\_client.webchat.receive\_activity

Span for receiving an activity from a WebChat conversation.

| Attribute | Type | Description |
| --- | --- | --- |
| `copilot.webchat.activity.id` | string | The received activity identifier |
| `copilot.webchat.activity.type` | string | The received activity type |
| `copilot.webchat.activity.conversation_id` | string | The WebChat conversation identifier |

##### agents.copilot\_client.webchat.end\_connection

Span for ending a WebChat connection.

| Attribute | Type | Description |
| --- | --- | --- |
| `copilot.webchat.conversation_id` | string | The WebChat conversation identifier |

##### agents.copilot\_client.execute\_streaming

Span for executing a streaming request to a Copilot Studio agent.

| Attribute | Type | Description |
| --- | --- | --- |
| `copilot.activity.type` | string | The type of activity |
| `copilot.activity.conversation_id` | string | The conversation identifier |

##### agents.copilot\_client.subscribe\_async

Span for subscribing to async events from a Copilot Studio agent.

| Attribute | Type | Description |
| --- | --- | --- |
| `copilot.subscribe_async.conversation_id` | string | The conversation identifier |
| `copilot.subscribe_async.last_received_event_id` | string | The last received event ID |

**`event.received` span event \(per received event\):**

| Attribute | Type | Description |
| --- | --- | --- |
| `copilot.subscribe_async.event.id` | string | The event identifier |
| `copilot.subscribe_async.event.activity.type` | string | The type of activity in the event |

#### Named pipe spans

Named pipe spans are emitted by the `@microsoft/agents-hosting-directline-namedpipes` package.

##### agents.named\_pipe.connect

Span for establishing a named pipe connection.

| Attribute | Type | Description |
| --- | --- | --- |
| `agents.named_pipe.pipe_name` | string | The connected pipe name |

##### agents.named\_pipe.dispatch

Span for dispatching an inbound named pipe request to the activity handler.

| Attribute | Type | Description |
| --- | --- | --- |
| `agents.named_pipe.request.verb` | string | The request verb |
| `agents.named_pipe.request.path` | string | The request path |
| `agents.named_pipe.response.status_code` | number | The response status code |

##### agents.named\_pipe.send

Span for sending a response over the named pipe.

| Attribute | Type | Description |
| --- | --- | --- |
| `agents.named_pipe.response.status_code` | number | The response status code |
| `agents.named_pipe.response.body_size` | number | The response body size in bytes |

#### Slack spans

Slack spans are emitted by the `@microsoft/agents-hosting-extensions-slack` package.

##### agents.slack.api.call

Span for an outbound Slack Web API call.

| Attribute | Type | Description |
| --- | --- | --- |
| `slack.api.method` | string | The Slack Web API method, such as `chat.postMessage` |
| `http.method` | string | Always `POST` |
| `http.status_code` | string | The HTTP response status code, or `unknown` when no response is available |
| `slack.api.error_code` | string | The Slack API error code \(only present when Slack returns one\) |
| `server.address` | string | Always `slack.com` |

### Error handling in spans

All spans created by the SDK automatically handle errors. When an exception occurs within a traced operation:

1. The span status is set to `ERROR` with the error message
2. The exception is recorded on the span via `recordException()`
3. The span's definition-specific end hook runs and can inspect the error
4. The span is ended and the original error is re-thrown

On success, the span status is set to `OK`.

### Filter JavaScript spans with a parent-based sampler

Warning

`AGENTS_TELEMETRY_DISABLED_SPAN_CATEGORIES` is deprecated and will be removed in a future release. It remains supported temporarily for backward compatibility, but new applications should configure an OpenTelemetry sampler instead.

Filtering belongs in the application's OpenTelemetry configuration. A custom sampler can reject selected SDK span names, while a parent-based delegate preserves normal sampling decisions and rejects descendants of a filtered parent span.

The following reusable sampler filters automatic typing-indicator telemetry. The `agents.app.typing_indicator` span is the parent of the adapter and connector spans created while sending that notification, so rejecting it suppresses the complete typing operation:

Install the additional packages used by the sampler example:

```bash
npm install @microsoft/agents-telemetry @opentelemetry/sdk-trace-base
```

Configure the sampler when you create the `NodeSDK` instance:

```typescript
import { SpanNames } from '@microsoft/agents-telemetry';
import { NodeSDK } from '@opentelemetry/sdk-node';
import {
  AlwaysOnSampler,
  ParentBasedSampler,
  SamplingDecision,
  type Sampler,
} from '@opentelemetry/sdk-trace-base';
import { ConsoleSpanExporter } from '@opentelemetry/sdk-trace-node';

class SpanNameFilteringSampler implements Sampler {
  private readonly filteredSpanNames: ReadonlySet<string>;
  private readonly parentBased = new ParentBasedSampler({
    root: new AlwaysOnSampler(),
  });

  constructor(spanNames: Iterable<string>) {
    this.filteredSpanNames = new Set(spanNames);
  }

  shouldSample: Sampler['shouldSample'] = (context, traceId, spanName, spanKind, attributes, links) => {
    return this.filteredSpanNames.has(spanName)
      ? { decision: SamplingDecision.NOT_RECORD }
      : this.parentBased.shouldSample(context, traceId, spanName, spanKind, attributes, links);
  }

  toString() {
    return `SpanNameFilteringSampler(${[...this.filteredSpanNames].join(',')})`;
  }
}

const sdk = new NodeSDK({
  sampler: new SpanNameFilteringSampler([
    SpanNames.AGENTS_APP_TYPING_INDICATOR,
  ]),
  traceExporter: new ConsoleSpanExporter(),
});

sdk.start();
```

Add other values from `SpanNames` when additional SDK spans should be filtered. Applications migrating from the deprecated `STORAGE`, `AUTHENTICATION`, `AUTHORIZATION`, or `DIALOGS` categories should list the corresponding span-name constants instead. This gives the application explicit control over its sampling policy without requiring SDK-specific environment configuration.

### JavaScript metrics

Metrics provide aggregated measurements of your agent's operation over time.

#### Activity counters

Counters track the total number of activities processed.

##### agents.activities.received

**Type:** Counter **Unit:** activities **Description:** Total number of activities received by the adapter.

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.type` | string | Type of activity received |
| `activity.channel_id` | string | Channel the activity came from |

##### agents.activities.sent

**Type:** Counter **Unit:** activities **Description:** Total number of outbound activities sent by the adapter.

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.type` | string | Type of activity sent |
| `activity.channel_id` | string | Target channel |
| `activity.conversation_id` | string | The conversation identifier |

##### agents.activities.updated

**Type:** Counter **Unit:** activities **Description:** Total number of activities updated by the adapter.

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.channel_id` | string | Channel where activity was updated |

##### agents.activities.deleted

**Type:** Counter **Unit:** activities **Description:** Total number of activities deleted by the adapter.

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.channel_id` | string | Channel where activity was deleted |

#### Request counters

Counters for outbound requests.

##### agents.connector.request.count

**Type:** Counter **Unit:** request **Description:** Total number of outbound connector HTTP requests.

| Attribute | Type | Description |
| --- | --- | --- |
| `operation` | string | Connector operation name \(reply.to.activity, send.to.conversation, etc.\) |
| `http.method` | string | HTTP method used \(POST, GET, DELETE, PUT\) |
| `http.status_code` | string | HTTP response status code |

##### agents.agent\_client.request.count

**Type:** Counter **Unit:** request **Description:** Total number of inter-agent calls.

| Attribute | Type | Description |
| --- | --- | --- |
| `target.endpoint` | string | Target agent endpoint |
| `target.client_id` | string | Target agent client ID |
| `http.status_code` | string | HTTP response status code |

##### agents.auth.token.request.count

**Type:** Counter **Unit:** request **Description:** Total number of token acquisition attempts.

| Attribute | Type | Description |
| --- | --- | --- |
| `auth.method` | string | The resolved `AuthType` value, or `obo`, `agentic_instance`, or `agentic_user` for those flows |
| `auth.success` | boolean | Whether the token acquisition succeeded |

##### agents.user\_token\_client.request.count

**Type:** Counter **Unit:** request **Description:** Total number of user token client HTTP requests.

| Attribute | Type | Description |
| --- | --- | --- |
| `operation` | string | Operation name \(get.user.token, sign.out, exchange.token, etc.\) |
| `http.method` | string | HTTP method used |
| `http.status_code` | string | HTTP response status code |

#### Turn counters

Counters for turn processing.

##### agents.turn.count

**Type:** Counter **Unit:** turn **Description:** Total turns processed.

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.type` | string | Type of activity processed |
| `activity.channel_id` | string | The channel identifier |

##### agents.turn.error.count

**Type:** Counter **Unit:** turn **Description:** Total turns that resulted in an error.

| Attribute | Type | Description |
| --- | --- | --- |
| `error.type` | string | Exception/error class name |

#### Duration histograms

Histograms track the distribution of operation durations.

##### agents.adapter.process.duration

**Type:** Histogram **Unit:** ms **Description:** Duration of the adapter process method in milliseconds.

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.type` | string | Type of activity processed |

##### agents.connector.request.duration

**Type:** Histogram **Unit:** ms **Description:** Duration of outbound connector HTTP requests in milliseconds.

| Attribute | Type | Description |
| --- | --- | --- |
| `operation` | string | Connector operation name |
| `http.method` | string | HTTP method used |
| `http.status_code` | string | HTTP response status code |

##### agents.agent\_client.request.duration

**Type:** Histogram **Unit:** ms **Description:** Duration of inter-agent call latency in milliseconds.

| Attribute | Type | Description |
| --- | --- | --- |
| `target.endpoint` | string | Target agent endpoint |
| `target.client_id` | string | Target agent client ID |
| `http.status_code` | string | HTTP response status code |

##### agents.turn.duration

**Type:** Histogram **Unit:** ms **Description:** Duration of end-to-end turn processing in milliseconds.

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.type` | string | Type of activity processed |
| `activity.channel_id` | string | The channel identifier |

##### agents.storage.operation.duration

**Type:** Histogram **Unit:** ms **Description:** Duration of storage operations in milliseconds.

| Attribute | Type | Description |
| --- | --- | --- |
| `storage.operation` | string | Storage operation type \(read, write, delete\) |
| `storage.key.count` | number | Number of keys in the operation |

##### agents.auth.token.duration

**Type:** Histogram **Unit:** ms **Description:** Duration of token acquisition latency in milliseconds.

| Attribute | Type | Description |
| --- | --- | --- |
| `auth.method` | string | Authentication method used |

##### agents.user\_token\_client.request.duration

**Type:** Histogram **Unit:** ms **Description:** Duration of user token client HTTP requests in milliseconds.

| Attribute | Type | Description |
| --- | --- | --- |
| `operation` | string | Operation name |
| `http.method` | string | HTTP method used |
| `http.status_code` | string | HTTP response status code |

#### Dialog metrics

Metrics for dialog lifecycle operations from `@microsoft/agents-hosting-dialogs`.

##### agents.dialogs.context.count

**Type:** Counter **Unit:** operations **Description:** Total number of dialog context operations \(begin, continue, end, replace, cancel\_all\).

| Attribute | Type | Description |
| --- | --- | --- |
| `operation` | string | `begin`, `continue`, `end`, `replace`, or `cancel_all` |
| `result.status` | string | The resulting dialog turn status |
| `dialog.cancel_parents` | boolean | Whether parent dialogs are canceled \(only present for `cancel_all`\) |

##### agents.dialogs.context.duration

**Type:** Histogram **Unit:** ms **Description:** Duration of dialog context operations in milliseconds.

| Attribute | Type | Description |
| --- | --- | --- |
| `operation` | string | `begin`, `continue`, `end`, `replace`, or `cancel_all` |
| `result.status` | string | The resulting dialog turn status |
| `dialog.cancel_parents` | boolean | Whether parent dialogs are canceled \(only present for `cancel_all`\) |

#### Proactive metrics

Metrics for proactive messaging operations.

##### agents.proactive.operation.count

**Type:** Counter **Unit:** operation **Description:** Total number of proactive send, continue, and create operations.

| Attribute | Type | Description |
| --- | --- | --- |
| `operation` | string | `send.activity`, `continue.conversation`, or `create.conversation` |
| `operation.success` | boolean | Whether the operation completed without an error |
| `activity.channel_id` | string | The channel identifier |
| `activity.type` | string | The activity type \(only present for `send.activity`\) |
| `proactive.has_auto_sign_in` | boolean | Whether auto sign-in is configured \(only present for `continue.conversation`\) |
| `proactive.store_conversation` | boolean | Whether the conversation is stored \(only present for `create.conversation`\) |
| `proactive.has_handler` | boolean | Whether a handler was provided \(only present for `create.conversation`\) |

##### agents.proactive.operation.duration

**Type:** Histogram **Unit:** ms **Description:** Duration of proactive operations in milliseconds.

| Attribute | Type | Description |
| --- | --- | --- |
| `operation` | string | `send.activity`, `continue.conversation`, or `create.conversation` |
| `operation.success` | boolean | Whether the operation completed without an error |
| `activity.channel_id` | string | The channel identifier |
| `activity.type` | string | The activity type \(only present for `send.activity`\) |
| `proactive.has_auto_sign_in` | boolean | Whether auto sign-in is configured \(only present for `continue.conversation`\) |
| `proactive.store_conversation` | boolean | Whether the conversation is stored \(only present for `create.conversation`\) |
| `proactive.has_handler` | boolean | Whether a handler was provided \(only present for `create.conversation`\) |

#### Copilot Studio client metrics

Metrics for the `@microsoft/agents-copilotstudio-client` package.

##### agents.copilot\_client.activities.received

**Type:** Counter **Unit:** activities **Description:** Total number of activities received from a Copilot Studio agent.

| Attribute | Type | Description |
| --- | --- | --- |
| `copilot.activity.type` | string | The received activity type |

##### agents.copilot\_client.activities.sent

**Type:** Counter **Unit:** activities **Description:** Total number of activities sent to a Copilot Studio agent.

| Attribute | Type | Description |
| --- | --- | --- |
| `copilot.activity.type` | string | The sent activity type |

##### agents.copilot\_client.conversations.started

**Type:** Counter **Unit:** conversations **Description:** Total number of conversations started with Copilot Studio agents.

| Attribute | Type | Description |
| --- | --- | --- |
| `operation` | string | Always `startConversationStreaming` |
| `copilot.emit_start_event` | boolean | `true` when a start event is emitted \(conditional\) |
| `copilot.request` | boolean | `true` when the request path is used \(conditional\) |

##### agents.copilot\_client.webchat.connection.count

**Type:** Counter **Unit:** connections **Description:** Total number of WebChat connections created.

| Attribute | Type | Description |
| --- | --- | --- |
| `copilot.webchat.show_typing` | boolean | Whether typing indicators are shown |

##### agents.copilot\_client.request.count

**Type:** Counter **Unit:** requests **Description:** Total number of HTTP/SSE requests to the Copilot Studio API.

| Attribute | Type | Description |
| --- | --- | --- |
| `operation` | string | Always `postRequestAsync` |
| `copilot.post_request.url` | string | The request URL |
| `copilot.post_request.method` | string | The HTTP method |

##### agents.copilot\_client.request.error.count

**Type:** Counter **Unit:** requests **Description:** Total number of failed requests to the Copilot Studio API.

| Attribute | Type | Description |
| --- | --- | --- |
| `operation` | string | Always `postRequestAsync` |
| `copilot.post_request.url` | string | The request URL |
| `copilot.post_request.method` | string | The HTTP method |
| `error.type` | string | The error class or thrown value type |

##### agents.copilot\_client.request.duration

**Type:** Histogram **Unit:** ms **Description:** Duration of requests to the Copilot Studio API in milliseconds.

| Attribute | Type | Description |
| --- | --- | --- |
| `operation` | string | `startConversationStreaming`, `sendActivityStreaming`, or `executeStreaming` |
| `copilot.emit_start_event` | boolean | `true` for a start-conversation event path \(conditional\) |
| `copilot.request` | boolean | `true` for a start-conversation request path \(conditional\) |
| `copilot.activity.type` | string | Activity type for send and execute operations |

##### agents.copilot\_client.stream.duration

**Type:** Histogram **Unit:** ms **Description:** Duration of SSE stream sessions in milliseconds.

| Attribute | Type | Description |
| --- | --- | --- |
| `operation` | string | `postRequestAsync` or `subscribeAsync` |
| `copilot.post_request.url` | string | The request URL \(only present for `postRequestAsync`\) |
| `copilot.post_request.method` | string | The HTTP method \(only present for `postRequestAsync`\) |

##### agents.copilot\_client.execute\_streaming.count

**Type:** Counter **Unit:** operations **Description:** Total number of streaming execution operations.

| Attribute | Type | Description |
| --- | --- | --- |
| `copilot.activity.type` | string | The activity type |

##### agents.copilot\_client.subscribe\_async.count

**Type:** Counter **Unit:** operations **Description:** Total number of async subscription operations.

| Attribute | Type | Description |
| --- | --- | --- |
| `operation` | string | Always `subscribeAsync` |

##### agents.copilot\_client.subscribe\_event.count

**Type:** Counter **Unit:** events **Description:** Total number of events received via async subscriptions.

| Attribute | Type | Description |
| --- | --- | --- |
| `copilot.subscribe_async.event.id` | string | The event identifier |
| `copilot.subscribe_async.event.activity.type` | string | The activity type in the event |

#### Named pipe metrics

Metrics emitted by the `@microsoft/agents-hosting-directline-namedpipes` package.

##### agents.named\_pipe.connection.count

**Type:** Counter **Unit:** connection **Description:** Total number of named pipe connections established.

*No metric attributes.*

##### agents.named\_pipe.dispatch.count

**Type:** Counter **Unit:** request **Description:** Total number of inbound requests dispatched to the activity handler.

| Attribute | Type | Description |
| --- | --- | --- |
| `request.verb` | string | The request verb |
| `request.path` | string | The request path |

##### agents.named\_pipe.dispatch.duration

**Type:** Histogram **Unit:** ms **Description:** Duration of activity-handler request dispatch in milliseconds.

| Attribute | Type | Description |
| --- | --- | --- |
| `request.verb` | string | The request verb |
| `request.path` | string | The request path |

##### agents.named\_pipe.dispatch.error.count

**Type:** Counter **Unit:** error **Description:** Total number of named pipe dispatch errors.

| Attribute | Type | Description |
| --- | --- | --- |
| `error.type` | string | The error class or thrown value type |

##### agents.named\_pipe.send.count

**Type:** Counter **Unit:** response **Description:** Total number of responses sent over the named pipe.

*No metric attributes.*

##### agents.named\_pipe.send.duration

**Type:** Histogram **Unit:** ms **Description:** Duration of named pipe response send operations in milliseconds.

*No metric attributes.*

#### Slack metrics

Metrics emitted by the `@microsoft/agents-hosting-extensions-slack` package.

##### agents.slack.api.request.count

**Type:** Counter **Unit:** request **Description:** Total number of outbound Slack Web API requests.

| Attribute | Type | Description |
| --- | --- | --- |
| `slack.api.method` | string | The Slack Web API method |
| `http.method` | string | Always `POST` |
| `http.status_code` | string | The HTTP response status code, or `unknown` |
| `slack.api.error_code` | string | The Slack API error code \(conditional\) |
| `operation.success` | boolean | Whether the operation completed without an error |

##### agents.slack.api.request.duration

**Type:** Histogram **Unit:** ms **Description:** Duration of outbound Slack Web API requests in milliseconds.

| Attribute | Type | Description |
| --- | --- | --- |
| `slack.api.method` | string | The Slack Web API method |
| `http.method` | string | Always `POST` |
| `http.status_code` | string | The HTTP response status code, or `unknown` |
| `slack.api.error_code` | string | The Slack API error code \(conditional\) |
| `operation.success` | boolean | Whether the operation completed without an error |

### JavaScript span constants reference

All span names are available as constants in the `@microsoft/agents-telemetry` package:

```typescript
import { SpanNames } from '@microsoft/agents-telemetry';

// CloudAdapter
SpanNames.ADAPTER_PROCESS                  // 'agents.adapter.process'
SpanNames.ADAPTER_SEND_ACTIVITIES          // 'agents.adapter.send_activities'
SpanNames.ADAPTER_UPDATE_ACTIVITY          // 'agents.adapter.update_activity'
SpanNames.ADAPTER_DELETE_ACTIVITY          // 'agents.adapter.delete_activity'
SpanNames.ADAPTER_CONTINUE_CONVERSATION    // 'agents.adapter.continue_conversation'
SpanNames.ADAPTER_CREATE_CONNECTOR_CLIENT  // 'agents.adapter.create_connector_client'
SpanNames.ADAPTER_CREATE_USER_TOKEN_CLIENT // 'agents.adapter.create_user_token_client'

// AgentApplication
SpanNames.AGENTS_APP_RUN               // 'agents.app.run'
SpanNames.AGENTS_APP_ROUTE_HANDLER     // 'agents.app.route_handler'
SpanNames.AGENTS_APP_BEFORE_TURN       // 'agents.app.before_turn'
SpanNames.AGENTS_APP_AFTER_TURN        // 'agents.app.after_turn'
SpanNames.AGENTS_APP_DOWNLOAD_FILES    // 'agents.app.download_files'
SpanNames.AGENTS_APP_TYPING_INDICATOR  // 'agents.app.typing_indicator'

// ConnectorClient
SpanNames.CONNECTOR_SEND_TO_CONVERSATION   // 'agents.connector.send_to_conversation'
SpanNames.CONNECTOR_REPLY_TO_ACTIVITY      // 'agents.connector.reply_to_activity'
SpanNames.CONNECTOR_UPDATE_ACTIVITY        // 'agents.connector.update_activity'
SpanNames.CONNECTOR_DELETE_ACTIVITY        // 'agents.connector.delete_activity'
SpanNames.CONNECTOR_CREATE_CONVERSATION    // 'agents.connector.create_conversation'
SpanNames.CONNECTOR_GET_CONVERSATIONS      // 'agents.connector.get_conversations'
SpanNames.CONNECTOR_GET_CONVERSATION_MEMBER // 'agents.connector.get_conversation_member'
SpanNames.CONNECTOR_UPLOAD_ATTACHMENT      // 'agents.connector.upload_attachment'
SpanNames.CONNECTOR_GET_ATTACHMENT         // 'agents.connector.get_attachment'
SpanNames.CONNECTOR_GET_ATTACHMENT_INFO    // 'agents.connector.get_attachment_info'

// Storage
SpanNames.STORAGE_READ                 // 'agents.storage.read'
SpanNames.STORAGE_WRITE                // 'agents.storage.write'
SpanNames.STORAGE_DELETE               // 'agents.storage.delete'

// AgentClient
SpanNames.AGENT_CLIENT_POST_ACTIVITY   // 'agents.agent_client.post_activity'

// Authentication
SpanNames.AUTHENTICATION_GET_ACCESS_TOKEN            // 'agents.authentication.get_access_token'
SpanNames.AUTHENTICATION_ACQUIRE_TOKEN_ON_BEHALF_OF  // 'agents.authentication.acquire_token_on_behalf_of'
SpanNames.AUTHENTICATION_GET_AGENTIC_INSTANCE_TOKEN  // 'agents.authentication.get_agentic_instance_token'
SpanNames.AUTHENTICATION_GET_AGENTIC_USER_TOKEN      // 'agents.authentication.get_agentic_user_token'

// Authorization
SpanNames.AUTHORIZATION_AGENTIC_TOKEN          // 'agents.authorization.agentic_token'
SpanNames.AUTHORIZATION_AZURE_BOT_TOKEN        // 'agents.authorization.azure_bot_token'
SpanNames.AUTHORIZATION_AZURE_BOT_OBO_TOKEN    // 'agents.authorization.azure_bot_obo_token'
SpanNames.AUTHORIZATION_AZURE_BOT_SIGNIN       // 'agents.authorization.azure_bot_signin'
SpanNames.AUTHORIZATION_AZURE_BOT_SIGNOUT      // 'agents.authorization.azure_bot_signout'

// UserTokenClient
SpanNames.USER_TOKEN_CLIENT_GET_USER_TOKEN              // 'agents.user_token_client.get_user_token'
SpanNames.USER_TOKEN_CLIENT_SIGN_OUT                    // 'agents.user_token_client.sign_out'
SpanNames.USER_TOKEN_CLIENT_GET_SIGN_IN_RESOURCE        // 'agents.user_token_client.get_sign_in_resource'
SpanNames.USER_TOKEN_CLIENT_EXCHANGE_TOKEN               // 'agents.user_token_client.exchange_token'
SpanNames.USER_TOKEN_CLIENT_GET_TOKEN_OR_SIGN_IN_RESOURCE // 'agents.user_token_client.get_token_or_sign_in_resource'
SpanNames.USER_TOKEN_CLIENT_GET_TOKEN_STATUS             // 'agents.user_token_client.get_token_status'
SpanNames.USER_TOKEN_CLIENT_GET_AAD_TOKENS               // 'agents.user_token_client.get_aad_tokens'

// Proactive
SpanNames.PROACTIVE_STORE_CONVERSATION       // 'agents.proactive.store_conversation'
SpanNames.PROACTIVE_GET_CONVERSATION         // 'agents.proactive.get_conversation'
SpanNames.PROACTIVE_GET_CONVERSATION_OR_THROW // 'agents.proactive.get_conversation_or_throw'
SpanNames.PROACTIVE_DELETE_CONVERSATION      // 'agents.proactive.delete_conversation'
SpanNames.PROACTIVE_SEND_ACTIVITY            // 'agents.proactive.send_activity'
SpanNames.PROACTIVE_CONTINUE_CONVERSATION    // 'agents.proactive.continue_conversation'
SpanNames.PROACTIVE_CREATE_CONVERSATION      // 'agents.proactive.create_conversation'

// TurnContext
SpanNames.TURN_SEND_ACTIVITIES         // 'agents.turn.send_activities'

// Dialogs
SpanNames.DIALOGS_RUN                  // 'agents.dialogs.run'
SpanNames.DIALOGS_CONTEXT_BEGIN        // 'agents.dialogs.context.begin'
SpanNames.DIALOGS_CONTEXT_CONTINUE     // 'agents.dialogs.context.continue'
SpanNames.DIALOGS_CONTEXT_END          // 'agents.dialogs.context.end'
SpanNames.DIALOGS_CONTEXT_REPLACE      // 'agents.dialogs.context.replace'
SpanNames.DIALOGS_CONTEXT_CANCEL_ALL   // 'agents.dialogs.context.cancel_all'

// Copilot Studio Client
SpanNames.COPILOT_START_CONVERSATION   // 'agents.copilot_client.start_conversation'
SpanNames.COPILOT_SEND_ACTIVITY        // 'agents.copilot_client.send_activity'
SpanNames.COPILOT_POST_REQUEST         // 'agents.copilot_client.post_request'
SpanNames.COPILOT_CREATE_CONNECTION    // 'agents.copilot_client.webchat.create_connection'
SpanNames.COPILOT_WEBCHAT_START_CONVERSATION // 'agents.copilot_client.webchat.start_conversation'
SpanNames.COPILOT_WEBCHAT_POST_ACTIVITY      // 'agents.copilot_client.webchat.post_activity'
SpanNames.COPILOT_WEBCHAT_RECEIVE_ACTIVITY   // 'agents.copilot_client.webchat.receive_activity'
SpanNames.COPILOT_WEBCHAT_END_CONNECTION     // 'agents.copilot_client.webchat.end_connection'
SpanNames.COPILOT_EXECUTE_STREAMING    // 'agents.copilot_client.execute_streaming'
SpanNames.COPILOT_SUBSCRIBE_ASYNC      // 'agents.copilot_client.subscribe_async'

// Named Pipe
SpanNames.NAMED_PIPE_CONNECT           // 'agents.named_pipe.connect'
SpanNames.NAMED_PIPE_DISPATCH          // 'agents.named_pipe.dispatch'
SpanNames.NAMED_PIPE_SEND              // 'agents.named_pipe.send'

// Slack
SpanNames.SLACK_API_CALL               // 'agents.slack.api.call'
```

### JavaScript metric constants reference

All metric names are available as constants:

```typescript
import { MetricNames } from '@microsoft/agents-telemetry';

// CloudAdapter
MetricNames.ADAPTER_PROCESS_DURATION      // 'agents.adapter.process.duration'

// Activity counters
MetricNames.ACTIVITIES_RECEIVED           // 'agents.activities.received'
MetricNames.ACTIVITIES_SENT               // 'agents.activities.sent'
MetricNames.ACTIVITIES_UPDATED            // 'agents.activities.updated'
MetricNames.ACTIVITIES_DELETED            // 'agents.activities.deleted'

// Connector metrics
MetricNames.CONNECTOR_REQUESTS            // 'agents.connector.request.count'
MetricNames.CONNECTOR_REQUEST_DURATION    // 'agents.connector.request.duration'

// AgentClient metrics
MetricNames.AGENT_CLIENT_REQUESTS         // 'agents.agent_client.request.count'
MetricNames.AGENT_CLIENT_REQUEST_DURATION // 'agents.agent_client.request.duration'

// Turn metrics
MetricNames.TURNS_COUNT                   // 'agents.turn.count'
MetricNames.TURNS_ERRORS                  // 'agents.turn.error.count'
MetricNames.TURN_DURATION                 // 'agents.turn.duration'

// Dialog metrics
MetricNames.DIALOGS_CONTEXT_COUNT         // 'agents.dialogs.context.count'
MetricNames.DIALOGS_CONTEXT_DURATION      // 'agents.dialogs.context.duration'

// Storage metrics
MetricNames.STORAGE_OPERATION_DURATION    // 'agents.storage.operation.duration'

// Authentication metrics
MetricNames.AUTH_TOKEN_REQUEST_COUNT      // 'agents.auth.token.request.count'
MetricNames.AUTH_TOKEN_DURATION           // 'agents.auth.token.duration'

// UserTokenClient metrics
MetricNames.USER_TOKEN_CLIENT_REQUESTS          // 'agents.user_token_client.request.count'
MetricNames.USER_TOKEN_CLIENT_REQUEST_DURATION  // 'agents.user_token_client.request.duration'

// Proactive metrics
MetricNames.PROACTIVE_OPERATION_COUNT     // 'agents.proactive.operation.count'
MetricNames.PROACTIVE_OPERATION_DURATION  // 'agents.proactive.operation.duration'

// Copilot Studio Client metrics
MetricNames.CSC_ACTIVITIES_RECEIVED       // 'agents.copilot_client.activities.received'
MetricNames.CSC_ACTIVITIES_SENT           // 'agents.copilot_client.activities.sent'
MetricNames.CSC_CONVERSATIONS_STARTED     // 'agents.copilot_client.conversations.started'
MetricNames.CSC_WEBCHAT_CONNECTIONS       // 'agents.copilot_client.webchat.connection.count'
MetricNames.CSC_REQUEST_COUNT             // 'agents.copilot_client.request.count'
MetricNames.CSC_REQUEST_ERRORS            // 'agents.copilot_client.request.error.count'
MetricNames.CSC_STREAM_DURATION           // 'agents.copilot_client.stream.duration'
MetricNames.CSC_REQUEST_DURATION          // 'agents.copilot_client.request.duration'
MetricNames.CSC_EXECUTE_STREAMING         // 'agents.copilot_client.execute_streaming.count'
MetricNames.CSC_SUBSCRIBE_ASYNC           // 'agents.copilot_client.subscribe_async.count'
MetricNames.CSC_SUBSCRIBE_EVENT           // 'agents.copilot_client.subscribe_event.count'

// Named Pipe metrics
MetricNames.NAMED_PIPE_CONNECTIONS         // 'agents.named_pipe.connection.count'
MetricNames.NAMED_PIPE_DISPATCHES          // 'agents.named_pipe.dispatch.count'
MetricNames.NAMED_PIPE_DISPATCH_DURATION   // 'agents.named_pipe.dispatch.duration'
MetricNames.NAMED_PIPE_DISPATCH_ERRORS     // 'agents.named_pipe.dispatch.error.count'
MetricNames.NAMED_PIPE_SENDS               // 'agents.named_pipe.send.count'
MetricNames.NAMED_PIPE_SEND_DURATION       // 'agents.named_pipe.send.duration'

// Slack metrics
MetricNames.SLACK_API_REQUESTS             // 'agents.slack.api.request.count'
MetricNames.SLACK_API_REQUEST_DURATION     // 'agents.slack.api.request.duration'
```

### JavaScript log records

The `@microsoft/agents-telemetry` `debug(namespace)` helper always writes through the SDK's `debug` logger. When the optional `@opentelemetry/api-logs` package is available, it also emits an OpenTelemetry log record through the logger named by `namespace`.

| Field | Value |
| --- | --- |
| Severity number | OpenTelemetry `DEBUG`, `INFO`, `WARN`, or `ERROR` |
| Severity text | `DEBUG`, `INFO`, `WARN`, or `ERROR` |
| Body | The message followed by serialized extra arguments |
| `log.namespace` | The logger namespace passed to `debug(namespace)` |
| `log.level` | Lowercase `debug`, `info`, `warn`, or `error` |

An `Error` argument is serialized as its name and message. Other non-string arguments are JSON-serialized when possible. Applications must configure an OpenTelemetry logger provider and processor/exporter to export these records. If `@opentelemetry/api-logs` is absent, tracing and metrics can still operate through `@opentelemetry/api`, while log emission falls back to the SDK's `debug` output only.

## C# telemetry

This section documents the traces and metrics emitted by the C# Agents SDK.

### System.Diagnostics integration

The C# SDK has **no dependency on OpenTelemetry**. All instrumentation is built on top of `System.Diagnostics`, the distributed-tracing and metrics layer built into the .NET runtime:

- Spans are `System.Diagnostics.Activity` objects created from a shared `ActivitySource`.
- Metrics are `Counter<T>` and `Histogram<T>` instruments created from a shared `Meter`.

Both are published under the source name **`Microsoft.Agents.Core`**. Any listener subscribed to that name receives the telemetry—OpenTelemetry is just one possible listener.

```csharp
// The single source used for all SDK traces and metrics
AgentsTelemetry.SourceName    // "Microsoft.Agents.Core"
AgentsTelemetry.SourceVersion // Assembly file version
AgentsTelemetry.ActivitySource // System.Diagnostics.ActivitySource
AgentsTelemetry.Meter          // System.Diagnostics.Metrics.Meter
```

This design means the SDK integrates naturally with any observability tool that understands `System.Diagnostics`, not only with the OpenTelemetry SDK.

### C# setup

Add the OpenTelemetry NuGet packages to your agent project:

```dotnetcli
dotnet add package OpenTelemetry.Extensions.Hosting
dotnet add package OpenTelemetry.Instrumentation.AspNetCore
dotnet add package OpenTelemetry.Exporter.OpenTelemetryProtocol
```

Then subscribe to the `Microsoft.Agents.Core` source and meter in `Program.cs`:

```csharp
using Microsoft.Agents.Core.Telemetry;
using Microsoft.Extensions.DependencyInjection;
using OpenTelemetry.Metrics;
using OpenTelemetry.Resources;
using OpenTelemetry.Trace;

builder.Services.AddOpenTelemetry()
    .ConfigureResource(r => r.AddService(
        serviceName: AgentsTelemetry.SourceName,
        serviceVersion: AgentsTelemetry.SourceVersion))
    .WithTracing(tracing => tracing
        .AddSource(AgentsTelemetry.SourceName)
        .AddAspNetCoreInstrumentation()
        .AddOtlpExporter())
    .WithMetrics(metrics => metrics
        .AddMeter(AgentsTelemetry.SourceName)
        .AddAspNetCoreInstrumentation()
        .AddOtlpExporter());
```

Because the SDK emits standard `System.Diagnostics` signals, you can substitute any exporter \(Console, Azure Monitor, Jaeger, Prometheus, etc.\) without changing the agent code.

Learn more in the [TelemetryAgent sample](https://github.com/microsoft/Agents-for-net/tree/main/src/samples/TelemetryAgent) and its shared [OpenTelemetry configuration helper](https://github.com/microsoft/Agents-for-net/blob/main/src/samples/Shared/AgentOtelExtension.cs).

### C# spans

In the C# SDK, what this document calls a "span" is a `System.Diagnostics.Activity` created from `AgentsTelemetry.ActivitySource`. The term "span" is used here for consistency with the JavaScript and Python SDKs, whose observability is built directly on OpenTelemetry. The underlying `System.Diagnostics.Activity` objects are fully compatible with OpenTelemetry when a listener such as the OpenTelemetry .NET SDK is configured.

#### C# CloudAdapter spans

`CloudAdapter` spans cover incoming activity processing, response handling, and connector creation.

##### agents.adapter.process

Main processing span for each incoming activity.

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.type` | string | The type of activity \(message, conversationUpdate, etc.\) |
| `activity.channel_id` | string | The channel the activity originated from |
| `activity.delivery_mode` | string | The delivery mode of the activity |
| `activity.conversation.id` | string | The conversation identifier |
| `activity.is_agentic_request` | boolean | Whether this is an agent-to-agent request |

##### agents.adapter.write\_response

Span used by response handlers for streamed activities, A2A responses, and the final `invoke` or `expectReplies` response.

| Attribute | Type | Description |
| --- | --- | --- |
| `activities.count` | integer | Number of activities in the response |
| `activity.conversation.id` | string | The conversation identifier |

##### agents.adapter.send\_activities

Span for sending one or more activities through the adapter.

| Attribute | Type | Description |
| --- | --- | --- |
| `activities.count` | integer | Number of activities being sent |
| `activity.conversation.id` | string | The conversation identifier |

##### agents.adapter.update\_activity

Span for updating an existing activity.

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.id` | string | The ID of the activity being updated |
| `activity.conversation.id` | string | The conversation identifier |

##### agents.adapter.delete\_activity

Span for deleting an activity.

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.type` | string | Always `"event"`; taken from the synthesized continuation activity |
| `activity.conversation.id` | string | The conversation identifier |

##### agents.adapter.continue\_conversation

Span for continuing a conversation proactively.

| Attribute | Type | Description |
| --- | --- | --- |
| `agent.app_id` | string | The agent's application ID |
| `activity.conversation.id` | string | The conversation identifier |
| `activity.is_agentic_request` | boolean | Whether this is an agentic request |

##### agents.adapter.create\_connector\_client

Span for creating a connector client instance.

| Attribute | Type | Description |
| --- | --- | --- |
| `service_url` | string | The Bot Framework service URL |
| `auth.scopes` | string | Comma-separated authentication scopes |
| `activity.is_agentic_request` | boolean | Whether this is for an agentic request |

##### agents.adapter.create\_user\_token\_client

Span for creating a user token client instance.

| Attribute | Type | Description |
| --- | --- | --- |
| `agents.token_service.endpoint` | string | The token service endpoint URL |

#### C# AgentApplication spans

`AgentApplication` spans cover turn execution, route handlers, and lifecycle events.

##### agents.app.run

Main execution span for a turn through `AgentApplication`.

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.type` | string | The type of activity being processed |
| `activity.name` | string | The name of the activity |
| `activity.channel_id` | string | The channel identifier |
| `activity.conversation.id` | string | The conversation identifier |
| `activity.id` | string | The activity identifier |
| `route.authorized` | boolean | Whether the request was authorized |
| `route.matched` | boolean | Whether a route handler matched the activity |

##### agents.app.route\_handler

Child span for executing a matched route handler.

| Attribute | Type | Description |
| --- | --- | --- |
| `route.is_invoke` | boolean | Whether this is an invoke activity route |
| `route.is_agentic` | boolean | Whether this is an agentic route |

##### agents.app.before\_turn

Span for before-turn handler execution. No additional attributes.

##### agents.app.after\_turn

Span for after-turn handler execution. No additional attributes.

##### agents.app.download\_files

Span for downloading file attachments.

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.attachments.count` | integer | Number of attachments on the activity |

##### agents.app.typing\_indicator

Span for sending an automatic typing indicator during a turn.

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.type` | string | Always `"typing"` |
| `activity.channel_id` | string | The channel identifier |
| `activity.conversation.id` | string | The conversation identifier |

#### C# TurnContext spans

`TurnContext` emits a span when it sends activities.

##### agents.turn.send\_activities

Span emitted by `TurnContext` each time activities are sent.

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.conversation.id` | string | The conversation identifier |

#### C# ConnectorClient spans

`ConnectorClient` spans cover outbound connector operations.

##### agents.connector.reply\_to\_activity

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.conversation.id` | string | The conversation identifier |
| `activity.id` | string | The activity being replied to |

##### agents.connector.send\_to\_conversation

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.conversation.id` | string | The target conversation identifier |
| `activity.id` | string | The activity identifier \(when provided\) |

##### agents.connector.update\_activity

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.conversation.id` | string | The conversation identifier |
| `activity.id` | string | The activity being updated |

##### agents.connector.delete\_activity

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.conversation.id` | string | The conversation identifier |
| `activity.id` | string | The activity being deleted |

##### agents.connector.create\_conversation

No span-level attributes.

##### agents.connector.get\_conversations

No span-level attributes.

##### agents.connector.get\_conversation\_members

This span covers both `GetConversationMembersAsync` and the singular `GetConversationMemberAsync` operation.

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.conversation.id` | string | The conversation identifier |

##### agents.connector.upload\_attachment

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.conversation.id` | string | The conversation identifier |

##### agents.connector.get\_attachment\_info

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.attachment.id` | string | The attachment identifier |

##### agents.connector.get\_attachment

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.attachment.id` | string | The attachment identifier |
| `view.id` | string | The view identifier |

#### C# UserTokenClient spans

User token client spans record `auth.connection.name`, `user.id`, and `activity.channel_id` when the scope receives those values. Missing channel IDs are recorded as `"unknown"`.

##### agents.user\_token\_client.get\_user\_token

| Attribute | Type | Description |
| --- | --- | --- |
| `auth.connection.name` | string | The OAuth connection name |
| `user.id` | string | The user identifier |
| `activity.channel_id` | string | The channel identifier |

##### agents.user\_token\_client.sign\_out

| Attribute | Type | Description |
| --- | --- | --- |
| `auth.connection.name` | string | The OAuth connection name |
| `user.id` | string | The user identifier |
| `activity.channel_id` | string | The channel identifier |

##### agents.user\_token\_client.get\_sign\_in\_resource

| Attribute | Type | Description |
| --- | --- | --- |
| `auth.connection.name` | string | The OAuth connection name |
| `user.id` | string | The user identifier |
| `activity.channel_id` | string | The channel identifier |

##### agents.user\_token\_client.exchange\_token

| Attribute | Type | Description |
| --- | --- | --- |
| `auth.connection.name` | string | The OAuth connection name |
| `user.id` | string | The user identifier |
| `activity.channel_id` | string | The channel identifier |

##### agents.user\_token\_client.get\_token\_or\_sign\_in\_resource

| Attribute | Type | Description |
| --- | --- | --- |
| `auth.connection.name` | string | The OAuth connection name |
| `user.id` | string | The user identifier |
| `activity.channel_id` | string | The channel identifier |

##### agents.user\_token\_client.get\_token\_status

| Attribute | Type | Description |
| --- | --- | --- |
| `user.id` | string | The user identifier |
| `activity.channel_id` | string | The channel identifier |

##### agents.user\_token\_client.get\_aad\_tokens

| Attribute | Type | Description |
| --- | --- | --- |
| `auth.connection.name` | string | The OAuth connection name |
| `user.id` | string | The user identifier |
| `activity.channel_id` | string | The channel identifier |

#### C# storage spans

`BlobsStorage` and `CosmosDbPartitionedStorage` emit these spans.

##### agents.storage.read

| Attribute | Type | Description |
| --- | --- | --- |
| `storage.keys.count` | integer | Number of keys being read |
| `storage.operation` | string | Always `"read"` |

##### agents.storage.write

| Attribute | Type | Description |
| --- | --- | --- |
| `storage.keys.count` | integer | Number of keys being written |
| `storage.operation` | string | Always `"write"` |

##### agents.storage.delete

| Attribute | Type | Description |
| --- | --- | --- |
| `storage.keys.count` | integer | Number of keys being deleted |
| `storage.operation` | string | Always `"delete"` |

#### C# authentication spans

Authentication spans cover access token acquisition and agentic token operations.

##### agents.authentication.get\_access\_token

| Attribute | Type | Description |
| --- | --- | --- |
| `auth.method` | string | The authentication method—value is `AuthTypes.ToString()` \(for example, `"ClientSecret"`, `"Certificate"`, `"CertificateSubjectName"`, `"UserManagedIdentity"`, `"SystemManagedIdentity"`, `"WorkloadIdentity"`, `"FederatedCredentials"`, or `"IdentityProxyManager"`\) |
| `auth.scopes` | string | Comma-separated authentication scopes; `"unknown"` when null or empty |

##### agents.authentication.acquire\_token\_on\_behalf\_of

| Attribute | Type | Description |
| --- | --- | --- |
| `auth.method` | string | Always `"obo"` |
| `auth.scopes` | string | Comma-separated authentication scopes; `"unknown"` when null or empty |

##### agents.authentication.get\_agentic\_instance\_token

| Attribute | Type | Description |
| --- | --- | --- |
| `auth.method` | string | Always `"agentic_instance"` |
| `agentic.instance_id` | string | The agentic application instance ID |

##### agents.authentication.get\_agentic\_user\_token

| Attribute | Type | Description |
| --- | --- | --- |
| `auth.method` | string | Always `"agentic_user"` |
| `agentic.instance_id` | string | The agentic application instance ID |
| `agentic.user_id` | string | The agentic user ID |
| `auth.scopes` | string | Comma-separated authentication scopes; `"unknown"` when null or empty |

#### C# authorization spans

Authorization spans cover user token retrieval, sign-in, and sign-out.

##### agents.authorization.agentic\_token

| Attribute | Type | Description |
| --- | --- | --- |
| `auth.handler.id` | string | The authorization handler identifier |
| `auth.connection.name` | string | The connection name \(omitted if not provided\) |
| `auth.scopes` | string | Comma-separated scopes \(omitted if not provided\) |

##### agents.authorization.azure\_bot\_token

| Attribute | Type | Description |
| --- | --- | --- |
| `auth.handler.id` | string | The authorization handler identifier |
| `auth.connection.name` | string | The connection name \(omitted if not provided\) |
| `auth.scopes` | string | Comma-separated scopes \(omitted if not provided\) |

##### agents.authorization.azure\_bot\_signin

| Attribute | Type | Description |
| --- | --- | --- |
| `auth.handler.id` | string | The authorization handler identifier |
| `auth.connection.name` | string | The connection name \(omitted if not provided\) |
| `auth.scopes` | string | Comma-separated scopes \(omitted if not provided\) |
| `activity.channel_id` | string | The channel identifier |

##### agents.authorization.azure\_bot\_signout

| Attribute | Type | Description |
| --- | --- | --- |
| `auth.handler.id` | string | The authorization handler identifier |
| `auth.connection.name` | string | The connection name |
| `activity.channel_id` | string | The channel identifier |

#### C# proactive spans

Proactive spans cover stored conversation references and messages sent outside a user-initiated turn.

##### agents.proactive.store\_conversation

Span for storing a conversation reference for later proactive use.

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.conversation.id` | string | The conversation identifier being stored |

##### agents.proactive.get\_conversation

Span for retrieving a stored conversation reference.

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.conversation.id` | string | The conversation identifier being retrieved |
| `proactive.conversation.found` | boolean | Whether the conversation was found |

##### agents.proactive.delete\_conversation

Span for deleting a stored conversation reference.

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.conversation.id` | string | The conversation identifier being deleted |

##### agents.proactive.send\_activity

Span for sending an activity proactively to an existing conversation. Supports an `ActivityLink` for telemetry correlation with the originating turn.

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.conversation.id` | string | The target conversation identifier |
| `activity.type` | string | The type of the activity being sent |
| `activity.channel_id` | string | The channel identifier |

##### agents.proactive.continue\_conversation

Span for continuing a stored conversation proactively. Supports an `ActivityLink` for telemetry correlation.

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.conversation.id` | string | The target conversation identifier |
| `activity.type` | string | The type of the continuation activity |
| `activity.channel_id` | string | The channel identifier |

##### agents.proactive.create\_conversation

Span for creating a new proactive conversation.

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.channel_id` | string | The target channel identifier |
| `proactive.members.count` | integer | Number of members in the conversation |

### C# error handling in spans

`TelemetryScope.SetError`, `Wrap`, and `WrapAsync` provide the following error recording behavior when used by an instrumented operation:

1. The span status is set to `Error` with the exception message.
2. An `exception` event is added to the `System.Diagnostics.Activity` with `exception.type`, `exception.message`, and `exception.stacktrace` tags, following OpenTelemetry semantic conventions.

On successful completion, the activity status remains `Unset`. The SDK doesn't explicitly set it to `Ok`.

### C# metrics

All metric instruments are created from `AgentsTelemetry.Meter` \(name `"Microsoft.Agents.Core"`\).

#### C# activity counters

Activity counters track incoming activities, outbound activities, updates, and deletions.

##### agents.activities.received

**Type:** Counter  
**Unit:** activity  
**Description:** Total activities received by the adapter.

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.type` | string | Activity type |
| `activity.channel_id` | string | Channel identifier |

##### agents.activities.sent

**Type:** Counter  
**Unit:** activity  
**Description:** Total outbound activities sent.

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.type` | string | Activity type |
| `activity.channel_id` | `ChannelId` | Raw `ChannelId` value; exporter representation can vary |

##### agents.activities.updated

**Type:** Counter  
**Unit:** activity  
**Description:** Total activity updates.

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.channel_id` | `ChannelId` | Raw `ChannelId` value; exporter representation can vary |

##### agents.activities.deleted

**Type:** Counter  
**Unit:** activity  
**Description:** Total activity deletions.

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.channel_id` | `ChannelId` | Raw `ChannelId` value; exporter representation can vary |

#### C# turn metrics

Turn metrics describe turn counts, errors, and end-to-end duration.

##### agents.turn.count

**Type:** Counter  
**Unit:** turn  
**Description:** Counter intended to track successfully processed turns.

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.type` | string | Activity type |
| `activity.channel_id` | string | Channel identifier |

##### agents.turn.error.count

**Type:** Counter  
**Unit:** turn  
**Description:** Counter intended to track turns that resulted in an error.

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.type` | string | Activity type |
| `activity.channel_id` | string | Channel identifier |

##### agents.turn.duration

**Type:** Histogram  
**Unit:** ms  
**Description:** End-to-end turn processing duration.

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.type` | string | Activity type |
| `activity.channel_id` | string | Channel identifier |

#### C# adapter metrics

Adapter metrics measure incoming activity processing duration.

##### agents.adapter.process.duration

**Type:** Histogram  
**Unit:** ms  
**Description:** Duration of the adapter process method.

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.type` | string | Activity type |
| `activity.channel_id` | string | Channel identifier |

#### C# connector metrics

Connector metrics count outbound HTTP requests and measure their duration.

##### agents.connector.request.count

**Type:** Counter  
**Unit:** request  
**Description:** Total outbound connector HTTP requests.

*No metric-level attributes.*

##### agents.connector.request.duration

**Type:** Histogram  
**Unit:** ms  
**Description:** Duration of outbound connector HTTP requests.

*No metric-level attributes.*

#### C# UserTokenClient metrics

User token client metrics count outbound HTTP requests and measure their duration.

##### agents.user\_token\_client.request.count

**Type:** Counter  
**Unit:** request  
**Description:** Total outbound user token client HTTP requests.

*No metric-level attributes.*

##### agents.user\_token\_client.request.duration

**Type:** Histogram  
**Unit:** ms  
**Description:** Duration of outbound user token client HTTP requests.

*No metric-level attributes.*

#### C# storage metrics

Storage metrics count read, write, and delete operations and measure their duration.

##### agents.storage.operation.total

**Type:** Counter  
**Unit:** operation  
**Description:** Total storage operations performed.

| Attribute | Type | Description |
| --- | --- | --- |
| `storage.operation` | string | `"read"`, `"write"`, or `"delete"` |

##### agents.storage.operation.duration

**Type:** Histogram  
**Unit:** ms  
**Description:** Duration of storage operations.

| Attribute | Type | Description |
| --- | --- | --- |
| `storage.operation` | string | `"read"`, `"write"`, or `"delete"` |

#### C# authentication metrics

Authentication metrics count token requests and measure their duration.

##### agents.auth.token.request.count

**Type:** Counter  
**Unit:** request  
**Description:** Total token requests made to the authentication service.

| Attribute | Type | Description |
| --- | --- | --- |
| `auth.method` | string | Authentication method \(e.g., `"ClientSecret"`, `"Certificate"`, `"obo"`, `"agentic_instance"`, `"agentic_user"`\) |

##### agents.auth.token.request.duration

**Type:** Histogram  
**Unit:** ms  
**Description:** Duration of token requests to the authentication service.

| Attribute | Type | Description |
| --- | --- | --- |
| `auth.method` | string | Authentication method |

### C# span constants reference

Span name constants are defined across several `Constants` classes in the SDK:

Note

The SDK's span name constants are `internal`, not public APIs. The following list shows their string values for reference.

```csharp
// CloudAdapter
"agents.adapter.process"
"agents.adapter.write_response"
"agents.adapter.send_activities"
"agents.adapter.update_activity"
"agents.adapter.delete_activity"
"agents.adapter.continue_conversation"
"agents.adapter.create_connector_client"
"agents.adapter.create_user_token_client"

// AgentApplication
"agents.app.run"
"agents.app.route_handler"
"agents.app.before_turn"
"agents.app.after_turn"
"agents.app.download_files"
"agents.app.typing_indicator"

// TurnContext
"agents.turn.send_activities"

// ConnectorClient
"agents.connector.reply_to_activity"
"agents.connector.send_to_conversation"
"agents.connector.update_activity"
"agents.connector.delete_activity"
"agents.connector.create_conversation"
"agents.connector.get_conversations"
"agents.connector.get_conversation_members"
"agents.connector.upload_attachment"
"agents.connector.get_attachment_info"
"agents.connector.get_attachment"

// UserTokenClient
"agents.user_token_client.get_user_token"
"agents.user_token_client.sign_out"
"agents.user_token_client.get_sign_in_resource"
"agents.user_token_client.exchange_token"
"agents.user_token_client.get_token_or_sign_in_resource"
"agents.user_token_client.get_token_status"
"agents.user_token_client.get_aad_tokens"

// Storage
"agents.storage.read"
"agents.storage.write"
"agents.storage.delete"

// Authentication
"agents.authentication.get_access_token"
"agents.authentication.acquire_token_on_behalf_of"
"agents.authentication.get_agentic_instance_token"
"agents.authentication.get_agentic_user_token"

// Authorization
"agents.authorization.agentic_token"
"agents.authorization.azure_bot_token"
"agents.authorization.azure_bot_signin"
"agents.authorization.azure_bot_signout"

// Proactive
"agents.proactive.store_conversation"
"agents.proactive.get_conversation"
"agents.proactive.delete_conversation"
"agents.proactive.send_activity"
"agents.proactive.continue_conversation"
"agents.proactive.create_conversation"
```

### C# attribute constants reference

All attribute key strings are defined in `Microsoft.Agents.Core.Telemetry.TagNames`:

```csharp
using Microsoft.Agents.Core.Telemetry;

TagNames.ActivityDeliveryMode   // "activity.delivery_mode"
TagNames.ActivityChannelId      // "activity.channel_id"
TagNames.ActivityId             // "activity.id"
TagNames.ActivityName           // "activity.name"
TagNames.ActivityCount          // "activities.count"
TagNames.ActivityType           // "activity.type"
TagNames.AgenticUserId          // "agentic.user_id"
TagNames.AgenticInstanceId      // "agentic.instance_id"
TagNames.AppId                  // "agent.app_id"
TagNames.AttachmentId           // "activity.attachment.id"
TagNames.AttachmentCount        // "activity.attachments.count"
TagNames.AuthHandlerId          // "auth.handler.id"
TagNames.AuthMethod             // "auth.method"
TagNames.AuthScopes             // "auth.scopes"
TagNames.AuthSuccess            // "auth.success"
TagNames.ConversationFound      // "proactive.conversation.found"
TagNames.ConversationId         // "activity.conversation.id"
TagNames.ExchangeConnection     // "auth.connection.name"
TagNames.HttpMethod             // "http.method"
TagNames.HttpStatusCode         // "http.status_code"
TagNames.IsAgentic              // "activity.is_agentic_request"
TagNames.KeyCount               // "storage.keys.count"
TagNames.MembersCount           // "proactive.members.count"
TagNames.Operation              // "operation"
TagNames.RouteAuthorized        // "route.authorized"
TagNames.RouteIsInvoke          // "route.is_invoke"
TagNames.RouteIsAgentic         // "route.is_agentic"
TagNames.RouteMatched           // "route.matched"
TagNames.ServiceUrl             // "service_url"
TagNames.StorageOperation       // "storage.operation"
TagNames.TokenServiceEndpoint   // "agents.token_service.endpoint"
TagNames.UserId                 // "user.id"
TagNames.ViewId                 // "view.id"
```

## Python telemetry

This section documents the OpenTelemetry spans and metrics emitted by the Python Agents SDK \(`microsoft-agents-hosting-core`\).

Note

The Python SDK uses different attribute key strings than the JavaScript SDK in several places. Differences are noted in each span and metric table.

### Python setup

`microsoft-agents-hosting-core` requires Python 3.10 or later and installs `opentelemetry-api` and `opentelemetry-sdk`. Install an exporter for your telemetry backend:

```bash
# For exporting to an OTLP collector (Jaeger, Grafana, Azure Monitor, etc.)
pip install opentelemetry-exporter-otlp
```

Configure providers **before** your agent starts processing requests:

```python
from opentelemetry import metrics, trace
from opentelemetry.sdk.metrics import MeterProvider
from opentelemetry.sdk.metrics.export import PeriodicExportingMetricReader
from opentelemetry.sdk.resources import Resource
from opentelemetry.sdk.trace import TracerProvider
from opentelemetry.sdk.trace.export import SimpleSpanProcessor
from opentelemetry.exporter.otlp.proto.grpc.trace_exporter import OTLPSpanExporter
from opentelemetry.exporter.otlp.proto.grpc.metric_exporter import OTLPMetricExporter

endpoint = "http://localhost:4317/"  # your OTLP collector

resource = Resource.create({
    "service.name": "my-agent",
    "service.version": "1.0.0",
})

# Tracing
tracer_provider = TracerProvider(resource=resource)
tracer_provider.add_span_processor(SimpleSpanProcessor(OTLPSpanExporter(endpoint=endpoint)))
trace.set_tracer_provider(tracer_provider)

# Metrics
meter_provider = MeterProvider(
    resource=resource,
    metric_readers=[PeriodicExportingMetricReader(OTLPMetricExporter(endpoint=endpoint))],
)
metrics.set_meter_provider(meter_provider)
```

Important

Configure providers before importing SDK modules such as `microsoft_agents.hosting.core`. The tracer and meter are resolved at import time. `microsoft_agents.activity` contains no telemetry and is safe to import beforehand.

The SDK can also instrument the `aiohttp` server, `aiohttp` client, and `requests` libraries via optional OpenTelemetry instrumentation packages:

```bash
pip install opentelemetry-instrumentation-aiohttp-server
pip install opentelemetry-instrumentation-aiohttp-client
pip install opentelemetry-instrumentation-requests
```

Learn more in the Python SDK's [OpenTelemetry quickstart configuration](https://github.com/microsoft/Agents-for-python/blob/main/test_samples/otel/quickstart/src/telemetry.py), which uses `AioHttpClientInstrumentor` and `RequestsInstrumentor`.

### Python spans

Python spans cover request processing, turn execution, messaging, storage, and authentication operations.

#### Python adapter spans

The `HttpAdapterBase` \(and its subclasses in `aiohttp`/`FastAPI` hosting packages\) emit spans for every incoming request and outgoing activity.

##### agents.adapter.process

Main processing span. Entered before the HTTP method check, so it fires for every call to `process_request`.

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.type` | string | Activity type \(message, invoke, etc.\)—set only after successful JSON parse |
| `activity.channel_id` | string | Channel identifier—set only after successful JSON parse |
| `activity.delivery_mode` | string | Delivery mode of the activity |
| `activity.conversation.id` | string | Conversation identifier |
| `activity.is_agentic_request` | boolean | Whether this is an agent-to-agent request |

Note

Attributes are set only after successful JSON parsing. If parsing fails or the request isn't a POST, activity type and channel default to `"unknown"` in metrics.

##### agents.adapter.write\_response

Emitted for activities that require a synchronous response: `invoke` activities and `expectReplies` delivery mode.

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.conversation.id` | string | Conversation identifier |

##### agents.adapter.send\_activities

Span for sending one or more activities through the adapter.

| Attribute | Type | Description |
| --- | --- | --- |
| `activities.count` | integer | Number of activities being sent |
| `activity.conversation.id` | string | Conversation identifier |

##### agents.adapter.update\_activity

Span for updating an activity.

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.id` | string | ID of the activity being updated |
| `activity.conversation.id` | string | Conversation identifier |

##### agents.adapter.delete\_activity

Span for deleting an activity.

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.id` | string | ID of the activity being deleted |
| `activity.conversation.id` | string | Conversation identifier |

##### agents.adapter.continue\_conversation

Span for proactively continuing a conversation.

| Attribute | Type | Description |
| --- | --- | --- |
| `agent.app_id` | string | The agent's application ID |
| `activity.conversation.id` | string | Conversation identifier |
| `activity.is_agentic_request` | boolean | Whether this is an agentic request |

##### agents.adapter.create\_connector\_client

Span for creating a connector client.

| Attribute | Type | Description |
| --- | --- | --- |
| `service_url` | string | Bot Framework service URL |
| `auth.scopes` | string | Comma-separated authentication scopes |
| `activity.is_agentic_request` | boolean | Whether this is for an agentic request |

##### agents.adapter.create\_user\_token\_client

Span for creating a user token client.

| Attribute | Type | Description |
| --- | --- | --- |
| `agents.token_service.endpoint` | string | Token service endpoint URL |
| `auth.scopes` | string | Comma-separated authentication scopes |

#### Python AgentApplication spans

`AgentApplication` \(the decorator-based programming model\) emits spans for turn lifecycle events.

##### agents.app.run

Main execution span for an `AgentApplication` turn.

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.type` | string | Type of activity being processed |
| `activity.id` | string | Activity identifier \(`"unknown"` if not set\) |
| `activity.name` | string | Activity name \(`"unknown"` if not set\) |
| `route.authorized` | boolean | Whether the route was authorized; added after routing completes |
| `route.matched` | boolean | Whether a route handler matched the activity; added after routing completes |

##### agents.app.route\_handler

Child span for executing a matched route handler.

| Attribute | Type | Description |
| --- | --- | --- |
| `route.is_invoke` | boolean | Whether this is an invoke activity route |
| `route.is_agentic` | boolean | Whether this is an agentic route |

##### agents.app.before\_turn

Span for before-turn handlers execution. No additional attributes.

##### agents.app.after\_turn

Span for after-turn handlers execution. No additional attributes.

##### agents.app.download\_files

Span for downloading file attachments.

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.attachments.count` | integer | Number of attachments \(0 when `activity.attachments` is None\) |

##### agents.app.typing\_indicator

Span for sending a typing indicator.

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.channel_id` | string | Channel identifier \(`"unknown"` if not provided\) |
| `activity.conversation.id` | string | Conversation identifier \(`"unknown"` if not provided\) |

#### Python proactive spans

Proactive conversation operations emit the following spans. Send and continue operations can include an OpenTelemetry link to the originating span context.

##### agents.proactive.store\_conversation

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.conversation.id` | string | Stored conversation identifier \(`"unknown"` if empty\) |

##### agents.proactive.get\_conversation

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.conversation.id` | string | Requested conversation identifier \(`"unknown"` if empty\) |
| `proactive.conversation.found` | boolean or string | Whether the conversation was found; `"unknown"` if the result was not shared with the span |

##### agents.proactive.delete\_conversation

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.conversation.id` | string | Deleted conversation identifier \(`"unknown"` if empty\) |

##### agents.proactive.send\_activity

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.conversation.id` | string | Target conversation identifier \(`"unknown"` if empty\) |
| `activity.type` | string | Activity type \(`"unknown"` if not provided\) |
| `activity.channel_id` | string | Channel identifier \(`"unknown"` if not provided\) |

##### agents.proactive.continue\_conversation

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.conversation.id` | string | Continued conversation identifier \(`"unknown"` if empty\) |
| `activity.type` | string | Activity type \(`"unknown"` if not provided\) |
| `activity.channel_id` | string | Channel identifier \(`"unknown"` if not provided\) |

##### agents.proactive.create\_conversation

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.channel_id` | string | Channel identifier |
| `proactive.members.count` | integer or string | Number of members when available |

#### Python TurnContext spans

`TurnContext` emits a span when it sends activities.

##### agents.turn.send\_activities

Emitted by `TurnContext` each time an activity is sent.

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.conversation.id` | string | Conversation identifier |

#### Python ConnectorClient spans

`ConnectorClient` wraps each outbound HTTP call in a span. HTTP method and status code appear only in metrics, not on the span itself.

##### agents.connector.reply\_to\_activity

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.conversation.id` | string | Conversation identifier |
| `activity.id` | string | The activity being replied to |

##### agents.connector.send\_to\_conversation

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.conversation.id` | string | Target conversation identifier |
| `activity.id` | string | Activity identifier, when provided |

##### agents.connector.update\_activity

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.conversation.id` | string | Conversation identifier |
| `activity.id` | string | The activity being updated |

##### agents.connector.delete\_activity

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.conversation.id` | string | Conversation identifier |
| `activity.id` | string | The activity being deleted |

##### agents.connector.create\_conversation

No span-level attributes. Metrics are recorded with `operation`, `http.method`, and `http.status_code`.

##### agents.connector.get\_conversations

No span-level attributes. Metrics are recorded with `operation`, `http.method`, and `http.status_code`.

##### agents.connector.get\_conversation\_members

No span-level attributes. Metrics are recorded with `operation`, `http.method`, and `http.status_code`.

##### agents.connector.upload\_attachment

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.conversation.id` | string | Conversation identifier |

##### agents.connector.get\_attachment\_info

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.attachment.id` | string | Attachment identifier |

##### agents.connector.get\_attachment

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.attachment.id` | string | Attachment identifier |
| `view.id` | string | View identifier |

#### Python storage spans

All storage implementations \(`MemoryStorage`, `BlobStorage`, `CosmosDbStorage`\) emit these spans.

##### agents.storage.read

| Attribute | Type | Description |
| --- | --- | --- |
| `storage.keys.count` | integer | Number of keys being read |
| `storage.operation` | string | Always `"read"` |

##### agents.storage.write

| Attribute | Type | Description |
| --- | --- | --- |
| `storage.keys.count` | integer | Number of keys being written |
| `storage.operation` | string | Always `"write"` |

##### agents.storage.delete

| Attribute | Type | Description |
| --- | --- | --- |
| `storage.keys.count` | integer | Number of keys being deleted |
| `storage.operation` | string | Always `"delete"` |

#### Python UserTokenClient spans

HTTP method and status code appear only in metrics, not on the span itself.

##### agents.user\_token\_client.get\_user\_token

| Attribute | Type | Description |
| --- | --- | --- |
| `auth.connection.name` | string | OAuth connection name |
| `user.id` | string | User identifier |
| `activity.channel_id` | string | Channel identifier \(`"unknown"` if not provided\) |

##### agents.user\_token\_client.sign\_out

| Attribute | Type | Description |
| --- | --- | --- |
| `auth.connection.name` | string | OAuth connection name \(`"unknown"` if None\) |
| `user.id` | string | User identifier |
| `activity.channel_id` | string | Channel identifier \(`"unknown"` if not provided\) |

##### agents.user\_token\_client.get\_sign\_in\_resource

This span has no caller-supplied telemetry attributes.

##### agents.user\_token\_client.exchange\_token

| Attribute | Type | Description |
| --- | --- | --- |
| `auth.connection.name` | string | OAuth connection name |
| `user.id` | string | User identifier |
| `activity.channel_id` | string | Channel identifier \(`"unknown"` if not provided\) |

##### agents.user\_token\_client.get\_token\_or\_sign\_in\_resource

| Attribute | Type | Description |
| --- | --- | --- |
| `auth.connection.name` | string | OAuth connection name |
| `user.id` | string | User identifier |
| `activity.channel_id` | string | Channel identifier \(`"unknown"` if not provided\) |

##### agents.user\_token\_client.get\_token\_status

| Attribute | Type | Description |
| --- | --- | --- |
| `user.id` | string | User identifier |
| `activity.channel_id` | string | Channel identifier \(`"unknown"` if not provided\) |
| `auth.connection.name` | string | Always `"unknown"` |

##### agents.user\_token\_client.get\_aad\_tokens

| Attribute | Type | Description |
| --- | --- | --- |
| `auth.connection.name` | string | OAuth connection name |
| `user.id` | string | User identifier |
| `activity.channel_id` | string | Channel identifier \(`"unknown"` if not provided\) |

#### Python authentication spans

MSAL token acquisition operations emit these spans. Each authentication span also records [authentication metrics](#python-authentication-metrics).

##### agents.authentication.get\_access\_token

Span for acquiring an access token.

| Attribute | Type | Description |
| --- | --- | --- |
| `auth.scopes` | string | Comma-separated authentication scopes |
| `auth.method` | string | Authentication method used \(e.g., `"secret"`, `"certificate"`, `"managed_identity"`\) |

##### agents.authentication.acquire\_token\_on\_behalf\_of

Span for acquiring a token using the on-behalf-of flow.

| Attribute | Type | Description |
| --- | --- | --- |
| `auth.scopes` | string | Comma-separated authentication scopes |

##### agents.authentication.get\_agentic\_instance\_token

Span for acquiring an agentic instance token.

| Attribute | Type | Description |
| --- | --- | --- |
| `agentic.instance_id` | string | The agentic application instance ID |

##### agents.authentication.get\_agentic\_user\_token

Span for acquiring an agentic user token.

| Attribute | Type | Description |
| --- | --- | --- |
| `agentic.instance_id` | string | The agentic application instance ID |
| `agentic.user_id` | string | The agentic user ID |
| `auth.scopes` | string | Comma-separated authentication scopes |

#### Python authorization spans

OAuth sign-in and token operations emit these spans.

##### agents.authorization.agentic\_token

Span for retrieving an agentic authorization token.

| Attribute | Type | Description |
| --- | --- | --- |
| `auth.handler.id` | string | The authorization handler identifier |
| `auth.connection.name` | string | The connection name used \(`"unknown"` if not provided\) |
| `auth.scopes` | string | Comma-separated authentication scopes \(omitted if no scopes provided\) |

##### agents.authorization.azure\_bot\_token

Span for retrieving an Azure Bot Service authorization token.

| Attribute | Type | Description |
| --- | --- | --- |
| `auth.handler.id` | string | The authorization handler identifier |
| `auth.connection.name` | string | The connection name used \(`"unknown"` if not provided\) |
| `auth.scopes` | string | Comma-separated authentication scopes \(omitted if no scopes provided\) |

##### agents.authorization.azure\_bot\_signin

Span for the Azure Bot Service sign-in flow.

| Attribute | Type | Description |
| --- | --- | --- |
| `auth.handler.id` | string | The authorization handler identifier |
| `auth.connection.name` | string | The connection name used \(`"unknown"` if not provided\) |
| `auth.scopes` | string | Comma-separated authentication scopes \(omitted if no scopes provided\) |

##### agents.authorization.azure\_bot\_signout

Span for signing out a user via Azure Bot Service.

| Attribute | Type | Description |
| --- | --- | --- |
| `auth.handler.id` | string | The authorization handler identifier |
| `auth.connection.name` | string | The connection name \(`"unknown"`—no connection name applies to sign-out\) |

### Python metrics

Python metrics aggregate activity processing, turn execution, storage operations, and outbound requests.

#### Python adapter metrics

Adapter metrics count activities and measure request processing duration.

##### agents.adapter.process.duration

**Type:** Histogram  
**Unit:** ms  
**Description:** Duration of each `process_request` call.

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.type` | string | Activity type \(`"unknown"` if JSON parsing failed\) |
| `activity.channel_id` | string | Channel identifier |

##### agents.activities.received

**Type:** Counter  
**Unit:** activity

**Description:** Total activities received—incremented once per `process_request` call, including non-POST and bad-JSON calls \(where type and channel default to `"unknown"`\).

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.type` | string | Activity type |
| `activity.channel_id` | string | Channel identifier |

##### agents.activities.sent

**Type:** Counter  
**Unit:** activity

**Description:** Total outbound activities sent.

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.type` | string | Activity type |
| `activity.channel_id` | string | Channel identifier |

##### agents.activities.updated

**Type:** Counter  
**Unit:** activity

**Description:** Total activity updates.

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.channel_id` | string | Channel identifier |

##### agents.activities.deleted

**Type:** Counter  
**Unit:** activity

**Description:** Total activity deletions.

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.channel_id` | string | Channel identifier |

#### Python turn metrics

Turn metrics track successful turns, failed turns, and end-to-end duration.

##### agents.turn.count

**Type:** Counter  
**Unit:** turn  
**Description:** Total successful turns \(no exception\).

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.type` | string | Activity type |
| `activity.channel_id` | string | Channel identifier |
| `activity.conversation.id` | string | Conversation identifier |
| `success` | boolean | Always `True` for this metric |

##### agents.turn.error.count

**Type:** Counter  
**Unit:** turn  
**Description:** Total turns that raised an exception.

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.type` | string | Activity type |
| `activity.channel_id` | string | Channel identifier |
| `activity.conversation.id` | string | Conversation identifier |
| `success` | boolean | Always `False` for this metric |

##### agents.turn.duration

**Type:** Histogram  
**Unit:** ms  
**Description:** End-to-end turn duration. Recorded on both success and error paths.

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.type` | string | Activity type |
| `activity.channel_id` | string | Channel identifier |
| `activity.conversation.id` | string | Conversation identifier |
| `success` | boolean | Whether the turn completed without error |

#### Python storage metrics

Storage metrics count read, write, and delete operations and measure their duration.

##### agents.storage.operation.total

**Type:** Counter  
**Unit:** operation  
**Description:** Total storage operations. The C# SDK also emits this metric; the JavaScript SDK doesn't.

| Attribute | Type | Description |
| --- | --- | --- |
| `storage.operation` | string | `"read"`, `"write"`, or `"delete"` |

##### agents.storage.operation.duration

**Type:** Histogram  
**Unit:** ms  
**Description:** Duration of storage operations.

| Attribute | Type | Description |
| --- | --- | --- |
| `storage.operation` | string | `"read"`, `"write"`, or `"delete"` |

#### Python connector metrics

Connector metrics count outbound HTTP requests and measure their duration.

##### agents.connector.request.count

**Type:** Counter  
**Unit:** request  
**Description:** Total outbound connector HTTP requests.

| Attribute | Type | Description |
| --- | --- | --- |
| `operation` | string | Span name of the operation \(e.g. `"agents.connector.reply_to_activity"`\) |
| `http.method` | string | HTTP method—present only when the HTTP response is available |
| `http.status_code` | integer | HTTP status code—present only when the HTTP response is available |

##### agents.connector.request.duration

**Type:** Histogram  
**Unit:** ms  
**Description:** Duration of outbound connector HTTP requests.

| Attribute | Type | Description |
| --- | --- | --- |
| `operation` | string | Span name of the operation |
| `http.method` | string | HTTP method—present only when the HTTP response is available |
| `http.status_code` | integer | HTTP status code—present only when the HTTP response is available |

#### Python UserTokenClient metrics

User token client metrics count HTTP requests and measure their duration.

##### agents.user\_token\_client.request.count

**Type:** Counter  
**Unit:** request  
**Description:** Total user token client HTTP requests.

| Attribute | Type | Description |
| --- | --- | --- |
| `operation` | string | Span name of the operation \(e.g. `"agents.user_token_client.get_user_token"`\) |
| `http.method` | string | HTTP method—present only when the HTTP response is available |
| `http.status_code` | integer | HTTP status code—present only when the HTTP response is available |

##### agents.user\_token\_client.request.duration

**Type:** Histogram  
**Unit:** ms  
**Description:** Duration of user token client HTTP requests.

| Attribute | Type | Description |
| --- | --- | --- |
| `operation` | string | Span name of the operation |
| `http.method` | string | HTTP method—present only when the HTTP response is available |
| `http.status_code` | integer | HTTP status code—present only when the HTTP response is available |

#### Python authentication metrics

Authentication metrics count token requests and measure their duration.

##### agents.auth.token.request.count

**Type:** Counter  
**Unit:** request  
**Description:** Total authentication token requests made by the SDK.

| Attribute | Type | Description |
| --- | --- | --- |
| `auth.method` | string | Authentication method used \(e.g., `"secret"`, `"certificate"`, `"obo"`, `"agentic_instance"`, `"agentic_user"`\) |
| `auth.success` | boolean | Whether the token request succeeded |

##### agents.auth.token.request.duration

**Type:** Histogram  
**Unit:** ms  
**Description:** Duration of authentication token requests.

| Attribute | Type | Description |
| --- | --- | --- |
| `auth.method` | string | Authentication method used |
| `auth.success` | boolean | Whether the token request succeeded |

### Filter Python spans

To suppress specific spans in production, use an OpenTelemetry [sampler](https://opentelemetry.io/docs/concepts/sampling/). A sampler receives the span name before the span is recorded and can return `DROP` to avoid recording and exporting that span.

```python
from opentelemetry.sdk.trace.sampling import (
    Decision,
    ParentBased,
    Sampler,
    SamplingResult,
    TraceIdRatioBased,
)

SUPPRESSED_SPANS = frozenset(
    {
        "agents.storage.read",
        "agents.storage.write",
        "agents.storage.delete",
    }
)

class SpanFilterSampler(Sampler):
    def __init__(self, delegate: Sampler) -> None:
        self._delegate = delegate

    def should_sample(
        self,
        parent_context,
        trace_id,
        name,
        kind=None,
        attributes=None,
        links=None,
        trace_state=None,
    ):
        if name in SUPPRESSED_SPANS:
            return SamplingResult(Decision.DROP)

        return self._delegate.should_sample(
            parent_context=parent_context,
            trace_id=trace_id,
            name=name,
            kind=kind,
            attributes=attributes,
            links=links,
            trace_state=trace_state,
        )

    def get_description(self):
        return f"SpanFilterSampler({self._delegate.get_description()})"

sampler = SpanFilterSampler(
    ParentBased(root=TraceIdRatioBased(0.1))
)
```

In the [Python setup](#python-setup) example, replace `TracerProvider(resource=resource)` with `TracerProvider(resource=resource, sampler=sampler)`. Keep the same resource and span processor. Don't register a second provider.

Importing SDK constants before provider setup can initialize the SDK tracer too early, so use literal span names in provider bootstrap code.

### Python error handling in spans

All SDK spans automatically handle errors. When an exception propagates out of a traced operation:

1. The span status is set to `ERROR`.
2. The exception is recorded on the span via `span.record_exception()`.
3. The exception is re-raised—it is never swallowed by the telemetry layer.

On clean exit, the span status is set to `OK`.

### Python span constants reference

Span name constants are defined across several modules in `microsoft_agents.hosting.core`:

```python
from microsoft_agents.hosting.core.telemetry.adapter import constants as adapter_constants
from microsoft_agents.hosting.core.app.telemetry import constants as app_constants
from microsoft_agents.hosting.core.app.proactive.telemetry import constants as proactive_constants
from microsoft_agents.hosting.core.connector.telemetry import constants as connector_constants
from microsoft_agents.hosting.core.storage.telemetry import constants as storage_constants
from microsoft_agents.hosting.core.telemetry.turn_context import constants as turn_context_constants
from microsoft_agents.hosting.core.authorization.telemetry import constants as auth_constants
from microsoft_agents.hosting.core.app.oauth.telemetry import constants as oauth_constants

# Adapter
adapter_constants.SPAN_PROCESS                    # 'agents.adapter.process'
adapter_constants.SPAN_SEND_ACTIVITIES            # 'agents.adapter.send_activities'
adapter_constants.SPAN_UPDATE_ACTIVITY            # 'agents.adapter.update_activity'
adapter_constants.SPAN_DELETE_ACTIVITY            # 'agents.adapter.delete_activity'
adapter_constants.SPAN_CONTINUE_CONVERSATION      # 'agents.adapter.continue_conversation'
adapter_constants.SPAN_CREATE_CONNECTOR_CLIENT    # 'agents.adapter.create_connector_client'
adapter_constants.SPAN_CREATE_USER_TOKEN_CLIENT   # 'agents.adapter.create_user_token_client'
adapter_constants.SPAN_WRITE_RESPONSE             # 'agents.adapter.write_response'

# AgentApplication
app_constants.SPAN_ON_TURN                        # 'agents.app.run'
app_constants.SPAN_ROUTE_HANDLER                  # 'agents.app.route_handler'
app_constants.SPAN_BEFORE_TURN                    # 'agents.app.before_turn'
app_constants.SPAN_AFTER_TURN                     # 'agents.app.after_turn'
app_constants.SPAN_DOWNLOAD_FILES                 # 'agents.app.download_files'
app_constants.SPAN_SEND_TYPING                     # 'agents.app.typing_indicator'

# Proactive
proactive_constants.SPAN_STORE_CONVERSATION       # 'agents.proactive.store_conversation'
proactive_constants.SPAN_GET_CONVERSATION         # 'agents.proactive.get_conversation'
proactive_constants.SPAN_DELETE_CONVERSATION      # 'agents.proactive.delete_conversation'
proactive_constants.SPAN_SEND_ACTIVITY            # 'agents.proactive.send_activity'
proactive_constants.SPAN_CONTINUE_CONVERSATION    # 'agents.proactive.continue_conversation'
proactive_constants.SPAN_CREATE_CONVERSATION      # 'agents.proactive.create_conversation'

# TurnContext
turn_context_constants.SPAN_TURN_SEND_ACTIVITIES  # 'agents.turn.send_activities'

# ConnectorClient
connector_constants.SPAN_REPLY_TO_ACTIVITY        # 'agents.connector.reply_to_activity'
connector_constants.SPAN_SEND_TO_CONVERSATION     # 'agents.connector.send_to_conversation'
connector_constants.SPAN_UPDATE_ACTIVITY          # 'agents.connector.update_activity'
connector_constants.SPAN_DELETE_ACTIVITY          # 'agents.connector.delete_activity'
connector_constants.SPAN_CREATE_CONVERSATION      # 'agents.connector.create_conversation'
connector_constants.SPAN_GET_CONVERSATIONS        # 'agents.connector.get_conversations'
connector_constants.SPAN_GET_CONVERSATION_MEMBERS # 'agents.connector.get_conversation_members'
connector_constants.SPAN_UPLOAD_ATTACHMENT        # 'agents.connector.upload_attachment'
connector_constants.SPAN_GET_ATTACHMENT           # 'agents.connector.get_attachment'
connector_constants.SPAN_GET_ATTACHMENT_INFO      # 'agents.connector.get_attachment_info'

# Storage
storage_constants.SPAN_STORAGE_READ               # 'agents.storage.read'
storage_constants.SPAN_STORAGE_WRITE              # 'agents.storage.write'
storage_constants.SPAN_STORAGE_DELETE             # 'agents.storage.delete'

# Authentication
auth_constants.SPAN_GET_ACCESS_TOKEN              # 'agents.authentication.get_access_token'
auth_constants.SPAN_ACQUIRE_TOKEN_ON_BEHALF_OF    # 'agents.authentication.acquire_token_on_behalf_of'
auth_constants.SPAN_GET_AGENTIC_INSTANCE_TOKEN    # 'agents.authentication.get_agentic_instance_token'
auth_constants.SPAN_GET_AGENTIC_USER_TOKEN        # 'agents.authentication.get_agentic_user_token'

# Authorization
oauth_constants.AGENTIC_TOKEN                     # 'agents.authorization.agentic_token'
oauth_constants.AZURE_BOT_TOKEN                   # 'agents.authorization.azure_bot_token'
oauth_constants.AZURE_BOT_SIGN_IN                 # 'agents.authorization.azure_bot_signin'
oauth_constants.AZURE_BOT_SIGN_OUT                # 'agents.authorization.azure_bot_signout'

# UserTokenClient
connector_constants.SPAN_GET_USER_TOKEN                  # 'agents.user_token_client.get_user_token'
connector_constants.SPAN_SIGN_OUT                        # 'agents.user_token_client.sign_out'
connector_constants.SPAN_GET_SIGN_IN_RESOURCE             # 'agents.user_token_client.get_sign_in_resource'
connector_constants.SPAN_EXCHANGE_TOKEN                  # 'agents.user_token_client.exchange_token'
connector_constants.SPAN_GET_TOKEN_OR_SIGN_IN_RESOURCE   # 'agents.user_token_client.get_token_or_sign_in_resource'
connector_constants.SPAN_GET_TOKEN_STATUS                # 'agents.user_token_client.get_token_status'
connector_constants.SPAN_GET_AAD_TOKENS                  # 'agents.user_token_client.get_aad_tokens'
```

### Python metric constants reference

Metric name constants identify counters and histograms in the corresponding modules:

```python
from microsoft_agents.hosting.core.telemetry.adapter import constants as adapter_constants
from microsoft_agents.hosting.core.app.telemetry import constants as app_constants
from microsoft_agents.hosting.core.connector.telemetry import constants as connector_constants
from microsoft_agents.hosting.core.storage.telemetry import constants as storage_constants
from microsoft_agents.hosting.core.authorization.telemetry import constants as auth_constants

# Adapter
adapter_constants.METRIC_ADAPTER_PROCESS_DURATION  # 'agents.adapter.process.duration'
adapter_constants.METRIC_ACTIVITIES_RECEIVED        # 'agents.activities.received'
adapter_constants.METRIC_ACTIVITIES_SENT            # 'agents.activities.sent'
adapter_constants.METRIC_ACTIVITIES_UPDATED         # 'agents.activities.updated'
adapter_constants.METRIC_ACTIVITIES_DELETED         # 'agents.activities.deleted'

# Turn
app_constants.METRIC_TURN_COUNT                     # 'agents.turn.count'
app_constants.METRIC_TURN_ERROR_COUNT               # 'agents.turn.error.count'
app_constants.METRIC_TURN_DURATION                  # 'agents.turn.duration'

# Storage
storage_constants.METRIC_STORAGE_OPERATION_TOTAL    # 'agents.storage.operation.total'
storage_constants.METRIC_STORAGE_OPERATION_DURATION # 'agents.storage.operation.duration'

# Connector
connector_constants.METRIC_CONNECTOR_REQUEST_COUNT          # 'agents.connector.request.count'
connector_constants.METRIC_CONNECTOR_REQUEST_DURATION       # 'agents.connector.request.duration'

# UserTokenClient
connector_constants.METRIC_USER_TOKEN_CLIENT_REQUEST_COUNT      # 'agents.user_token_client.request.count'
connector_constants.METRIC_USER_TOKEN_CLIENT_REQUEST_DURATION   # 'agents.user_token_client.request.duration'

# Authentication
auth_constants.METRIC_AUTH_TOKEN_REQUEST_COUNT      # 'agents.auth.token.request.count'
auth_constants.METRIC_AUTH_TOKEN_REQUEST_DURATION   # 'agents.auth.token.request.duration'
```

## Common span attributes

These attributes appear across multiple spans and follow OpenTelemetry semantic conventions where applicable. Attribute names and types can differ by SDK. C# and Python variants are noted below.

| Attribute | Type | Description |
| --- | --- | --- |
| `activity.type` | string | Bot Framework activity type \(message, conversationUpdate, invoke, etc.\) |
| `activity.id` | string | Unique identifier for the activity |
| `activity.name` | string | Name of the activity \(C# and Python\) |
| `activity.channel_id` | string | Channel identifier \(msteams, webchat, directline, etc.\) |
| `activity.conversation_id` | string | Unique identifier for the conversation; C# and Python use `activity.conversation.id` |
| `activity.is_agentic` | boolean | Whether this is an agentic \(agent-to-agent\) request; C# and Python use `activity.is_agentic_request` |
| `activity.delivery_mode` | string | The delivery mode of the activity |
| `auth.scope` | string | Authentication scope for token requests \(JavaScript only\) |
| `auth.scopes` | string\[\] or string | Authentication scopes; JavaScript records an array, while C# and Python record a comma-separated string |
| `auth.method` | string | Authentication method used; C# `get_access_token` uses `AuthTypes` enum values, while other C# authentication operations use `"obo"`, `"agentic_instance"`, or `"agentic_user"` |
| `auth.connection.name` | string | The OAuth connection name |
| `auth.handler.id` | string | The authorization handler identifier |
| `error.type` | string | Exception or error class name when an error occurs \(JavaScript only; C# and Python use an `exception` event with `exception.type`\) |
| `http.method` | string | HTTP method for outbound requests \(not emitted by C#\) |
| `http.status_code` | string or integer | HTTP response status code; not emitted by C#. JavaScript records a string, and Python records an integer. |
| `user.id` | string | The user identifier |

## Span kind reference

OpenTelemetry uses `SpanKind` to categorize spans. The SDK spans documented in this article use `INTERNAL` in JavaScript, C#, and Python. The other kinds in the following table describe OpenTelemetry categories, not kinds emitted by these SDK spans.

| Kind | Value | Usage |
| --- | --- | --- |
| `INTERNAL` | 0 | Internal operations within the SDK |
| `SERVER` | 1 | Handling incoming requests |
| `CLIENT` | 2 | Making outbound calls |
| `PRODUCER` | 3 | Producing messages to a broker |
| `CONSUMER` | 4 | Consuming messages from a broker |

## Related information

- [Microsoft 365 Agents SDK overview](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/agents-sdk-overview)
- [AgentApplication in Microsoft 365 Agents SDK](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/agent-application)
- [Use storage in your agent](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/storage)
