<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/bf-migration-nodejs -->
<!-- Sitemap-Last-Modified: 2025-08-20 -->

# Azure Bot Framework SDK to Microsoft 365 Agents SDK migration guidance for nodejs

This article describes the required changes to migrate from Bot Framework SDK for Node.js.

## Prerequisites

- [Node.js](https://nodejs.org) version 20 or higher
- Existing Bot Framework SDK project
- Azure Bot Service resource \(remains unchanged during migration\)

## NodeJS SDK Code changes

The changes in this section are due to differences between the [Azure Bot Framework SDK](https://learn.microsoft.com/en-us/azure/bot-service/index-bf-sdk) and the [Microsoft 365 Agents SDK JavaScript](https://learn.microsoft.com/en-us/javascript/api/overview/agents-overview) .

### Azure resources

Your Azure resources remain unchanged. You need to reference your appsettings properties for `MicrosoftAppType`, `MicrosoftAppId`, `MicrosoftAppPassword`, and `MicrosoftAppTenantId`. However those setting names are no longer used and can be deleted later. [Learn more about environment configuration](#environment-configuration)

### First steps

Apply the following changes first to address most differences. You'll still need to debug and check for other differences after you apply these changes.

#### Update package dependencies

This change doesn't get all required namespaces settled, but it covers the bulk of them.

| Scenario | Bot Framework SDK | Agents SDK |
| --- | --- | --- |
| Core hosting | [`botbuilder`](https://learn.microsoft.com/en-us/javascript/api/botbuilder) | [`@microsoft/agents-hosting`](https://learn.microsoft.com/en-us/javascript/api/%40microsoft/agents-hosting) |
| Activity schema | [`botframework-schema`](https://learn.microsoft.com/en-us/javascript/api/botframework-schema) | [`@microsoft/agents-activity`](https://learn.microsoft.com/en-us/javascript/api/@microsoft/agents-activity) |
| Dialogs | [`botbuilder-dialogs`](https://learn.microsoft.com/en-us/javascript/api/botbuilder-dialogs) | [`@microsoft/agents-hosting-dialogs`](https://learn.microsoft.com/en-us/javascript/api/@microsoft/agents-hosting-dialogs) |
| Azure Cosmos DB | [`botbuilder-azure`](https://learn.microsoft.com/en-us/javascript/api/botbuilder-azure) | [`@microsoft/agents-hosting-storage-cosmos`](https://learn.microsoft.com/en-us/javascript/api/@microsoft/agents-hosting-storage-cosmos) |
| Azure Blob Storage | [`botbuilder-azure-blobs`](https://learn.microsoft.com/en-us/javascript/api/botbuilder-azure-blobs) | [`@microsoft/agents-hosting-storage-blob`](https://learn.microsoft.com/en-us/javascript/api/@microsoft/agents-hosting-storage-blob) |
| Express server utilities | Manual setup | [`@microsoft/agents-hosting-express`](https://learn.microsoft.com/en-us/javascript/api/@microsoft/agents-hosting-express) |

#### Bots using Teams

If your bot uses Teams, add a package dependency for [`@microsoft/agents-hosting-extensions-teams`](https://www.npmjs.com/package/@microsoft/agents-hosting-extensions-teams)

#### Update imports/require

Use find and replace to make the following changes:

| Bot Framework | Agents SDK |
| --- | --- |
| `require('botframework-schema');` | `require('@microsoft/agents-activity')` |
| `require('botbuilder');` | `require('@microsoft/agents-hosting')` |
| `require('botbuilder-dialogs');` | `require('@microsoft/agents-hosting-dialogs')` |

### Agents SDK Activity class

The [`@microsoft/agents-activity`](https://learn.microsoft.com/en-us/javascript/api/@microsoft/agents-activity) package includes the [Activity class](https://learn.microsoft.com/en-us/javascript/api/@microsoft/agents-activity/activity) to perform parsing based on [zod](https://zod.dev/). You can parse and validate your custom activities from JSON with [`Activity.fromJson()`](https://learn.microsoft.com/en-us/javascript/api/@microsoft/agents-activity/activity#@microsoft-agents-activity-activity-fromjson) or from literal JavaScript objects with [`Activity.fromObject()`](https://learn.microsoft.com/en-us/javascript/api/@microsoft/agents-activity/activity#@microsoft-agents-activity-activity-fromobject).

Additionally, the `Activity` class centralizes all operations related to activity payload, such as [`getConversationReference`](https://learn.microsoft.com/en-us/javascript/api/@microsoft/agents-activity/activity#@microsoft-agents-activity-activity-getconversationreference). The methods in the following table moved from [`TurnContext`](https://learn.microsoft.com/en-us/javascript/api/botbuilder-core/turncontext) and now operate over the current activity instance:

| Bot Framework static method | Agents SDK instance method |
| --- | --- |
| [`TurnContext.applyConversationReference`](https://learn.microsoft.com/en-us/javascript/api/botbuilder-core/turncontext#botbuilder-core-turncontext-applyconversationreference) | [`activity.applyConversationReference`](https://learn.microsoft.com/en-us/javascript/api/@microsoft/agents-activity/activity#@microsoft-agents-activity-activity-applyconversationreference) |
| [`TurnContext.getConversationReference`](https://learn.microsoft.com/en-us/javascript/api/botbuilder-core/turncontext#botbuilder-core-turncontext-getconversationreference) | [`activity.getConversationReference`](https://learn.microsoft.com/en-us/javascript/api/@microsoft/agents-activity/activity#@microsoft-agents-activity-activity-getconversationreference) |
| [`TurnContext.getReplyConversationReference`](https://learn.microsoft.com/en-us/javascript/api/botbuilder-core/turncontext#botbuilder-core-turncontext-getreplyconversationreference) | [`activity.getReplyConversationReference`](https://learn.microsoft.com/en-us/javascript/api/@microsoft/agents-activity/activity#@microsoft-agents-activity-activity-getreplyconversationreference) |
| [`TurnContext.removeRecipientMention`](https://learn.microsoft.com/en-us/javascript/api/botbuilder-core/turncontext#botbuilder-core-turncontext-removerecipientmention) | [`activity.removeRecipientMention`](https://learn.microsoft.com/en-us/javascript/api/@microsoft/agents-activity/activity#@microsoft-agents-activity-activity-removerecipientmention) |
| [`TurnContext.getMentions`](https://learn.microsoft.com/en-us/javascript/api/botbuilder-core/turncontext#botbuilder-core-turncontext-getmentions) | [`activity.getMentions`](https://learn.microsoft.com/en-us/javascript/api/@microsoft/agents-activity/activity#@microsoft-agents-activity-activity-getmentions) |
| [`TurnContext.removeMentionText`](https://learn.microsoft.com/en-us/javascript/api/botbuilder-core/turncontext#botbuilder-core-turncontext-removementiontext) | [`activity.removeMentionText`](https://learn.microsoft.com/en-us/javascript/api/@microsoft/agents-activity/activity#@microsoft-agents-activity-activity-removementiontext) |

### Startup and Configuration

The Agents SDK configuration system replaces the [`ConfigurationBotFrameworkAuthentication`](https://learn.microsoft.com/en-us/javascript/api/botbuilder-core/configurationbotframeworkauthentication) class with the [`AuthConfiguration`](https://learn.microsoft.com/en-us/javascript/api/@microsoft/agents-hosting/authconfiguration) interface.

To load the configuration from the default `.env` file uses [`loadAuthConfigFromEnv`](https://learn.microsoft.com/en-us/javascript/api/@microsoft/agents-hosting/#@microsoft-agents-hosting-loadauthconfigfromenv).

Important

The configuration variables are described in [Configure authentication in JavaScript](https://github.com/microsoft/Agents/blob/main/docs/HowTo/azurebot-auth-for-js.md).

#### Environment Configuration

Create a `.env` file with the following variables:

```env
# Required for Azure Bot Service
clientId=your-app-id
clientSecret=your-app-secret  
tenantId=your-tenant-id

# Optional - for local debugging
PORT=3978
DEBUG=true
```

**Migration Note**: Update your environment variable names as shown in the following table:

| Bot Framework SDK | Agents SDK |
| --- | --- |
| `MicrosoftAppId` | `clientId` |
| `MicrosoftAppPassword` | `clientSecret` |
| `MicrosoftAppTenantId` | `tenantId` |

#### Authentication and Security

When Bot Framework SDK authorizes incoming requests, it includes JSON Web Token \(JWT\) authorization tokens in the stack. Agents SDK doesn't. When using a web server runtime such as express you have to configure a JWT middleware to authorize incoming requests based on the JWT Bearer token, the Agents SDK provides the [`authorizeJWT(AuthConfiguration)`](https://learn.microsoft.com/en-us/javascript/api/@microsoft/agents-hosting/#@microsoft-agents-hosting-authorizejwt) method.

**JWT Middleware \(Required for production\):**

```javascript
import { authorizeJWT, loadAuthConfigFromEnv } from '@microsoft/agents-hosting'

const authConfig = loadAuthConfigFromEnv()
server.use(authorizeJWT(authConfig))
```

**Local Development:**

For local debugging, JWT validation can be disabled:

```javascript
// Only for local development - NEVER in production
if (process.env.NODE_ENV === 'development') {
    // JWT validation disabled for local testing
} else {
    server.use(authorizeJWT(authConfig))
}
```

### Server Setup Options

The Agents SDK provides two approaches for setting up your server:

- [startServer method](#use-startserver-method)
- [Manual Express setup](#manual-express-setup)

#### Use startServer method

Use this simplified approach for new projects when you want a minimal setup and don't need custom middleware.

Update your initialization code from `botbuilder`:

```javascript
const { EchoBot } = require('./bot');
const {
    CloudAdapter,
    ConfigurationBotFrameworkAuthentication
} = require('botbuilder');
const botFrameworkAuthentication = new ConfigurationBotFrameworkAuthentication(process.env);
const adapter = new CloudAdapter(botFrameworkAuthentication);
const myBot = new EchoBot();
const server = express();
server.use(express.json());
server.post('/api/messages', async (req, res) => 
    await adapter.process(req, res, (context) => 
      myBot.run(context));
);
```

To agents-hosting with [`startServer()`](https://learn.microsoft.com/en-us/javascript/api/@microsoft/agents-hosting-express#@microsoft-agents-hosting-express-startserver):

```javascript
const { EchoBot } = require('./bot');
const { startServer } = require('@microsoft/agents-hosting-express')
startServer(new EchoBot());
```

#### Manual Express setup

Use this approach when migrating existing bots, need custom middleware, want full control over Express configuration

```javascript
const { EchoBot } = require('./bot');
const {
    CloudAdapter,
    loadAuthConfigFromEnv, // Update
    authorizeJWT // Update
} = require('@microsoft/agents-hosting'); // Update
const authConfig = loadAuthConfigFromEnv(); // Update
const adapter = new CloudAdapter(authConfig); // Update
const myBot = new EchoBot();
const server = express();
server.use(express.json());
server.use(authorizeJWT(authConfig)); // Update
server.post('/api/messages', async (req, res) => 
    await adapter.process(req, res, (context) => 
      myBot.run(context));
);

const port = process.env.PORT || 3978;
server.listen(port, () => {
    console.log(`Server listening on port ${port}`);
}).on('error', (err) => {
    console.error('Server failed to start:', err);
    process.exit(1);
});
```

### ActivityHandler support

Most bots created with the Bot Framework SDK are based on the [`botbuilder-core.ActivityHandler`](https://learn.microsoft.com/en-us/javascript/api/botbuilder-core/activityhandler) base class.

The Agents SDK provides a compatible [`agents-hosting.ActivityHandler`](https://learn.microsoft.com/en-us/javascript/api/@microsoft/agents-hosting/activityhandler) that maintains the same API surface for easier migration.

#### Key differences

Some key differences between the Bot Framework SDK and the Agents SDK include:

**Handler Parameters:**

| SDK | Handler Type |
| --- | --- |
| Bot Framework SDK | [`BotHandler`](https://learn.microsoft.com/en-us/javascript/api/botbuilder-core/bothandler) |
| Agents SDK | [`AgentHandler`](https://learn.microsoft.com/en-us/javascript/api/@microsoft/agents-hosting/agenthandler) |

**Additional Methods in Agents SDK:**

| Method | Description |
| --- | --- |
| [`onMessageDelete`](https://learn.microsoft.com/en-us/javascript/api/@microsoft/agents-hosting/activityhandler#@microsoft-agents-hosting-activityhandler-onmessagedelete) | Handles message deletion activities |
| [`onMessageUpdate`](https://learn.microsoft.com/en-us/javascript/api/@microsoft/agents-hosting/activityhandler#@microsoft-agents-hosting-activityhandler-onmessageupdate) | Handles message update activities |
| [`onSignInInvoke`](https://learn.microsoft.com/en-us/javascript/api/@microsoft/agents-hosting/activityhandler#@microsoft-agents-hosting-activityhandler-onsignininvoke) | Handles sign-in invoke activities |

**Missing Methods in Agents SDK:**

| Method | Reason |
| --- | --- |
| `onCommand` | Command activities aren't supported |
| `onCommandResult` | Command result activities aren't supported |
| `onEvent` | Generic event handling \(specific event types like `onTokenResponseEvent` are still supported\) |
| `onTokenResponseEvent` | OAuth token response events |

**Method Signature Changes:**

All handler methods return `ActivityHandler` instead of `this` for method chaining. Handler functions use the `AgentHandler` type, which has the same signature as `BotHandler`

#### Migration Example:

- [Before](#tabpanel_1_before)
- [After](#tabpanel_1_after)

Bot Framework SDK:

```javascript
const { ActivityHandler } = require('botbuilder');

class MyBot extends ActivityHandler {
    constructor() {
        super();
        this.onMessage(async (context, next) => {
            await context.sendActivity('Hello!');
            await next();
        });
    }
}
```

Agents SDK:

```javascript
const { ActivityHandler } = require('@microsoft/agents-hosting');

class MyBot extends ActivityHandler {
    constructor() {
        super();
        this.onMessage(async (context, next) => {
            await context.sendActivity('Hello!');
            await next();
        });
    }
}
```

The migration is mostly straightforward, with the main change being the import statement and handler type. Most existing `ActivityHandler`-based bots should work with minimal modifications.

Important

The `ActivityHandler` is deprecated in favor of the new [`AgentApplication`](https://learn.microsoft.com/en-us/javascript/api/@microsoft/agents-hosting/agentapplication) class

### Migrating from `ActivityHandler` to `AgentApplication`

While `ActivityHandler` is supported for backward compatibility, the recommended approach is to use `AgentApplication`:

- [Before](#tabpanel_2_before)
- [After](#tabpanel_2_after)

Using `ActivityHandler`:

```javascript
import { ActivityHandler } from '@microsoft/agents-hosting'

class MyBot extends ActivityHandler {
    constructor() {
        super()
        this.onMessage(async (context, next) => {
            await context.sendActivity('Hello!')
            await next()
        })
        
        this.onMembersAdded(async (context, next) => {
            await context.sendActivity('Welcome!')
            await next()
        })
    }
}
```

Using `AgentApplication`:

```javascript
import { AgentApplication, MemoryStorage } from '@microsoft/agents-hosting'

const agent = new AgentApplication({
    storage: new MemoryStorage()
})

agent.onMessage(async (context, state) => {
    await context.sendActivity('Hello!')
})

agent.onConversationUpdate('membersAdded', async (context, state) => {
    await context.sendActivity('Welcome!')
})

// Additional capabilities
agent.onMessage('/reset', async (context, state) => {
    state.deleteConversationState()
    await context.sendActivity('State cleared!')
})
```

#### Key Differences

The following table describes key feature differences between `ActivityHandler` and `AgentApplication`:

| Feature | **`ActivityHandler`** | **`AgentApplication`** |
| --- | --- | --- |
| **State Management** | Manual state management required | Built-in state management provided |
| **Event Handling** | Generic event handlers \(for example, `onMembersAdded`\) | More specific event handlers \(for example, `membersAdded`\) |
| **Next Function** | Handlers require calling `next()` | Handlers don't require calling `next()` |
| **Storage** | Manual storage configuration | Built-in storage support with automatic state persistence |

## Common Migration Patterns

Some common migration patterns are:

- [Simple Echo Bot](#simple-echo-bot)
- [State Management](#state-management)
- [Inheriting from AgentApplication](#inheriting-from-agentapplication)

### Simple Echo Bot

- [Before](#tabpanel_3_before)
- [After](#tabpanel_3_after)

Bot Framework

```javascript
const { ActivityHandler } = require('botbuilder')

class EchoBot extends ActivityHandler {
    constructor() {
        super()
        this.onMessage(async (context, next) => {
            await context.sendActivity(`You said: ${context.activity.text}`)
            await next()
        })
    }
}
```

Agents SDK

```javascript
import { AgentApplication, MessageFactory } from '@microsoft/agents-hosting'

const agent = new AgentApplication()

agent.onMessage(async (context) => {
    const replyText = `Echo: ${context.activity.text}`
    await context.sendActivity(MessageFactory.text(replyText))
})
```

### State Management

Using `AgentApplication`:

```javascript
import { AgentApplication, MemoryStorage } from '@microsoft/agents-hosting'

const agent = new AgentApplication({
    storage: new MemoryStorage()
})

agent.onMessage('/count', async (context, state) => {
    const count = state.conversation.count ?? 0
    state.conversation.count = count + 1
    await context.sendActivity(`Count: ${state.conversation.count}`)
})
```

### Inheriting from AgentApplication

For more complex scenarios, you can create a class that inherits from `AgentApplication`:

```javascript
import { AgentApplication, MemoryStorage, MessageFactory } from '@microsoft/agents-hosting'

class MyAgent extends AgentApplication {
    constructor() {
        super({
            storage: new MemoryStorage()
        })
        this.setupRoutes()
    }
    
    setupRoutes() {
        this.onMessage('/help', this.handleHelp)
        this.onMessage('/status', this.handleStatus)
        this.onMessage('/reset', this.handleReset)
        
        this.onActivity('message', this.handleDefault)
        this.onConversationUpdate('membersAdded', this.handleWelcome)
    }
    
    handleHelp = async (context, state) => {
        const helpText = `
                Available commands:
                - /help - Show this help message
                - /status - Show current status
                - /reset - Reset conversation state
        `
        await context.sendActivity(MessageFactory.text(helpText))
    }
    
    handleStatus = async (context, state) => {
        const messageCount = state.conversation.messageCount ?? 0
        await context.sendActivity(`Messages processed: ${messageCount}`)
    }
    
    handleReset = async (context, state) => {
        state.deleteConversationState()
        await context.sendActivity('Conversation state has been reset.')
    }
    
    handleWelcome = async (context, state) => {
        const welcomeText = 'Welcome! Type /help to see available commands.'
        await context.sendActivity(MessageFactory.text(welcomeText))
    }
    
    handleDefault = async (context, state) => {
        // Increment message counter
        const messageCount = (state.conversation.messageCount ?? 0) + 1
        state.conversation.messageCount = messageCount
        
        const replyText = `Echo: ${context.activity.text} (Message #${messageCount})`
        await context.sendActivity(MessageFactory.text(replyText))
    }
}

export default new MyAgent()
```

#### Benefits of this pattern

| Benefit | Description |
| --- | --- |
| **Better organization** | Separate methods for different handlers |
| **Reusability** | Can be easily extended or inherited further |
| **Testability** | Individual methods can be unit tested |
| **Maintainability** | Cleaner code structure for complex bots |
| **Arrow functions** | Automatically bind `this` context without needing `.bind()` |

## Related Content

- [Azure Bot Framework SDK to Agents SDK migration guidance](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/bf-migration-guidance)
- [Azure Bot Framework SDK to Microsoft 365 Agents SDK migration guidance for .NET](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/bf-migration-dotnet)
- [Azure Bot Framework SDK to Microsoft 365 Agents SDK migration guidance for Python](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/bf-migration-python)
