<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/teams/teams-context -->
<!-- Sitemap-Last-Modified: 2026-08-25 -->

# Access Microsoft Teams conversation members

## Get conversation members

From within a handler, use the Teams API client to retrieve one member or page through a conversation roster.

```csharp
var api = turnContext.Client;

// Get a single member
var member = await api.Conversations.GetMemberByIdAsync(
    turnContext.Activity.Conversation.Id,
    turnContext.Activity.From.Id,
    cancellationToken: cancellationToken);

// Page through all members
string? continuationToken = null;
do
{
    var page = await api.Conversations.GetMembersPagedAsync(
        turnContext.Activity.Conversation.Id,
        100,
        continuationToken,
        cancellationToken: cancellationToken);
    continuationToken = page.ContinuationToken;

    foreach (var teamMember in page.Members)
    {
        // Process each member
    }
}
while (continuationToken != null);

// Query a specific team's roster
var teamId = turnContext.Activity.TeamsGetTeamInfo()?.Id;
var teamPage = await api.Conversations.GetMembersPagedAsync(
    teamId!,
    100,
    continuationToken: null,
    cancellationToken: cancellationToken);
```

```javascript
import { teamsGetTeamInfo } from '@microsoft/agents-hosting-extensions-msteams'

const client = teamsExt.getTeamsClient(context)
const conversationId = context.activity.conversation.id

// Get a single member
const member = await client.conversations.getMemberById(conversationId, context.activity.from.id)
console.log(`Name: ${member.name}`)

// Get all members at once
const allMembers = await client.conversations.getMembers(conversationId)

// Page through members
let continuationToken
do {
  const page = await client.conversations.getPagedMembers(conversationId, 100, continuationToken)
  continuationToken = page.continuationToken
  for (const member of page.members) {
    console.log(member.name)
  }
} while (continuationToken)

// Query a specific team's roster
const teamId = teamsGetTeamInfo(context.activity)?.id
const teamMembers = await client.conversations.getMembers(teamId)
```

Note

Inside a Teams extension route handler, `context` is a `TeamsTurnContext`, so you can use the `context.client` shorthand instead of `teamsExt.getTeamsClient(context)`.

Get the Teams API client from the handler `context`, and then call the conversation member operations. The `members(conversation_id)` method returns an operations object with `get`, `get_paged`, and `get_all` methods:

```python
api = teams.get_teams_api_client(context)
conversation_id = context.activity.conversation.id

# Get a single member
member = await api.conversations.members(conversation_id).get(context.activity.from_property.id)

# Get all members at once
all_members = await api.conversations.members(conversation_id).get_all()

# Page through members
result = await api.conversations.members(conversation_id).get_paged(page_size=100)
for member in result.members:
    print(member.name)
continuation_token = result.continuation_token

# Query a specific team's roster
team_id = context.activity.get_team_info().id
team_members = await api.conversations.members(team_id).get_all()
```

Note

Within a Teams route handler, you can also use the shorthand `context.api_client` instead of `teams.get_teams_api_client(context)`.

## Teams API client

The Teams extension registers an API client on the turn context for any activity arriving on the Teams channel.

Use the `Client` property on `ITeamsTurnContext` to retrieve it:

```csharp
var api = turnContext.Client;
```

Use the client directly for conversation member operations. Feature-specific operations are documented with their corresponding feature.

Note

The client is only available for activities on the Teams channel, where `Activity.ChannelId == Channels.Msteams`.

Call `getTeamsClient(context)` on the `TeamsAgentExtension` instance you registered during setup:

```javascript
const client = teamsExt.getTeamsClient(context)
```

Inside a Teams extension route handler, `context` is a `TeamsTurnContext`, so the `context.client` shorthand returns the same client.

Use the client directly for conversation member operations. Feature-specific operations are documented with their corresponding feature.

Note

`getTeamsClient()` throws an error if the Teams API client isn't available on the turn context. The client is only set for activities where `activity.channelId === 'msteams'`.

Use `teams.get_teams_api_client(context)` to retrieve it. Within a Teams route handler, the shorthand `context.api_client` returns the same client:

```python
client = teams.get_teams_api_client(context)
# or, inside a handler:
client = context.api_client
```

Use the client directly for conversation member operations. Feature-specific operations are documented with their corresponding feature.

Note

The client is only available for activities on the Teams channel.

## Related content

- [Teams extension overview](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/teams/teams-extension)
- [Handle meeting events](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/teams/teams-meetings)
- [Handle lifecycle events](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/teams/teams-configuration-lifecycle)
