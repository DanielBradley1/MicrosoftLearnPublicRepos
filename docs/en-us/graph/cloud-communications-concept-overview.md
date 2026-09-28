<!-- Source: https://learn.microsoft.com/en-us/graph/cloud-communications-concept-overview -->
<!-- Sitemap-Last-Modified: 2024-11-07 -->

# Cloud communications API overview

The cloud communications API in Microsoft Graph adds a new dimension to how your apps and services interact with users through various communications-related features, such as calling and online meetings. Grow your business by expediting how you respond to your customers’ needs and how your employees collaborate with each other.

To discover the benefits of using the cloud communications API to build service applications \([bots](https://microsoftgraph.github.io/microsoft-graph-comms-samples/docs/articles/calls/register-calling-bot.html?q=create%20bot)\), see the following sections.

## Handle incoming calls

It can be overwhelming at times when workers receive a lot of business calls and it isn't possible, or productive, to answer all of them. A bot can serve as a front-desk assistant and handle these calls by rejecting what seem like spam calls, and redirecting \(forwarding\) specific calls to a different number.

You can use the cloud communications API to:

- Have a user [call a bot](https://learn.microsoft.com/en-us/graph/api/application-post-calls) through VoIP.
- Have a bot [redirect the incoming call](https://learn.microsoft.com/en-us/graph/api/call-redirect) to the appropriate agent if necessary.
- Have a bot [answer](https://learn.microsoft.com/en-us/graph/api/call-answer) or [reject](https://learn.microsoft.com/en-us/graph/api/call-reject) the call.

## Simplify the customer service experience

Whether you own a large helpdesk service or a small storefront, it can be difficult to handle multiple customer requests, especially if you don’t have any context of what problem they’re trying to solve beforehand. Handle incoming calls from customers through an **Interactive Voice Response** \(IVR\) system, where a bot will initially interact with them.

When a customer is prompted for a response from the bot, the customer can press a key on their keypad that corresponds to their selection. The bot can then gather the dial-tone multi-frequency \(DTMF\) from the customer.

You can use the cloud communications API to build a bot that:

- [Answers a call](https://learn.microsoft.com/en-us/graph/api/call-answer) from a customer.
- [Plays a prompt](https://learn.microsoft.com/en-us/graph/api/call-playprompt) to inform and prompt a customer for a selection.
- [Subscribes to a tone](https://learn.microsoft.com/en-us/graph/api/call-subscribetotone) to gather the DTMF from a customer.
- [Transfers a customer](https://learn.microsoft.com/en-us/graph/api/call-transfer) to an agent.
- [Ends a call](https://learn.microsoft.com/en-us/graph/api/call-delete) with a customer.

![Image of a bot providing options for call transfer](https://learn.microsoft.com/en-us/graph/images/communications-ivr-transfer.png)

To create a more intelligent interaction between your customers and your bot, when a customer is prompted for a response, they will be able to directly speak about what they need help with.

Integrating with a natural language processing service means that the customer's speech can be analyzed for its sentiment. The bot can then respond to the customer's need accordingly.

Note

You might not record or otherwise persist media content from calls or meetings that your application accesses, or data derived from that media content. Make sure you are compliant with the laws and regulations of your area regarding data protection and confidentiality of communications. Please see the [Terms of Use](https://learn.microsoft.com/en-us/legal/microsoft-apis/terms-of-use) and consult with your legal counsel for more information.

You can use the cloud communications API to build a bot that:

- [Answers a call](https://learn.microsoft.com/en-us/graph/api/call-answer) from a customer.
- [Plays a prompt](https://learn.microsoft.com/en-us/graph/api/call-playprompt) to inform and prompt the customer to speak.
- [Records a short audio clip](https://learn.microsoft.com/en-us/graph/api/call-record) of a customer speaking.
- [Plays a prompt](https://learn.microsoft.com/en-us/graph/api/call-playprompt) with the appropriate response to the customer, after their speech is analyzed.

![Image of a bot that prompts a user to give a voice response](https://learn.microsoft.com/en-us/graph/images/communications-ivr.png)

## Collaborate through group calls

Enable users to engage with coworkers or customers by creating a group call so that everyone can contribute to the conversation.

You can use the cloud communications API to build a bot that:

- [Creates a group call](https://learn.microsoft.com/en-us/graph/api/application-post-calls#example-3-create-a-group-call-with-service-hosted-media) with multiple participants.
- [Invites another bot or user](https://learn.microsoft.com/en-us/graph/api/participant-invite) to an existing group call.
- [Joins an existing group call](https://learn.microsoft.com/en-us/graph/api/application-post-calls#example-5-join-scheduled-meeting-with-service-hosted-media) as a bot.
- [Lists the participants](https://learn.microsoft.com/en-us/graph/api/call-list-participants) in the group call.
- [Mutes another participant](https://learn.microsoft.com/en-us/graph/api/participant-mute).

## Send reminders reliably

To enable users to send customers a reminder for an appointment or a reminder for a payment deadline that’s approaching, you can have a bot call the customer automatically.

You can use the cloud communications API to build a bot that:

- [Calls a customer](https://learn.microsoft.com/en-us/graph/api/application-post-calls) on Teams.
- [Plays a recorded prompt](https://learn.microsoft.com/en-us/graph/api/call-playprompt) to serve as a reminder.
- [Ends the call](https://learn.microsoft.com/en-us/graph/api/call-delete).

## Set up online meetings

Whether scheduling a meeting between a doctor and a patient or between a user and their direct reports, you can build solutions that generate meetings that users can rely on. For added flexibility, users can call other users and invite them to the meeting while it's ongoing.

You can use the cloud communications API to:

- Have a user [create an online meeting](https://learn.microsoft.com/en-us/graph/api/application-post-onlinemeetings).
- Have a user [retrieve the details](https://learn.microsoft.com/en-us/graph/api/onlinemeeting-get) of an online meeting.
- Have a bot or a user [join an online meeting](https://learn.microsoft.com/en-us/graph/api/application-post-calls#example-5-join-scheduled-meeting-with-service-hosted-media).

## API reference

Looking for the API reference for this service?

- [Cloud communications API in Microsoft Graph v1.0](https://learn.microsoft.com/en-us/graph/api/resources/communications-api-overview?view=graph-rest-1.0&preserve-view=true)
- [Cloud communications API in Microsoft Graph beta](https://learn.microsoft.com/en-us/graph/api/resources/communications-api-overview?view=graph-rest-beta&preserve-view=true)

## Related content

- Use bots to [get started](https://learn.microsoft.com/en-us/graph/cloud-communications-get-started).
- Learn more about [calls](https://learn.microsoft.com/en-us/graph/cloud-communications-calls), [media](https://learn.microsoft.com/en-us/graph/cloud-communications-media), and [online meetings](https://learn.microsoft.com/en-us/graph/cloud-communications-online-meetings).
- View the API usage [limits](https://learn.microsoft.com/en-us/graph/throttling-limits#cloud-communication-service-limits).
- Learn how to [manage phone numbers](https://learn.microsoft.com/en-us/graph/cloud-communications-phone-number) for your bots.
- [Cloud communications API samples](https://github.com/microsoftgraph/microsoft-graph-comms-samples)
