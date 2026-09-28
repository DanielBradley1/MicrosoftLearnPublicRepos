<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/teams/teams-feedback -->
<!-- Sitemap-Last-Modified: 2026-08-25 -->

# Use AI citations and collect feedback in Microsoft Teams

AI responses commonly include citations and feedback controls. An AI engine can return source markers such as `[doc1]` in generated text. `StreamingResponse` converts those markers to numbered references, attaches the corresponding citation metadata, and adds thumbs-up and thumbs-down controls to the final message.

## Add citations and feedback to a streaming response

Add each citation in the same order as its marker in the generated text. When text is queued, the streaming response converts `[doc1]` or `[docs1]` to `[1]` by using `CitationUtils.FormatCitationsResponse`. You typically don't need to call the formatting utility directly.

```csharp
using Microsoft.Agents.Core.Models;

var citations = new List<Citation>
{
    new(
        content: "Contoso offers 30 days of annual leave.",
        title: "Contoso employee handbook",
        url: "https://www.example.com/handbook")
};

turnContext.StreamingResponse.FeedbackLoopEnabled = true;
turnContext.StreamingResponse.EnableGeneratedByAILabel = true;

turnContext.StreamingResponse.QueueTextChunk(
    "Contoso employees receive 30 days of annual leave [doc1].");

turnContext.StreamingResponse.AddCitations(citations);

await turnContext.StreamingResponse.EndStreamAsync(cancellationToken);
```

Use `AddCitation(citation, position)` when you need to assign a specific reference number. Use `AddCitations(citations)` to number a collection in list order.

```javascript
context.streamingResponse.setFeedbackLoop(true)

context.streamingResponse.queueTextChunk(
  'Contoso employees receive 30 days of annual leave [doc1].'
)

context.streamingResponse.setCitations([
  {
    content: 'Contoso offers 30 days of annual leave.',
    title: 'Contoso employee handbook',
    url: 'https://www.example.com/handbook',
    filepath: null
  }
])

await context.streamingResponse.endStream()
```

```python
from microsoft_agents.hosting.core import Citation

context.streaming_response.set_feedback_loop(True)

context.streaming_response.queue_text_chunk(
    "Contoso employees receive 30 days of annual leave [doc1]."
)

context.streaming_response.set_citations(
    [
        Citation(
            content="Contoso offers 30 days of annual leave.",
            title="Contoso employee handbook",
            url="https://www.example.com/handbook",
        )
    ]
)

await context.streaming_response.end_stream()
```

## Handle submitted feedback

Register an `AgentApplication.OnFeedbackLoop` handler in the agent constructor:

```csharp
public MyAgent(AgentApplicationOptions options) : base(options)
{
    OnFeedbackLoop(OnFeedbackAsync);
}

private Task OnFeedbackAsync(
    ITurnContext turnContext,
    ITurnState turnState,
    FeedbackData feedbackData,
    CancellationToken cancellationToken)
{
    var reaction = feedbackData.ActionValue?.Reaction;
    var feedbackText = feedbackData.ActionValue?.Feedback;
    var activityId = feedbackData.ReplyToId;

    // Store or process the feedback for the referenced activity.
    return Task.CompletedTask;
}
```

```javascript
import { onTeamsFeedbackLoop } from '@microsoft/agents-hosting-extensions-msteams'

onTeamsFeedbackLoop(app, async (context, state, feedbackData) => {
  const reaction = feedbackData.actionValue?.reaction
  const feedbackText = feedbackData.actionValue?.feedback
  const activityId = feedbackData.replyToId

  // Store or process the feedback for the referenced activity.
})
```

The Python SDK can enable feedback controls on a streaming response. A typed incoming feedback route isn't currently exposed.

The value in `FeedbackData.ActionValue.Reaction` represents the thumbs-up or thumbs-down feedback selection. It's separate from an emoji message reaction activity.

## Handle message reactions

Message reactions are emoji reactions that users add to or remove from a message. They arrive as message reaction activities rather than feedback-loop submissions.

Register the standard `AgentApplication` message reaction routes:

```csharp
public MyAgent(AgentApplicationOptions options) : base(options)
{
    OnMessageReactionsAdded(OnReactionsAddedAsync);
    OnMessageReactionsRemoved(OnReactionsRemovedAsync);
}

private Task OnReactionsAddedAsync(
    ITurnContext turnContext,
    ITurnState turnState,
    CancellationToken cancellationToken)
{
    foreach (var reaction in turnContext.Activity.ReactionsAdded)
    {
        // Process reaction.Type for turnContext.Activity.ReplyToId.
    }

    return Task.CompletedTask;
}

private Task OnReactionsRemovedAsync(
    ITurnContext turnContext,
    ITurnState turnState,
    CancellationToken cancellationToken)
{
    foreach (var reaction in turnContext.Activity.ReactionsRemoved)
    {
        // Process reaction.Type for turnContext.Activity.ReplyToId.
    }

    return Task.CompletedTask;
}
```

```javascript
import {
  onTeamsMessageReactionsAdded,
  onTeamsMessageReactionsRemoved
} from '@microsoft/agents-hosting-extensions-msteams'

onTeamsMessageReactionsAdded(app, async (context) => {
  for (const reaction of context.activity.reactionsAdded ?? []) {
    // Process reaction.type for context.activity.replyToId.
  }
})

onTeamsMessageReactionsRemoved(app, async (context) => {
  for (const reaction of context.activity.reactionsRemoved ?? []) {
    // Process reaction.type for context.activity.replyToId.
  }
})
```

A typed Teams message reaction route isn't currently exposed in the Python SDK.

For supported reaction types and client behavior, see:

- [Build agents that use emoji reactions in Teams chat](https://learn.microsoft.com/en-us/microsoftteams/platform/agents-in-teams/agent-reactions)
- [Teams reactions reference](https://learn.microsoft.com/en-us/microsoftteams/platform/agents-in-teams/teams-reactions-reference)

## Related content

- [Teams extension overview](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/teams/teams-extension)
- [Handle Teams messages](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/teams/teams-messages)
- [Handle meeting events](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/teams/teams-meetings)
- [Use Adaptive Cards in agents](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/adaptive-cards)
