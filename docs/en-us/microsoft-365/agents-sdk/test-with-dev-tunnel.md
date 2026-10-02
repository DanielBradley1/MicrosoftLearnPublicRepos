<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/test-with-dev-tunnel -->
<!-- Sitemap-Last-Modified: 2026-08-25 -->

# Test a local agent with a dev tunnel

A dev tunnel gives Azure Bot Service a public HTTPS endpoint that forwards requests to your locally running agent. Use a tunnel when you need to test through Microsoft Teams, Microsoft Copilot, or another channel that can't connect directly to `localhost`.

For tests that don't require a hosted channel, use [Microsoft 365 Agents Playground](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/test-with-toolkit-project) instead.

## Prerequisites

Before you start:

- Run your agent locally and identify its port. Agents SDK samples use port `3978` by default.
- [Provision an Azure Bot resource](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/provision-azure-bot-service-manually) and enable the channel you want to test.
- [Configure the agent connection](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/configure-authentication-msal) with credentials that match the Azure Bot resource.
- Install the `devtunnel` CLI. For installation options on Windows, macOS, and Linux, see [Create and host a tunnel](https://learn.microsoft.com/en-us/azure/developer/dev-tunnels/get-started#install).

Important

Use a client secret or certificate for local testing through a dev tunnel. Managed identity and federated credentials require the agent code to run in its configured Azure hosting environment.

## Start the agent

Run the agent and verify that its activity endpoint is listening locally. The default endpoint is:

```text
http://localhost:3978/api/messages
```

If your project uses another port or route, use that value in the following steps.

## Create and host the tunnel

Sign in to dev tunnels:

```bash
devtunnel user login
```

Host the local agent port:

```bash
devtunnel host -p 3978 --allow-anonymous
```

`--allow-anonymous` allows Azure Bot Service to reach the public tunnel endpoint. Agent authentication still validates requests at `/api/messages`.

The command returns a public URL similar to:

```text
https://<tunnel-id>-3978.<region>.devtunnels.ms
```

Keep the command running while you test.

## Configure the Azure Bot messaging endpoint

1. In the Azure portal, open your Azure Bot resource.
2. Select **Settings** > **Configuration**.
3. Set **Messaging endpoint** to the public tunnel URL followed by your agent route:

   ```text
   https://<tunnel-id>-3978.<region>.devtunnels.ms/api/messages
   ```

4. Save the configuration.

If the tunnel URL changes, update the messaging endpoint before testing again. You can create a persistent named tunnel if you need a stable URL; see the [dev tunnels CLI reference](https://learn.microsoft.com/en-us/azure/developer/dev-tunnels/cli-commands).

## Test through the channel

Send a message to the agent from the configured channel. The request flows from the channel to Azure Bot Service, through the dev tunnel, and into the local `/api/messages` endpoint.

Use the dev tunnel inspect URL shown by the CLI to diagnose whether requests reach the tunnel. Use your agent logs to diagnose authentication, routing, and handler errors after the request reaches the local process.

Warning

A public tunnel exposes the selected local port to the internet. Run only the service you intend to test, keep authentication enabled, and stop the tunnel when testing is complete.
