<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/ux-custom-engine-agent -->
<!-- Sitemap-Last-Modified: 2025-11-19 -->

# Custom engine agent user experience features

Microsoft 365 Copilot is the user interface for AI. Custom engine agents are specialized chat experiences designed to harness the powerful capabilities of Large Language Models \(LLMs\) for seamless user interaction. Agents act as automated helpers that users interact with to perform tasks grounded in organizational data.

The agent user experience \(UX\) provides intuitive, efficient, and contextually relevant interactions to enhance user satisfaction and productivity. This article describes the native UX features on Copilot chat and Teams platform that you can apply and customize in your custom engine agents to enhance user interactions.

## Prompt starters

Prompt starters, also known as conversation starters, provide predefined prompts in your agent to help users initiate interactions. You can define the initial conversation messages in the latest `manifest.json`.

![A screenshot of zero prompt](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/agent-ux/zero-prompts.png)

For more information, see [Create prompt suggestions](https://learn.microsoft.com/en-us/microsoftteams/platform/bots/how-to/conversations/prompt-suggestions?context=/microsoft-365/copilot/extensibility/context).

## Suggested prompts

Suggested prompts guide users to the next best actions based on the conversation context, user profiles, and organizational preferences. These prompts replace the existing dynamic suggested actions functionality and can also be displayed within Adaptive Card responses.

![A screenshot of Suggested prompt](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/agent-ux/suggested-prompts.png)

For more information, see [Create prompt suggestions](https://learn.microsoft.com/en-us/microsoftteams/platform/bots/how-to/conversations/prompt-suggestions?context=/microsoft-365/copilot/extensibility/context).

## Streaming responses

Streaming responses are designed to enhance the user experience by providing visual real-time updates as the agent processes a request. This helps to prevent noticeable delays and makes interactions feel faster and more engaging.

![A screenshot of streaming response](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/agent-ux/streaming-response.png)

You can implement streaming responses by using the Teams SDK. For more information, see [Streaming messages](https://learn.microsoft.com/en-us/microsoftteams/platform/bots/streaming-ux?context=/microsoft-365/copilot/extensibility/context).

## Citations

Citations are references to the sources of information used by the agent to generate its responses. These citations help to ensure transparency, credibility, and trustworthiness in agent interactions.

![A screenshot of citations](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/agent-ux/citations.png)

Citations are returned by the model, and you can interact them with Teams SDK. For more information, see [Citations](https://learn.microsoft.com/en-us/microsoftteams/platform/bots/how-to/bot-messages-ai-generated-content#citations).

## AI labels

AI labels are automatically added to all agents' messages to indicate that Ai generated a response. This transparency helps users distinguish between AI-generated and human-generated content and fosters trust in agent responses. These labels are automatically added to AI-generated messages when you use the Teams SDK.

![A screenshot of AI labels](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/agent-ux/ai-labels.png)

For more information, see [Enhance AI-generated messages](https://learn.microsoft.com/en-us/microsoftteams/platform/bots/how-to/bot-messages-ai-generated-content#sensitivity-label?context=/microsoft-365/copilot/extensibility/context).

## Feedback loop

Feedback loops are mechanisms that allow users to provide feedback on an agent's responses. This feedback helps refine and improve the agent's performance over time to help it become more accurate and useful.

![A screenshot of feedback loop](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/agent-ux/feedback.png)

For more information, see [Feedback buttons](https://learn.microsoft.com/en-us/microsoftteams/platform/bots/how-to/bot-messages-ai-generated-content#feedback-buttons?context=/microsoft-365/copilot/extensibility/context).

## Asynchronous patterns

Custom engine agents can handle multiple tasks concurrently without blocking the main thread. Users can keep chatting with an agent while a task is in process, even when the task takes a few minutes or days. After the task is completed, the agent sends a notification to the user. These patterns are common scenarios for Teams bots, and are available in Copilot chat as well.

For more information, see [Implement asynchronous and proactive messaging in custom engine agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/custom-engine-agent-asynchronous-flow).

### Follow-up messages

Follow-up messages on user-initiated workflows keep users informed about the status of their requests or jobs. For example, an IT agent updates the user when a new laptop purchase request is approved.

Note

Custom engine agents build with Copilot Studio don't support asynchronous messages.

### Long-running task

Long-running tasks are another type of user-initiated workflow where a process takes a long time to complete. For instance, a business document management agent might handle batch processing of multiple contract documents. While the process is still running, the user can continue chatting since the messages are nonblocking.

To send a follow-up message or wait for a long-running task, you can use the turn context object's `SendActivity` \(or `SendActivityAsync` in C#\) in the `async`/`await` pattern with [Teams SDK](https://learn.microsoft.com/en-us/microsoftteams/platform/teams-ai-library/).

### Proactive messages

Proactive messages are agent-initiated messages based on predefined triggers; for example, sending reminders and alerts.

## Related content

- [Implement asynchronous and proactive messaging in custom engine agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/custom-engine-agent-asynchronous-flow)
- [Custom engine agent overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/overview-custom-engine-agent)
