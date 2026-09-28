<!-- Source: https://learn.microsoft.com/en-us/graph/cloud-communications-calls -->
<!-- Sitemap-Last-Modified: 2024-11-07 -->

# Supported call types

This article describes the supported call types in the cloud communications API in Microsoft Graph and how they're used for the signaling process.

## Peer-to-peer calls

A call is peer-to-peer \(P2P\) when one participant is directly calling another participant. If a bot calls a user, and the user is the only calling target specified, this is an example of a P2P call.

![P2P call diagram](https://learn.microsoft.com/en-us/graph/images/communications-p2p-call.png)

If a user wants to call a bot, the bot doesn't need any additional permissions in order to respond to the P2P call. In order for a bot to call a user, it must have the Calls.Initiate.All permission for a P2P call.

## Group calls

A group call occurs if there are either three or more participants in the call, or if [meeting coordinates](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeeting) were specified when the call was initially created.

You can create a group call through Microsoft Teams, for example.

![Group call diagram](https://learn.microsoft.com/en-us/graph/images/communications-group-call.png)

Currently, bots are able to:

- Create group calls
- Join exisiting group calls
- Invite other participants into an existing group call
- Be invited into existing group calls

## Related content

- [Teams API overview](https://learn.microsoft.com/en-us/graph/teams-concept-overview)
- [Permissions for calls](https://learn.microsoft.com/en-us/graph/permissions-reference)
