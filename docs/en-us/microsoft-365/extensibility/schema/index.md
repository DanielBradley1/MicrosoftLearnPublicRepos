<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# Microsoft 365 app manifest schema reference

The app manifest for Microsoft 365 is a JSON file that describes the functionality and configuration of your app, and how it integrates with Microsoft 365 products, including Microsoft 365 Copilot, Teams, Outlook, and more.

The app manifest is part of the unified Microsoft 365 app package: a simple zip folder that includes app manifest, icons, and optional Copilot agent manifest definitions. Using a common packaging format, you can submit Microsoft 365 Copilot agents, Teams apps, SharePoint Framework apps, Graph connectors, and Office Add-ins to the [Microsoft 365 and Copilot program](https://learn.microsoft.com/en-us/partner-center/marketplace-offers/add-in-submission-guide) in Microsoft Partner Center as a Store offer, or submit directly to your organization's app catalog. Microsoft 365 apps are centrally deployed and managed from the [Integrated Apps](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/test-and-deploy-microsoft-365-apps) portal of Microsoft 365 admin center.

## What's new in manifest version 1.30

August 2026

```http
https://developer.microsoft.com/json-schemas/teams/v1.30/MicrosoftTeams.schema.json
```

Added support for Encryption-Decryption feature for Outlook Add-ins using the new [`headerName`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-auto-run-events-array-events-options?view=m365-app-1.30#headername) and [`sendMode`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-auto-run-events-array-events-options?view=m365-app-1.30#sendmode) properties.

## All generally available versions

  


<details>
<summary>**Version 1.29**</summary>

### Version 1.29

June 2026

```http
https://developer.microsoft.com/json-schemas/teams/v1.29/MicrosoftTeams.schema.json
```

- Enabled [human to agent one-turn conversation](https://learn.microsoft.com/en-us/microsoftteams/platform/agents-in-teams/targeted-messages) and add a new property [triggers](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-compose-extensions-commands?view=m365-app-1.30#triggers).
- Added support for dynamic tool discovery that allows Microsoft 365 agents to fetch the MCP server's tool list at runtime by calling the server's `tools/list` method. To enable dynamic discovery, provide the `remoteServerURL` and omit the [`mcpToolDescription`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-connectors-tool-source-remote-mcp-server?view=m365-app-1.30) property.
- Added support for Azure Key Vault authentication using [`AzureKeyVault`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-connectors-tool-source-remote-mcp-server-authorization?view=m365-app-1.30) property that allows you to store and manage your MCP server credentials in your own [Azure Key Vault](https://learn.microsoft.com/en-us/microsoftteams/platform/m365-apps/agent-connectors#configure-authentication) instance. This gives you full control over secret lifecycle management, including rotation, access policies, and audit logging.
</details>

  


<details>
<summary>**Version 1.28**</summary>

### Version 1.28

May 2026

```http
https://developer.microsoft.com/json-schemas/teams/v1.28/MicrosoftTeams.schema.json
```

- Expanded the range of icons array for extension tab groups \([extensionRibbonsCustomTabGroupsItem](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-custom-tab-groups-item?view=m365-app-1.30) object\) to minItems = 3 \(from 1\) and maxItems = 8 \(from 3\).
- Enable Office Add-ins to show or hide ribbon buttons, controls, and groups in custom or contextual tabs across Word, Excel, and PowerPoint \(Win32, Mac, Web\) using the new property [visible](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-array-tabs-item?view=m365-app-1.30#visible) for dynamic UI and less clutter.
- The [`agentSkills`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-skills?view=m365-app-1.30#rootagentskills-object) property allows developers to package AI agent skills as elements.
</details>

  


<details>
<summary>**Version 1.27**</summary>

### Version 1.27

May 2026

```http
https://developer.microsoft.com/json-schemas/teams/v1.27/MicrosoftTeams.schema.json
```

- Added [agent connectors](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-connectors) node to enable [configuration of connections](https://learn.microsoft.com/en-us/microsoftteams/platform/m365-apps/agent-connectors) between Microsoft 365 agents and external data sources through MCP servers.
- Added a new command [type](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-command-lists-commands) and a new property [prompt](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-command-lists-commands) under bots commands.
</details>

  


<details>
<summary>**Version 1.26**</summary>

### Version 1.26

April 2026

```http
https://developer.microsoft.com/json-schemas/teams/v1.26/MicrosoftTeams.schema.json
```

- Added optional [composeExtensions.authorization.oAuthConfiguration](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-compose-extensions-authorization-o-auth-configuration) object to implement [Open Authorization \(OAuth\) 2.0 support for API-based message extensions](https://learn.microsoft.com/en-us/microsoftteams/platform/messaging-extensions/api-based-oauth).
- Added [features](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-description) descriptions list to [showcase agent and app features to a profile card](https://learn.microsoft.com/en-us/microsoftteams/platform/bots/how-to/teams-conversational-ai/ai-ux) that appears when the user hovers over the app icon.
- [KeyTips](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-custom-control-menu-item) let developers set custom shortcut keys in Office, giving users more efficient ways to work in Word, Excel, and PowerPoint.
</details>

  


<details>
<summary>**Version 1.25**</summary>

### Version 1.25

January 2026

```http
https://developer.microsoft.com/json-schemas/teams/v1.25/MicrosoftTeams.schema.json
```

- New [agenticUserTemplates](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root?view=m365-app-1.30#agenticusertemplates) node to reference an [Agent 365 blueprint](https://learn.microsoft.com/en-us/microsoft-agent-365/developer/registration), enabling the instantiation of an AI agent with its own Microsoft Entra Agent ID within your organization.
- Added [supportsChannelFeatures](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root?view=m365-app-1.30#supportschannelfeatures) to opt in your app to [next level channel features, including shared and private channels](https://learn.microsoft.com/en-us/microsoftteams/platform/build-apps-for-shared-private-channels).
- Enhanced support for Excel custom functions, including [customFunctions.enum](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/enum?view=m365-app-1.30) to provide [autocomplete options for custom functions](https://learn.microsoft.com/en-us/office/dev/add-ins/excel/custom-functions-custom-enums) and additional [function properties](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-function?view=m365-app-1.30#properties) and datatypes from [CustomFunctionsRuntime 1.5](https://learn.microsoft.com/en-us/javascript/api/requirement-sets/excel/custom-functions-requirement-sets).
</details>

  


<details>
<summary>**Version 1.24**</summary>

### Version 1.24

October 2025

```http
https://developer.microsoft.com/json-schemas/teams/v1.24/MicrosoftTeams.schema.json
```

- Added [executeDataFunction](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-runtimes-actions-item?view=m365-app-1.30#type) action type to enable Copilot agents to invoke Office Add-ins functions and serve as [natural language interfaces to add-ins](https://learn.microsoft.com/en-us/office/dev/add-ins/design/agent-and-add-in-overview). The overall functionality of combining Copilot agents with Office Add-ins remains in preview.
- Introduced [windowsExtensions](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-alternate-versions-array-hide-windows-extensions?view=m365-app-1.30) mechanism to specify which COM- and VSTO-based add-ins should be disabled with the equivalent JavaScript add-in is installed. For more details, see [Option to disable the Windows-only add-in instead](https://learn.microsoft.com/en-us/office/dev/add-ins/develop/make-office-add-in-compatible-with-existing-com-add-in#option-to-disable-the-windows-only-add-in-instead-preview).
- Added [keyboardShortcuts](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-keyboard-shortcut?view=m365-app-1.30) to support [backwards compatibility of Office Add-ins with keyboard shortcuts](https://learn.microsoft.com/en-us/office/dev/add-ins/design/keyboard-shortcuts#support-backward-compatibility-for-add-ins-with-a-unified-manifest-in-appsource) and their localized strings \(if applicable\).
- Increased [bot commands](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-command-lists?view=m365-app-1.30#commands) limit from 10 to 12 to accommodate Microsoft Copilot Studio agents, which support up to 12 starter prompts.

  

</details>

  


<details>
<summary>**Version 1.23**</summary>

### Version 1.23

July 2025

```http
https://developer.microsoft.com/json-schemas/teams/v1.23/MicrosoftTeams.schema.json
```

- Updated `extensionRibbonsCustomTabGroupsItem` to include the [`overriddenByRibbonApi` property](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-custom-tab-groups-item?view=m365-app-1.30#overriddenByRibbonApi-property), which hides groups in apps that support custom contextual tabs via the `Office.ribbon.requestCreateControls` API. Removed redundant node `extensionCommonCustomControlMenu`.
- Added bot [`registrationInfo`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-registration-info?view=m365-app-1.30) field to accommodate system-generated metadata for agents built with Microsoft Copilot Studio and other tools.
- Improved description for [`spamReportingOptions`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-spam-pre-processing-dialog?view=m365-app-1.30#spamReportingOptions-property)

  

</details>

  


<details>
<summary>**Version 1.22**</summary>

### Version 1.22

May 2025

```http
https://developer.microsoft.com/json-schemas/teams/v1.22/MicrosoftTeams.schema.json
```

- Added [`activityIcons`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-activities-activity-icons?view=m365-app-1.30) and [`allowedIconIds`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-activities-activity-types?view=m365-app-1.30#allowedIconIds-property) properties to customize app icons in a user's activity feed. `activityIcons` defines the icon, while `allowedIconIds` specifies which icons appear for each activity type. For more information, see the [Teams activity feed](https://learn.microsoft.com/en-us/graph/teams-send-activityfeednotifications) and [custom icon guidelines](https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines#custom-activity-icons).
- Added the [`type property`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-spam-pre-processing-dialog-spam-reporting-options?view=m365-app-1.30#type-property) to the spam reporting preprocessing dialog to support either radio buttons or checkboxes for reporting options. For details, see [Configure the manifest](https://learn.microsoft.com/en-us/office/dev/add-ins/outlook/spam-reporting#configure-the-manifest).
- Added [`nestedAppAuthInfo`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-web-application-info?view=m365-app-1.30#nestedAppAuthInfo-property) property to enable prefetching of a nested app authentication token when a tab is loads. To details more, see [Nested app authentication](https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/authentication/nested-authentication).

  

</details>

  


<details>
<summary>**Version 1.21**</summary>

### Version 1.21

April 2025

```http
https://developer.microsoft.com/json-schemas/teams/v1.21/MicrosoftTeams.schema.json
```

- Developers can now specify a [32x32 color icon](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-icons?view=m365-app-1.30#color32x32) with a transparent background to ensure a consistent appearance when your app runs in Outlook and Microsoft 365. To learn more see,[Teams app package color icon](https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/build-and-test/apps-package#color-icon).
- Introduced new *copilot* value for [`bots.scopes`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots?view=m365-app-1.30#scopes) and [`defaultInstallScope`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root?view=m365-app-1.30#defaultinstallscope). To learn more, see [Build with Teams AI library](https://learn.microsoft.com/en-us/microsoftteams/platform/bots/how-to/teams-conversational-ai/how-conversation-ai-get-started).
- Added [`backgroundLoadConfiguration`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-background-load-configuration?view=m365-app-1.30) object to enable tab apps to [opt in to precaching](https://learn.microsoft.com/en-us/microsoftteams/platform/tabs/how-to/app-caching#enable-precaching-for-tab-app) for a faster initial load experience.

  

</details>

  


<details>
<summary>**Version 1.20**</summary>

### Version 1.20

March 2025

```http
https://developer.microsoft.com/json-schemas/teams/v1.20/MicrosoftTeams.schema.json
```

- Added [`elementRelationshipSet`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-element-relationship-set?view=m365-app-1.30) and [`requirementSet`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/element-requirement-set?view=m365-app-1.30) \(for `composeExtensions`, `bots`, and `staticTabs`\) objects so that apps can specify [runtime requirements in Microsoft 365 hosts](https://learn.microsoft.com/en-us/microsoftteams/platform/m365-apps/specify-runtime-requirements).
- Added [`intuneInfo`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-intune-info?view=m365-app-1.30) object for [Outlook Add-ins to attest to Intune Mobile App Management \(MAM\) support](https://learn.microsoft.com/en-us/javascript/api/outlook/office.mailbox) in order to signal compliance with organizational data protection policies.
- Added [`fixedControls`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-array-fixed-control-item?view=m365-app-1.30) object to build custom [spam-reporting handling with Outlook Add-ins](https://learn.microsoft.com/en-us/office/dev/add-ins/outlook/spam-reporting).

  

</details>

  


<details>
<summary>**Version 1.19**</summary>

### Version 1.19

September 2024

```http
https://developer.microsoft.com/json-schemas/teams/v1.19/MicrosoftTeams.schema.json
```

- Added [`copilotAgents`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-copilot-agents?view=m365-app-1.30) object for publishing [declarative agents for Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/overview-declarative-agent).
- Added [`defaultLanguageFile`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-localization-info?view=m365-app-1.30#defaultlanguagefile), a new required property for [Copilot agents that support multiple languages](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/localize-agents).

  

</details>

  


<details>
<summary>**Version 1.18** *Not available.*</summary>
</details>

  


<details>
<summary>**Version 1.17**</summary>

### Version 1.17

April 2024

```http
https://developer.microsoft.com/json-schemas/teams/v1.17/MicrosoftTeams.schema.json
```

- Added support for [mobile specific manifest elements for Outlook extensions](https://learn.microsoft.com/en-us/office/dev/add-ins/outlook/outlook-mobile-addins).
- Added `semanticDescription` field for Copilot for Microsoft 365. [Learn more](https://learn.microsoft.com/en-us/microsoftteams/platform/messaging-extensions/high-quality-message-extension?tabs=tasks#semantic-description).
- Added support for [creating message extensions](https://learn.microsoft.com/en-us/microsoftteams/platform/messaging-extensions/api-based-overview) from an existing API.
- Added apps to easily show as cards on [Viva Connections Dashboard](https://learn.microsoft.com/en-us/sharepoint/dev/spfx/viva/bot-powered/overview-bot-powered-aces).
- Added new [sample prompts](https://learn.microsoft.com/en-us/microsoftteams/platform/messaging-extensions/high-quality-message-extension?tabs=tasks#sample-prompts) to guide users who install or enable a plugin for the first time.
- Added [bot configurations](https://learn.microsoft.com/en-us/microsoftteams/platform/bots/how-to/bot-configuration-experience) changes.
- Deprecated `packageName` property.
- Deprecated `callingSidePanel` from manifest.

  

</details>

  


<details>
<summary>**Version 1.16**</summary>

### Version 1.16

February 2023

```http
https://developer.microsoft.com/json-schemas/teams/v1.16/MicrosoftTeams.schema.json
```

- Added `supportsAnonymousGuestUsers` in `meetingExtensionDefinition`.
- Added `team` and `groupChat` to the scope of staticTab.
- Added `privateChatTab`, `meetingChatTab`, `meetingDetailsTab`, `meetingSidePanel`, `meetingStage`, `teamLevelApp` to the context of staticTab.

  

</details>

  


<details>
<summary>**Version 1.15**</summary>

### Version 1.15

November 2022

```http
https://developer.microsoft.com/json-schemas/teams/v1.15/MicrosoftTeams.schema.json
```

- Added `supportsAnonymizedPayloads` feature. A Boolean that indicates whether the app's link message handler supports anonymous invoke flow.

  

</details>

  


<details>
<summary>**Version 1.14**</summary>

### Version 1.14

July 2022

```http
https://developer.microsoft.com/json-schemas/teams/v1.14/MicrosoftTeams.schema.json
```

- Added `supportedChannelTypes` feature. List of 'nonstandard' channel types that the app supports. Note: Channels of standard type are supported by default if the app supports team scope.
- Added `supportsStreaming`feature. A Boolean value indicating whether this app can stream the meeting's audio video content to a Real-Time Messaging Protocol \(RTMP\) endpoint.

  

</details>

  


<details>
<summary>**Version 1.13**</summary>

### Version 1.13

May 2022

```http
https://developer.microsoft.com/json-schemas/teams/v1.13/MicrosoftTeams.schema.json
```

With the release of version 1.13 of the App manifest, developers can build and update their app \(formerly Teams app\) to run in Microsoft 365 hosts such as Outlook, Teams, and Microsoft Teams App across web, desktop, and mobile. From this version release, it eases deployment workflow and provides a streamlined way to deliver cross-platform apps to an expanded user audience via a single codebase. For more details on host application feature support, visit [TeamsJS capability support across Microsoft 365](https://learn.microsoft.com/en-us/microsoftteams/platform/m365-apps/teamsjs-support-m365).

- This schema version supports extending Teams apps to other parts of the Microsoft 365 ecosystem. More info at [https://aka.ms/extendteamsapps](https://aka.ms/extendteamsapps).

  

</details>

## What's new in manifest version 1.29

June 2026

```http
https://developer.microsoft.com/json-schemas/teams/v1.29/MicrosoftTeams.schema.json
```

- Enabled [human to agent one-turn conversation](https://learn.microsoft.com/en-us/microsoftteams/platform/agents-in-teams/targeted-messages) and add a new property [triggers](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-compose-extensions-commands?view=m365-app-1.30#triggers)
- Added support for dynamic tool discovery that allows Microsoft 365 agents to fetch the MCP server's tool list at runtime by calling the server's `tools/list` method. To enable dynamic discovery, provide the `remoteServerURL` and omit the [`mcpToolDescription`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-connectors-tool-source-remote-mcp-server?view=m365-app-1.30) property.
- Added support for Azure Key Vault authentication using [`AzureKeyVault`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-connectors-tool-source-remote-mcp-server-authorization?view=m365-app-1.30) property that allows you to store and manage your MCP server credentials in your own [Azure Key Vault](https://learn.microsoft.com/en-us/microsoftteams/platform/m365-apps/agent-connectors#configure-authentication) instance. This gives you full control over secret lifecycle management, including rotation, access policies, and audit logging.

## All generally available versions

  


<details>
<summary>**Version 1.29**</summary>

### Version 1.29

June 2026

```http
https://developer.microsoft.com/json-schemas/teams/v1.29/MicrosoftTeams.schema.json
```

- Enabled [human to agent one-turn conversation](https://learn.microsoft.com/en-us/microsoftteams/platform/agents-in-teams/targeted-messages) and add a new property [triggers](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-compose-extensions-commands?view=m365-app-1.30#triggers).
- Added support for dynamic tool discovery that allows Microsoft 365 agents to fetch the MCP server's tool list at runtime by calling the server's `tools/list` method. To enable dynamic discovery, provide the `remoteServerURL` and omit the [`mcpToolDescription`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-connectors-tool-source-remote-mcp-server?view=m365-app-1.30) property.
- Added support for Azure Key Vault authentication using [`AzureKeyVault`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-connectors-tool-source-remote-mcp-server-authorization?view=m365-app-1.30) property that allows you to store and manage your MCP server credentials in your own [Azure Key Vault](https://learn.microsoft.com/en-us/microsoftteams/platform/m365-apps/agent-connectors#configure-authentication) instance. This gives you full control over secret lifecycle management, including rotation, access policies, and audit logging.
</details>

  


<details>
<summary>**Version 1.28**</summary>

### Version 1.28

May 2026

```http
https://developer.microsoft.com/json-schemas/teams/v1.28/MicrosoftTeams.schema.json
```

- Expanded the range of icons array for extension tab groups \([extensionRibbonsCustomTabGroupsItem](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-custom-tab-groups-item?view=m365-app-1.30) object\) to minItems = 3 \(from 1\) and maxItems = 8 \(from 3\).
- Enable Office Add-ins to show or hide ribbon buttons, controls, and groups in custom or contextual tabs across Word, Excel, and PowerPoint \(Win32, Mac, Web\) using the new property [visible](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-array-tabs-item?view=m365-app-1.30#visible) for dynamic UI and less clutter.
- The [`agentSkills`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-skills?view=m365-app-1.30#rootagentskills-object) property allows developers to package AI agent skills as elements.
</details>

  


<details>
<summary>**Version 1.27**</summary>

### Version 1.27

May 2026

```http
https://developer.microsoft.com/json-schemas/teams/v1.27/MicrosoftTeams.schema.json
```

- Added [agent connectors](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-connectors) node to enable [configuration of connections](https://learn.microsoft.com/en-us/microsoftteams/platform/m365-apps/agent-connectors) between Microsoft 365 agents and external data sources through MCP servers.
- Added a new command [type](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-command-lists-commands) and a new property [prompt](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-command-lists-commands) under bots commands.
</details>

  


<details>
<summary>**Version 1.26**</summary>

### Version 1.26

April 2026

```http
https://developer.microsoft.com/json-schemas/teams/v1.26/MicrosoftTeams.schema.json
```

- Added optional [composeExtensions.authorization.oAuthConfiguration](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-compose-extensions-authorization-o-auth-configuration) object to implement [Open Authorization \(OAuth\) 2.0 support for API-based message extensions](https://learn.microsoft.com/en-us/microsoftteams/platform/messaging-extensions/api-based-oauth).
- Added [features](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-description) descriptions list to [showcase agent and app features to a profile card](https://learn.microsoft.com/en-us/microsoftteams/platform/bots/how-to/teams-conversational-ai/ai-ux) that appears when the user hovers over the app icon.
- [KeyTips](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-custom-control-menu-item) let developers set custom shortcut keys in Office, giving users more efficient ways to work in Word, Excel, and PowerPoint.
</details>

  


<details>
<summary>**Version 1.25**</summary>

### Version 1.25

January 2026

```http
https://developer.microsoft.com/json-schemas/teams/v1.25/MicrosoftTeams.schema.json
```

- New [agenticUserTemplates](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root?view=m365-app-1.30#agenticusertemplates) node to reference an [Agent 365 blueprint](https://learn.microsoft.com/en-us/microsoft-agent-365/developer/registration), enabling the instantiation of an AI agent with its own Microsoft Entra Agent ID within your organization.
- Added [supportsChannelFeatures](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root?view=m365-app-1.30#supportschannelfeatures) to opt in your app to [next level channel features, including shared and private channels](https://learn.microsoft.com/en-us/microsoftteams/platform/build-apps-for-shared-private-channels).
- Enhanced support for Excel custom functions, including [customFunctions.enum](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/enum?view=m365-app-1.30) to provide [autocomplete options for custom functions](https://learn.microsoft.com/en-us/office/dev/add-ins/excel/custom-functions-custom-enums) and additional [function properties](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-function?view=m365-app-1.30#properties) and datatypes from [CustomFunctionsRuntime 1.5](https://learn.microsoft.com/en-us/javascript/api/requirement-sets/excel/custom-functions-requirement-sets).
</details>

  


<details>
<summary>**Version 1.24**</summary>

### Version 1.24

October 2025

```http
https://developer.microsoft.com/json-schemas/teams/v1.24/MicrosoftTeams.schema.json
```

- Added [executeDataFunction](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-runtimes-actions-item?view=m365-app-1.30#type) action type to enable Copilot agents to invoke Office Add-ins functions and serve as [natural language interfaces to add-ins](https://learn.microsoft.com/en-us/office/dev/add-ins/design/agent-and-add-in-overview). The overall functionality of combining Copilot agents with Office Add-ins remains in preview.
- Introduced [windowsExtensions](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-alternate-versions-array-hide-windows-extensions?view=m365-app-1.30) mechanism to specify which COM- and VSTO-based add-ins should be disabled with the equivalent JavaScript add-in is installed. For more details, see [Option to disable the Windows-only add-in instead](https://learn.microsoft.com/en-us/office/dev/add-ins/develop/make-office-add-in-compatible-with-existing-com-add-in#option-to-disable-the-windows-only-add-in-instead-preview).
- Added [keyboardShortcuts](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-keyboard-shortcut?view=m365-app-1.30) to support [backwards compatibility of Office Add-ins with keyboard shortcuts](https://learn.microsoft.com/en-us/office/dev/add-ins/design/keyboard-shortcuts#support-backward-compatibility-for-add-ins-with-a-unified-manifest-in-appsource) and their localized strings \(if applicable\).
- Increased [bot commands](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-command-lists?view=m365-app-1.30#commands) limit from 10 to 12 to accommodate Microsoft Copilot Studio agents, which support up to 12 starter prompts.

  

</details>

  


<details>
<summary>**Version 1.23**</summary>

### Version 1.23

July 2025

```http
https://developer.microsoft.com/json-schemas/teams/v1.23/MicrosoftTeams.schema.json
```

- Updated `extensionRibbonsCustomTabGroupsItem` to include the [`overriddenByRibbonApi` property](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-custom-tab-groups-item?view=m365-app-1.30#overriddenByRibbonApi-property), which hides groups in apps that support custom contextual tabs via the `Office.ribbon.requestCreateControls` API. Removed redundant node `extensionCommonCustomControlMenu`.
- Added bot [`registrationInfo`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-registration-info?view=m365-app-1.30) field to accommodate system-generated metadata for agents built with Microsoft Copilot Studio and other tools.
- Improved description for [`spamReportingOptions`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-spam-pre-processing-dialog?view=m365-app-1.30#spamReportingOptions-property)

  

</details>

  


<details>
<summary>**Version 1.22**</summary>

### Version 1.22

May 2025

```http
https://developer.microsoft.com/json-schemas/teams/v1.22/MicrosoftTeams.schema.json
```

- Added [`activityIcons`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-activities-activity-icons?view=m365-app-1.30) and [`allowedIconIds`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-activities-activity-types?view=m365-app-1.30#allowedIconIds-property) properties to customize app icons in a user's activity feed. `activityIcons` defines the icon, while `allowedIconIds` specifies which icons appear for each activity type. For more information, see the [Teams activity feed](https://learn.microsoft.com/en-us/graph/teams-send-activityfeednotifications) and [custom icon guidelines](https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines#custom-activity-icons).
- Added the [`type property`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-spam-pre-processing-dialog-spam-reporting-options?view=m365-app-1.30#type-property) to the spam reporting preprocessing dialog to support either radio buttons or checkboxes for reporting options. For details, see [Configure the manifest](https://learn.microsoft.com/en-us/office/dev/add-ins/outlook/spam-reporting#configure-the-manifest).
- Added [`nestedAppAuthInfo`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-web-application-info?view=m365-app-1.30#nestedAppAuthInfo-property) property to enable prefetching of a nested app authentication token when a tab is loads. To details more, see [Nested app authentication](https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/authentication/nested-authentication).

  

</details>

  


<details>
<summary>**Version 1.21**</summary>

### Version 1.21

April 2025

```http
https://developer.microsoft.com/json-schemas/teams/v1.21/MicrosoftTeams.schema.json
```

- Developers can now specify a [32x32 color icon](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-icons?view=m365-app-1.30#color32x32) with a transparent background to ensure a consistent appearance when your app runs in Outlook and Microsoft 365. To learn more see,[Teams app package color icon](https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/build-and-test/apps-package#color-icon).
- Introduced new *copilot* value for [`bots.scopes`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots?view=m365-app-1.30#scopes) and [`defaultInstallScope`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root?view=m365-app-1.30#defaultinstallscope). To learn more, see [Build with Teams AI library](https://learn.microsoft.com/en-us/microsoftteams/platform/bots/how-to/teams-conversational-ai/how-conversation-ai-get-started).
- Added [`backgroundLoadConfiguration`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-background-load-configuration?view=m365-app-1.30) object to enable tab apps to [opt in to precaching](https://learn.microsoft.com/en-us/microsoftteams/platform/tabs/how-to/app-caching#enable-precaching-for-tab-app) for a faster initial load experience.

  

</details>

  


<details>
<summary>**Version 1.20**</summary>

### Version 1.20

March 2025

```http
https://developer.microsoft.com/json-schemas/teams/v1.20/MicrosoftTeams.schema.json
```

- Added [`elementRelationshipSet`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-element-relationship-set?view=m365-app-1.30) and [`requirementSet`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/element-requirement-set?view=m365-app-1.30) \(for `composeExtensions`, `bots`, and `staticTabs`\) objects so that apps can specify [runtime requirements in Microsoft 365 hosts](https://learn.microsoft.com/en-us/microsoftteams/platform/m365-apps/specify-runtime-requirements).
- Added [`intuneInfo`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-intune-info?view=m365-app-1.30) object for [Outlook Add-ins to attest to Intune Mobile App Management \(MAM\) support](https://learn.microsoft.com/en-us/javascript/api/outlook/office.mailbox) in order to signal compliance with organizational data protection policies.
- Added [`fixedControls`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-array-fixed-control-item?view=m365-app-1.30) object to build custom [spam-reporting handling with Outlook Add-ins](https://learn.microsoft.com/en-us/office/dev/add-ins/outlook/spam-reporting).

  

</details>

  


<details>
<summary>**Version 1.19**</summary>

### Version 1.19

September 2024

```http
https://developer.microsoft.com/json-schemas/teams/v1.19/MicrosoftTeams.schema.json
```

- Added [`copilotAgents`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-copilot-agents?view=m365-app-1.30) object for publishing [declarative agents for Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/overview-declarative-agent).
- Added [`defaultLanguageFile`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-localization-info?view=m365-app-1.30#defaultlanguagefile), a new required property for [Copilot agents that support multiple languages](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/localize-agents).

  

</details>

  


<details>
<summary>**Version 1.18** *Not available.*</summary>
</details>

  


<details>
<summary>**Version 1.17**</summary>

### Version 1.17

April 2024

```http
https://developer.microsoft.com/json-schemas/teams/v1.17/MicrosoftTeams.schema.json
```

- Added support for [mobile specific manifest elements for Outlook extensions](https://learn.microsoft.com/en-us/office/dev/add-ins/outlook/outlook-mobile-addins).
- Added `semanticDescription` field for Copilot for Microsoft 365. [Learn more](https://learn.microsoft.com/en-us/microsoftteams/platform/messaging-extensions/high-quality-message-extension?tabs=tasks#semantic-description).
- Added support for [creating message extensions](https://learn.microsoft.com/en-us/microsoftteams/platform/messaging-extensions/api-based-overview) from an existing API.
- Added apps to easily show as cards on [Viva Connections Dashboard](https://learn.microsoft.com/en-us/sharepoint/dev/spfx/viva/bot-powered/overview-bot-powered-aces).
- Added new [sample prompts](https://learn.microsoft.com/en-us/microsoftteams/platform/messaging-extensions/high-quality-message-extension?tabs=tasks#sample-prompts) to guide users who install or enable a plugin for the first time.
- Added [bot configurations](https://learn.microsoft.com/en-us/microsoftteams/platform/bots/how-to/bot-configuration-experience) changes.
- Deprecated `packageName` property.
- Deprecated `callingSidePanel` from manifest.

  

</details>

  


<details>
<summary>**Version 1.16**</summary>

### Version 1.16

February 2023

```http
https://developer.microsoft.com/json-schemas/teams/v1.16/MicrosoftTeams.schema.json
```

- Added `supportsAnonymousGuestUsers` in `meetingExtensionDefinition`.
- Added `team` and `groupChat` to the scope of staticTab.
- Added `privateChatTab`, `meetingChatTab`, `meetingDetailsTab`, `meetingSidePanel`, `meetingStage`, `teamLevelApp` to the context of staticTab.

  

</details>

  


<details>
<summary>**Version 1.15**</summary>

### Version 1.15

November 2022

```http
https://developer.microsoft.com/json-schemas/teams/v1.15/MicrosoftTeams.schema.json
```

- Added `supportsAnonymizedPayloads` feature. A Boolean that indicates whether the app's link message handler supports anonymous invoke flow.

  

</details>

  


<details>
<summary>**Version 1.14**</summary>

### Version 1.14

July 2022

```http
https://developer.microsoft.com/json-schemas/teams/v1.14/MicrosoftTeams.schema.json
```

- Added `supportedChannelTypes` feature. List of 'nonstandard' channel types that the app supports. Note: Channels of standard type are supported by default if the app supports team scope.
- Added `supportsStreaming`feature. A Boolean value indicating whether this app can stream the meeting's audio video content to a Real-Time Messaging Protocol \(RTMP\) endpoint.

  

</details>

  


<details>
<summary>**Version 1.13**</summary>

### Version 1.13

May 2022

```http
https://developer.microsoft.com/json-schemas/teams/v1.13/MicrosoftTeams.schema.json
```

With the release of version 1.13 of the App manifest, developers can build and update their app \(formerly Teams app\) to run in Microsoft 365 hosts such as Outlook, Teams, and Microsoft Teams App across web, desktop, and mobile. From this version release, it eases deployment workflow and provides a streamlined way to deliver cross-platform apps to an expanded user audience via a single codebase. For more details on host application feature support, visit [TeamsJS capability support across Microsoft 365](https://learn.microsoft.com/en-us/microsoftteams/platform/m365-apps/teamsjs-support-m365).

- This schema version supports extending Teams apps to other parts of the Microsoft 365 ecosystem. More info at [https://aka.ms/extendteamsapps](https://aka.ms/extendteamsapps).

  

</details>

## What's new in manifest version 1.28

May 2026

```http
https://developer.microsoft.com/json-schemas/teams/v1.28/MicrosoftTeams.schema.json
```

- Added [agent connectors](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-connectors) node to enable [configuration of connections](https://learn.microsoft.com/en-us/microsoftteams/platform/m365-apps/agent-connectors) between Microsoft 365 agents and external data sources through MCP servers.
- Added a new command [type](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-command-lists-commands) and a new property [prompt](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-command-lists-commands) under bots commands.

## All generally available versions

  


<details>
<summary>**Version 1.29**</summary>

### Version 1.29

June 2026

```http
https://developer.microsoft.com/json-schemas/teams/v1.29/MicrosoftTeams.schema.json
```

- Enabled [human to agent one-turn conversation](https://learn.microsoft.com/en-us/microsoftteams/platform/agents-in-teams/targeted-messages) and add a new property [triggers](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-compose-extensions-commands?view=m365-app-1.30#triggers).
- Added support for dynamic tool discovery that allows Microsoft 365 agents to fetch the MCP server's tool list at runtime by calling the server's `tools/list` method. To enable dynamic discovery, provide the `remoteServerURL` and omit the [`mcpToolDescription`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-connectors-tool-source-remote-mcp-server?view=m365-app-1.30) property.
- Added support for Azure Key Vault authentication using [`AzureKeyVault`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-connectors-tool-source-remote-mcp-server-authorization?view=m365-app-1.30) property that allows you to store and manage your MCP server credentials in your own [Azure Key Vault](https://learn.microsoft.com/en-us/microsoftteams/platform/m365-apps/agent-connectors#configure-authentication) instance. This gives you full control over secret lifecycle management, including rotation, access policies, and audit logging.
</details>

  


<details>
<summary>**Version 1.28**</summary>

### Version 1.28

May 2026

```http
https://developer.microsoft.com/json-schemas/teams/v1.28/MicrosoftTeams.schema.json
```

- Expanded the range of icons array for extension tab groups \([extensionRibbonsCustomTabGroupsItem](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-custom-tab-groups-item?view=m365-app-1.30) object\) to minItems = 3 \(from 1\) and maxItems = 8 \(from 3\).
- Enable Office Add-ins to show or hide ribbon buttons, controls, and groups in custom or contextual tabs across Word, Excel, and PowerPoint \(Win32, Mac, Web\) using the new property [visible](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-array-tabs-item?view=m365-app-1.30#visible) for dynamic UI and less clutter.
- The [`agentSkills`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-skills?view=m365-app-1.30#rootagentskills-object) property allows developers to package AI agent skills as elements.
</details>

  


<details>
<summary>**Version 1.27**</summary>

### Version 1.27

May 2026

```http
https://developer.microsoft.com/json-schemas/teams/v1.27/MicrosoftTeams.schema.json
```

- Added [agent connectors](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-connectors) node to enable [configuration of connections](https://learn.microsoft.com/en-us/microsoftteams/platform/m365-apps/agent-connectors) between Microsoft 365 agents and external data sources through MCP servers.
- Added a new command [type](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-command-lists-commands) and a new property [prompt](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-command-lists-commands) under bots commands.
</details>

  


<details>
<summary>**Version 1.26**</summary>

### Version 1.26

April 2026

```http
https://developer.microsoft.com/json-schemas/teams/v1.26/MicrosoftTeams.schema.json
```

- Added optional [composeExtensions.authorization.oAuthConfiguration](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-compose-extensions-authorization-o-auth-configuration) object to implement [Open Authorization \(OAuth\) 2.0 support for API-based message extensions](https://learn.microsoft.com/en-us/microsoftteams/platform/messaging-extensions/api-based-oauth).
- Added [features](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-description) descriptions list to [showcase agent and app features to a profile card](https://learn.microsoft.com/en-us/microsoftteams/platform/bots/how-to/teams-conversational-ai/ai-ux) that appears when the user hovers over the app icon.
- [KeyTips](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-custom-control-menu-item) let developers set custom shortcut keys in Office, giving users more efficient ways to work in Word, Excel, and PowerPoint.
</details>

  


<details>
<summary>**Version 1.25**</summary>

### Version 1.25

January 2026

```http
https://developer.microsoft.com/json-schemas/teams/v1.25/MicrosoftTeams.schema.json
```

- New [agenticUserTemplates](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root?view=m365-app-1.30#agenticusertemplates) node to reference an [Agent 365 blueprint](https://learn.microsoft.com/en-us/microsoft-agent-365/developer/registration), enabling the instantiation of an AI agent with its own Microsoft Entra Agent ID within your organization.
- Added [supportsChannelFeatures](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root?view=m365-app-1.30#supportschannelfeatures) to opt in your app to [next level channel features, including shared and private channels](https://learn.microsoft.com/en-us/microsoftteams/platform/build-apps-for-shared-private-channels).
- Enhanced support for Excel custom functions, including [customFunctions.enum](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/enum?view=m365-app-1.30) to provide [autocomplete options for custom functions](https://learn.microsoft.com/en-us/office/dev/add-ins/excel/custom-functions-custom-enums) and additional [function properties](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-function?view=m365-app-1.30#properties) and datatypes from [CustomFunctionsRuntime 1.5](https://learn.microsoft.com/en-us/javascript/api/requirement-sets/excel/custom-functions-requirement-sets).
</details>

  


<details>
<summary>**Version 1.24**</summary>

### Version 1.24

October 2025

```http
https://developer.microsoft.com/json-schemas/teams/v1.24/MicrosoftTeams.schema.json
```

- Added [executeDataFunction](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-runtimes-actions-item?view=m365-app-1.30#type) action type to enable Copilot agents to invoke Office Add-ins functions and serve as [natural language interfaces to add-ins](https://learn.microsoft.com/en-us/office/dev/add-ins/design/agent-and-add-in-overview). The overall functionality of combining Copilot agents with Office Add-ins remains in preview.
- Introduced [windowsExtensions](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-alternate-versions-array-hide-windows-extensions?view=m365-app-1.30) mechanism to specify which COM- and VSTO-based add-ins should be disabled with the equivalent JavaScript add-in is installed. For more details, see [Option to disable the Windows-only add-in instead](https://learn.microsoft.com/en-us/office/dev/add-ins/develop/make-office-add-in-compatible-with-existing-com-add-in#option-to-disable-the-windows-only-add-in-instead-preview).
- Added [keyboardShortcuts](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-keyboard-shortcut?view=m365-app-1.30) to support [backwards compatibility of Office Add-ins with keyboard shortcuts](https://learn.microsoft.com/en-us/office/dev/add-ins/design/keyboard-shortcuts#support-backward-compatibility-for-add-ins-with-a-unified-manifest-in-appsource) and their localized strings \(if applicable\).
- Increased [bot commands](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-command-lists?view=m365-app-1.30#commands) limit from 10 to 12 to accommodate Microsoft Copilot Studio agents, which support up to 12 starter prompts.

  

</details>

  


<details>
<summary>**Version 1.23**</summary>

### Version 1.23

July 2025

```http
https://developer.microsoft.com/json-schemas/teams/v1.23/MicrosoftTeams.schema.json
```

- Updated `extensionRibbonsCustomTabGroupsItem` to include the [`overriddenByRibbonApi` property](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-custom-tab-groups-item?view=m365-app-1.30#overriddenByRibbonApi-property), which hides groups in apps that support custom contextual tabs via the `Office.ribbon.requestCreateControls` API. Removed redundant node `extensionCommonCustomControlMenu`.
- Added bot [`registrationInfo`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-registration-info?view=m365-app-1.30) field to accommodate system-generated metadata for agents built with Microsoft Copilot Studio and other tools.
- Improved description for [`spamReportingOptions`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-spam-pre-processing-dialog?view=m365-app-1.30#spamReportingOptions-property)

  

</details>

  


<details>
<summary>**Version 1.22**</summary>

### Version 1.22

May 2025

```http
https://developer.microsoft.com/json-schemas/teams/v1.22/MicrosoftTeams.schema.json
```

- Added [`activityIcons`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-activities-activity-icons?view=m365-app-1.30) and [`allowedIconIds`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-activities-activity-types?view=m365-app-1.30#allowedIconIds-property) properties to customize app icons in a user's activity feed. `activityIcons` defines the icon, while `allowedIconIds` specifies which icons appear for each activity type. For more information, see the [Teams activity feed](https://learn.microsoft.com/en-us/graph/teams-send-activityfeednotifications) and [custom icon guidelines](https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines#custom-activity-icons).
- Added the [`type property`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-spam-pre-processing-dialog-spam-reporting-options?view=m365-app-1.30#type-property) to the spam reporting preprocessing dialog to support either radio buttons or checkboxes for reporting options. For details, see [Configure the manifest](https://learn.microsoft.com/en-us/office/dev/add-ins/outlook/spam-reporting#configure-the-manifest).
- Added [`nestedAppAuthInfo`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-web-application-info?view=m365-app-1.30#nestedAppAuthInfo-property) property to enable prefetching of a nested app authentication token when a tab is loads. To details more, see [Nested app authentication](https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/authentication/nested-authentication).

  

</details>

  


<details>
<summary>**Version 1.21**</summary>

### Version 1.21

April 2025

```http
https://developer.microsoft.com/json-schemas/teams/v1.21/MicrosoftTeams.schema.json
```

- Developers can now specify a [32x32 color icon](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-icons?view=m365-app-1.30#color32x32) with a transparent background to ensure a consistent appearance when your app runs in Outlook and Microsoft 365. To learn more see,[Teams app package color icon](https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/build-and-test/apps-package#color-icon).
- Introduced new *copilot* value for [`bots.scopes`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots?view=m365-app-1.30#scopes) and [`defaultInstallScope`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root?view=m365-app-1.30#defaultinstallscope). To learn more, see [Build with Teams AI library](https://learn.microsoft.com/en-us/microsoftteams/platform/bots/how-to/teams-conversational-ai/how-conversation-ai-get-started).
- Added [`backgroundLoadConfiguration`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-background-load-configuration?view=m365-app-1.30) object to enable tab apps to [opt in to precaching](https://learn.microsoft.com/en-us/microsoftteams/platform/tabs/how-to/app-caching#enable-precaching-for-tab-app) for a faster initial load experience.

  

</details>

  


<details>
<summary>**Version 1.20**</summary>

### Version 1.20

March 2025

```http
https://developer.microsoft.com/json-schemas/teams/v1.20/MicrosoftTeams.schema.json
```

- Added [`elementRelationshipSet`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-element-relationship-set?view=m365-app-1.30) and [`requirementSet`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/element-requirement-set?view=m365-app-1.30) \(for `composeExtensions`, `bots`, and `staticTabs`\) objects so that apps can specify [runtime requirements in Microsoft 365 hosts](https://learn.microsoft.com/en-us/microsoftteams/platform/m365-apps/specify-runtime-requirements).
- Added [`intuneInfo`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-intune-info?view=m365-app-1.30) object for [Outlook Add-ins to attest to Intune Mobile App Management \(MAM\) support](https://learn.microsoft.com/en-us/javascript/api/outlook/office.mailbox) in order to signal compliance with organizational data protection policies.
- Added [`fixedControls`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-array-fixed-control-item?view=m365-app-1.30) object to build custom [spam-reporting handling with Outlook Add-ins](https://learn.microsoft.com/en-us/office/dev/add-ins/outlook/spam-reporting).

  

</details>

  


<details>
<summary>**Version 1.19**</summary>

### Version 1.19

September 2024

```http
https://developer.microsoft.com/json-schemas/teams/v1.19/MicrosoftTeams.schema.json
```

- Added [`copilotAgents`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-copilot-agents?view=m365-app-1.30) object for publishing [declarative agents for Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/overview-declarative-agent).
- Added [`defaultLanguageFile`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-localization-info?view=m365-app-1.30#defaultlanguagefile), a new required property for [Copilot agents that support multiple languages](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/localize-agents).

  

</details>

  


<details>
<summary>**Version 1.18** *Not available.*</summary>
</details>

  


<details>
<summary>**Version 1.17**</summary>

### Version 1.17

April 2024

```http
https://developer.microsoft.com/json-schemas/teams/v1.17/MicrosoftTeams.schema.json
```

- Added support for [mobile specific manifest elements for Outlook extensions](https://learn.microsoft.com/en-us/office/dev/add-ins/outlook/outlook-mobile-addins).
- Added `semanticDescription` field for Copilot for Microsoft 365. [Learn more](https://learn.microsoft.com/en-us/microsoftteams/platform/messaging-extensions/high-quality-message-extension?tabs=tasks#semantic-description).
- Added support for [creating message extensions](https://learn.microsoft.com/en-us/microsoftteams/platform/messaging-extensions/api-based-overview) from an existing API.
- Added apps to easily show as cards on [Viva Connections Dashboard](https://learn.microsoft.com/en-us/sharepoint/dev/spfx/viva/bot-powered/overview-bot-powered-aces).
- Added new [sample prompts](https://learn.microsoft.com/en-us/microsoftteams/platform/messaging-extensions/high-quality-message-extension?tabs=tasks#sample-prompts) to guide users who install or enable a plugin for the first time.
- Added [bot configurations](https://learn.microsoft.com/en-us/microsoftteams/platform/bots/how-to/bot-configuration-experience) changes.
- Deprecated `packageName` property.
- Deprecated `callingSidePanel` from manifest.

  

</details>

  


<details>
<summary>**Version 1.16**</summary>

### Version 1.16

February 2023

```http
https://developer.microsoft.com/json-schemas/teams/v1.16/MicrosoftTeams.schema.json
```

- Added `supportsAnonymousGuestUsers` in `meetingExtensionDefinition`.
- Added `team` and `groupChat` to the scope of staticTab.
- Added `privateChatTab`, `meetingChatTab`, `meetingDetailsTab`, `meetingSidePanel`, `meetingStage`, `teamLevelApp` to the context of staticTab.

  

</details>

  


<details>
<summary>**Version 1.15**</summary>

### Version 1.15

November 2022

```http
https://developer.microsoft.com/json-schemas/teams/v1.15/MicrosoftTeams.schema.json
```

- Added `supportsAnonymizedPayloads` feature. A Boolean that indicates whether the app's link message handler supports anonymous invoke flow.

  

</details>

  


<details>
<summary>**Version 1.14**</summary>

### Version 1.14

July 2022

```http
https://developer.microsoft.com/json-schemas/teams/v1.14/MicrosoftTeams.schema.json
```

- Added `supportedChannelTypes` feature. List of 'nonstandard' channel types that the app supports. Note: Channels of standard type are supported by default if the app supports team scope.
- Added `supportsStreaming`feature. A Boolean value indicating whether this app can stream the meeting's audio video content to a Real-Time Messaging Protocol \(RTMP\) endpoint.

  

</details>

  


<details>
<summary>**Version 1.13**</summary>

### Version 1.13

May 2022

```http
https://developer.microsoft.com/json-schemas/teams/v1.13/MicrosoftTeams.schema.json
```

With the release of version 1.13 of the App manifest, developers can build and update their app \(formerly Teams app\) to run in Microsoft 365 hosts such as Outlook, Teams, and Microsoft Teams App across web, desktop, and mobile. From this version release, it eases deployment workflow and provides a streamlined way to deliver cross-platform apps to an expanded user audience via a single codebase. For more details on host application feature support, visit [TeamsJS capability support across Microsoft 365](https://learn.microsoft.com/en-us/microsoftteams/platform/m365-apps/teamsjs-support-m365).

- This schema version supports extending Teams apps to other parts of the Microsoft 365 ecosystem. More info at [https://aka.ms/extendteamsapps](https://aka.ms/extendteamsapps).

  

</details>

## What's new in manifest version 1.27

May 2026

```http
https://developer.microsoft.com/json-schemas/teams/v1.27/MicrosoftTeams.schema.json
```

- Added [agent connectors](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-connectors) node to enable [configuration of connections](https://learn.microsoft.com/en-us/microsoftteams/platform/m365-apps/agent-connectors) between Microsoft 365 agents and external data sources through MCP servers.
- Added a new command [type](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-command-lists-commands) and a new property [prompt](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-command-lists-commands) under bots commands.

## All generally available versions

  


<details>
<summary>**Version 1.29**</summary>

### Version 1.29

June 2026

```http
https://developer.microsoft.com/json-schemas/teams/v1.29/MicrosoftTeams.schema.json
```

- Enabled [human to agent one-turn conversation](https://learn.microsoft.com/en-us/microsoftteams/platform/agents-in-teams/targeted-messages) and add a new property [triggers](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-compose-extensions-commands?view=m365-app-1.30#triggers).
- Added support for dynamic tool discovery that allows Microsoft 365 agents to fetch the MCP server's tool list at runtime by calling the server's `tools/list` method. To enable dynamic discovery, provide the `remoteServerURL` and omit the [`mcpToolDescription`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-connectors-tool-source-remote-mcp-server?view=m365-app-1.30) property.
- Added support for Azure Key Vault authentication using [`AzureKeyVault`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-connectors-tool-source-remote-mcp-server-authorization?view=m365-app-1.30) property that allows you to store and manage your MCP server credentials in your own [Azure Key Vault](https://learn.microsoft.com/en-us/microsoftteams/platform/m365-apps/agent-connectors#configure-authentication) instance. This gives you full control over secret lifecycle management, including rotation, access policies, and audit logging.
</details>

  


<details>
<summary>**Version 1.28**</summary>

### Version 1.28

May 2026

```http
https://developer.microsoft.com/json-schemas/teams/v1.28/MicrosoftTeams.schema.json
```

- Expanded the range of icons array for extension tab groups \([extensionRibbonsCustomTabGroupsItem](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-custom-tab-groups-item?view=m365-app-1.30) object\) to minItems = 3 \(from 1\) and maxItems = 8 \(from 3\).
- Enable Office Add-ins to show or hide ribbon buttons, controls, and groups in custom or contextual tabs across Word, Excel, and PowerPoint \(Win32, Mac, Web\) using the new property [visible](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-array-tabs-item?view=m365-app-1.30#visible) for dynamic UI and less clutter.
- The [`agentSkills`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-skills?view=m365-app-1.30#rootagentskills-object) property allows developers to package AI agent skills as elements.
</details>

  


<details>
<summary>**Version 1.27**</summary>

### Version 1.27

May 2026

```http
https://developer.microsoft.com/json-schemas/teams/v1.27/MicrosoftTeams.schema.json
```

- Added [agent connectors](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-connectors) node to enable [configuration of connections](https://learn.microsoft.com/en-us/microsoftteams/platform/m365-apps/agent-connectors) between Microsoft 365 agents and external data sources through MCP servers.
- Added a new command [type](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-command-lists-commands) and a new property [prompt](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-command-lists-commands) under bots commands.
</details>

  


<details>
<summary>**Version 1.26**</summary>

### Version 1.26

April 2026

```http
https://developer.microsoft.com/json-schemas/teams/v1.26/MicrosoftTeams.schema.json
```

- Added optional [composeExtensions.authorization.oAuthConfiguration](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-compose-extensions-authorization-o-auth-configuration) object to implement [Open Authorization \(OAuth\) 2.0 support for API-based message extensions](https://learn.microsoft.com/en-us/microsoftteams/platform/messaging-extensions/api-based-oauth).
- Added [features](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-description) descriptions list to [showcase agent and app features to a profile card](https://learn.microsoft.com/en-us/microsoftteams/platform/bots/how-to/teams-conversational-ai/ai-ux) that appears when the user hovers over the app icon.
- [KeyTips](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-custom-control-menu-item) let developers set custom shortcut keys in Office, giving users more efficient ways to work in Word, Excel, and PowerPoint.
</details>

  


<details>
<summary>**Version 1.25**</summary>

### Version 1.25

January 2026

```http
https://developer.microsoft.com/json-schemas/teams/v1.25/MicrosoftTeams.schema.json
```

- New [agenticUserTemplates](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root?view=m365-app-1.30#agenticusertemplates) node to reference an [Agent 365 blueprint](https://learn.microsoft.com/en-us/microsoft-agent-365/developer/registration), enabling the instantiation of an AI agent with its own Microsoft Entra Agent ID within your organization.
- Added [supportsChannelFeatures](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root?view=m365-app-1.30#supportschannelfeatures) to opt in your app to [next level channel features, including shared and private channels](https://learn.microsoft.com/en-us/microsoftteams/platform/build-apps-for-shared-private-channels).
- Enhanced support for Excel custom functions, including [customFunctions.enum](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/enum?view=m365-app-1.30) to provide [autocomplete options for custom functions](https://learn.microsoft.com/en-us/office/dev/add-ins/excel/custom-functions-custom-enums) and additional [function properties](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-function?view=m365-app-1.30#properties) and datatypes from [CustomFunctionsRuntime 1.5](https://learn.microsoft.com/en-us/javascript/api/requirement-sets/excel/custom-functions-requirement-sets).
</details>

  


<details>
<summary>**Version 1.24**</summary>

### Version 1.24

October 2025

```http
https://developer.microsoft.com/json-schemas/teams/v1.24/MicrosoftTeams.schema.json
```

- Added [executeDataFunction](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-runtimes-actions-item?view=m365-app-1.30#type) action type to enable Copilot agents to invoke Office Add-ins functions and serve as [natural language interfaces to add-ins](https://learn.microsoft.com/en-us/office/dev/add-ins/design/agent-and-add-in-overview). The overall functionality of combining Copilot agents with Office Add-ins remains in preview.
- Introduced [windowsExtensions](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-alternate-versions-array-hide-windows-extensions?view=m365-app-1.30) mechanism to specify which COM- and VSTO-based add-ins should be disabled with the equivalent JavaScript add-in is installed. For more details, see [Option to disable the Windows-only add-in instead](https://learn.microsoft.com/en-us/office/dev/add-ins/develop/make-office-add-in-compatible-with-existing-com-add-in#option-to-disable-the-windows-only-add-in-instead-preview).
- Added [keyboardShortcuts](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-keyboard-shortcut?view=m365-app-1.30) to support [backwards compatibility of Office Add-ins with keyboard shortcuts](https://learn.microsoft.com/en-us/office/dev/add-ins/design/keyboard-shortcuts#support-backward-compatibility-for-add-ins-with-a-unified-manifest-in-appsource) and their localized strings \(if applicable\).
- Increased [bot commands](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-command-lists?view=m365-app-1.30#commands) limit from 10 to 12 to accommodate Microsoft Copilot Studio agents, which support up to 12 starter prompts.

  

</details>

  


<details>
<summary>**Version 1.23**</summary>

### Version 1.23

July 2025

```http
https://developer.microsoft.com/json-schemas/teams/v1.23/MicrosoftTeams.schema.json
```

- Updated `extensionRibbonsCustomTabGroupsItem` to include the [`overriddenByRibbonApi` property](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-custom-tab-groups-item?view=m365-app-1.30#overriddenByRibbonApi-property), which hides groups in apps that support custom contextual tabs via the `Office.ribbon.requestCreateControls` API. Removed redundant node `extensionCommonCustomControlMenu`.
- Added bot [`registrationInfo`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-registration-info?view=m365-app-1.30) field to accommodate system-generated metadata for agents built with Microsoft Copilot Studio and other tools.
- Improved description for [`spamReportingOptions`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-spam-pre-processing-dialog?view=m365-app-1.30#spamReportingOptions-property)

  

</details>

  


<details>
<summary>**Version 1.22**</summary>

### Version 1.22

May 2025

```http
https://developer.microsoft.com/json-schemas/teams/v1.22/MicrosoftTeams.schema.json
```

- Added [`activityIcons`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-activities-activity-icons?view=m365-app-1.30) and [`allowedIconIds`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-activities-activity-types?view=m365-app-1.30#allowedIconIds-property) properties to customize app icons in a user's activity feed. `activityIcons` defines the icon, while `allowedIconIds` specifies which icons appear for each activity type. For more information, see the [Teams activity feed](https://learn.microsoft.com/en-us/graph/teams-send-activityfeednotifications) and [custom icon guidelines](https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines#custom-activity-icons).
- Added the [`type property`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-spam-pre-processing-dialog-spam-reporting-options?view=m365-app-1.30#type-property) to the spam reporting preprocessing dialog to support either radio buttons or checkboxes for reporting options. For details, see [Configure the manifest](https://learn.microsoft.com/en-us/office/dev/add-ins/outlook/spam-reporting#configure-the-manifest).
- Added [`nestedAppAuthInfo`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-web-application-info?view=m365-app-1.30#nestedAppAuthInfo-property) property to enable prefetching of a nested app authentication token when a tab is loads. To details more, see [Nested app authentication](https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/authentication/nested-authentication).

  

</details>

  


<details>
<summary>**Version 1.21**</summary>

### Version 1.21

April 2025

```http
https://developer.microsoft.com/json-schemas/teams/v1.21/MicrosoftTeams.schema.json
```

- Developers can now specify a [32x32 color icon](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-icons?view=m365-app-1.30#color32x32) with a transparent background to ensure a consistent appearance when your app runs in Outlook and Microsoft 365. To learn more see,[Teams app package color icon](https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/build-and-test/apps-package#color-icon).
- Introduced new *copilot* value for [`bots.scopes`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots?view=m365-app-1.30#scopes) and [`defaultInstallScope`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root?view=m365-app-1.30#defaultinstallscope). To learn more, see [Build with Teams AI library](https://learn.microsoft.com/en-us/microsoftteams/platform/bots/how-to/teams-conversational-ai/how-conversation-ai-get-started).
- Added [`backgroundLoadConfiguration`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-background-load-configuration?view=m365-app-1.30) object to enable tab apps to [opt in to precaching](https://learn.microsoft.com/en-us/microsoftteams/platform/tabs/how-to/app-caching#enable-precaching-for-tab-app) for a faster initial load experience.

  

</details>

  


<details>
<summary>**Version 1.20**</summary>

### Version 1.20

March 2025

```http
https://developer.microsoft.com/json-schemas/teams/v1.20/MicrosoftTeams.schema.json
```

- Added [`elementRelationshipSet`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-element-relationship-set?view=m365-app-1.30) and [`requirementSet`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/element-requirement-set?view=m365-app-1.30) \(for `composeExtensions`, `bots`, and `staticTabs`\) objects so that apps can specify [runtime requirements in Microsoft 365 hosts](https://learn.microsoft.com/en-us/microsoftteams/platform/m365-apps/specify-runtime-requirements).
- Added [`intuneInfo`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-intune-info?view=m365-app-1.30) object for [Outlook Add-ins to attest to Intune Mobile App Management \(MAM\) support](https://learn.microsoft.com/en-us/javascript/api/outlook/office.mailbox) in order to signal compliance with organizational data protection policies.
- Added [`fixedControls`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-array-fixed-control-item?view=m365-app-1.30) object to build custom [spam-reporting handling with Outlook Add-ins](https://learn.microsoft.com/en-us/office/dev/add-ins/outlook/spam-reporting).

  

</details>

  


<details>
<summary>**Version 1.19**</summary>

### Version 1.19

September 2024

```http
https://developer.microsoft.com/json-schemas/teams/v1.19/MicrosoftTeams.schema.json
```

- Added [`copilotAgents`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-copilot-agents?view=m365-app-1.30) object for publishing [declarative agents for Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/overview-declarative-agent).
- Added [`defaultLanguageFile`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-localization-info?view=m365-app-1.30#defaultlanguagefile), a new required property for [Copilot agents that support multiple languages](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/localize-agents).

  

</details>

  


<details>
<summary>**Version 1.18** *Not available.*</summary>
</details>

  


<details>
<summary>**Version 1.17**</summary>

### Version 1.17

April 2024

```http
https://developer.microsoft.com/json-schemas/teams/v1.17/MicrosoftTeams.schema.json
```

- Added support for [mobile specific manifest elements for Outlook extensions](https://learn.microsoft.com/en-us/office/dev/add-ins/outlook/outlook-mobile-addins).
- Added `semanticDescription` field for Copilot for Microsoft 365. [Learn more](https://learn.microsoft.com/en-us/microsoftteams/platform/messaging-extensions/high-quality-message-extension?tabs=tasks#semantic-description).
- Added support for [creating message extensions](https://learn.microsoft.com/en-us/microsoftteams/platform/messaging-extensions/api-based-overview) from an existing API.
- Added apps to easily show as cards on [Viva Connections Dashboard](https://learn.microsoft.com/en-us/sharepoint/dev/spfx/viva/bot-powered/overview-bot-powered-aces).
- Added new [sample prompts](https://learn.microsoft.com/en-us/microsoftteams/platform/messaging-extensions/high-quality-message-extension?tabs=tasks#sample-prompts) to guide users who install or enable a plugin for the first time.
- Added [bot configurations](https://learn.microsoft.com/en-us/microsoftteams/platform/bots/how-to/bot-configuration-experience) changes.
- Deprecated `packageName` property.
- Deprecated `callingSidePanel` from manifest.

  

</details>

  


<details>
<summary>**Version 1.16**</summary>

### Version 1.16

February 2023

```http
https://developer.microsoft.com/json-schemas/teams/v1.16/MicrosoftTeams.schema.json
```

- Added `supportsAnonymousGuestUsers` in `meetingExtensionDefinition`.
- Added `team` and `groupChat` to the scope of staticTab.
- Added `privateChatTab`, `meetingChatTab`, `meetingDetailsTab`, `meetingSidePanel`, `meetingStage`, `teamLevelApp` to the context of staticTab.

  

</details>

  


<details>
<summary>**Version 1.15**</summary>

### Version 1.15

November 2022

```http
https://developer.microsoft.com/json-schemas/teams/v1.15/MicrosoftTeams.schema.json
```

- Added `supportsAnonymizedPayloads` feature. A Boolean that indicates whether the app's link message handler supports anonymous invoke flow.

  

</details>

  


<details>
<summary>**Version 1.14**</summary>

### Version 1.14

July 2022

```http
https://developer.microsoft.com/json-schemas/teams/v1.14/MicrosoftTeams.schema.json
```

- Added `supportedChannelTypes` feature. List of 'nonstandard' channel types that the app supports. Note: Channels of standard type are supported by default if the app supports team scope.
- Added `supportsStreaming`feature. A Boolean value indicating whether this app can stream the meeting's audio video content to a Real-Time Messaging Protocol \(RTMP\) endpoint.

  

</details>

  


<details>
<summary>**Version 1.13**</summary>

### Version 1.13

May 2022

```http
https://developer.microsoft.com/json-schemas/teams/v1.13/MicrosoftTeams.schema.json
```

With the release of version 1.13 of the App manifest, developers can build and update their app \(formerly Teams app\) to run in Microsoft 365 hosts such as Outlook, Teams, and Microsoft Teams App across web, desktop, and mobile. From this version release, it eases deployment workflow and provides a streamlined way to deliver cross-platform apps to an expanded user audience via a single codebase. For more details on host application feature support, visit [TeamsJS capability support across Microsoft 365](https://learn.microsoft.com/en-us/microsoftteams/platform/m365-apps/teamsjs-support-m365).

- This schema version supports extending Teams apps to other parts of the Microsoft 365 ecosystem. More info at [https://aka.ms/extendteamsapps](https://aka.ms/extendteamsapps).

  

</details>

## What's new in manifest version 1.26

April 2026

```http
https://developer.microsoft.com/json-schemas/teams/v1.26/MicrosoftTeams.schema.json
```

- Added optional [composeExtensions.authorization.oAuthConfiguration](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-compose-extensions-authorization-o-auth-configuration?view=m365-app-1.30) object to implement [Open Authorization \(OAuth\) 2.0 support for API-based message extensions](https://learn.microsoft.com/en-us/microsoftteams/platform/messaging-extensions/api-based-oauth).
- Added [features](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-description?view=m365-app-1.30) descriptions list to [showcase agent and app features to a profile card](https://learn.microsoft.com/en-us/microsoftteams/platform/bots/how-to/teams-conversational-ai/ai-ux) that appears when the user hovers over the app icon.
- [KeyTips](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-custom-control-menu-item?view=m365-app-1.30) let developers set custom shortcut keys in Office, giving users more efficient ways to work in Word, Excel, and PowerPoint.

## All generally available versions

  


<details>
<summary>**Version 1.29**</summary>

### Version 1.29

June 2026

```http
https://developer.microsoft.com/json-schemas/teams/v1.29/MicrosoftTeams.schema.json
```

- Enabled [human to agent one-turn conversation](https://learn.microsoft.com/en-us/microsoftteams/platform/agents-in-teams/targeted-messages) and add a new property [triggers](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-compose-extensions-commands?view=m365-app-1.30#triggers).
- Added support for dynamic tool discovery that allows Microsoft 365 agents to fetch the MCP server's tool list at runtime by calling the server's `tools/list` method. To enable dynamic discovery, provide the `remoteServerURL` and omit the [`mcpToolDescription`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-connectors-tool-source-remote-mcp-server?view=m365-app-1.30) property.
- Added support for Azure Key Vault authentication using [`AzureKeyVault`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-connectors-tool-source-remote-mcp-server-authorization?view=m365-app-1.30) property that allows you to store and manage your MCP server credentials in your own [Azure Key Vault](https://learn.microsoft.com/en-us/microsoftteams/platform/m365-apps/agent-connectors#configure-authentication) instance. This gives you full control over secret lifecycle management, including rotation, access policies, and audit logging.
</details>

  


<details>
<summary>**Version 1.28**</summary>

### Version 1.28

May 2026

```http
https://developer.microsoft.com/json-schemas/teams/v1.28/MicrosoftTeams.schema.json
```

- Expanded the range of icons array for extension tab groups \([extensionRibbonsCustomTabGroupsItem](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-custom-tab-groups-item?view=m365-app-1.30) object\) to minItems = 3 \(from 1\) and maxItems = 8 \(from 3\).
- Enable Office Add-ins to show or hide ribbon buttons, controls, and groups in custom or contextual tabs across Word, Excel, and PowerPoint \(Win32, Mac, Web\) using the new property [visible](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-array-tabs-item?view=m365-app-1.30#visible) for dynamic UI and less clutter.
- The [`agentSkills`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-skills?view=m365-app-1.30#rootagentskills-object) property allows developers to package AI agent skills as elements.
</details>

  


<details>
<summary>**Version 1.27**</summary>

### Version 1.27

May 2026

```http
https://developer.microsoft.com/json-schemas/teams/v1.27/MicrosoftTeams.schema.json
```

- Added [agent connectors](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-connectors) node to enable [configuration of connections](https://learn.microsoft.com/en-us/microsoftteams/platform/m365-apps/agent-connectors) between Microsoft 365 agents and external data sources through MCP servers.
- Added a new command [type](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-command-lists-commands) and a new property [prompt](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-command-lists-commands) under bots commands.
</details>

  


<details>
<summary>**Version 1.26**</summary>

### Version 1.26

April 2026

```http
https://developer.microsoft.com/json-schemas/teams/v1.26/MicrosoftTeams.schema.json
```

- Added optional [composeExtensions.authorization.oAuthConfiguration](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-compose-extensions-authorization-o-auth-configuration) object to implement [Open Authorization \(OAuth\) 2.0 support for API-based message extensions](https://learn.microsoft.com/en-us/microsoftteams/platform/messaging-extensions/api-based-oauth).
- Added [features](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-description) descriptions list to [showcase agent and app features to a profile card](https://learn.microsoft.com/en-us/microsoftteams/platform/bots/how-to/teams-conversational-ai/ai-ux) that appears when the user hovers over the app icon.
- [KeyTips](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-custom-control-menu-item) let developers set custom shortcut keys in Office, giving users more efficient ways to work in Word, Excel, and PowerPoint.
</details>

  


<details>
<summary>**Version 1.25**</summary>

### Version 1.25

January 2026

```http
https://developer.microsoft.com/json-schemas/teams/v1.25/MicrosoftTeams.schema.json
```

- New [agenticUserTemplates](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root?view=m365-app-1.30#agenticusertemplates) node to reference an [Agent 365 blueprint](https://learn.microsoft.com/en-us/microsoft-agent-365/developer/registration), enabling the instantiation of an AI agent with its own Microsoft Entra Agent ID within your organization.
- Added [supportsChannelFeatures](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root?view=m365-app-1.30#supportschannelfeatures) to opt in your app to [next level channel features, including shared and private channels](https://learn.microsoft.com/en-us/microsoftteams/platform/build-apps-for-shared-private-channels).
- Enhanced support for Excel custom functions, including [customFunctions.enum](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/enum?view=m365-app-1.30) to provide [autocomplete options for custom functions](https://learn.microsoft.com/en-us/office/dev/add-ins/excel/custom-functions-custom-enums) and additional [function properties](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-function?view=m365-app-1.30#properties) and datatypes from [CustomFunctionsRuntime 1.5](https://learn.microsoft.com/en-us/javascript/api/requirement-sets/excel/custom-functions-requirement-sets).
</details>

  


<details>
<summary>**Version 1.24**</summary>

### Version 1.24

October 2025

```http
https://developer.microsoft.com/json-schemas/teams/v1.24/MicrosoftTeams.schema.json
```

- Added [executeDataFunction](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-runtimes-actions-item?view=m365-app-1.30#type) action type to enable Copilot agents to invoke Office Add-ins functions and serve as [natural language interfaces to add-ins](https://learn.microsoft.com/en-us/office/dev/add-ins/design/agent-and-add-in-overview). The overall functionality of combining Copilot agents with Office Add-ins remains in preview.
- Introduced [windowsExtensions](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-alternate-versions-array-hide-windows-extensions?view=m365-app-1.30) mechanism to specify which COM- and VSTO-based add-ins should be disabled with the equivalent JavaScript add-in is installed. For more details, see [Option to disable the Windows-only add-in instead](https://learn.microsoft.com/en-us/office/dev/add-ins/develop/make-office-add-in-compatible-with-existing-com-add-in#option-to-disable-the-windows-only-add-in-instead-preview).
- Added [keyboardShortcuts](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-keyboard-shortcut?view=m365-app-1.30) to support [backwards compatibility of Office Add-ins with keyboard shortcuts](https://learn.microsoft.com/en-us/office/dev/add-ins/design/keyboard-shortcuts#support-backward-compatibility-for-add-ins-with-a-unified-manifest-in-appsource) and their localized strings \(if applicable\).
- Increased [bot commands](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-command-lists?view=m365-app-1.30#commands) limit from 10 to 12 to accommodate Microsoft Copilot Studio agents, which support up to 12 starter prompts.

  

</details>

  


<details>
<summary>**Version 1.23**</summary>

### Version 1.23

July 2025

```http
https://developer.microsoft.com/json-schemas/teams/v1.23/MicrosoftTeams.schema.json
```

- Updated `extensionRibbonsCustomTabGroupsItem` to include the [`overriddenByRibbonApi` property](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-custom-tab-groups-item?view=m365-app-1.30#overriddenByRibbonApi-property), which hides groups in apps that support custom contextual tabs via the `Office.ribbon.requestCreateControls` API. Removed redundant node `extensionCommonCustomControlMenu`.
- Added bot [`registrationInfo`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-registration-info?view=m365-app-1.30) field to accommodate system-generated metadata for agents built with Microsoft Copilot Studio and other tools.
- Improved description for [`spamReportingOptions`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-spam-pre-processing-dialog?view=m365-app-1.30#spamReportingOptions-property)

  

</details>

  


<details>
<summary>**Version 1.22**</summary>

### Version 1.22

May 2025

```http
https://developer.microsoft.com/json-schemas/teams/v1.22/MicrosoftTeams.schema.json
```

- Added [`activityIcons`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-activities-activity-icons?view=m365-app-1.30) and [`allowedIconIds`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-activities-activity-types?view=m365-app-1.30#allowedIconIds-property) properties to customize app icons in a user's activity feed. `activityIcons` defines the icon, while `allowedIconIds` specifies which icons appear for each activity type. For more information, see the [Teams activity feed](https://learn.microsoft.com/en-us/graph/teams-send-activityfeednotifications) and [custom icon guidelines](https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines#custom-activity-icons).
- Added the [`type property`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-spam-pre-processing-dialog-spam-reporting-options?view=m365-app-1.30#type-property) to the spam reporting preprocessing dialog to support either radio buttons or checkboxes for reporting options. For details, see [Configure the manifest](https://learn.microsoft.com/en-us/office/dev/add-ins/outlook/spam-reporting#configure-the-manifest).
- Added [`nestedAppAuthInfo`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-web-application-info?view=m365-app-1.30#nestedAppAuthInfo-property) property to enable prefetching of a nested app authentication token when a tab is loads. To details more, see [Nested app authentication](https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/authentication/nested-authentication).

  

</details>

  


<details>
<summary>**Version 1.21**</summary>

### Version 1.21

April 2025

```http
https://developer.microsoft.com/json-schemas/teams/v1.21/MicrosoftTeams.schema.json
```

- Developers can now specify a [32x32 color icon](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-icons?view=m365-app-1.30#color32x32) with a transparent background to ensure a consistent appearance when your app runs in Outlook and Microsoft 365. To learn more see,[Teams app package color icon](https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/build-and-test/apps-package#color-icon).
- Introduced new *copilot* value for [`bots.scopes`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots?view=m365-app-1.30#scopes) and [`defaultInstallScope`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root?view=m365-app-1.30#defaultinstallscope). To learn more, see [Build with Teams AI library](https://learn.microsoft.com/en-us/microsoftteams/platform/bots/how-to/teams-conversational-ai/how-conversation-ai-get-started).
- Added [`backgroundLoadConfiguration`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-background-load-configuration?view=m365-app-1.30) object to enable tab apps to [opt in to precaching](https://learn.microsoft.com/en-us/microsoftteams/platform/tabs/how-to/app-caching#enable-precaching-for-tab-app) for a faster initial load experience.

  

</details>

  


<details>
<summary>**Version 1.20**</summary>

### Version 1.20

March 2025

```http
https://developer.microsoft.com/json-schemas/teams/v1.20/MicrosoftTeams.schema.json
```

- Added [`elementRelationshipSet`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-element-relationship-set?view=m365-app-1.30) and [`requirementSet`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/element-requirement-set?view=m365-app-1.30) \(for `composeExtensions`, `bots`, and `staticTabs`\) objects so that apps can specify [runtime requirements in Microsoft 365 hosts](https://learn.microsoft.com/en-us/microsoftteams/platform/m365-apps/specify-runtime-requirements).
- Added [`intuneInfo`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-intune-info?view=m365-app-1.30) object for [Outlook Add-ins to attest to Intune Mobile App Management \(MAM\) support](https://learn.microsoft.com/en-us/javascript/api/outlook/office.mailbox) in order to signal compliance with organizational data protection policies.
- Added [`fixedControls`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-array-fixed-control-item?view=m365-app-1.30) object to build custom [spam-reporting handling with Outlook Add-ins](https://learn.microsoft.com/en-us/office/dev/add-ins/outlook/spam-reporting).

  

</details>

  


<details>
<summary>**Version 1.19**</summary>

### Version 1.19

September 2024

```http
https://developer.microsoft.com/json-schemas/teams/v1.19/MicrosoftTeams.schema.json
```

- Added [`copilotAgents`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-copilot-agents?view=m365-app-1.30) object for publishing [declarative agents for Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/overview-declarative-agent).
- Added [`defaultLanguageFile`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-localization-info?view=m365-app-1.30#defaultlanguagefile), a new required property for [Copilot agents that support multiple languages](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/localize-agents).

  

</details>

  


<details>
<summary>**Version 1.18** *Not available.*</summary>
</details>

  


<details>
<summary>**Version 1.17**</summary>

### Version 1.17

April 2024

```http
https://developer.microsoft.com/json-schemas/teams/v1.17/MicrosoftTeams.schema.json
```

- Added support for [mobile specific manifest elements for Outlook extensions](https://learn.microsoft.com/en-us/office/dev/add-ins/outlook/outlook-mobile-addins).
- Added `semanticDescription` field for Copilot for Microsoft 365. [Learn more](https://learn.microsoft.com/en-us/microsoftteams/platform/messaging-extensions/high-quality-message-extension?tabs=tasks#semantic-description).
- Added support for [creating message extensions](https://learn.microsoft.com/en-us/microsoftteams/platform/messaging-extensions/api-based-overview) from an existing API.
- Added apps to easily show as cards on [Viva Connections Dashboard](https://learn.microsoft.com/en-us/sharepoint/dev/spfx/viva/bot-powered/overview-bot-powered-aces).
- Added new [sample prompts](https://learn.microsoft.com/en-us/microsoftteams/platform/messaging-extensions/high-quality-message-extension?tabs=tasks#sample-prompts) to guide users who install or enable a plugin for the first time.
- Added [bot configurations](https://learn.microsoft.com/en-us/microsoftteams/platform/bots/how-to/bot-configuration-experience) changes.
- Deprecated `packageName` property.
- Deprecated `callingSidePanel` from manifest.

  

</details>

  


<details>
<summary>**Version 1.16**</summary>

### Version 1.16

February 2023

```http
https://developer.microsoft.com/json-schemas/teams/v1.16/MicrosoftTeams.schema.json
```

- Added `supportsAnonymousGuestUsers` in `meetingExtensionDefinition`.
- Added `team` and `groupChat` to the scope of staticTab.
- Added `privateChatTab`, `meetingChatTab`, `meetingDetailsTab`, `meetingSidePanel`, `meetingStage`, `teamLevelApp` to the context of staticTab.

  

</details>

  


<details>
<summary>**Version 1.15**</summary>

### Version 1.15

November 2022

```http
https://developer.microsoft.com/json-schemas/teams/v1.15/MicrosoftTeams.schema.json
```

- Added `supportsAnonymizedPayloads` feature. A Boolean that indicates whether the app's link message handler supports anonymous invoke flow.

  

</details>

  


<details>
<summary>**Version 1.14**</summary>

### Version 1.14

July 2022

```http
https://developer.microsoft.com/json-schemas/teams/v1.14/MicrosoftTeams.schema.json
```

- Added `supportedChannelTypes` feature. List of 'nonstandard' channel types that the app supports. Note: Channels of standard type are supported by default if the app supports team scope.
- Added `supportsStreaming`feature. A Boolean value indicating whether this app can stream the meeting's audio video content to a Real-Time Messaging Protocol \(RTMP\) endpoint.

  

</details>

  


<details>
<summary>**Version 1.13**</summary>

### Version 1.13

May 2022

```http
https://developer.microsoft.com/json-schemas/teams/v1.13/MicrosoftTeams.schema.json
```

With the release of version 1.13 of the App manifest, developers can build and update their app \(formerly Teams app\) to run in Microsoft 365 hosts such as Outlook, Teams, and Microsoft Teams App across web, desktop, and mobile. From this version release, it eases deployment workflow and provides a streamlined way to deliver cross-platform apps to an expanded user audience via a single codebase. For more details on host application feature support, visit [TeamsJS capability support across Microsoft 365](https://learn.microsoft.com/en-us/microsoftteams/platform/m365-apps/teamsjs-support-m365).

- This schema version supports extending Teams apps to other parts of the Microsoft 365 ecosystem. More info at [https://aka.ms/extendteamsapps](https://aka.ms/extendteamsapps).

  

</details>

## What's new in manifest version 1.25

January 2026

```http
https://developer.microsoft.com/json-schemas/teams/v1.25/MicrosoftTeams.schema.json
```

- New [agenticUserTemplates](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root?view=m365-app-1.30#agenticusertemplates) node to reference an [Agent 365 blueprint](https://learn.microsoft.com/en-us/microsoft-agent-365/developer/registration), enabling the instantiation of an AI agent with its own Microsoft Entra Agent ID within your organization.
- Added [supportsChannelFeatures](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root?view=m365-app-1.30#supportschannelfeatures) to opt in your app to [next level channel features, including shared and private channels](https://learn.microsoft.com/en-us/microsoftteams/platform/build-apps-for-shared-private-channels).
- Enhanced support for Excel custom functions, including [customFunctions.enum](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/enum?view=m365-app-1.30) to provide [autocomplete options for custom functions](https://learn.microsoft.com/en-us/office/dev/add-ins/excel/custom-functions-custom-enums) and additional [function properties](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-function?view=m365-app-1.30#properties) and datatypes from [CustomFunctionsRuntime 1.5](https://learn.microsoft.com/en-us/javascript/api/requirement-sets/excel/custom-functions-requirement-sets).

## All generally available versions

  


<details>
<summary>**Version 1.29**</summary>

### Version 1.29

June 2026

```http
https://developer.microsoft.com/json-schemas/teams/v1.29/MicrosoftTeams.schema.json
```

- Enabled [human to agent one-turn conversation](https://learn.microsoft.com/en-us/microsoftteams/platform/agents-in-teams/targeted-messages) and add a new property [triggers](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-compose-extensions-commands?view=m365-app-1.30#triggers).
- Added support for dynamic tool discovery that allows Microsoft 365 agents to fetch the MCP server's tool list at runtime by calling the server's `tools/list` method. To enable dynamic discovery, provide the `remoteServerURL` and omit the [`mcpToolDescription`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-connectors-tool-source-remote-mcp-server?view=m365-app-1.30) property.
- Added support for Azure Key Vault authentication using [`AzureKeyVault`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-connectors-tool-source-remote-mcp-server-authorization?view=m365-app-1.30) property that allows you to store and manage your MCP server credentials in your own [Azure Key Vault](https://learn.microsoft.com/en-us/microsoftteams/platform/m365-apps/agent-connectors#configure-authentication) instance. This gives you full control over secret lifecycle management, including rotation, access policies, and audit logging.
</details>

  


<details>
<summary>**Version 1.28**</summary>

### Version 1.28

May 2026

```http
https://developer.microsoft.com/json-schemas/teams/v1.28/MicrosoftTeams.schema.json
```

- Expanded the range of icons array for extension tab groups \([extensionRibbonsCustomTabGroupsItem](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-custom-tab-groups-item?view=m365-app-1.30) object\) to minItems = 3 \(from 1\) and maxItems = 8 \(from 3\).
- Enable Office Add-ins to show or hide ribbon buttons, controls, and groups in custom or contextual tabs across Word, Excel, and PowerPoint \(Win32, Mac, Web\) using the new property [visible](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-array-tabs-item?view=m365-app-1.30#visible) for dynamic UI and less clutter.
- The [`agentSkills`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-skills?view=m365-app-1.30#rootagentskills-object) property allows developers to package AI agent skills as elements.
</details>

  


<details>
<summary>**Version 1.27**</summary>

### Version 1.27

May 2026

```http
https://developer.microsoft.com/json-schemas/teams/v1.27/MicrosoftTeams.schema.json
```

- Added [agent connectors](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-connectors) node to enable [configuration of connections](https://learn.microsoft.com/en-us/microsoftteams/platform/m365-apps/agent-connectors) between Microsoft 365 agents and external data sources through MCP servers.
- Added a new command [type](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-command-lists-commands) and a new property [prompt](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-command-lists-commands) under bots commands.
</details>

  


<details>
<summary>**Version 1.26**</summary>

### Version 1.26

April 2026

```http
https://developer.microsoft.com/json-schemas/teams/v1.26/MicrosoftTeams.schema.json
```

- Added optional [composeExtensions.authorization.oAuthConfiguration](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-compose-extensions-authorization-o-auth-configuration) object to implement [Open Authorization \(OAuth\) 2.0 support for API-based message extensions](https://learn.microsoft.com/en-us/microsoftteams/platform/messaging-extensions/api-based-oauth).
- Added [features](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-description) descriptions list to [showcase agent and app features to a profile card](https://learn.microsoft.com/en-us/microsoftteams/platform/bots/how-to/teams-conversational-ai/ai-ux) that appears when the user hovers over the app icon.
- [KeyTips](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-custom-control-menu-item) let developers set custom shortcut keys in Office, giving users more efficient ways to work in Word, Excel, and PowerPoint.
</details>

  


<details>
<summary>**Version 1.25**</summary>

### Version 1.25

January 2026

```http
https://developer.microsoft.com/json-schemas/teams/v1.25/MicrosoftTeams.schema.json
```

- New [agenticUserTemplates](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root?view=m365-app-1.30#agenticusertemplates) node to reference an [Agent 365 blueprint](https://learn.microsoft.com/en-us/microsoft-agent-365/developer/registration), enabling the instantiation of an AI agent with its own Microsoft Entra Agent ID within your organization.
- Added [supportsChannelFeatures](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root?view=m365-app-1.30#supportschannelfeatures) to opt in your app to [next level channel features, including shared and private channels](https://learn.microsoft.com/en-us/microsoftteams/platform/build-apps-for-shared-private-channels).
- Enhanced support for Excel custom functions, including [customFunctions.enum](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/enum?view=m365-app-1.30) to provide [autocomplete options for custom functions](https://learn.microsoft.com/en-us/office/dev/add-ins/excel/custom-functions-custom-enums) and additional [function properties](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-function?view=m365-app-1.30#properties) and datatypes from [CustomFunctionsRuntime 1.5](https://learn.microsoft.com/en-us/javascript/api/requirement-sets/excel/custom-functions-requirement-sets).
</details>

  


<details>
<summary>**Version 1.24**</summary>

### Version 1.24

October 2025

```http
https://developer.microsoft.com/json-schemas/teams/v1.24/MicrosoftTeams.schema.json
```

- Added [executeDataFunction](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-runtimes-actions-item?view=m365-app-1.30#type) action type to enable Copilot agents to invoke Office Add-ins functions and serve as [natural language interfaces to add-ins](https://learn.microsoft.com/en-us/office/dev/add-ins/design/agent-and-add-in-overview). The overall functionality of combining Copilot agents with Office Add-ins remains in preview.
- Introduced [windowsExtensions](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-alternate-versions-array-hide-windows-extensions?view=m365-app-1.30) mechanism to specify which COM- and VSTO-based add-ins should be disabled with the equivalent JavaScript add-in is installed. For more details, see [Option to disable the Windows-only add-in instead](https://learn.microsoft.com/en-us/office/dev/add-ins/develop/make-office-add-in-compatible-with-existing-com-add-in#option-to-disable-the-windows-only-add-in-instead-preview).
- Added [keyboardShortcuts](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-keyboard-shortcut?view=m365-app-1.30) to support [backwards compatibility of Office Add-ins with keyboard shortcuts](https://learn.microsoft.com/en-us/office/dev/add-ins/design/keyboard-shortcuts#support-backward-compatibility-for-add-ins-with-a-unified-manifest-in-appsource) and their localized strings \(if applicable\).
- Increased [bot commands](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-command-lists?view=m365-app-1.30#commands) limit from 10 to 12 to accommodate Microsoft Copilot Studio agents, which support up to 12 starter prompts.

  

</details>

  


<details>
<summary>**Version 1.23**</summary>

### Version 1.23

July 2025

```http
https://developer.microsoft.com/json-schemas/teams/v1.23/MicrosoftTeams.schema.json
```

- Updated `extensionRibbonsCustomTabGroupsItem` to include the [`overriddenByRibbonApi` property](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-custom-tab-groups-item?view=m365-app-1.30#overriddenByRibbonApi-property), which hides groups in apps that support custom contextual tabs via the `Office.ribbon.requestCreateControls` API. Removed redundant node `extensionCommonCustomControlMenu`.
- Added bot [`registrationInfo`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-registration-info?view=m365-app-1.30) field to accommodate system-generated metadata for agents built with Microsoft Copilot Studio and other tools.
- Improved description for [`spamReportingOptions`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-spam-pre-processing-dialog?view=m365-app-1.30#spamReportingOptions-property)

  

</details>

  


<details>
<summary>**Version 1.22**</summary>

### Version 1.22

May 2025

```http
https://developer.microsoft.com/json-schemas/teams/v1.22/MicrosoftTeams.schema.json
```

- Added [`activityIcons`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-activities-activity-icons?view=m365-app-1.30) and [`allowedIconIds`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-activities-activity-types?view=m365-app-1.30#allowedIconIds-property) properties to customize app icons in a user's activity feed. `activityIcons` defines the icon, while `allowedIconIds` specifies which icons appear for each activity type. For more information, see the [Teams activity feed](https://learn.microsoft.com/en-us/graph/teams-send-activityfeednotifications) and [custom icon guidelines](https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines#custom-activity-icons).
- Added the [`type property`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-spam-pre-processing-dialog-spam-reporting-options?view=m365-app-1.30#type-property) to the spam reporting preprocessing dialog to support either radio buttons or checkboxes for reporting options. For details, see [Configure the manifest](https://learn.microsoft.com/en-us/office/dev/add-ins/outlook/spam-reporting#configure-the-manifest).
- Added [`nestedAppAuthInfo`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-web-application-info?view=m365-app-1.30#nestedAppAuthInfo-property) property to enable prefetching of a nested app authentication token when a tab is loads. To details more, see [Nested app authentication](https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/authentication/nested-authentication).

  

</details>

  


<details>
<summary>**Version 1.21**</summary>

### Version 1.21

April 2025

```http
https://developer.microsoft.com/json-schemas/teams/v1.21/MicrosoftTeams.schema.json
```

- Developers can now specify a [32x32 color icon](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-icons?view=m365-app-1.30#color32x32) with a transparent background to ensure a consistent appearance when your app runs in Outlook and Microsoft 365. To learn more see,[Teams app package color icon](https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/build-and-test/apps-package#color-icon).
- Introduced new *copilot* value for [`bots.scopes`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots?view=m365-app-1.30#scopes) and [`defaultInstallScope`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root?view=m365-app-1.30#defaultinstallscope). To learn more, see [Build with Teams AI library](https://learn.microsoft.com/en-us/microsoftteams/platform/bots/how-to/teams-conversational-ai/how-conversation-ai-get-started).
- Added [`backgroundLoadConfiguration`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-background-load-configuration?view=m365-app-1.30) object to enable tab apps to [opt in to precaching](https://learn.microsoft.com/en-us/microsoftteams/platform/tabs/how-to/app-caching#enable-precaching-for-tab-app) for a faster initial load experience.

  

</details>

  


<details>
<summary>**Version 1.20**</summary>

### Version 1.20

March 2025

```http
https://developer.microsoft.com/json-schemas/teams/v1.20/MicrosoftTeams.schema.json
```

- Added [`elementRelationshipSet`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-element-relationship-set?view=m365-app-1.30) and [`requirementSet`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/element-requirement-set?view=m365-app-1.30) \(for `composeExtensions`, `bots`, and `staticTabs`\) objects so that apps can specify [runtime requirements in Microsoft 365 hosts](https://learn.microsoft.com/en-us/microsoftteams/platform/m365-apps/specify-runtime-requirements).
- Added [`intuneInfo`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-intune-info?view=m365-app-1.30) object for [Outlook Add-ins to attest to Intune Mobile App Management \(MAM\) support](https://learn.microsoft.com/en-us/javascript/api/outlook/office.mailbox) in order to signal compliance with organizational data protection policies.
- Added [`fixedControls`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-array-fixed-control-item?view=m365-app-1.30) object to build custom [spam-reporting handling with Outlook Add-ins](https://learn.microsoft.com/en-us/office/dev/add-ins/outlook/spam-reporting).

  

</details>

  


<details>
<summary>**Version 1.19**</summary>

### Version 1.19

September 2024

```http
https://developer.microsoft.com/json-schemas/teams/v1.19/MicrosoftTeams.schema.json
```

- Added [`copilotAgents`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-copilot-agents?view=m365-app-1.30) object for publishing [declarative agents for Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/overview-declarative-agent).
- Added [`defaultLanguageFile`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-localization-info?view=m365-app-1.30#defaultlanguagefile), a new required property for [Copilot agents that support multiple languages](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/localize-agents).

  

</details>

  


<details>
<summary>**Version 1.18** *Not available.*</summary>
</details>

  


<details>
<summary>**Version 1.17**</summary>

### Version 1.17

April 2024

```http
https://developer.microsoft.com/json-schemas/teams/v1.17/MicrosoftTeams.schema.json
```

- Added support for [mobile specific manifest elements for Outlook extensions](https://learn.microsoft.com/en-us/office/dev/add-ins/outlook/outlook-mobile-addins).
- Added `semanticDescription` field for Copilot for Microsoft 365. [Learn more](https://learn.microsoft.com/en-us/microsoftteams/platform/messaging-extensions/high-quality-message-extension?tabs=tasks#semantic-description).
- Added support for [creating message extensions](https://learn.microsoft.com/en-us/microsoftteams/platform/messaging-extensions/api-based-overview) from an existing API.
- Added apps to easily show as cards on [Viva Connections Dashboard](https://learn.microsoft.com/en-us/sharepoint/dev/spfx/viva/bot-powered/overview-bot-powered-aces).
- Added new [sample prompts](https://learn.microsoft.com/en-us/microsoftteams/platform/messaging-extensions/high-quality-message-extension?tabs=tasks#sample-prompts) to guide users who install or enable a plugin for the first time.
- Added [bot configurations](https://learn.microsoft.com/en-us/microsoftteams/platform/bots/how-to/bot-configuration-experience) changes.
- Deprecated `packageName` property.
- Deprecated `callingSidePanel` from manifest.

  

</details>

  


<details>
<summary>**Version 1.16**</summary>

### Version 1.16

February 2023

```http
https://developer.microsoft.com/json-schemas/teams/v1.16/MicrosoftTeams.schema.json
```

- Added `supportsAnonymousGuestUsers` in `meetingExtensionDefinition`.
- Added `team` and `groupChat` to the scope of staticTab.
- Added `privateChatTab`, `meetingChatTab`, `meetingDetailsTab`, `meetingSidePanel`, `meetingStage`, `teamLevelApp` to the context of staticTab.

  

</details>

  


<details>
<summary>**Version 1.15**</summary>

### Version 1.15

November 2022

```http
https://developer.microsoft.com/json-schemas/teams/v1.15/MicrosoftTeams.schema.json
```

- Added `supportsAnonymizedPayloads` feature. A Boolean that indicates whether the app's link message handler supports anonymous invoke flow.

  

</details>

  


<details>
<summary>**Version 1.14**</summary>

### Version 1.14

July 2022

```http
https://developer.microsoft.com/json-schemas/teams/v1.14/MicrosoftTeams.schema.json
```

- Added `supportedChannelTypes` feature. List of 'nonstandard' channel types that the app supports. Note: Channels of standard type are supported by default if the app supports team scope.
- Added `supportsStreaming`feature. A Boolean value indicating whether this app can stream the meeting's audio video content to a Real-Time Messaging Protocol \(RTMP\) endpoint.

  

</details>

  


<details>
<summary>**Version 1.13**</summary>

### Version 1.13

May 2022

```http
https://developer.microsoft.com/json-schemas/teams/v1.13/MicrosoftTeams.schema.json
```

With the release of version 1.13 of the App manifest, developers can build and update their app \(formerly Teams app\) to run in Microsoft 365 hosts such as Outlook, Teams, and Microsoft Teams App across web, desktop, and mobile. From this version release, it eases deployment workflow and provides a streamlined way to deliver cross-platform apps to an expanded user audience via a single codebase. For more details on host application feature support, visit [TeamsJS capability support across Microsoft 365](https://learn.microsoft.com/en-us/microsoftteams/platform/m365-apps/teamsjs-support-m365).

- This schema version supports extending Teams apps to other parts of the Microsoft 365 ecosystem. More info at [https://aka.ms/extendteamsapps](https://aka.ms/extendteamsapps).

  

</details>

## What's new in manifest version 1.24

October 2025

```http
https://developer.microsoft.com/json-schemas/teams/v1.24/MicrosoftTeams.schema.json
```

- Added [executeDataFunction](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-runtimes-actions-item?view=m365-app-1.30#type) action type to enable Copilot agents to invoke Office Add-ins functions and serve as [natural language interfaces to add-ins](https://learn.microsoft.com/en-us/office/dev/add-ins/design/agent-and-add-in-overview). The overall functionality of combining Copilot agents with Office Add-ins remains in preview.
- Introduced [windowsExtensions](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-alternate-versions-array-hide-windows-extensions?view=m365-app-1.30) mechanism to specify which COM- and VSTO-based add-ins should be disabled with the equivalent JavaScript add-in is installed. For more details, see [Option to disable the Windows-only add-in instead](https://learn.microsoft.com/en-us/office/dev/add-ins/develop/make-office-add-in-compatible-with-existing-com-add-in#option-to-disable-the-windows-only-add-in-instead-preview).
- Added [keyboardShortcuts](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-keyboard-shortcut?view=m365-app-1.30) to support [backwards compatibility of Office Add-ins with keyboard shortcuts](https://learn.microsoft.com/en-us/office/dev/add-ins/design/keyboard-shortcuts#support-backward-compatibility-for-add-ins-with-a-unified-manifest-in-appsource) and their localized strings \(if applicable\).
- Increased [bot commands](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-command-lists?view=m365-app-1.30#commands) limit from 10 to 12 to accommodate Microsoft Copilot Studio agents, which support up to 12 starter prompts.

## All generally available versions

  


<details>
<summary>**Version 1.29**</summary>

### Version 1.29

June 2026

```http
https://developer.microsoft.com/json-schemas/teams/v1.29/MicrosoftTeams.schema.json
```

- Enabled [human to agent one-turn conversation](https://learn.microsoft.com/en-us/microsoftteams/platform/agents-in-teams/targeted-messages) and add a new property [triggers](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-compose-extensions-commands?view=m365-app-1.30#triggers).
- Added support for dynamic tool discovery that allows Microsoft 365 agents to fetch the MCP server's tool list at runtime by calling the server's `tools/list` method. To enable dynamic discovery, provide the `remoteServerURL` and omit the [`mcpToolDescription`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-connectors-tool-source-remote-mcp-server?view=m365-app-1.30) property.
- Added support for Azure Key Vault authentication using [`AzureKeyVault`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-connectors-tool-source-remote-mcp-server-authorization?view=m365-app-1.30) property that allows you to store and manage your MCP server credentials in your own [Azure Key Vault](https://learn.microsoft.com/en-us/microsoftteams/platform/m365-apps/agent-connectors#configure-authentication) instance. This gives you full control over secret lifecycle management, including rotation, access policies, and audit logging.
</details>

  


<details>
<summary>**Version 1.28**</summary>

### Version 1.28

May 2026

```http
https://developer.microsoft.com/json-schemas/teams/v1.28/MicrosoftTeams.schema.json
```

- Expanded the range of icons array for extension tab groups \([extensionRibbonsCustomTabGroupsItem](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-custom-tab-groups-item?view=m365-app-1.30) object\) to minItems = 3 \(from 1\) and maxItems = 8 \(from 3\).
- Enable Office Add-ins to show or hide ribbon buttons, controls, and groups in custom or contextual tabs across Word, Excel, and PowerPoint \(Win32, Mac, Web\) using the new property [visible](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-array-tabs-item?view=m365-app-1.30#visible) for dynamic UI and less clutter.
- The [`agentSkills`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-skills?view=m365-app-1.30#rootagentskills-object) property allows developers to package AI agent skills as elements.
</details>

  


<details>
<summary>**Version 1.27**</summary>

### Version 1.27

May 2026

```http
https://developer.microsoft.com/json-schemas/teams/v1.27/MicrosoftTeams.schema.json
```

- Added [agent connectors](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-connectors) node to enable [configuration of connections](https://learn.microsoft.com/en-us/microsoftteams/platform/m365-apps/agent-connectors) between Microsoft 365 agents and external data sources through MCP servers.
- Added a new command [type](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-command-lists-commands) and a new property [prompt](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-command-lists-commands) under bots commands.
</details>

  


<details>
<summary>**Version 1.26**</summary>

### Version 1.26

April 2026

```http
https://developer.microsoft.com/json-schemas/teams/v1.26/MicrosoftTeams.schema.json
```

- Added optional [composeExtensions.authorization.oAuthConfiguration](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-compose-extensions-authorization-o-auth-configuration) object to implement [Open Authorization \(OAuth\) 2.0 support for API-based message extensions](https://learn.microsoft.com/en-us/microsoftteams/platform/messaging-extensions/api-based-oauth).
- Added [features](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-description) descriptions list to [showcase agent and app features to a profile card](https://learn.microsoft.com/en-us/microsoftteams/platform/bots/how-to/teams-conversational-ai/ai-ux) that appears when the user hovers over the app icon.
- [KeyTips](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-custom-control-menu-item) let developers set custom shortcut keys in Office, giving users more efficient ways to work in Word, Excel, and PowerPoint.
</details>

  


<details>
<summary>**Version 1.25**</summary>

### Version 1.25

January 2026

```http
https://developer.microsoft.com/json-schemas/teams/v1.25/MicrosoftTeams.schema.json
```

- New [agenticUserTemplates](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root?view=m365-app-1.30#agenticusertemplates) node to reference an [Agent 365 blueprint](https://learn.microsoft.com/en-us/microsoft-agent-365/developer/registration), enabling the instantiation of an AI agent with its own Microsoft Entra Agent ID within your organization.
- Added [supportsChannelFeatures](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root?view=m365-app-1.30#supportschannelfeatures) to opt in your app to [next level channel features, including shared and private channels](https://learn.microsoft.com/en-us/microsoftteams/platform/build-apps-for-shared-private-channels).
- Enhanced support for Excel custom functions, including [customFunctions.enum](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/enum?view=m365-app-1.30) to provide [autocomplete options for custom functions](https://learn.microsoft.com/en-us/office/dev/add-ins/excel/custom-functions-custom-enums) and additional [function properties](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-function?view=m365-app-1.30#properties) and datatypes from [CustomFunctionsRuntime 1.5](https://learn.microsoft.com/en-us/javascript/api/requirement-sets/excel/custom-functions-requirement-sets).
</details>

  


<details>
<summary>**Version 1.24**</summary>

### Version 1.24

October 2025

```http
https://developer.microsoft.com/json-schemas/teams/v1.24/MicrosoftTeams.schema.json
```

- Added [executeDataFunction](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-runtimes-actions-item?view=m365-app-1.30#type) action type to enable Copilot agents to invoke Office Add-ins functions and serve as [natural language interfaces to add-ins](https://learn.microsoft.com/en-us/office/dev/add-ins/design/agent-and-add-in-overview). The overall functionality of combining Copilot agents with Office Add-ins remains in preview.
- Introduced [windowsExtensions](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-alternate-versions-array-hide-windows-extensions?view=m365-app-1.30) mechanism to specify which COM- and VSTO-based add-ins should be disabled with the equivalent JavaScript add-in is installed. For more details, see [Option to disable the Windows-only add-in instead](https://learn.microsoft.com/en-us/office/dev/add-ins/develop/make-office-add-in-compatible-with-existing-com-add-in#option-to-disable-the-windows-only-add-in-instead-preview).
- Added [keyboardShortcuts](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-keyboard-shortcut?view=m365-app-1.30) to support [backwards compatibility of Office Add-ins with keyboard shortcuts](https://learn.microsoft.com/en-us/office/dev/add-ins/design/keyboard-shortcuts#support-backward-compatibility-for-add-ins-with-a-unified-manifest-in-appsource) and their localized strings \(if applicable\).
- Increased [bot commands](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-command-lists?view=m365-app-1.30#commands) limit from 10 to 12 to accommodate Microsoft Copilot Studio agents, which support up to 12 starter prompts.

  

</details>

  


<details>
<summary>**Version 1.23**</summary>

### Version 1.23

July 2025

```http
https://developer.microsoft.com/json-schemas/teams/v1.23/MicrosoftTeams.schema.json
```

- Updated `extensionRibbonsCustomTabGroupsItem` to include the [`overriddenByRibbonApi` property](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-custom-tab-groups-item?view=m365-app-1.30#overriddenByRibbonApi-property), which hides groups in apps that support custom contextual tabs via the `Office.ribbon.requestCreateControls` API. Removed redundant node `extensionCommonCustomControlMenu`.
- Added bot [`registrationInfo`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-registration-info?view=m365-app-1.30) field to accommodate system-generated metadata for agents built with Microsoft Copilot Studio and other tools.
- Improved description for [`spamReportingOptions`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-spam-pre-processing-dialog?view=m365-app-1.30#spamReportingOptions-property)

  

</details>

  


<details>
<summary>**Version 1.22**</summary>

### Version 1.22

May 2025

```http
https://developer.microsoft.com/json-schemas/teams/v1.22/MicrosoftTeams.schema.json
```

- Added [`activityIcons`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-activities-activity-icons?view=m365-app-1.30) and [`allowedIconIds`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-activities-activity-types?view=m365-app-1.30#allowedIconIds-property) properties to customize app icons in a user's activity feed. `activityIcons` defines the icon, while `allowedIconIds` specifies which icons appear for each activity type. For more information, see the [Teams activity feed](https://learn.microsoft.com/en-us/graph/teams-send-activityfeednotifications) and [custom icon guidelines](https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines#custom-activity-icons).
- Added the [`type property`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-spam-pre-processing-dialog-spam-reporting-options?view=m365-app-1.30#type-property) to the spam reporting preprocessing dialog to support either radio buttons or checkboxes for reporting options. For details, see [Configure the manifest](https://learn.microsoft.com/en-us/office/dev/add-ins/outlook/spam-reporting#configure-the-manifest).
- Added [`nestedAppAuthInfo`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-web-application-info?view=m365-app-1.30#nestedAppAuthInfo-property) property to enable prefetching of a nested app authentication token when a tab is loads. To details more, see [Nested app authentication](https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/authentication/nested-authentication).

  

</details>

  


<details>
<summary>**Version 1.21**</summary>

### Version 1.21

April 2025

```http
https://developer.microsoft.com/json-schemas/teams/v1.21/MicrosoftTeams.schema.json
```

- Developers can now specify a [32x32 color icon](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-icons?view=m365-app-1.30#color32x32) with a transparent background to ensure a consistent appearance when your app runs in Outlook and Microsoft 365. To learn more see,[Teams app package color icon](https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/build-and-test/apps-package#color-icon).
- Introduced new *copilot* value for [`bots.scopes`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots?view=m365-app-1.30#scopes) and [`defaultInstallScope`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root?view=m365-app-1.30#defaultinstallscope). To learn more, see [Build with Teams AI library](https://learn.microsoft.com/en-us/microsoftteams/platform/bots/how-to/teams-conversational-ai/how-conversation-ai-get-started).
- Added [`backgroundLoadConfiguration`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-background-load-configuration?view=m365-app-1.30) object to enable tab apps to [opt in to precaching](https://learn.microsoft.com/en-us/microsoftteams/platform/tabs/how-to/app-caching#enable-precaching-for-tab-app) for a faster initial load experience.

  

</details>

  


<details>
<summary>**Version 1.20**</summary>

### Version 1.20

March 2025

```http
https://developer.microsoft.com/json-schemas/teams/v1.20/MicrosoftTeams.schema.json
```

- Added [`elementRelationshipSet`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-element-relationship-set?view=m365-app-1.30) and [`requirementSet`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/element-requirement-set?view=m365-app-1.30) \(for `composeExtensions`, `bots`, and `staticTabs`\) objects so that apps can specify [runtime requirements in Microsoft 365 hosts](https://learn.microsoft.com/en-us/microsoftteams/platform/m365-apps/specify-runtime-requirements).
- Added [`intuneInfo`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-intune-info?view=m365-app-1.30) object for [Outlook Add-ins to attest to Intune Mobile App Management \(MAM\) support](https://learn.microsoft.com/en-us/javascript/api/outlook/office.mailbox) in order to signal compliance with organizational data protection policies.
- Added [`fixedControls`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-array-fixed-control-item?view=m365-app-1.30) object to build custom [spam-reporting handling with Outlook Add-ins](https://learn.microsoft.com/en-us/office/dev/add-ins/outlook/spam-reporting).

  

</details>

  


<details>
<summary>**Version 1.19**</summary>

### Version 1.19

September 2024

```http
https://developer.microsoft.com/json-schemas/teams/v1.19/MicrosoftTeams.schema.json
```

- Added [`copilotAgents`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-copilot-agents?view=m365-app-1.30) object for publishing [declarative agents for Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/overview-declarative-agent).
- Added [`defaultLanguageFile`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-localization-info?view=m365-app-1.30#defaultlanguagefile), a new required property for [Copilot agents that support multiple languages](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/localize-agents).

  

</details>

  


<details>
<summary>**Version 1.18** *Not available.*</summary>
</details>

  


<details>
<summary>**Version 1.17**</summary>

### Version 1.17

April 2024

```http
https://developer.microsoft.com/json-schemas/teams/v1.17/MicrosoftTeams.schema.json
```

- Added support for [mobile specific manifest elements for Outlook extensions](https://learn.microsoft.com/en-us/office/dev/add-ins/outlook/outlook-mobile-addins).
- Added `semanticDescription` field for Copilot for Microsoft 365. [Learn more](https://learn.microsoft.com/en-us/microsoftteams/platform/messaging-extensions/high-quality-message-extension?tabs=tasks#semantic-description).
- Added support for [creating message extensions](https://learn.microsoft.com/en-us/microsoftteams/platform/messaging-extensions/api-based-overview) from an existing API.
- Added apps to easily show as cards on [Viva Connections Dashboard](https://learn.microsoft.com/en-us/sharepoint/dev/spfx/viva/bot-powered/overview-bot-powered-aces).
- Added new [sample prompts](https://learn.microsoft.com/en-us/microsoftteams/platform/messaging-extensions/high-quality-message-extension?tabs=tasks#sample-prompts) to guide users who install or enable a plugin for the first time.
- Added [bot configurations](https://learn.microsoft.com/en-us/microsoftteams/platform/bots/how-to/bot-configuration-experience) changes.
- Deprecated `packageName` property.
- Deprecated `callingSidePanel` from manifest.

  

</details>

  


<details>
<summary>**Version 1.16**</summary>

### Version 1.16

February 2023

```http
https://developer.microsoft.com/json-schemas/teams/v1.16/MicrosoftTeams.schema.json
```

- Added `supportsAnonymousGuestUsers` in `meetingExtensionDefinition`.
- Added `team` and `groupChat` to the scope of staticTab.
- Added `privateChatTab`, `meetingChatTab`, `meetingDetailsTab`, `meetingSidePanel`, `meetingStage`, `teamLevelApp` to the context of staticTab.

  

</details>

  


<details>
<summary>**Version 1.15**</summary>

### Version 1.15

November 2022

```http
https://developer.microsoft.com/json-schemas/teams/v1.15/MicrosoftTeams.schema.json
```

- Added `supportsAnonymizedPayloads` feature. A Boolean that indicates whether the app's link message handler supports anonymous invoke flow.

  

</details>

  


<details>
<summary>**Version 1.14**</summary>

### Version 1.14

July 2022

```http
https://developer.microsoft.com/json-schemas/teams/v1.14/MicrosoftTeams.schema.json
```

- Added `supportedChannelTypes` feature. List of 'nonstandard' channel types that the app supports. Note: Channels of standard type are supported by default if the app supports team scope.
- Added `supportsStreaming`feature. A Boolean value indicating whether this app can stream the meeting's audio video content to a Real-Time Messaging Protocol \(RTMP\) endpoint.

  

</details>

  


<details>
<summary>**Version 1.13**</summary>

### Version 1.13

May 2022

```http
https://developer.microsoft.com/json-schemas/teams/v1.13/MicrosoftTeams.schema.json
```

With the release of version 1.13 of the App manifest, developers can build and update their app \(formerly Teams app\) to run in Microsoft 365 hosts such as Outlook, Teams, and Microsoft Teams App across web, desktop, and mobile. From this version release, it eases deployment workflow and provides a streamlined way to deliver cross-platform apps to an expanded user audience via a single codebase. For more details on host application feature support, visit [TeamsJS capability support across Microsoft 365](https://learn.microsoft.com/en-us/microsoftteams/platform/m365-apps/teamsjs-support-m365).

- This schema version supports extending Teams apps to other parts of the Microsoft 365 ecosystem. More info at [https://aka.ms/extendteamsapps](https://aka.ms/extendteamsapps).

  

</details>

## What's new in Version 1.23

July 2025

```http
https://developer.microsoft.com/json-schemas/teams/v1.23/MicrosoftTeams.schema.json
```

- Updated `extensionRibbonsCustomTabGroupsItem` to include the [`overriddenByRibbonApi` property](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-custom-tab-groups-item?view=m365-app-1.30#overriddenByRibbonApi-property), which hides groups in apps that support custom contextual tabs via the `Office.ribbon.requestCreateControls` API. Removed redundant node `extensionCommonCustomControlMenu`.
- Added bot [`registrationInfo`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-registration-info?view=m365-app-1.30) field to accommodate system-generated metadata for agents built with Microsoft Copilot Studio and other tools.
- Improved description for [`spamReportingOptions`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-spam-pre-processing-dialog?view=m365-app-1.30#spamReportingOptions-property)

## All generally available versions

  


<details>
<summary>**Version 1.29**</summary>

### Version 1.29

June 2026

```http
https://developer.microsoft.com/json-schemas/teams/v1.29/MicrosoftTeams.schema.json
```

- Enabled [human to agent one-turn conversation](https://learn.microsoft.com/en-us/microsoftteams/platform/agents-in-teams/targeted-messages) and add a new property [triggers](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-compose-extensions-commands?view=m365-app-1.30#triggers).
- Added support for dynamic tool discovery that allows Microsoft 365 agents to fetch the MCP server's tool list at runtime by calling the server's `tools/list` method. To enable dynamic discovery, provide the `remoteServerURL` and omit the [`mcpToolDescription`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-connectors-tool-source-remote-mcp-server?view=m365-app-1.30) property.
- Added support for Azure Key Vault authentication using [`AzureKeyVault`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-connectors-tool-source-remote-mcp-server-authorization?view=m365-app-1.30) property that allows you to store and manage your MCP server credentials in your own [Azure Key Vault](https://learn.microsoft.com/en-us/microsoftteams/platform/m365-apps/agent-connectors#configure-authentication) instance. This gives you full control over secret lifecycle management, including rotation, access policies, and audit logging.
</details>

  


<details>
<summary>**Version 1.28**</summary>

### Version 1.28

May 2026

```http
https://developer.microsoft.com/json-schemas/teams/v1.28/MicrosoftTeams.schema.json
```

- Expanded the range of icons array for extension tab groups \([extensionRibbonsCustomTabGroupsItem](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-custom-tab-groups-item?view=m365-app-1.30) object\) to minItems = 3 \(from 1\) and maxItems = 8 \(from 3\).
- Enable Office Add-ins to show or hide ribbon buttons, controls, and groups in custom or contextual tabs across Word, Excel, and PowerPoint \(Win32, Mac, Web\) using the new property [visible](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-array-tabs-item?view=m365-app-1.30#visible) for dynamic UI and less clutter.
- The [`agentSkills`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-skills?view=m365-app-1.30#rootagentskills-object) property allows developers to package AI agent skills as elements.
</details>

  


<details>
<summary>**Version 1.27**</summary>

### Version 1.27

May 2026

```http
https://developer.microsoft.com/json-schemas/teams/v1.27/MicrosoftTeams.schema.json
```

- Added [agent connectors](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-connectors) node to enable [configuration of connections](https://learn.microsoft.com/en-us/microsoftteams/platform/m365-apps/agent-connectors) between Microsoft 365 agents and external data sources through MCP servers.
- Added a new command [type](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-command-lists-commands) and a new property [prompt](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-command-lists-commands) under bots commands.
</details>

  


<details>
<summary>**Version 1.26**</summary>

### Version 1.26

April 2026

```http
https://developer.microsoft.com/json-schemas/teams/v1.26/MicrosoftTeams.schema.json
```

- Added optional [composeExtensions.authorization.oAuthConfiguration](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-compose-extensions-authorization-o-auth-configuration) object to implement [Open Authorization \(OAuth\) 2.0 support for API-based message extensions](https://learn.microsoft.com/en-us/microsoftteams/platform/messaging-extensions/api-based-oauth).
- Added [features](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-description) descriptions list to [showcase agent and app features to a profile card](https://learn.microsoft.com/en-us/microsoftteams/platform/bots/how-to/teams-conversational-ai/ai-ux) that appears when the user hovers over the app icon.
- [KeyTips](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-custom-control-menu-item) let developers set custom shortcut keys in Office, giving users more efficient ways to work in Word, Excel, and PowerPoint.
</details>

  


<details>
<summary>**Version 1.25**</summary>

### Version 1.25

January 2026

```http
https://developer.microsoft.com/json-schemas/teams/v1.25/MicrosoftTeams.schema.json
```

- New [agenticUserTemplates](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root?view=m365-app-1.30#agenticusertemplates) node to reference an [Agent 365 blueprint](https://learn.microsoft.com/en-us/microsoft-agent-365/developer/registration), enabling the instantiation of an AI agent with its own Microsoft Entra Agent ID within your organization.
- Added [supportsChannelFeatures](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root?view=m365-app-1.30#supportschannelfeatures) to opt in your app to [next level channel features, including shared and private channels](https://learn.microsoft.com/en-us/microsoftteams/platform/build-apps-for-shared-private-channels).
- Enhanced support for Excel custom functions, including [customFunctions.enum](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/enum?view=m365-app-1.30) to provide [autocomplete options for custom functions](https://learn.microsoft.com/en-us/office/dev/add-ins/excel/custom-functions-custom-enums) and additional [function properties](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-function?view=m365-app-1.30#properties) and datatypes from [CustomFunctionsRuntime 1.5](https://learn.microsoft.com/en-us/javascript/api/requirement-sets/excel/custom-functions-requirement-sets).
</details>

  


<details>
<summary>**Version 1.24**</summary>

### Version 1.24

October 2025

```http
https://developer.microsoft.com/json-schemas/teams/v1.24/MicrosoftTeams.schema.json
```

- Added [executeDataFunction](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-runtimes-actions-item?view=m365-app-1.30#type) action type to enable Copilot agents to invoke Office Add-ins functions and serve as [natural language interfaces to add-ins](https://learn.microsoft.com/en-us/office/dev/add-ins/design/agent-and-add-in-overview). The overall functionality of combining Copilot agents with Office Add-ins remains in preview.
- Introduced [windowsExtensions](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-alternate-versions-array-hide-windows-extensions?view=m365-app-1.30) mechanism to specify which COM- and VSTO-based add-ins should be disabled with the equivalent JavaScript add-in is installed. For more details, see [Option to disable the Windows-only add-in instead](https://learn.microsoft.com/en-us/office/dev/add-ins/develop/make-office-add-in-compatible-with-existing-com-add-in#option-to-disable-the-windows-only-add-in-instead-preview).
- Added [keyboardShortcuts](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-keyboard-shortcut?view=m365-app-1.30) to support [backwards compatibility of Office Add-ins with keyboard shortcuts](https://learn.microsoft.com/en-us/office/dev/add-ins/design/keyboard-shortcuts#support-backward-compatibility-for-add-ins-with-a-unified-manifest-in-appsource) and their localized strings \(if applicable\).
- Increased [bot commands](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-command-lists?view=m365-app-1.30#commands) limit from 10 to 12 to accommodate Microsoft Copilot Studio agents, which support up to 12 starter prompts.

  

</details>

  


<details>
<summary>**Version 1.23**</summary>

### Version 1.23

July 2025

```http
https://developer.microsoft.com/json-schemas/teams/v1.23/MicrosoftTeams.schema.json
```

- Updated `extensionRibbonsCustomTabGroupsItem` to include the [`overriddenByRibbonApi` property](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-custom-tab-groups-item?view=m365-app-1.30#overriddenByRibbonApi-property), which hides groups in apps that support custom contextual tabs via the `Office.ribbon.requestCreateControls` API. Removed redundant node `extensionCommonCustomControlMenu`.
- Added bot [`registrationInfo`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-registration-info?view=m365-app-1.30) field to accommodate system-generated metadata for agents built with Microsoft Copilot Studio and other tools.
- Improved description for [`spamReportingOptions`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-spam-pre-processing-dialog?view=m365-app-1.30#spamReportingOptions-property)

  

</details>

  


<details>
<summary>**Version 1.22**</summary>

### Version 1.22

May 2025

```http
https://developer.microsoft.com/json-schemas/teams/v1.22/MicrosoftTeams.schema.json
```

- Added [`activityIcons`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-activities-activity-icons?view=m365-app-1.30) and [`allowedIconIds`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-activities-activity-types?view=m365-app-1.30#allowedIconIds-property) properties to customize app icons in a user's activity feed. `activityIcons` defines the icon, while `allowedIconIds` specifies which icons appear for each activity type. For more information, see the [Teams activity feed](https://learn.microsoft.com/en-us/graph/teams-send-activityfeednotifications) and [custom icon guidelines](https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines#custom-activity-icons).
- Added the [`type property`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-spam-pre-processing-dialog-spam-reporting-options?view=m365-app-1.30#type-property) to the spam reporting preprocessing dialog to support either radio buttons or checkboxes for reporting options. For details, see [Configure the manifest](https://learn.microsoft.com/en-us/office/dev/add-ins/outlook/spam-reporting#configure-the-manifest).
- Added [`nestedAppAuthInfo`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-web-application-info?view=m365-app-1.30#nestedAppAuthInfo-property) property to enable prefetching of a nested app authentication token when a tab is loads. To details more, see [Nested app authentication](https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/authentication/nested-authentication).

  

</details>

  


<details>
<summary>**Version 1.21**</summary>

### Version 1.21

April 2025

```http
https://developer.microsoft.com/json-schemas/teams/v1.21/MicrosoftTeams.schema.json
```

- Developers can now specify a [32x32 color icon](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-icons?view=m365-app-1.30#color32x32) with a transparent background to ensure a consistent appearance when your app runs in Outlook and Microsoft 365. To learn more see,[Teams app package color icon](https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/build-and-test/apps-package#color-icon).
- Introduced new *copilot* value for [`bots.scopes`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots?view=m365-app-1.30#scopes) and [`defaultInstallScope`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root?view=m365-app-1.30#defaultinstallscope). To learn more, see [Build with Teams AI library](https://learn.microsoft.com/en-us/microsoftteams/platform/bots/how-to/teams-conversational-ai/how-conversation-ai-get-started).
- Added [`backgroundLoadConfiguration`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-background-load-configuration?view=m365-app-1.30) object to enable tab apps to [opt in to precaching](https://learn.microsoft.com/en-us/microsoftteams/platform/tabs/how-to/app-caching#enable-precaching-for-tab-app) for a faster initial load experience.

  

</details>

  


<details>
<summary>**Version 1.20**</summary>

### Version 1.20

March 2025

```http
https://developer.microsoft.com/json-schemas/teams/v1.20/MicrosoftTeams.schema.json
```

- Added [`elementRelationshipSet`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-element-relationship-set?view=m365-app-1.30) and [`requirementSet`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/element-requirement-set?view=m365-app-1.30) \(for `composeExtensions`, `bots`, and `staticTabs`\) objects so that apps can specify [runtime requirements in Microsoft 365 hosts](https://learn.microsoft.com/en-us/microsoftteams/platform/m365-apps/specify-runtime-requirements).
- Added [`intuneInfo`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-intune-info?view=m365-app-1.30) object for [Outlook Add-ins to attest to Intune Mobile App Management \(MAM\) support](https://learn.microsoft.com/en-us/javascript/api/outlook/office.mailbox) in order to signal compliance with organizational data protection policies.
- Added [`fixedControls`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-array-fixed-control-item?view=m365-app-1.30) object to build custom [spam-reporting handling with Outlook Add-ins](https://learn.microsoft.com/en-us/office/dev/add-ins/outlook/spam-reporting).

  

</details>

  


<details>
<summary>**Version 1.19**</summary>

### Version 1.19

September 2024

```http
https://developer.microsoft.com/json-schemas/teams/v1.19/MicrosoftTeams.schema.json
```

- Added [`copilotAgents`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-copilot-agents?view=m365-app-1.30) object for publishing [declarative agents for Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/overview-declarative-agent).
- Added [`defaultLanguageFile`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-localization-info?view=m365-app-1.30#defaultlanguagefile), a new required property for [Copilot agents that support multiple languages](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/localize-agents).

  

</details>

  


<details>
<summary>**Version 1.18** *Not available.*</summary>
</details>

  


<details>
<summary>**Version 1.17**</summary>

### Version 1.17

April 2024

```http
https://developer.microsoft.com/json-schemas/teams/v1.17/MicrosoftTeams.schema.json
```

- Added support for [mobile specific manifest elements for Outlook extensions](https://learn.microsoft.com/en-us/office/dev/add-ins/outlook/outlook-mobile-addins).
- Added `semanticDescription` field for Copilot for Microsoft 365. [Learn more](https://learn.microsoft.com/en-us/microsoftteams/platform/messaging-extensions/high-quality-message-extension?tabs=tasks#semantic-description).
- Added support for [creating message extensions](https://learn.microsoft.com/en-us/microsoftteams/platform/messaging-extensions/api-based-overview) from an existing API.
- Added apps to easily show as cards on [Viva Connections Dashboard](https://learn.microsoft.com/en-us/sharepoint/dev/spfx/viva/bot-powered/overview-bot-powered-aces).
- Added new [sample prompts](https://learn.microsoft.com/en-us/microsoftteams/platform/messaging-extensions/high-quality-message-extension?tabs=tasks#sample-prompts) to guide users who install or enable a plugin for the first time.
- Added [bot configurations](https://learn.microsoft.com/en-us/microsoftteams/platform/bots/how-to/bot-configuration-experience) changes.
- Deprecated `packageName` property.
- Deprecated `callingSidePanel` from manifest.

  

</details>

  


<details>
<summary>**Version 1.16**</summary>

### Version 1.16

February 2023

```http
https://developer.microsoft.com/json-schemas/teams/v1.16/MicrosoftTeams.schema.json
```

- Added `supportsAnonymousGuestUsers` in `meetingExtensionDefinition`.
- Added `team` and `groupChat` to the scope of staticTab.
- Added `privateChatTab`, `meetingChatTab`, `meetingDetailsTab`, `meetingSidePanel`, `meetingStage`, `teamLevelApp` to the context of staticTab.

  

</details>

  


<details>
<summary>**Version 1.15**</summary>

### Version 1.15

November 2022

```http
https://developer.microsoft.com/json-schemas/teams/v1.15/MicrosoftTeams.schema.json
```

- Added `supportsAnonymizedPayloads` feature. A Boolean that indicates whether the app's link message handler supports anonymous invoke flow.

  

</details>

  


<details>
<summary>**Version 1.14**</summary>

### Version 1.14

July 2022

```http
https://developer.microsoft.com/json-schemas/teams/v1.14/MicrosoftTeams.schema.json
```

- Added `supportedChannelTypes` feature. List of 'nonstandard' channel types that the app supports. Note: Channels of standard type are supported by default if the app supports team scope.
- Added `supportsStreaming`feature. A Boolean value indicating whether this app can stream the meeting's audio video content to a Real-Time Messaging Protocol \(RTMP\) endpoint.

  

</details>

  


<details>
<summary>**Version 1.13**</summary>

### Version 1.13

May 2022

```http
https://developer.microsoft.com/json-schemas/teams/v1.13/MicrosoftTeams.schema.json
```

With the release of version 1.13 of the App manifest, developers can build and update their app \(formerly Teams app\) to run in Microsoft 365 hosts such as Outlook, Teams, and Microsoft Teams App across web, desktop, and mobile. From this version release, it eases deployment workflow and provides a streamlined way to deliver cross-platform apps to an expanded user audience via a single codebase. For more details on host application feature support, visit [TeamsJS capability support across Microsoft 365](https://learn.microsoft.com/en-us/microsoftteams/platform/m365-apps/teamsjs-support-m365).

- This schema version supports extending Teams apps to other parts of the Microsoft 365 ecosystem. More info at [https://aka.ms/extendteamsapps](https://aka.ms/extendteamsapps).

  

</details>

## What's new in Version 1.22

May 2025

```http
https://developer.microsoft.com/json-schemas/teams/v1.22/MicrosoftTeams.schema.json
```

- Added [`activityIcons`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-activities-activity-icons?view=m365-app-1.30) and [`allowedIconIds`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-activities-activity-types?view=m365-app-1.30#allowedIconIds-property) properties to customize app icons in a user's activity feed. `activityIcons` defines the icon, while `allowedIconIds` specifies which icons appear for each activity type. For more information, see the [Teams activity feed](https://learn.microsoft.com/en-us/graph/teams-send-activityfeednotifications) and [custom icon guidelines](https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines#custom-activity-icons).
- Added the [`type property`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-spam-pre-processing-dialog-spam-reporting-options?view=m365-app-1.30#type-property) to the spam reporting preprocessing dialog to support either radio buttons or checkboxes for reporting options. For details, see [Configure the manifest](https://learn.microsoft.com/en-us/office/dev/add-ins/outlook/spam-reporting#configure-the-manifest).
- Added [`nestedAppAuthInfo`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-web-application-info?view=m365-app-1.30#nestedAppAuthInfo-property) property to enable prefetching of a nested app authentication token when a tab is loaded. See [Nested app authentication](https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/authentication/nested-authentication) to learn more.

## All generally available versions

  


<details>
<summary>**Version 1.29**</summary>

### Version 1.29

June 2026

```http
https://developer.microsoft.com/json-schemas/teams/v1.29/MicrosoftTeams.schema.json
```

- Enabled [human to agent one-turn conversation](https://learn.microsoft.com/en-us/microsoftteams/platform/agents-in-teams/targeted-messages) and add a new property [triggers](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-compose-extensions-commands?view=m365-app-1.30#triggers).
- Added support for dynamic tool discovery that allows Microsoft 365 agents to fetch the MCP server's tool list at runtime by calling the server's `tools/list` method. To enable dynamic discovery, provide the `remoteServerURL` and omit the [`mcpToolDescription`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-connectors-tool-source-remote-mcp-server?view=m365-app-1.30) property.
- Added support for Azure Key Vault authentication using [`AzureKeyVault`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-connectors-tool-source-remote-mcp-server-authorization?view=m365-app-1.30) property that allows you to store and manage your MCP server credentials in your own [Azure Key Vault](https://learn.microsoft.com/en-us/microsoftteams/platform/m365-apps/agent-connectors#configure-authentication) instance. This gives you full control over secret lifecycle management, including rotation, access policies, and audit logging.
</details>

  


<details>
<summary>**Version 1.28**</summary>

### Version 1.28

May 2026

```http
https://developer.microsoft.com/json-schemas/teams/v1.28/MicrosoftTeams.schema.json
```

- Expanded the range of icons array for extension tab groups \([extensionRibbonsCustomTabGroupsItem](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-custom-tab-groups-item?view=m365-app-1.30) object\) to minItems = 3 \(from 1\) and maxItems = 8 \(from 3\).
- Enable Office Add-ins to show or hide ribbon buttons, controls, and groups in custom or contextual tabs across Word, Excel, and PowerPoint \(Win32, Mac, Web\) using the new property [visible](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-array-tabs-item?view=m365-app-1.30#visible) for dynamic UI and less clutter.
- The [`agentSkills`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-skills?view=m365-app-1.30#rootagentskills-object) property allows developers to package AI agent skills as elements.
</details>

  


<details>
<summary>**Version 1.27**</summary>

### Version 1.27

May 2026

```http
https://developer.microsoft.com/json-schemas/teams/v1.27/MicrosoftTeams.schema.json
```

- Added [agent connectors](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-connectors) node to enable [configuration of connections](https://learn.microsoft.com/en-us/microsoftteams/platform/m365-apps/agent-connectors) between Microsoft 365 agents and external data sources through MCP servers.
- Added a new command [type](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-command-lists-commands) and a new property [prompt](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-command-lists-commands) under bots commands.
</details>

  


<details>
<summary>**Version 1.26**</summary>

### Version 1.26

April 2026

```http
https://developer.microsoft.com/json-schemas/teams/v1.26/MicrosoftTeams.schema.json
```

- Added optional [composeExtensions.authorization.oAuthConfiguration](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-compose-extensions-authorization-o-auth-configuration) object to implement [Open Authorization \(OAuth\) 2.0 support for API-based message extensions](https://learn.microsoft.com/en-us/microsoftteams/platform/messaging-extensions/api-based-oauth).
- Added [features](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-description) descriptions list to [showcase agent and app features to a profile card](https://learn.microsoft.com/en-us/microsoftteams/platform/bots/how-to/teams-conversational-ai/ai-ux) that appears when the user hovers over the app icon.
- [KeyTips](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-custom-control-menu-item) let developers set custom shortcut keys in Office, giving users more efficient ways to work in Word, Excel, and PowerPoint.
</details>

  


<details>
<summary>**Version 1.25**</summary>

### Version 1.25

January 2026

```http
https://developer.microsoft.com/json-schemas/teams/v1.25/MicrosoftTeams.schema.json
```

- New [agenticUserTemplates](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root?view=m365-app-1.30#agenticusertemplates) node to reference an [Agent 365 blueprint](https://learn.microsoft.com/en-us/microsoft-agent-365/developer/registration), enabling the instantiation of an AI agent with its own Microsoft Entra Agent ID within your organization.
- Added [supportsChannelFeatures](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root?view=m365-app-1.30#supportschannelfeatures) to opt in your app to [next level channel features, including shared and private channels](https://learn.microsoft.com/en-us/microsoftteams/platform/build-apps-for-shared-private-channels).
- Enhanced support for Excel custom functions, including [customFunctions.enum](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/enum?view=m365-app-1.30) to provide [autocomplete options for custom functions](https://learn.microsoft.com/en-us/office/dev/add-ins/excel/custom-functions-custom-enums) and additional [function properties](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-function?view=m365-app-1.30#properties) and datatypes from [CustomFunctionsRuntime 1.5](https://learn.microsoft.com/en-us/javascript/api/requirement-sets/excel/custom-functions-requirement-sets).
</details>

  


<details>
<summary>**Version 1.24**</summary>

### Version 1.24

October 2025

```http
https://developer.microsoft.com/json-schemas/teams/v1.24/MicrosoftTeams.schema.json
```

- Added [executeDataFunction](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-runtimes-actions-item?view=m365-app-1.30#type) action type to enable Copilot agents to invoke Office Add-ins functions and serve as [natural language interfaces to add-ins](https://learn.microsoft.com/en-us/office/dev/add-ins/design/agent-and-add-in-overview). The overall functionality of combining Copilot agents with Office Add-ins remains in preview.
- Introduced [windowsExtensions](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-alternate-versions-array-hide-windows-extensions?view=m365-app-1.30) mechanism to specify which COM- and VSTO-based add-ins should be disabled with the equivalent JavaScript add-in is installed. For more details, see [Option to disable the Windows-only add-in instead](https://learn.microsoft.com/en-us/office/dev/add-ins/develop/make-office-add-in-compatible-with-existing-com-add-in#option-to-disable-the-windows-only-add-in-instead-preview).
- Added [keyboardShortcuts](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-keyboard-shortcut?view=m365-app-1.30) to support [backwards compatibility of Office Add-ins with keyboard shortcuts](https://learn.microsoft.com/en-us/office/dev/add-ins/design/keyboard-shortcuts#support-backward-compatibility-for-add-ins-with-a-unified-manifest-in-appsource) and their localized strings \(if applicable\).
- Increased [bot commands](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-command-lists?view=m365-app-1.30#commands) limit from 10 to 12 to accommodate Microsoft Copilot Studio agents, which support up to 12 starter prompts.

  

</details>

  


<details>
<summary>**Version 1.23**</summary>

### Version 1.23

July 2025

```http
https://developer.microsoft.com/json-schemas/teams/v1.23/MicrosoftTeams.schema.json
```

- Updated `extensionRibbonsCustomTabGroupsItem` to include the [`overriddenByRibbonApi` property](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-custom-tab-groups-item?view=m365-app-1.30#overriddenByRibbonApi-property), which hides groups in apps that support custom contextual tabs via the `Office.ribbon.requestCreateControls` API. Removed redundant node `extensionCommonCustomControlMenu`.
- Added bot [`registrationInfo`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-registration-info?view=m365-app-1.30) field to accommodate system-generated metadata for agents built with Microsoft Copilot Studio and other tools.
- Improved description for [`spamReportingOptions`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-spam-pre-processing-dialog?view=m365-app-1.30#spamReportingOptions-property)

  

</details>

  


<details>
<summary>**Version 1.22**</summary>

### Version 1.22

May 2025

```http
https://developer.microsoft.com/json-schemas/teams/v1.22/MicrosoftTeams.schema.json
```

- Added [`activityIcons`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-activities-activity-icons?view=m365-app-1.30) and [`allowedIconIds`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-activities-activity-types?view=m365-app-1.30#allowedIconIds-property) properties to customize app icons in a user's activity feed. `activityIcons` defines the icon, while `allowedIconIds` specifies which icons appear for each activity type. For more information, see the [Teams activity feed](https://learn.microsoft.com/en-us/graph/teams-send-activityfeednotifications) and [custom icon guidelines](https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines#custom-activity-icons).
- Added the [`type property`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-spam-pre-processing-dialog-spam-reporting-options?view=m365-app-1.30#type-property) to the spam reporting preprocessing dialog to support either radio buttons or checkboxes for reporting options. For details, see [Configure the manifest](https://learn.microsoft.com/en-us/office/dev/add-ins/outlook/spam-reporting#configure-the-manifest).
- Added [`nestedAppAuthInfo`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-web-application-info?view=m365-app-1.30#nestedAppAuthInfo-property) property to enable prefetching of a nested app authentication token when a tab is loads. To details more, see [Nested app authentication](https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/authentication/nested-authentication).

  

</details>

  


<details>
<summary>**Version 1.21**</summary>

### Version 1.21

April 2025

```http
https://developer.microsoft.com/json-schemas/teams/v1.21/MicrosoftTeams.schema.json
```

- Developers can now specify a [32x32 color icon](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-icons?view=m365-app-1.30#color32x32) with a transparent background to ensure a consistent appearance when your app runs in Outlook and Microsoft 365. To learn more see,[Teams app package color icon](https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/build-and-test/apps-package#color-icon).
- Introduced new *copilot* value for [`bots.scopes`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots?view=m365-app-1.30#scopes) and [`defaultInstallScope`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root?view=m365-app-1.30#defaultinstallscope). To learn more, see [Build with Teams AI library](https://learn.microsoft.com/en-us/microsoftteams/platform/bots/how-to/teams-conversational-ai/how-conversation-ai-get-started).
- Added [`backgroundLoadConfiguration`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-background-load-configuration?view=m365-app-1.30) object to enable tab apps to [opt in to precaching](https://learn.microsoft.com/en-us/microsoftteams/platform/tabs/how-to/app-caching#enable-precaching-for-tab-app) for a faster initial load experience.

  

</details>

  


<details>
<summary>**Version 1.20**</summary>

### Version 1.20

March 2025

```http
https://developer.microsoft.com/json-schemas/teams/v1.20/MicrosoftTeams.schema.json
```

- Added [`elementRelationshipSet`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-element-relationship-set?view=m365-app-1.30) and [`requirementSet`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/element-requirement-set?view=m365-app-1.30) \(for `composeExtensions`, `bots`, and `staticTabs`\) objects so that apps can specify [runtime requirements in Microsoft 365 hosts](https://learn.microsoft.com/en-us/microsoftteams/platform/m365-apps/specify-runtime-requirements).
- Added [`intuneInfo`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-intune-info?view=m365-app-1.30) object for [Outlook Add-ins to attest to Intune Mobile App Management \(MAM\) support](https://learn.microsoft.com/en-us/javascript/api/outlook/office.mailbox) in order to signal compliance with organizational data protection policies.
- Added [`fixedControls`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-array-fixed-control-item?view=m365-app-1.30) object to build custom [spam-reporting handling with Outlook Add-ins](https://learn.microsoft.com/en-us/office/dev/add-ins/outlook/spam-reporting).

  

</details>

  


<details>
<summary>**Version 1.19**</summary>

### Version 1.19

September 2024

```http
https://developer.microsoft.com/json-schemas/teams/v1.19/MicrosoftTeams.schema.json
```

- Added [`copilotAgents`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-copilot-agents?view=m365-app-1.30) object for publishing [declarative agents for Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/overview-declarative-agent).
- Added [`defaultLanguageFile`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-localization-info?view=m365-app-1.30#defaultlanguagefile), a new required property for [Copilot agents that support multiple languages](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/localize-agents).

  

</details>

  


<details>
<summary>**Version 1.18** *Not available.*</summary>
</details>

  


<details>
<summary>**Version 1.17**</summary>

### Version 1.17

April 2024

```http
https://developer.microsoft.com/json-schemas/teams/v1.17/MicrosoftTeams.schema.json
```

- Added support for [mobile specific manifest elements for Outlook extensions](https://learn.microsoft.com/en-us/office/dev/add-ins/outlook/outlook-mobile-addins).
- Added `semanticDescription` field for Copilot for Microsoft 365. [Learn more](https://learn.microsoft.com/en-us/microsoftteams/platform/messaging-extensions/high-quality-message-extension?tabs=tasks#semantic-description).
- Added support for [creating message extensions](https://learn.microsoft.com/en-us/microsoftteams/platform/messaging-extensions/api-based-overview) from an existing API.
- Added apps to easily show as cards on [Viva Connections Dashboard](https://learn.microsoft.com/en-us/sharepoint/dev/spfx/viva/bot-powered/overview-bot-powered-aces).
- Added new [sample prompts](https://learn.microsoft.com/en-us/microsoftteams/platform/messaging-extensions/high-quality-message-extension?tabs=tasks#sample-prompts) to guide users who install or enable a plugin for the first time.
- Added [bot configurations](https://learn.microsoft.com/en-us/microsoftteams/platform/bots/how-to/bot-configuration-experience) changes.
- Deprecated `packageName` property.
- Deprecated `callingSidePanel` from manifest.

  

</details>

  


<details>
<summary>**Version 1.16**</summary>

### Version 1.16

February 2023

```http
https://developer.microsoft.com/json-schemas/teams/v1.16/MicrosoftTeams.schema.json
```

- Added `supportsAnonymousGuestUsers` in `meetingExtensionDefinition`.
- Added `team` and `groupChat` to the scope of staticTab.
- Added `privateChatTab`, `meetingChatTab`, `meetingDetailsTab`, `meetingSidePanel`, `meetingStage`, `teamLevelApp` to the context of staticTab.

  

</details>

  


<details>
<summary>**Version 1.15**</summary>

### Version 1.15

November 2022

```http
https://developer.microsoft.com/json-schemas/teams/v1.15/MicrosoftTeams.schema.json
```

- Added `supportsAnonymizedPayloads` feature. A Boolean that indicates whether the app's link message handler supports anonymous invoke flow.

  

</details>

  


<details>
<summary>**Version 1.14**</summary>

### Version 1.14

July 2022

```http
https://developer.microsoft.com/json-schemas/teams/v1.14/MicrosoftTeams.schema.json
```

- Added `supportedChannelTypes` feature. List of 'nonstandard' channel types that the app supports. Note: Channels of standard type are supported by default if the app supports team scope.
- Added `supportsStreaming`feature. A Boolean value indicating whether this app can stream the meeting's audio video content to a Real-Time Messaging Protocol \(RTMP\) endpoint.

  

</details>

  


<details>
<summary>**Version 1.13**</summary>

### Version 1.13

May 2022

```http
https://developer.microsoft.com/json-schemas/teams/v1.13/MicrosoftTeams.schema.json
```

With the release of version 1.13 of the App manifest, developers can build and update their app \(formerly Teams app\) to run in Microsoft 365 hosts such as Outlook, Teams, and Microsoft Teams App across web, desktop, and mobile. From this version release, it eases deployment workflow and provides a streamlined way to deliver cross-platform apps to an expanded user audience via a single codebase. For more details on host application feature support, visit [TeamsJS capability support across Microsoft 365](https://learn.microsoft.com/en-us/microsoftteams/platform/m365-apps/teamsjs-support-m365).

- This schema version supports extending Teams apps to other parts of the Microsoft 365 ecosystem. More info at [https://aka.ms/extendteamsapps](https://aka.ms/extendteamsapps).

  

</details>

## What's new in Version 1.21

April 2025

```http
https://developer.microsoft.com/json-schemas/teams/v1.21/MicrosoftTeams.schema.json
```

- Developers can now specify a [32x32 color icon](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-icons?view=m365-app-1.30#color32x32) with a transparent background to ensure a consistent appearance when your app runs in Outlook and Microsoft 365. To learn more see,[Teams app package color icon](https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/build-and-test/apps-package#color-icon).
- Introduced new *copilot* value for [`bots.scopes`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots?view=m365-app-1.30#scopes) and [`defaultInstallScope`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root?view=m365-app-1.30#defaultinstallscope). To learn more, see [Build with Teams AI library](https://learn.microsoft.com/en-us/microsoftteams/platform/bots/how-to/teams-conversational-ai/how-conversation-ai-get-started).
- Added [`backgroundLoadConfiguration`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-background-load-configuration?view=m365-app-1.30) object to enable tab apps to [opt in to precaching](https://learn.microsoft.com/en-us/microsoftteams/platform/tabs/how-to/app-caching#enable-precaching-for-tab-app) for a faster initial load experience.

## All generally available versions

  


<details>
<summary>**Version 1.29**</summary>

### Version 1.29

June 2026

```http
https://developer.microsoft.com/json-schemas/teams/v1.29/MicrosoftTeams.schema.json
```

- Enabled [human to agent one-turn conversation](https://learn.microsoft.com/en-us/microsoftteams/platform/agents-in-teams/targeted-messages) and add a new property [triggers](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-compose-extensions-commands?view=m365-app-1.30#triggers).
- Added support for dynamic tool discovery that allows Microsoft 365 agents to fetch the MCP server's tool list at runtime by calling the server's `tools/list` method. To enable dynamic discovery, provide the `remoteServerURL` and omit the [`mcpToolDescription`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-connectors-tool-source-remote-mcp-server?view=m365-app-1.30) property.
- Added support for Azure Key Vault authentication using [`AzureKeyVault`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-connectors-tool-source-remote-mcp-server-authorization?view=m365-app-1.30) property that allows you to store and manage your MCP server credentials in your own [Azure Key Vault](https://learn.microsoft.com/en-us/microsoftteams/platform/m365-apps/agent-connectors#configure-authentication) instance. This gives you full control over secret lifecycle management, including rotation, access policies, and audit logging.
</details>

  


<details>
<summary>**Version 1.28**</summary>

### Version 1.28

May 2026

```http
https://developer.microsoft.com/json-schemas/teams/v1.28/MicrosoftTeams.schema.json
```

- Expanded the range of icons array for extension tab groups \([extensionRibbonsCustomTabGroupsItem](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-custom-tab-groups-item?view=m365-app-1.30) object\) to minItems = 3 \(from 1\) and maxItems = 8 \(from 3\).
- Enable Office Add-ins to show or hide ribbon buttons, controls, and groups in custom or contextual tabs across Word, Excel, and PowerPoint \(Win32, Mac, Web\) using the new property [visible](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-array-tabs-item?view=m365-app-1.30#visible) for dynamic UI and less clutter.
- The [`agentSkills`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-skills?view=m365-app-1.30#rootagentskills-object) property allows developers to package AI agent skills as elements.
</details>

  


<details>
<summary>**Version 1.27**</summary>

### Version 1.27

May 2026

```http
https://developer.microsoft.com/json-schemas/teams/v1.27/MicrosoftTeams.schema.json
```

- Added [agent connectors](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-connectors) node to enable [configuration of connections](https://learn.microsoft.com/en-us/microsoftteams/platform/m365-apps/agent-connectors) between Microsoft 365 agents and external data sources through MCP servers.
- Added a new command [type](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-command-lists-commands) and a new property [prompt](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-command-lists-commands) under bots commands.
</details>

  


<details>
<summary>**Version 1.26**</summary>

### Version 1.26

April 2026

```http
https://developer.microsoft.com/json-schemas/teams/v1.26/MicrosoftTeams.schema.json
```

- Added optional [composeExtensions.authorization.oAuthConfiguration](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-compose-extensions-authorization-o-auth-configuration) object to implement [Open Authorization \(OAuth\) 2.0 support for API-based message extensions](https://learn.microsoft.com/en-us/microsoftteams/platform/messaging-extensions/api-based-oauth).
- Added [features](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-description) descriptions list to [showcase agent and app features to a profile card](https://learn.microsoft.com/en-us/microsoftteams/platform/bots/how-to/teams-conversational-ai/ai-ux) that appears when the user hovers over the app icon.
- [KeyTips](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-custom-control-menu-item) let developers set custom shortcut keys in Office, giving users more efficient ways to work in Word, Excel, and PowerPoint.
</details>

  


<details>
<summary>**Version 1.25**</summary>

### Version 1.25

January 2026

```http
https://developer.microsoft.com/json-schemas/teams/v1.25/MicrosoftTeams.schema.json
```

- New [agenticUserTemplates](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root?view=m365-app-1.30#agenticusertemplates) node to reference an [Agent 365 blueprint](https://learn.microsoft.com/en-us/microsoft-agent-365/developer/registration), enabling the instantiation of an AI agent with its own Microsoft Entra Agent ID within your organization.
- Added [supportsChannelFeatures](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root?view=m365-app-1.30#supportschannelfeatures) to opt in your app to [next level channel features, including shared and private channels](https://learn.microsoft.com/en-us/microsoftteams/platform/build-apps-for-shared-private-channels).
- Enhanced support for Excel custom functions, including [customFunctions.enum](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/enum?view=m365-app-1.30) to provide [autocomplete options for custom functions](https://learn.microsoft.com/en-us/office/dev/add-ins/excel/custom-functions-custom-enums) and additional [function properties](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-function?view=m365-app-1.30#properties) and datatypes from [CustomFunctionsRuntime 1.5](https://learn.microsoft.com/en-us/javascript/api/requirement-sets/excel/custom-functions-requirement-sets).
</details>

  


<details>
<summary>**Version 1.24**</summary>

### Version 1.24

October 2025

```http
https://developer.microsoft.com/json-schemas/teams/v1.24/MicrosoftTeams.schema.json
```

- Added [executeDataFunction](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-runtimes-actions-item?view=m365-app-1.30#type) action type to enable Copilot agents to invoke Office Add-ins functions and serve as [natural language interfaces to add-ins](https://learn.microsoft.com/en-us/office/dev/add-ins/design/agent-and-add-in-overview). The overall functionality of combining Copilot agents with Office Add-ins remains in preview.
- Introduced [windowsExtensions](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-alternate-versions-array-hide-windows-extensions?view=m365-app-1.30) mechanism to specify which COM- and VSTO-based add-ins should be disabled with the equivalent JavaScript add-in is installed. For more details, see [Option to disable the Windows-only add-in instead](https://learn.microsoft.com/en-us/office/dev/add-ins/develop/make-office-add-in-compatible-with-existing-com-add-in#option-to-disable-the-windows-only-add-in-instead-preview).
- Added [keyboardShortcuts](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-keyboard-shortcut?view=m365-app-1.30) to support [backwards compatibility of Office Add-ins with keyboard shortcuts](https://learn.microsoft.com/en-us/office/dev/add-ins/design/keyboard-shortcuts#support-backward-compatibility-for-add-ins-with-a-unified-manifest-in-appsource) and their localized strings \(if applicable\).
- Increased [bot commands](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-command-lists?view=m365-app-1.30#commands) limit from 10 to 12 to accommodate Microsoft Copilot Studio agents, which support up to 12 starter prompts.

  

</details>

  


<details>
<summary>**Version 1.23**</summary>

### Version 1.23

July 2025

```http
https://developer.microsoft.com/json-schemas/teams/v1.23/MicrosoftTeams.schema.json
```

- Updated `extensionRibbonsCustomTabGroupsItem` to include the [`overriddenByRibbonApi` property](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-custom-tab-groups-item?view=m365-app-1.30#overriddenByRibbonApi-property), which hides groups in apps that support custom contextual tabs via the `Office.ribbon.requestCreateControls` API. Removed redundant node `extensionCommonCustomControlMenu`.
- Added bot [`registrationInfo`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-registration-info?view=m365-app-1.30) field to accommodate system-generated metadata for agents built with Microsoft Copilot Studio and other tools.
- Improved description for [`spamReportingOptions`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-spam-pre-processing-dialog?view=m365-app-1.30#spamReportingOptions-property)

  

</details>

  


<details>
<summary>**Version 1.22**</summary>

### Version 1.22

May 2025

```http
https://developer.microsoft.com/json-schemas/teams/v1.22/MicrosoftTeams.schema.json
```

- Added [`activityIcons`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-activities-activity-icons?view=m365-app-1.30) and [`allowedIconIds`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-activities-activity-types?view=m365-app-1.30#allowedIconIds-property) properties to customize app icons in a user's activity feed. `activityIcons` defines the icon, while `allowedIconIds` specifies which icons appear for each activity type. For more information, see the [Teams activity feed](https://learn.microsoft.com/en-us/graph/teams-send-activityfeednotifications) and [custom icon guidelines](https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines#custom-activity-icons).
- Added the [`type property`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-spam-pre-processing-dialog-spam-reporting-options?view=m365-app-1.30#type-property) to the spam reporting preprocessing dialog to support either radio buttons or checkboxes for reporting options. For details, see [Configure the manifest](https://learn.microsoft.com/en-us/office/dev/add-ins/outlook/spam-reporting#configure-the-manifest).
- Added [`nestedAppAuthInfo`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-web-application-info?view=m365-app-1.30#nestedAppAuthInfo-property) property to enable prefetching of a nested app authentication token when a tab is loads. To details more, see [Nested app authentication](https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/authentication/nested-authentication).

  

</details>

  


<details>
<summary>**Version 1.21**</summary>

### Version 1.21

April 2025

```http
https://developer.microsoft.com/json-schemas/teams/v1.21/MicrosoftTeams.schema.json
```

- Developers can now specify a [32x32 color icon](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-icons?view=m365-app-1.30#color32x32) with a transparent background to ensure a consistent appearance when your app runs in Outlook and Microsoft 365. To learn more see,[Teams app package color icon](https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/build-and-test/apps-package#color-icon).
- Introduced new *copilot* value for [`bots.scopes`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots?view=m365-app-1.30#scopes) and [`defaultInstallScope`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root?view=m365-app-1.30#defaultinstallscope). To learn more, see [Build with Teams AI library](https://learn.microsoft.com/en-us/microsoftteams/platform/bots/how-to/teams-conversational-ai/how-conversation-ai-get-started).
- Added [`backgroundLoadConfiguration`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-background-load-configuration?view=m365-app-1.30) object to enable tab apps to [opt in to precaching](https://learn.microsoft.com/en-us/microsoftteams/platform/tabs/how-to/app-caching#enable-precaching-for-tab-app) for a faster initial load experience.

  

</details>

  


<details>
<summary>**Version 1.20**</summary>

### Version 1.20

March 2025

```http
https://developer.microsoft.com/json-schemas/teams/v1.20/MicrosoftTeams.schema.json
```

- Added [`elementRelationshipSet`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-element-relationship-set?view=m365-app-1.30) and [`requirementSet`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/element-requirement-set?view=m365-app-1.30) \(for `composeExtensions`, `bots`, and `staticTabs`\) objects so that apps can specify [runtime requirements in Microsoft 365 hosts](https://learn.microsoft.com/en-us/microsoftteams/platform/m365-apps/specify-runtime-requirements).
- Added [`intuneInfo`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-intune-info?view=m365-app-1.30) object for [Outlook Add-ins to attest to Intune Mobile App Management \(MAM\) support](https://learn.microsoft.com/en-us/javascript/api/outlook/office.mailbox) in order to signal compliance with organizational data protection policies.
- Added [`fixedControls`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-array-fixed-control-item?view=m365-app-1.30) object to build custom [spam-reporting handling with Outlook Add-ins](https://learn.microsoft.com/en-us/office/dev/add-ins/outlook/spam-reporting).

  

</details>

  


<details>
<summary>**Version 1.19**</summary>

### Version 1.19

September 2024

```http
https://developer.microsoft.com/json-schemas/teams/v1.19/MicrosoftTeams.schema.json
```

- Added [`copilotAgents`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-copilot-agents?view=m365-app-1.30) object for publishing [declarative agents for Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/overview-declarative-agent).
- Added [`defaultLanguageFile`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-localization-info?view=m365-app-1.30#defaultlanguagefile), a new required property for [Copilot agents that support multiple languages](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/localize-agents).

  

</details>

  


<details>
<summary>**Version 1.18** *Not available.*</summary>
</details>

  


<details>
<summary>**Version 1.17**</summary>

### Version 1.17

April 2024

```http
https://developer.microsoft.com/json-schemas/teams/v1.17/MicrosoftTeams.schema.json
```

- Added support for [mobile specific manifest elements for Outlook extensions](https://learn.microsoft.com/en-us/office/dev/add-ins/outlook/outlook-mobile-addins).
- Added `semanticDescription` field for Copilot for Microsoft 365. [Learn more](https://learn.microsoft.com/en-us/microsoftteams/platform/messaging-extensions/high-quality-message-extension?tabs=tasks#semantic-description).
- Added support for [creating message extensions](https://learn.microsoft.com/en-us/microsoftteams/platform/messaging-extensions/api-based-overview) from an existing API.
- Added apps to easily show as cards on [Viva Connections Dashboard](https://learn.microsoft.com/en-us/sharepoint/dev/spfx/viva/bot-powered/overview-bot-powered-aces).
- Added new [sample prompts](https://learn.microsoft.com/en-us/microsoftteams/platform/messaging-extensions/high-quality-message-extension?tabs=tasks#sample-prompts) to guide users who install or enable a plugin for the first time.
- Added [bot configurations](https://learn.microsoft.com/en-us/microsoftteams/platform/bots/how-to/bot-configuration-experience) changes.
- Deprecated `packageName` property.
- Deprecated `callingSidePanel` from manifest.

  

</details>

  


<details>
<summary>**Version 1.16**</summary>

### Version 1.16

February 2023

```http
https://developer.microsoft.com/json-schemas/teams/v1.16/MicrosoftTeams.schema.json
```

- Added `supportsAnonymousGuestUsers` in `meetingExtensionDefinition`.
- Added `team` and `groupChat` to the scope of staticTab.
- Added `privateChatTab`, `meetingChatTab`, `meetingDetailsTab`, `meetingSidePanel`, `meetingStage`, `teamLevelApp` to the context of staticTab.

  

</details>

  


<details>
<summary>**Version 1.15**</summary>

### Version 1.15

November 2022

```http
https://developer.microsoft.com/json-schemas/teams/v1.15/MicrosoftTeams.schema.json
```

- Added `supportsAnonymizedPayloads` feature. A Boolean that indicates whether the app's link message handler supports anonymous invoke flow.

  

</details>

  


<details>
<summary>**Version 1.14**</summary>

### Version 1.14

July 2022

```http
https://developer.microsoft.com/json-schemas/teams/v1.14/MicrosoftTeams.schema.json
```

- Added `supportedChannelTypes` feature. List of 'nonstandard' channel types that the app supports. Note: Channels of standard type are supported by default if the app supports team scope.
- Added `supportsStreaming`feature. A Boolean value indicating whether this app can stream the meeting's audio video content to a Real-Time Messaging Protocol \(RTMP\) endpoint.

  

</details>

  


<details>
<summary>**Version 1.13**</summary>

### Version 1.13

May 2022

```http
https://developer.microsoft.com/json-schemas/teams/v1.13/MicrosoftTeams.schema.json
```

With the release of version 1.13 of the App manifest, developers can build and update their app \(formerly Teams app\) to run in Microsoft 365 hosts such as Outlook, Teams, and Microsoft Teams App across web, desktop, and mobile. From this version release, it eases deployment workflow and provides a streamlined way to deliver cross-platform apps to an expanded user audience via a single codebase. For more details on host application feature support, visit [TeamsJS capability support across Microsoft 365](https://learn.microsoft.com/en-us/microsoftteams/platform/m365-apps/teamsjs-support-m365).

- This schema version supports extending Teams apps to other parts of the Microsoft 365 ecosystem. More info at [https://aka.ms/extendteamsapps](https://aka.ms/extendteamsapps).

  

</details>

## What's new in Version 1.20

March 2025

```http
https://developer.microsoft.com/json-schemas/teams/v1.20/MicrosoftTeams.schema.json
```

- Added [`elementRelationshipSet`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-element-relationship-set?view=m365-app-1.30) and [`requirementSet`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/element-requirement-set?view=m365-app-1.30) \(for `composeExtensions`, `bots`, and `staticTabs`\) objects so that apps can specify [runtime requirements in Microsoft 365 hosts](https://learn.microsoft.com/en-us/microsoftteams/platform/m365-apps/specify-runtime-requirements).
- Added [`intuneInfo`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-intune-info?view=m365-app-1.30) object for [Outlook Add-ins to attest to Intune Mobile App Management \(MAM\) support](https://learn.microsoft.com/en-us/javascript/api/outlook/office.mailbox) in order to signal compliance with organizational data protection policies.
- Added [`fixedControls`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-array-fixed-control-item?view=m365-app-1.30) object to build custom [spam-reporting handling with Outlook Add-ins](https://learn.microsoft.com/en-us/office/dev/add-ins/outlook/spam-reporting).

## All generally available versions

  


<details>
<summary>**Version 1.29**</summary>

### Version 1.29

June 2026

```http
https://developer.microsoft.com/json-schemas/teams/v1.29/MicrosoftTeams.schema.json
```

- Enabled [human to agent one-turn conversation](https://learn.microsoft.com/en-us/microsoftteams/platform/agents-in-teams/targeted-messages) and add a new property [triggers](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-compose-extensions-commands?view=m365-app-1.30#triggers).
- Added support for dynamic tool discovery that allows Microsoft 365 agents to fetch the MCP server's tool list at runtime by calling the server's `tools/list` method. To enable dynamic discovery, provide the `remoteServerURL` and omit the [`mcpToolDescription`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-connectors-tool-source-remote-mcp-server?view=m365-app-1.30) property.
- Added support for Azure Key Vault authentication using [`AzureKeyVault`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-connectors-tool-source-remote-mcp-server-authorization?view=m365-app-1.30) property that allows you to store and manage your MCP server credentials in your own [Azure Key Vault](https://learn.microsoft.com/en-us/microsoftteams/platform/m365-apps/agent-connectors#configure-authentication) instance. This gives you full control over secret lifecycle management, including rotation, access policies, and audit logging.
</details>

  


<details>
<summary>**Version 1.28**</summary>

### Version 1.28

May 2026

```http
https://developer.microsoft.com/json-schemas/teams/v1.28/MicrosoftTeams.schema.json
```

- Expanded the range of icons array for extension tab groups \([extensionRibbonsCustomTabGroupsItem](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-custom-tab-groups-item?view=m365-app-1.30) object\) to minItems = 3 \(from 1\) and maxItems = 8 \(from 3\).
- Enable Office Add-ins to show or hide ribbon buttons, controls, and groups in custom or contextual tabs across Word, Excel, and PowerPoint \(Win32, Mac, Web\) using the new property [visible](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-array-tabs-item?view=m365-app-1.30#visible) for dynamic UI and less clutter.
- The [`agentSkills`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-skills?view=m365-app-1.30#rootagentskills-object) property allows developers to package AI agent skills as elements.
</details>

  


<details>
<summary>**Version 1.27**</summary>

### Version 1.27

May 2026

```http
https://developer.microsoft.com/json-schemas/teams/v1.27/MicrosoftTeams.schema.json
```

- Added [agent connectors](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-connectors) node to enable [configuration of connections](https://learn.microsoft.com/en-us/microsoftteams/platform/m365-apps/agent-connectors) between Microsoft 365 agents and external data sources through MCP servers.
- Added a new command [type](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-command-lists-commands) and a new property [prompt](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-command-lists-commands) under bots commands.
</details>

  


<details>
<summary>**Version 1.26**</summary>

### Version 1.26

April 2026

```http
https://developer.microsoft.com/json-schemas/teams/v1.26/MicrosoftTeams.schema.json
```

- Added optional [composeExtensions.authorization.oAuthConfiguration](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-compose-extensions-authorization-o-auth-configuration) object to implement [Open Authorization \(OAuth\) 2.0 support for API-based message extensions](https://learn.microsoft.com/en-us/microsoftteams/platform/messaging-extensions/api-based-oauth).
- Added [features](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-description) descriptions list to [showcase agent and app features to a profile card](https://learn.microsoft.com/en-us/microsoftteams/platform/bots/how-to/teams-conversational-ai/ai-ux) that appears when the user hovers over the app icon.
- [KeyTips](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-custom-control-menu-item) let developers set custom shortcut keys in Office, giving users more efficient ways to work in Word, Excel, and PowerPoint.
</details>

  


<details>
<summary>**Version 1.25**</summary>

### Version 1.25

January 2026

```http
https://developer.microsoft.com/json-schemas/teams/v1.25/MicrosoftTeams.schema.json
```

- New [agenticUserTemplates](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root?view=m365-app-1.30#agenticusertemplates) node to reference an [Agent 365 blueprint](https://learn.microsoft.com/en-us/microsoft-agent-365/developer/registration), enabling the instantiation of an AI agent with its own Microsoft Entra Agent ID within your organization.
- Added [supportsChannelFeatures](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root?view=m365-app-1.30#supportschannelfeatures) to opt in your app to [next level channel features, including shared and private channels](https://learn.microsoft.com/en-us/microsoftteams/platform/build-apps-for-shared-private-channels).
- Enhanced support for Excel custom functions, including [customFunctions.enum](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/enum?view=m365-app-1.30) to provide [autocomplete options for custom functions](https://learn.microsoft.com/en-us/office/dev/add-ins/excel/custom-functions-custom-enums) and additional [function properties](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-function?view=m365-app-1.30#properties) and datatypes from [CustomFunctionsRuntime 1.5](https://learn.microsoft.com/en-us/javascript/api/requirement-sets/excel/custom-functions-requirement-sets).
</details>

  


<details>
<summary>**Version 1.24**</summary>

### Version 1.24

October 2025

```http
https://developer.microsoft.com/json-schemas/teams/v1.24/MicrosoftTeams.schema.json
```

- Added [executeDataFunction](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-runtimes-actions-item?view=m365-app-1.30#type) action type to enable Copilot agents to invoke Office Add-ins functions and serve as [natural language interfaces to add-ins](https://learn.microsoft.com/en-us/office/dev/add-ins/design/agent-and-add-in-overview). The overall functionality of combining Copilot agents with Office Add-ins remains in preview.
- Introduced [windowsExtensions](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-alternate-versions-array-hide-windows-extensions?view=m365-app-1.30) mechanism to specify which COM- and VSTO-based add-ins should be disabled with the equivalent JavaScript add-in is installed. For more details, see [Option to disable the Windows-only add-in instead](https://learn.microsoft.com/en-us/office/dev/add-ins/develop/make-office-add-in-compatible-with-existing-com-add-in#option-to-disable-the-windows-only-add-in-instead-preview).
- Added [keyboardShortcuts](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-keyboard-shortcut?view=m365-app-1.30) to support [backwards compatibility of Office Add-ins with keyboard shortcuts](https://learn.microsoft.com/en-us/office/dev/add-ins/design/keyboard-shortcuts#support-backward-compatibility-for-add-ins-with-a-unified-manifest-in-appsource) and their localized strings \(if applicable\).
- Increased [bot commands](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-command-lists?view=m365-app-1.30#commands) limit from 10 to 12 to accommodate Microsoft Copilot Studio agents, which support up to 12 starter prompts.

  

</details>

  


<details>
<summary>**Version 1.23**</summary>

### Version 1.23

July 2025

```http
https://developer.microsoft.com/json-schemas/teams/v1.23/MicrosoftTeams.schema.json
```

- Updated `extensionRibbonsCustomTabGroupsItem` to include the [`overriddenByRibbonApi` property](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-custom-tab-groups-item?view=m365-app-1.30#overriddenByRibbonApi-property), which hides groups in apps that support custom contextual tabs via the `Office.ribbon.requestCreateControls` API. Removed redundant node `extensionCommonCustomControlMenu`.
- Added bot [`registrationInfo`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-registration-info?view=m365-app-1.30) field to accommodate system-generated metadata for agents built with Microsoft Copilot Studio and other tools.
- Improved description for [`spamReportingOptions`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-spam-pre-processing-dialog?view=m365-app-1.30#spamReportingOptions-property)

  

</details>

  


<details>
<summary>**Version 1.22**</summary>

### Version 1.22

May 2025

```http
https://developer.microsoft.com/json-schemas/teams/v1.22/MicrosoftTeams.schema.json
```

- Added [`activityIcons`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-activities-activity-icons?view=m365-app-1.30) and [`allowedIconIds`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-activities-activity-types?view=m365-app-1.30#allowedIconIds-property) properties to customize app icons in a user's activity feed. `activityIcons` defines the icon, while `allowedIconIds` specifies which icons appear for each activity type. For more information, see the [Teams activity feed](https://learn.microsoft.com/en-us/graph/teams-send-activityfeednotifications) and [custom icon guidelines](https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines#custom-activity-icons).
- Added the [`type property`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-spam-pre-processing-dialog-spam-reporting-options?view=m365-app-1.30#type-property) to the spam reporting preprocessing dialog to support either radio buttons or checkboxes for reporting options. For details, see [Configure the manifest](https://learn.microsoft.com/en-us/office/dev/add-ins/outlook/spam-reporting#configure-the-manifest).
- Added [`nestedAppAuthInfo`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-web-application-info?view=m365-app-1.30#nestedAppAuthInfo-property) property to enable prefetching of a nested app authentication token when a tab is loads. To details more, see [Nested app authentication](https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/authentication/nested-authentication).

  

</details>

  


<details>
<summary>**Version 1.21**</summary>

### Version 1.21

April 2025

```http
https://developer.microsoft.com/json-schemas/teams/v1.21/MicrosoftTeams.schema.json
```

- Developers can now specify a [32x32 color icon](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-icons?view=m365-app-1.30#color32x32) with a transparent background to ensure a consistent appearance when your app runs in Outlook and Microsoft 365. To learn more see,[Teams app package color icon](https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/build-and-test/apps-package#color-icon).
- Introduced new *copilot* value for [`bots.scopes`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots?view=m365-app-1.30#scopes) and [`defaultInstallScope`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root?view=m365-app-1.30#defaultinstallscope). To learn more, see [Build with Teams AI library](https://learn.microsoft.com/en-us/microsoftteams/platform/bots/how-to/teams-conversational-ai/how-conversation-ai-get-started).
- Added [`backgroundLoadConfiguration`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-background-load-configuration?view=m365-app-1.30) object to enable tab apps to [opt in to precaching](https://learn.microsoft.com/en-us/microsoftteams/platform/tabs/how-to/app-caching#enable-precaching-for-tab-app) for a faster initial load experience.

  

</details>

  


<details>
<summary>**Version 1.20**</summary>

### Version 1.20

March 2025

```http
https://developer.microsoft.com/json-schemas/teams/v1.20/MicrosoftTeams.schema.json
```

- Added [`elementRelationshipSet`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-element-relationship-set?view=m365-app-1.30) and [`requirementSet`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/element-requirement-set?view=m365-app-1.30) \(for `composeExtensions`, `bots`, and `staticTabs`\) objects so that apps can specify [runtime requirements in Microsoft 365 hosts](https://learn.microsoft.com/en-us/microsoftteams/platform/m365-apps/specify-runtime-requirements).
- Added [`intuneInfo`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-intune-info?view=m365-app-1.30) object for [Outlook Add-ins to attest to Intune Mobile App Management \(MAM\) support](https://learn.microsoft.com/en-us/javascript/api/outlook/office.mailbox) in order to signal compliance with organizational data protection policies.
- Added [`fixedControls`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-array-fixed-control-item?view=m365-app-1.30) object to build custom [spam-reporting handling with Outlook Add-ins](https://learn.microsoft.com/en-us/office/dev/add-ins/outlook/spam-reporting).

  

</details>

  


<details>
<summary>**Version 1.19**</summary>

### Version 1.19

September 2024

```http
https://developer.microsoft.com/json-schemas/teams/v1.19/MicrosoftTeams.schema.json
```

- Added [`copilotAgents`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-copilot-agents?view=m365-app-1.30) object for publishing [declarative agents for Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/overview-declarative-agent).
- Added [`defaultLanguageFile`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-localization-info?view=m365-app-1.30#defaultlanguagefile), a new required property for [Copilot agents that support multiple languages](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/localize-agents).

  

</details>

  


<details>
<summary>**Version 1.18** *Not available.*</summary>
</details>

  


<details>
<summary>**Version 1.17**</summary>

### Version 1.17

April 2024

```http
https://developer.microsoft.com/json-schemas/teams/v1.17/MicrosoftTeams.schema.json
```

- Added support for [mobile specific manifest elements for Outlook extensions](https://learn.microsoft.com/en-us/office/dev/add-ins/outlook/outlook-mobile-addins).
- Added `semanticDescription` field for Copilot for Microsoft 365. [Learn more](https://learn.microsoft.com/en-us/microsoftteams/platform/messaging-extensions/high-quality-message-extension?tabs=tasks#semantic-description).
- Added support for [creating message extensions](https://learn.microsoft.com/en-us/microsoftteams/platform/messaging-extensions/api-based-overview) from an existing API.
- Added apps to easily show as cards on [Viva Connections Dashboard](https://learn.microsoft.com/en-us/sharepoint/dev/spfx/viva/bot-powered/overview-bot-powered-aces).
- Added new [sample prompts](https://learn.microsoft.com/en-us/microsoftteams/platform/messaging-extensions/high-quality-message-extension?tabs=tasks#sample-prompts) to guide users who install or enable a plugin for the first time.
- Added [bot configurations](https://learn.microsoft.com/en-us/microsoftteams/platform/bots/how-to/bot-configuration-experience) changes.
- Deprecated `packageName` property.
- Deprecated `callingSidePanel` from manifest.

  

</details>

  


<details>
<summary>**Version 1.16**</summary>

### Version 1.16

February 2023

```http
https://developer.microsoft.com/json-schemas/teams/v1.16/MicrosoftTeams.schema.json
```

- Added `supportsAnonymousGuestUsers` in `meetingExtensionDefinition`.
- Added `team` and `groupChat` to the scope of staticTab.
- Added `privateChatTab`, `meetingChatTab`, `meetingDetailsTab`, `meetingSidePanel`, `meetingStage`, `teamLevelApp` to the context of staticTab.

  

</details>

  


<details>
<summary>**Version 1.15**</summary>

### Version 1.15

November 2022

```http
https://developer.microsoft.com/json-schemas/teams/v1.15/MicrosoftTeams.schema.json
```

- Added `supportsAnonymizedPayloads` feature. A Boolean that indicates whether the app's link message handler supports anonymous invoke flow.

  

</details>

  


<details>
<summary>**Version 1.14**</summary>

### Version 1.14

July 2022

```http
https://developer.microsoft.com/json-schemas/teams/v1.14/MicrosoftTeams.schema.json
```

- Added `supportedChannelTypes` feature. List of 'nonstandard' channel types that the app supports. Note: Channels of standard type are supported by default if the app supports team scope.
- Added `supportsStreaming`feature. A Boolean value indicating whether this app can stream the meeting's audio video content to a Real-Time Messaging Protocol \(RTMP\) endpoint.

  

</details>

  


<details>
<summary>**Version 1.13**</summary>

### Version 1.13

May 2022

```http
https://developer.microsoft.com/json-schemas/teams/v1.13/MicrosoftTeams.schema.json
```

With the release of version 1.13 of the App manifest, developers can build and update their app \(formerly Teams app\) to run in Microsoft 365 hosts such as Outlook, Teams, and Microsoft Teams App across web, desktop, and mobile. From this version release, it eases deployment workflow and provides a streamlined way to deliver cross-platform apps to an expanded user audience via a single codebase. For more details on host application feature support, visit [TeamsJS capability support across Microsoft 365](https://learn.microsoft.com/en-us/microsoftteams/platform/m365-apps/teamsjs-support-m365).

- This schema version supports extending Teams apps to other parts of the Microsoft 365 ecosystem. More info at [https://aka.ms/extendteamsapps](https://aka.ms/extendteamsapps).

  

</details>

## What's new in Version 1.19

September 2024

```http
https://developer.microsoft.com/json-schemas/teams/v1.19/MicrosoftTeams.schema.json
```

- Added [`copilotAgents`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-copilot-agents?view=m365-app-1.30) object for publishing [declarative agents for Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/overview-declarative-agent).
- Added [`defaultLanguageFile`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-localization-info?view=m365-app-1.30#defaultlanguagefile), a new required property for [Copilot agents that support multiple languages](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/localize-agents).

## All generally available versions

  


<details>
<summary>**Version 1.29**</summary>

### Version 1.29

June 2026

```http
https://developer.microsoft.com/json-schemas/teams/v1.29/MicrosoftTeams.schema.json
```

- Enabled [human to agent one-turn conversation](https://learn.microsoft.com/en-us/microsoftteams/platform/agents-in-teams/targeted-messages) and add a new property [triggers](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-compose-extensions-commands?view=m365-app-1.30#triggers).
- Added support for dynamic tool discovery that allows Microsoft 365 agents to fetch the MCP server's tool list at runtime by calling the server's `tools/list` method. To enable dynamic discovery, provide the `remoteServerURL` and omit the [`mcpToolDescription`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-connectors-tool-source-remote-mcp-server?view=m365-app-1.30) property.
- Added support for Azure Key Vault authentication using [`AzureKeyVault`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-connectors-tool-source-remote-mcp-server-authorization?view=m365-app-1.30) property that allows you to store and manage your MCP server credentials in your own [Azure Key Vault](https://learn.microsoft.com/en-us/microsoftteams/platform/m365-apps/agent-connectors#configure-authentication) instance. This gives you full control over secret lifecycle management, including rotation, access policies, and audit logging.
</details>

  


<details>
<summary>**Version 1.28**</summary>

### Version 1.28

May 2026

```http
https://developer.microsoft.com/json-schemas/teams/v1.28/MicrosoftTeams.schema.json
```

- Expanded the range of icons array for extension tab groups \([extensionRibbonsCustomTabGroupsItem](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-custom-tab-groups-item?view=m365-app-1.30) object\) to minItems = 3 \(from 1\) and maxItems = 8 \(from 3\).
- Enable Office Add-ins to show or hide ribbon buttons, controls, and groups in custom or contextual tabs across Word, Excel, and PowerPoint \(Win32, Mac, Web\) using the new property [visible](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-array-tabs-item?view=m365-app-1.30#visible) for dynamic UI and less clutter.
- The [`agentSkills`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-skills?view=m365-app-1.30#rootagentskills-object) property allows developers to package AI agent skills as elements.
</details>

  


<details>
<summary>**Version 1.27**</summary>

### Version 1.27

May 2026

```http
https://developer.microsoft.com/json-schemas/teams/v1.27/MicrosoftTeams.schema.json
```

- Added [agent connectors](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-connectors) node to enable [configuration of connections](https://learn.microsoft.com/en-us/microsoftteams/platform/m365-apps/agent-connectors) between Microsoft 365 agents and external data sources through MCP servers.
- Added a new command [type](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-command-lists-commands) and a new property [prompt](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-command-lists-commands) under bots commands.
</details>

  


<details>
<summary>**Version 1.26**</summary>

### Version 1.26

April 2026

```http
https://developer.microsoft.com/json-schemas/teams/v1.26/MicrosoftTeams.schema.json
```

- Added optional [composeExtensions.authorization.oAuthConfiguration](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-compose-extensions-authorization-o-auth-configuration) object to implement [Open Authorization \(OAuth\) 2.0 support for API-based message extensions](https://learn.microsoft.com/en-us/microsoftteams/platform/messaging-extensions/api-based-oauth).
- Added [features](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-description) descriptions list to [showcase agent and app features to a profile card](https://learn.microsoft.com/en-us/microsoftteams/platform/bots/how-to/teams-conversational-ai/ai-ux) that appears when the user hovers over the app icon.
- [KeyTips](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-custom-control-menu-item) let developers set custom shortcut keys in Office, giving users more efficient ways to work in Word, Excel, and PowerPoint.
</details>

  


<details>
<summary>**Version 1.25**</summary>

### Version 1.25

January 2026

```http
https://developer.microsoft.com/json-schemas/teams/v1.25/MicrosoftTeams.schema.json
```

- New [agenticUserTemplates](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root?view=m365-app-1.30#agenticusertemplates) node to reference an [Agent 365 blueprint](https://learn.microsoft.com/en-us/microsoft-agent-365/developer/registration), enabling the instantiation of an AI agent with its own Microsoft Entra Agent ID within your organization.
- Added [supportsChannelFeatures](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root?view=m365-app-1.30#supportschannelfeatures) to opt in your app to [next level channel features, including shared and private channels](https://learn.microsoft.com/en-us/microsoftteams/platform/build-apps-for-shared-private-channels).
- Enhanced support for Excel custom functions, including [customFunctions.enum](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/enum?view=m365-app-1.30) to provide [autocomplete options for custom functions](https://learn.microsoft.com/en-us/office/dev/add-ins/excel/custom-functions-custom-enums) and additional [function properties](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-function?view=m365-app-1.30#properties) and datatypes from [CustomFunctionsRuntime 1.5](https://learn.microsoft.com/en-us/javascript/api/requirement-sets/excel/custom-functions-requirement-sets).
</details>

  


<details>
<summary>**Version 1.24**</summary>

### Version 1.24

October 2025

```http
https://developer.microsoft.com/json-schemas/teams/v1.24/MicrosoftTeams.schema.json
```

- Added [executeDataFunction](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-runtimes-actions-item?view=m365-app-1.30#type) action type to enable Copilot agents to invoke Office Add-ins functions and serve as [natural language interfaces to add-ins](https://learn.microsoft.com/en-us/office/dev/add-ins/design/agent-and-add-in-overview). The overall functionality of combining Copilot agents with Office Add-ins remains in preview.
- Introduced [windowsExtensions](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-alternate-versions-array-hide-windows-extensions?view=m365-app-1.30) mechanism to specify which COM- and VSTO-based add-ins should be disabled with the equivalent JavaScript add-in is installed. For more details, see [Option to disable the Windows-only add-in instead](https://learn.microsoft.com/en-us/office/dev/add-ins/develop/make-office-add-in-compatible-with-existing-com-add-in#option-to-disable-the-windows-only-add-in-instead-preview).
- Added [keyboardShortcuts](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-keyboard-shortcut?view=m365-app-1.30) to support [backwards compatibility of Office Add-ins with keyboard shortcuts](https://learn.microsoft.com/en-us/office/dev/add-ins/design/keyboard-shortcuts#support-backward-compatibility-for-add-ins-with-a-unified-manifest-in-appsource) and their localized strings \(if applicable\).
- Increased [bot commands](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-command-lists?view=m365-app-1.30#commands) limit from 10 to 12 to accommodate Microsoft Copilot Studio agents, which support up to 12 starter prompts.

  

</details>

  


<details>
<summary>**Version 1.23**</summary>

### Version 1.23

July 2025

```http
https://developer.microsoft.com/json-schemas/teams/v1.23/MicrosoftTeams.schema.json
```

- Updated `extensionRibbonsCustomTabGroupsItem` to include the [`overriddenByRibbonApi` property](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-custom-tab-groups-item?view=m365-app-1.30#overriddenByRibbonApi-property), which hides groups in apps that support custom contextual tabs via the `Office.ribbon.requestCreateControls` API. Removed redundant node `extensionCommonCustomControlMenu`.
- Added bot [`registrationInfo`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-registration-info?view=m365-app-1.30) field to accommodate system-generated metadata for agents built with Microsoft Copilot Studio and other tools.
- Improved description for [`spamReportingOptions`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-spam-pre-processing-dialog?view=m365-app-1.30#spamReportingOptions-property)

  

</details>

  


<details>
<summary>**Version 1.22**</summary>

### Version 1.22

May 2025

```http
https://developer.microsoft.com/json-schemas/teams/v1.22/MicrosoftTeams.schema.json
```

- Added [`activityIcons`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-activities-activity-icons?view=m365-app-1.30) and [`allowedIconIds`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-activities-activity-types?view=m365-app-1.30#allowedIconIds-property) properties to customize app icons in a user's activity feed. `activityIcons` defines the icon, while `allowedIconIds` specifies which icons appear for each activity type. For more information, see the [Teams activity feed](https://learn.microsoft.com/en-us/graph/teams-send-activityfeednotifications) and [custom icon guidelines](https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines#custom-activity-icons).
- Added the [`type property`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-spam-pre-processing-dialog-spam-reporting-options?view=m365-app-1.30#type-property) to the spam reporting preprocessing dialog to support either radio buttons or checkboxes for reporting options. For details, see [Configure the manifest](https://learn.microsoft.com/en-us/office/dev/add-ins/outlook/spam-reporting#configure-the-manifest).
- Added [`nestedAppAuthInfo`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-web-application-info?view=m365-app-1.30#nestedAppAuthInfo-property) property to enable prefetching of a nested app authentication token when a tab is loads. To details more, see [Nested app authentication](https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/authentication/nested-authentication).

  

</details>

  


<details>
<summary>**Version 1.21**</summary>

### Version 1.21

April 2025

```http
https://developer.microsoft.com/json-schemas/teams/v1.21/MicrosoftTeams.schema.json
```

- Developers can now specify a [32x32 color icon](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-icons?view=m365-app-1.30#color32x32) with a transparent background to ensure a consistent appearance when your app runs in Outlook and Microsoft 365. To learn more see,[Teams app package color icon](https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/build-and-test/apps-package#color-icon).
- Introduced new *copilot* value for [`bots.scopes`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots?view=m365-app-1.30#scopes) and [`defaultInstallScope`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root?view=m365-app-1.30#defaultinstallscope). To learn more, see [Build with Teams AI library](https://learn.microsoft.com/en-us/microsoftteams/platform/bots/how-to/teams-conversational-ai/how-conversation-ai-get-started).
- Added [`backgroundLoadConfiguration`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-background-load-configuration?view=m365-app-1.30) object to enable tab apps to [opt in to precaching](https://learn.microsoft.com/en-us/microsoftteams/platform/tabs/how-to/app-caching#enable-precaching-for-tab-app) for a faster initial load experience.

  

</details>

  


<details>
<summary>**Version 1.20**</summary>

### Version 1.20

March 2025

```http
https://developer.microsoft.com/json-schemas/teams/v1.20/MicrosoftTeams.schema.json
```

- Added [`elementRelationshipSet`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-element-relationship-set?view=m365-app-1.30) and [`requirementSet`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/element-requirement-set?view=m365-app-1.30) \(for `composeExtensions`, `bots`, and `staticTabs`\) objects so that apps can specify [runtime requirements in Microsoft 365 hosts](https://learn.microsoft.com/en-us/microsoftteams/platform/m365-apps/specify-runtime-requirements).
- Added [`intuneInfo`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-intune-info?view=m365-app-1.30) object for [Outlook Add-ins to attest to Intune Mobile App Management \(MAM\) support](https://learn.microsoft.com/en-us/javascript/api/outlook/office.mailbox) in order to signal compliance with organizational data protection policies.
- Added [`fixedControls`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-array-fixed-control-item?view=m365-app-1.30) object to build custom [spam-reporting handling with Outlook Add-ins](https://learn.microsoft.com/en-us/office/dev/add-ins/outlook/spam-reporting).

  

</details>

  


<details>
<summary>**Version 1.19**</summary>

### Version 1.19

September 2024

```http
https://developer.microsoft.com/json-schemas/teams/v1.19/MicrosoftTeams.schema.json
```

- Added [`copilotAgents`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-copilot-agents?view=m365-app-1.30) object for publishing [declarative agents for Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/overview-declarative-agent).
- Added [`defaultLanguageFile`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-localization-info?view=m365-app-1.30#defaultlanguagefile), a new required property for [Copilot agents that support multiple languages](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/localize-agents).

  

</details>

  


<details>
<summary>**Version 1.18** *Not available.*</summary>
</details>

  


<details>
<summary>**Version 1.17**</summary>

### Version 1.17

April 2024

```http
https://developer.microsoft.com/json-schemas/teams/v1.17/MicrosoftTeams.schema.json
```

- Added support for [mobile specific manifest elements for Outlook extensions](https://learn.microsoft.com/en-us/office/dev/add-ins/outlook/outlook-mobile-addins).
- Added `semanticDescription` field for Copilot for Microsoft 365. [Learn more](https://learn.microsoft.com/en-us/microsoftteams/platform/messaging-extensions/high-quality-message-extension?tabs=tasks#semantic-description).
- Added support for [creating message extensions](https://learn.microsoft.com/en-us/microsoftteams/platform/messaging-extensions/api-based-overview) from an existing API.
- Added apps to easily show as cards on [Viva Connections Dashboard](https://learn.microsoft.com/en-us/sharepoint/dev/spfx/viva/bot-powered/overview-bot-powered-aces).
- Added new [sample prompts](https://learn.microsoft.com/en-us/microsoftteams/platform/messaging-extensions/high-quality-message-extension?tabs=tasks#sample-prompts) to guide users who install or enable a plugin for the first time.
- Added [bot configurations](https://learn.microsoft.com/en-us/microsoftteams/platform/bots/how-to/bot-configuration-experience) changes.
- Deprecated `packageName` property.
- Deprecated `callingSidePanel` from manifest.

  

</details>

  


<details>
<summary>**Version 1.16**</summary>

### Version 1.16

February 2023

```http
https://developer.microsoft.com/json-schemas/teams/v1.16/MicrosoftTeams.schema.json
```

- Added `supportsAnonymousGuestUsers` in `meetingExtensionDefinition`.
- Added `team` and `groupChat` to the scope of staticTab.
- Added `privateChatTab`, `meetingChatTab`, `meetingDetailsTab`, `meetingSidePanel`, `meetingStage`, `teamLevelApp` to the context of staticTab.

  

</details>

  


<details>
<summary>**Version 1.15**</summary>

### Version 1.15

November 2022

```http
https://developer.microsoft.com/json-schemas/teams/v1.15/MicrosoftTeams.schema.json
```

- Added `supportsAnonymizedPayloads` feature. A Boolean that indicates whether the app's link message handler supports anonymous invoke flow.

  

</details>

  


<details>
<summary>**Version 1.14**</summary>

### Version 1.14

July 2022

```http
https://developer.microsoft.com/json-schemas/teams/v1.14/MicrosoftTeams.schema.json
```

- Added `supportedChannelTypes` feature. List of 'nonstandard' channel types that the app supports. Note: Channels of standard type are supported by default if the app supports team scope.
- Added `supportsStreaming`feature. A Boolean value indicating whether this app can stream the meeting's audio video content to a Real-Time Messaging Protocol \(RTMP\) endpoint.

  

</details>

  


<details>
<summary>**Version 1.13**</summary>

### Version 1.13

May 2022

```http
https://developer.microsoft.com/json-schemas/teams/v1.13/MicrosoftTeams.schema.json
```

With the release of version 1.13 of the App manifest, developers can build and update their app \(formerly Teams app\) to run in Microsoft 365 hosts such as Outlook, Teams, and Microsoft Teams App across web, desktop, and mobile. From this version release, it eases deployment workflow and provides a streamlined way to deliver cross-platform apps to an expanded user audience via a single codebase. For more details on host application feature support, visit [TeamsJS capability support across Microsoft 365](https://learn.microsoft.com/en-us/microsoftteams/platform/m365-apps/teamsjs-support-m365).

- This schema version supports extending Teams apps to other parts of the Microsoft 365 ecosystem. More info at [https://aka.ms/extendteamsapps](https://aka.ms/extendteamsapps).

  

</details>

## What's new in developer preview

Commit history: [https://github.com/microsoft/json-schemas/commits/live/teams/vDevPreview](https://github.com/microsoft/json-schemas/commits/live/teams/vDevPreview)

```http
https://developer.microsoft.com/json-schemas/teams/vDevPreview/MicrosoftTeams.schema.json
```

### June 2026

- Added support for Encryption-Decryption feature for Outlook Add-ins using the new [`headerName`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-auto-run-events-array-events-options?view=m365-app-1.30#headername) property.
- Added the new [`supportsSessions`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots?view=m365-app-1.30#supportssessions) property to enable bots in Teams to have topic-based conversations with users.
- Added support for abbreviated application name in app bar using the new [`abbreviated`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-name?view=m365-app-1.30#abbreviated) property.
- Increased `maxLength` in [`validDomains`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root?view=m365-app-1.30#validdomains) array from 16 to 100 to enable legacy Office Add-in migration to new unified manifest.

## Previous preview releases

  


<details>
<summary>**2026**</summary>

### May 2026

- Allow ISVs to submit MCP Servers directly for certification, simplifying the onboarding path using [`AzureKeyVault`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-connectors-tool-source-local-mcp-server-authorization?view=m365-app-1.30#type) property.
- The [`agentSkills`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-skills?view=m365-app-1.30#rootagentskills-object) property allows developers to package AI agent skills as elements.

### April 2026

- Enable Office Add-ins to show or hide ribbon buttons, controls, and groups in custom or contextual tabs across Word, Excel, and PowerPoint \(Win32, Mac, Web\) using the new property [visible](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-array-tabs-item?view=m365-app-1.30#visible) for dynamic UI and less clutter.
- Increase `maxLength` in [validDomains](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root?view=m365-app-1.30#validdomains) array from 16 to 100 to enable legacy Office Add-in migration to new unified manifest.
- Enable human to agent one-turn conversation and add a new property [triggers](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-compose-extensions-commands?view=m365-app-1.30#triggers) to enable slash commands.
- Added a new command [type](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-command-lists-commands?view=m365-app-1.30#type) and a new property [prompt](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-command-lists-commands?view=m365-app-1.30#prompt) under bots commands.

  


### February 2026

- Extended the description length for Excel custom functions [`customFunctions`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-custom-functions?view=m365-app-1.30) from 128 to 1024 characters.
- Extended the description length for custom function [parameters](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-function-parameter?view=m365-app-1.30) from 128 to 512 characters.
- Expanded the range of icons array for extension tab groups \([extensionRibbonsCustomTabGroupsItem](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-custom-tab-groups-item?view=m365-app-1.30) object\) to minItems = 3 \(from 1\) and maxItems = 8 \(from 3\).
</details>

  


<details>
<summary>**2025**</summary>

### November 2025

- New [agenticUserTemplates](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root?view=m365-app-1.30#agenticusertemplates) node to reference an [Agent 365 blueprint](https://learn.microsoft.com/en-us/microsoft-agent-365/developer/registration), enabling the instantiation of an AI agent with its own Microsoft Entra Agent ID within your organization.
- Added [agent connectors](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-connectors?view=m365-app-1.30) for [configuring agent connections](https://learn.microsoft.com/en-us/microsoftteams/platform/m365-apps/agent-connectors) from Microsoft 365 to external data sources, including MCP servers and OpenAPI-based systems.
- Enhanced support for Excel custom functions, including [customFunctions.enum](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/enum?view=m365-app-1.30) to provide [autocomplete options for custom functions](https://learn.microsoft.com/en-us/office/dev/add-ins/excel/custom-functions-custom-enums) and additional [function properties](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-function?view=m365-app-1.30#properties) and datatypes from [CustomFunctionsRuntime 1.5](https://learn.microsoft.com/en-us/javascript/api/requirement-sets/excel/custom-functions-requirement-sets).

### October 2025

- Added [supportsChannelFeatures](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root?view=m365-app-1.30#supportschannelfeatures) to opt in your app to [next level channel features, including shared and private channels](https://learn.microsoft.com/en-us/microsoftteams/platform/build-apps-for-shared-private-channels).

### September 2025

- Added [keyboardShortcuts](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-keyboard-shortcut?view=m365-app-1.30) to support [backwards compatibility of Office Add-ins with keyboard shortcuts](https://learn.microsoft.com/en-us/office/dev/add-ins/design/keyboard-shortcuts#support-backward-compatibility-for-add-ins-with-a-unified-manifest-in-appsource) and their localized strings \(if applicable\).

### August 2025

- Increased [bot commands](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-command-lists?view=m365-app-1.30#commands) limit from 10 to 12 to accomodate Microsoft Copilot Studio agents, which support up to 12 starter prompts.
- Introduced [windowsExtensions](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-alternate-versions-array-hide-windows-extensions?view=m365-app-1.30) mechanism to specify which COM- and VSTO-based add-ins should be disabled with the equivalent JavaScript add-in is installed. For more details, see [Option to disable the Windows-only add-in instead](https://learn.microsoft.com/en-us/office/dev/add-ins/develop/make-office-add-in-compatible-with-existing-com-add-in#option-to-disable-the-windows-only-add-in-instead-preview).

### July 2025

- Added bot [`registrationInfo`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-registration-info?view=m365-app-1.30) field to accommodate system-generated metadata for agents built with Microsoft Copilot Studio and other tools.
- Improved description for [`spamReportingOptions`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-spam-pre-processing-dialog?view=m365-app-1.30#spamReportingOptions-property)

### May 2025

- Added new [`type`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-spam-pre-processing-dialog-spam-reporting-options?view=m365-app-1.30#type-property) property to customize the spam reporting preprocessing dialog with either radio buttons or checkboxes, giving users clear options when reporting messages. To learn more, see [Configure the manifest](https://learn.microsoft.com/en-us/office/dev/add-ins/outlook/spam-reporting#configure-the-manifest).
- Added [`spamNeverShowAgainOption`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-spam-pre-processing-dialog?view=m365-app-1.30#spamNeverShowAgainOption-property) property that allows users to opt out of seeing preprocessing dialogs in future spam reports. For details, see [Suppress the preprocessing dialog](https://learn.microsoft.com/en-us/office/dev/add-ins/outlook/spam-reporting#suppress-the-preprocessing-dialog).

### April 2025

- Added [`customEngineAgents`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-copilot-agents-custom-engine-agents?view=m365-app-1.30) object to enable [custom engine agents to surface in Microsoft 365 Copilot Chat](https://learn.microsoft.com/en-us/microsoftteams/platform/bots/how-to/teams-conversational-ai/how-conversation-ai-get-started#add-support-for-microsoft-365-copilot-chat). Additionally, introduced new *copilot* value for [`bots.scopes`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots?view=m365-app-1.30#scopes) and [`defaultInstallScope`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root?view=m365-app-1.30#defaultinstallscope).
- Added the [`activityIcons`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-activities-activity-icons?view=m365-app-1.30) property, which allows developers to specify the icon of their app that appears in a user’s activity feed. The [`allowedIconIds`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-activities-activity-types?view=m365-app-1.30#allowediconids) property enables further customization of which icon appears for each activity type. For more info, see [Send activity feed notifications to users in Microsoft Teams](https://learn.microsoft.com/en-us/graph/teams-send-activityfeednotifications) and [Custom activity icons](https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines#custom-activity-icons) Teams store validation guidelines.
- Added the [`nestedAppAuthInfo`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-web-application-info?view=m365-app-1.30#nestedAppAuthInfo-property) property which enables the prefetching of an nested app authentication token based on its contents when the tab is loaded. To learn more, see [Nested app authentication](https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/authentication/nested-authentication).

### March 2025

- Added [`customFunctions`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-custom-functions?view=m365-app-1.30) object to support implementing [new functions to Excel](https://learn.microsoft.com/en-us/office/dev/add-ins/excel/custom-functions-overview) by defining those functions in JavaScript as part of an add-in.
- Added [`keyboardShortcuts`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-keyboard-shortcut?view=m365-app-1.30) object to support implementing [custom keyboard shortcuts to your Office add-in](https://learn.microsoft.com/en-us/office/dev/add-ins/design/keyboard-shortcuts).
- Added [`backgroundLoadConfiguration`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-background-load-configuration?view=m365-app-1.30) object to enable tab apps to [opt in to precaching](https://learn.microsoft.com/en-us/microsoftteams/platform/tabs/how-to/app-caching#enable-precaching-for-tab-app) for a faster initial load experience.
</details>

  


<details>
<summary>**2024**</summary>

### November 2024

- Introduced optional `abbreviated` property for [app display name](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-name) to display abbreviated name on the app bar.
- [Stream bot messages](https://learn.microsoft.com/en-us/microsoftteams/platform/bots/streaming-ux) to deliver the bot's response to users in real-time.

### October 2024

- Introduced [runtime requirements](https://learn.microsoft.com/en-us/microsoftteams/platform/m365-apps/specify-runtime-requirements) in app manifest to tailor your app's behavior in Microsoft 365 hosts.
- copilotExtensions renamed to [copilotAgents](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-copilot-agents?view=m365-app-prev&preserve-view=true) in developer preview app manifest.

### September 2024

- Added support for [nested app authentication](https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/authentication/nested-authentication) for single-page applications embedded within the host environment.

### June 2024

- Introduced [preapproval of RSC permissions](https://learn.microsoft.com/en-us/microsoftteams/platform/graph-api/rsc/preapproval-instruction-docs), allowing admins to manage RSC permissions for app installation.

### May 2024

- Enhance your Copilot message extension plugin with [Copilot to hand off a conversation](https://learn.microsoft.com/en-us/microsoftteams/platform/bots/how-to/conversations/bot-copilot-handoff) to your custom engine copilot.
- With `developer.contactInfo`, app developers can provide customer support, updates to the apps, security and compliance information, and bug fixes to their users. [Learn more](https://learn.microsoft.com/en-us/MicrosoftTeams/manage-apps#developer-provided-app-information-support-and-documentation).
- You can specify a [32x32 color icon](https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/build-and-test/apps-package#color-icon) with a transparent background to ensure a consistent appearance when your app runs in Outlook and Microsoft 365. To learn more see,[Teams app package color icon](https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/build-and-test/apps-package#color-icon).

### March 2024

- Learn to [extend static tabs](https://learn.microsoft.com/en-us/microsoftteams/platform/tabs/what-are-tabs) to channels with a customizable experience.

### February 2024

- Introduced `systemDefault` reserved activity type for [send activity feed notifications](https://learn.microsoft.com/en-us/microsoftteams/platform/tabs/send-activity-feed-notification?tabs=desktop#requirements-to-use-the-activity-feed-notification-apis).

### January 2024

- [Actions](https://learn.microsoft.com/en-us/microsoftteams/platform/m365-apps/actions-in-m365) help to integrate your app into your user's workflow by enabling easy discoverability and seamless interaction with the content. Extend your app across Microsoft 365 > Actions in Microsoft 365.

  

</details>

  


<details>
<summary>**2023**</summary>

### November 2023

- Extend an [action-based Teams message extension](https://learn.microsoft.com/en-us/microsoftteams/platform/m365-apps/extend-m365-teams-message-extension) across Microsoft 365.
- [Build a bot-based message extension](https://learn.microsoft.com/en-us/microsoftteams/platform/messaging-extensions/build-bot-based-message-extension) and [extend the message extension as plugin for Microsoft Copilot](https://learn.microsoft.com/en-us/microsoftteams/platform/messaging-extensions/high-quality-message-extension) for Microsoft 365. Included in the guidelines are instructions how to create or upgrade a message extension plugin for Microsoft Copilot for Microsoft 365.
- [Microsoft Adaptive Card Previewer](https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/build-and-test/adaptive-card-previewer) enables you to preview Adaptive Cards created for Teams bot and message extension when you refine the designs.

### October 2023

- Introduced the `extensions` property in public developer preview app manifest schema.
- [Build message extensions using API](https://learn.microsoft.com/en-us/microsoftteams/platform/messaging-extensions/api-based-overview) \(API-based\) to interact directly with third-party data, apps, and services.

### August 2023

- Use [Adaptive Card-based Loop components](https://learn.microsoft.com/en-us/microsoftteams/platform/m365-apps/design-loop-components) to build collaborative experiences within Teams message extensions that work across Microsoft 365.
- Use `callRecording` API to [fetch meeting recording from all meetings](https://learn.microsoft.com/en-us/microsoftteams/platform/graph-api/meeting-transcripts/overview-transcripts).

### July 2023

- Your [bot can mention tags in text messages and Adaptive Cards posted in channels](https://learn.microsoft.com/en-us/microsoftteams/platform/bots/how-to/conversations/channel-and-group-conversations#tag-mention).

### May 2023

- Use a [deep link to open a tab app in meeting side panel](https://learn.microsoft.com/en-us/microsoftteams/platform/apps-in-teams-meetings/build-tabs-for-meeting#deep-link-to-meeting-side-panel) in Teams mobile client.
- [Assistants API](https://learn.microsoft.com/en-us/microsoftteams/platform/bots/how-to/teams%20conversational%20ai/teams-conversation-ai-overview#assistants-api) allows you to create powerful AI assistants capable of performing various of tasks that are difficult to code using traditional methods.
- [Extend Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoftteams/platform/messaging-extensions/how-to-extend-copilot) to integrate with Microsoft Teams apps to turn your app into the most powerful productivity tool.

### January 2023

- Send notifications to specific participants on a meeting stage with [targeted in-meeting notification](https://learn.microsoft.com/en-us/microsoftteams/platform/apps-in-teams-meetings/in-meeting-notification-for-meeting#targeted-in-meeting-notification).

  

</details>

  


<details>
<summary>**2022**</summary>

### December 2022

- [Use share in meeting](https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/build-and-test/share-in-meeting) to share any document or third-party app to the meeting stage.

### November 2022

- Enable bots to [receive all conversation messages without being @mentioned](https://learn.microsoft.com/en-us/microsoftteams/platform/bots/how-to/conversations/channel-messages-with-rsc) in relevant contexts.

### September 2022

- Use apps in Teams meetings [scheduled through public channels](https://learn.microsoft.com/en-us/microsoftteams/platform/apps-in-teams-meetings/teams-apps-in-meetings).

### August 2022

- Share [apps to the Teams meeting stage in mobile](https://learn.microsoft.com/en-us/microsoftteams/platform/apps-in-teams-meetings/teams-apps-in-meetings).
- Use [toggle incoming audio API](https://learn.microsoft.com/en-us/microsoftteams/platform/apps-in-teams-meetings/api-references?tabs=dotnet) to toggle the incoming audio state setting for the user in Teams meeting stage from mute to unmute or vice-versa.
- Use [Collaboration controls](https://learn.microsoft.com/en-us/microsoftteams/platform/samples/collaboration-control) to build custom collaborative experiences and integrate with Microsoft 365 services

### May 2022

- Use [Live Share](https://learn.microsoft.com/en-us/microsoftteams/platform/apps-in-teams-meetings/teams-live-share-overview) to transform Teams apps into collaborative multi-user experiences without writing any dedicated back-end code.

  

</details>

  


<details>
<summary>**2021**</summary>

### October 2021

- [Enable bots](https://learn.microsoft.com/en-us/microsoftteams/platform/bots/how-to/conversations/conversation-basics) to receive all channel messages using resource-specific consent \(RSC\).

### June 2021

- Use [resource-specific consent permissions](https://learn.microsoft.com/en-us/microsoftteams/platform/graph-api/rsc/resource-specific-consent) to allow the app to access the data of a specific instance of a resource type.

  

</details>

## See also

- [Agents are apps for Microsoft 365 \(Microsoft 365 Copilot\)](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/agents-are-apps)
- [Localize your agent \(Microsoft 365 Copilot\)](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/localize-agents)
- [Specify Microsoft 365 host runtime requirements in app manifest \(Microsoft Teams\)](https://learn.microsoft.com/en-us/microsoftteams/platform/m365-apps/specify-runtime-requirements)
- [Localize your app \(Microsoft Teams\)](https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/build-and-test/apps-localization)
