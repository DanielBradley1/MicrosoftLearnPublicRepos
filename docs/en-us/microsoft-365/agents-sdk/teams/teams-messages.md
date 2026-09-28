<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/teams/teams-messages -->
<!-- Sitemap-Last-Modified: 2026-08-25 -->

# Handle messages in Microsoft Teams

Use standard `AgentApplication` routes for message activities. Access Adaptive Card `Action.Execute` handling through `AgentApplication.AdaptiveCards`.

## Send targeted messages

With targeted messages, an agent can communicate privately with one user inside a channel, group chat, or meeting chat. Other participants can't see the message.

All agents in Teams can send targeted messages. The recipient must be a member of the current conversation.

Use the Teams API client to page through the conversation roster. Create one activity for each intended recipient and send it with `SendTargetedActivityAsync`:

```csharp
[TeamsMessageRoute("targeted")]
public async Task SendTargetedMessagesAsync(
    ITeamsTurnContext turnContext,
    ITurnState turnState,
    CancellationToken cancellationToken)
{
    var api = turnContext.Client;
    string? continuationToken = null;

    do
    {
        var page = await api.Conversations.GetMembersPagedAsync(
            turnContext.Activity.Conversation.Id,
            100,
            continuationToken,
            cancellationToken: cancellationToken);

        continuationToken = page.ContinuationToken;

        foreach (var member in page.Members ?? [])
        {
            var activity = Activity.CreateMessageActivity()
                .WithText(
                    $"{member.Name}, this is a targeted message - only you can see it.");

            activity.Recipient = new ChannelAccount
            {
                Id = member.Id,
                Name = member.Name,
                Role = RoleTypes.User
            };

            await turnContext.SendTargetedActivityAsync(
                activity,
                cancellationToken);
        }
    }
    while (continuationToken is not null);
}
```

Set the activity recipient to a member of the current conversation, and send it with `sendTargetedActivity`:

```javascript
import { Activity } from '@microsoft/agents-activity'

const activity = Activity.fromObject({
  type: 'message',
  text: `${member.name}, this is a targeted message - only you can see it.`,
  recipient: {
    id: member.id,
    name: member.name,
    role: 'user'
  }
})

await context.sendTargetedActivity(activity)
```

Set the activity recipient to a member of the current conversation, and send it with `send_targeted_activity`:

```python
from microsoft_agents.activity import Activity, ChannelAccount

activity = Activity(
    type="message",
    text=f"{member.name}, this is a targeted message - only you can see it.",
    recipient=ChannelAccount(
        id=member.id,
        name=member.name,
        role="user",
    ),
)

await context.send_targeted_activity(activity)
```

Targeted messages expire after 24 hours and don't support reactions, threaded replies, or forwarding. For privacy guidance, Prompt Preview, and client behavior, see [Send and receive targeted messages](https://learn.microsoft.com/en-us/microsoftteams/platform/agents-in-teams/targeted-messages).

Note

The [`supportsTargetedMessages`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots#supportstargetedmessages) manifest property opts an agent in to **receive** targeted messages from users. It isn't required for sending targeted messages.

### Add Prompt Preview

Prompt Preview displays the user's original targeted request above an agent response. It preserves the prompt-response context while respecting the visibility of the original request.

In reactive scenarios, `TeamsTurnContext` automatically adds Prompt Preview metadata to every message sent in response to an inbound targeted message. This example sends a private response:

```csharp
[TeamsMessageRoute("promptpreview")]
public static async Task SendPromptPreviewAsync(
    ITeamsTurnContext turnContext,
    ITurnState turnState,
    CancellationToken cancellationToken)
{
    var response = Activity.CreateMessageActivity()
        .WithText("This response includes a preview of your original prompt.")
        .WithRecipient(turnContext.Activity.From, isTargeted: true);

    await turnContext.SendActivityAsync(response, cancellationToken);
}
```

To send a public response with Prompt Preview, omit `WithRecipient`. Only share a targeted request publicly after the user explicitly approves sharing it.

For a proactive response sent outside the original turn, add the original targeted message ID explicitly. Proactive continuation handlers receive an `ITurnContext`, so wrap it in a `TeamsTurnContext` to use the targeted-message helper:

```csharp
[ContinueConversation("prompt-preview")]
public static async Task SendPromptPreviewProactivelyAsync(
    ITurnContext turnContext,
    ITurnState turnState,
    CancellationToken cancellationToken)
{
    var teamsTurnContext = new TeamsTurnContext(turnContext);

    ITeamsActivity response = new TeamsActivity
    {
        Type = ActivityTypes.Message,
        Text = "The requested work is complete.",
        Recipient = recipient
    };

    response.AddTargetedMessageInfo(targetedMessageId);

    await teamsTurnContext.SendTargetedActivityAsync(
        response,
        cancellationToken);
}
```

The example assumes that `recipient` and `targetedMessageId` were saved from the original turn and loaded from durable storage. It sends a private proactive response. To send it publicly, omit `Recipient` and call `teamsTurnContext.SendActivityAsync(response, cancellationToken)`.

When normalizing a reactive response, `TeamsTurnContext` removes quoted-reply entities and their inline placeholders. It preserves an existing `targetedMessageInfo` entity or adds one that references the inbound targeted message. This prevents a private targeted prompt from being represented as a standard quoted reply.

## Send quoted replies

Quoted replies identify an earlier message and help readers navigate back to it. Use a quoted reply for an earlier public message. Use **Prompt Preview** instead when responding to a targeted request.

Create a `TeamsActivity` and call `AddQuotedReply` with the ID of the message to quote:

```csharp
[TeamsMessageRoute("quotedreply")]
public static async Task SendQuotedReplyAsync(
    ITeamsTurnContext turnContext,
    ITurnState turnState,
    CancellationToken cancellationToken)
{
    var messageId = turnContext.Activity.Id
        ?? throw new InvalidOperationException(
            "The incoming activity must have an ID to create a quoted reply.");

    ITeamsActivity reply = new TeamsActivity
    {
        Type = ActivityTypes.Message,
        Text = string.Empty
    };

    reply.AddQuotedReply(
        messageId,
        "This response includes a quoted reply to your message.");

    await turnContext.SendActivityAsync(reply, cancellationToken);
}
```

`AddQuotedReply` adds both the Teams quoted-reply entity and the required inline placeholder to the activity.

To inspect quoted messages on an inbound activity, call `GetQuotedMessages`:

```csharp
foreach (var entity in turnContext.Activity.GetQuotedMessages())
{
    var quotedReply = entity.QuotedReply;
    if (quotedReply is null)
    {
        continue;
    }

    var quotedMessageId = quotedReply.MessageId;
    // Use the message ID to correlate the reply with application data.
}
```

Each `QuotedReplyData` object includes the quoted message ID and can include the sender ID, sender name, preview text, timestamp, deletion status, and whether Teams validated the message reference.

For client behavior and platform limitations, see [Quoted replies in targeted messages](https://learn.microsoft.com/en-us/microsoftteams/platform/agents-in-teams/targeted-messages#quoted-replies-in-targeted-messages).

## Slash commands

Slash commands make agent features discoverable from the Teams compose box. Agent slash commands use targeted messaging so users can invoke a command privately in a group conversation.

Declare the commands and their triggers in the Microsoft 365 app manifest. Set `supportsTargetedMessages` to `true` because selecting one of these commands sends a targeted message from the user to the agent:

```json
{
  "bots": [
    {
      "botId": "{{BOT_ID}}",
      "scopes": ["personal", "team", "groupChat"],
      "supportsTargetedMessages": true,
      "commandLists": [
        {
          "scopes": ["personal", "team", "groupChat"],
          "triggers": ["slash", "mention"],
          "commands": [
            {
              "title": "status",
              "description": "Show the current project status"
            }
          ]
        }
      ]
    }
  ]
}
```

Teams delivers the selected command through the normal message route. The agent is responsible for parsing the message text and dispatching the command. Action-type message extension commands can also declare a `slash` trigger.

For command behavior, manifest options, and privacy guidance, see [Expose slash commands from agents and apps](https://learn.microsoft.com/en-us/microsoftteams/platform/agents-in-teams/agent-slash-commands).

## Message formatting and suggested actions

Use standard Agents SDK activities to send formatted text and suggested actions. Teams supports only a subset of Markdown and XML formatting, and displays at most three suggested actions.

- [Customize agent messages](https://learn.microsoft.com/en-us/microsoftteams/platform/bots/how-to/format-your-bot-messages)
- [Dynamically guide users with suggested actions](https://learn.microsoft.com/en-us/microsoftteams/platform/bots/how-to/conversations/suggested-actions)

## Related content

- [Teams extension overview](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/teams/teams-extension)
- [Handle meeting events](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/teams/teams-meetings)
- [Collect feedback](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/teams/teams-feedback)
- [Use Adaptive Cards in agents](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/adaptive-cards)
