<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/test-with-toolkit-project -->
<!-- Sitemap-Last-Modified: 2026-07-28 -->

# Test your agent locally in Microsoft 365 Agents Playground

The details of how to test your agent locally depend on how you created your agent.

You can create an agent using the Microsoft 365 Agents SDK in three ways:

- Start with the Microsoft 365 Agents Toolkit in C#, JavaScript, or Python using Visual Studio or Visual Studio Code
- Clone from a sample and open in your IDE
- Use the CLI

## Start your project with the toolkit

If you start with the Agents Toolkit, you have everything set up to test by using the Agents Playground straight away. You can test in the Agents Playground either locally, or in Microsoft Copilot or Microsoft Teams. This scenario is covered in:

- [Visual Studio Code walkthrough](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/create-new-toolkit-project-vsc)
- [Visual Studio walkthrough](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/create-new-toolkit-project-vs)

## Start your project by cloning or with the CLI

If you start your project by using the CLI or clone a sample and open in your IDE, you can use the local Agents Playground to test. The Agents Playground connects to your local code.

You can install the Agents Playground by using one of the following methods:

### Option 1: Install the standalone binary

- [Windows](#tabpanel_1_windows)
- [Linux](#tabpanel_1_linux)

```cmd
winget install agentsplayground
```

```bash
curl -s https://raw.githubusercontent.com/OfficeDev/microsoft-365-agents-toolkit/dev/.github/scripts/install-agentsplayground-linux.sh | bash
```

### Option 2: Install using npm

- Install Node.js \(if not already installed\): Download and install the latest Node.js from [nodejs.org](https://nodejs.org/).
- Install the Agents Playground package:

  For global installation \(recommended\):

  ```bash
  npm install -g @microsoft/m365agentsplayground
  ```


  For project-specific installation:


  ```bash
  npm install -D @microsoft/m365agentsplayground
  ```

## Test your agent

1. After you create your quickstart agent or clone a sample from the repo, use it with the Agents Playground.
2. The Agents Playground supports both anonymous and authenticated modes. For anonymous testing, no other configuration is required. If you want to test with authentication, you need to configure Microsoft Entra ID app registrations for both the Agents Playground \(options are provided in the text that follows\) and your application. For information, see [Provisioning an Azure Bot to use with Agents SDK](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/provision-azure-bot-service-manually).
3. Configure your ports correctly in your app. Select an available port for your agent \(the default is 3978, but you can use any available port\).
4. Run your code.
5. Open the Agents Playground and start with your agent's endpoint:

   ```bash
   agentsplayground -e "http://localhost:<your-agent-port>/api/messages" -c "emulator"
   ```


   Configure authentication if required by your agent:


   ```bash
   agentsplayground -e "http://localhost:<your-agent-port>/api/messages" -c "emulator" --client-id "your-client-id" --client-secret "your-client-secret" --tenant-id "your-tenant-id"
   ```


   Key options:


   - `-e, --app-endpoint`: Your agent's endpoint URL \(for example, `http://localhost:3978/api/messages`\)
   - `-c, --channel-id`: Channel type \(for example, `emulator`, `webchat`, `msteams`\). Each channel provides different user experience and activity properties.
   - `--client-id`: Client ID for authentication
   - `--client-secret`: Client secret for authentication
   - `--tenant-id`: Tenant ID for authentication


   Use `agentsplayground --help` to see the full list of available options.


   Alternatively, you can use environment variables instead of CLI options. If both are specified, the CLI option has higher priority.


   ```bash
   export BOT_ENDPOINT="http://localhost:<your-agent-port>/api/messages"
   export DEFAULT_CHANNEL_ID="emulator"
   export AUTH_CLIENT_ID="your-client-id"
   export AUTH_CLIENT_SECRET="your-client-secret"
   export AUTH_TENANT_ID="your-tenant-id"
   ```


   When your agent starts, it opens as seen in the following image. You can ask questions and test your agent in the playground interface.


   ![Microsoft 365 Agents Playground](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/media/toolkit-project-vsc/vsc-toolkit-teams-app-test-tool.png)

Wherever possible, start with the Microsoft 365 Agents Toolkit. The toolkit makes getting started, testing locally, and deploying *easier and quicker*. It abstracts much of the manual setup of the Azure Bot Service and Azure App registrations so you don't have to. By starting manually, you must perform these manual steps yourself.

## Summary

You tested your Microsoft 365 Agents SDK locally by using the Microsoft 365 Agents Playground. You started with a cloned sample from the GitHub repo or from the CLI.
