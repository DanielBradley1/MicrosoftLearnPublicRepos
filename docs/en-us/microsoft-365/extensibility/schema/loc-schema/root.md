<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/loc-schema/root?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# Localization schema root object

Configure your app to support multiple languages and regions, ensuring accessibility and usability across various locales.

[The localization JSON schema](#syntax) defines how to add support of a client language settings in the App manifest. For detailed instructions on how to enable localization for your app, refer to the [**App localization guidance**](https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/build-and-test/apps-localization). For instructions on how to localize an agent, see [Localize agents for Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/localize-agents).

In the manifest schema, the [`localizationInfo`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-localization-info?view=m365-app-1.30) property lets developers support multiple languages for their apps using [`additionalLanguages`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-localization-info-additional-languages?view=m365-app-1.30). The [`file`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-localization-info-additional-languages?view=m365-app-1.30#file) sub-property indicates the relative path to the JSON file that defines the app's supported languages.

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "$schema": "{string}",
  "name.short": "{string}",
  "name.full": "{string}",
  "description.short": "{string}",
  "description.full": "{string}",
  "localizationKeys": {
    "^\[\[[a-zA-Z_][a-zA-Z0-9_]*\]\]$": "{string}"
  },
  "staticTabs.name": "{string}",
  "bots.commandLists.commands.title": "{string}",
  "bots.commandLists.commands.description": "{string}",
  "composeExtensions.commands.title": "{string}",
  "composeExtensions.commands.description": "{string}",
  "composeExtensions.commands.parameters.title": "{string}",
  "composeExtensions.commands.parameters.description": "{string}",
  "composeExtensions.commands.parameters.value": "{string}",
  "composeExtensions.commands.parameters.choices.title": "{string}",
  "composeExtensions.commands.taskInfo.title": "{string}",
  "activities.activityTypes.description": "{string}",
  "activities.activityTypes.templateText": "{string}",
  "meetingExtensionDefinition.scenes.name": "{string}",
  "meetingExtensionDefinition.videoFilters.name": "{string}",
  "extensions.audienceClaimUrl": "{string}",
  "extensions.ribbons.tabs.label": "{string}",
  "extensions.ribbons.tabs.customMobileRibbonGroups.label": "{string}",
  "extensions.ribbons.tabs.customMobileRibbonGroups.controls.icons.url": "{string}",
  "extensions.ribbons.tabs.groups.icons.url": "{string}",
  "extensions.ribbons.tabs.groups.label": "{string}",
  "extensions.ribbons.tabs.groups.controls.icons.url": "{string}",
  "extensions.ribbons.tabs.groups.controls.label": "{string}",
  "extensions.ribbons.tabs.groups.controls.supertip.title": "{string}",
  "extensions.ribbons.tabs.groups.controls.supertip.description": "{string}",
  "extensions.ribbons.tabs.groups.controls.items.icons.url": "{string}",
  "extensions.ribbons.tabs.groups.controls.items.label": "{string}",
  "extensions.ribbons.tabs.groups.controls.items.supertip.title": "{string}",
  "extensions.ribbons.tabs.groups.controls.items.supertip.description": "{string}",
  "extensions.runtimes.code.page": "{string}",
  "extensions.runtimes.code.script": "{string}",
  "extensions.runtimes.actions.displayName": "{string}",
  "extensions.alternates.alternateIcons.icon.url": "{string}",
  "extensions.alternates.alternateIcons.highResolutionIcon.url": "{string}",
  "extensions.getStartedMessages.title": "{string}",
  "extensions.getStartedMessages.description": "{string}",
  "extensions.getStartedMessages.learnMoreUrl": "{string}",
  "extensions.contentRuntimes.code.page": "{string}",
  "extensions.runtimes.customFunctions.functions.name": "{string}",
  "extensions.runtimes.customFunctions.functions.description": "{string}",
  "extensions.runtimes.customFunctions.functions.parameters.name": "{string}",
  "extensions.runtimes.customFunctions.functions.parameters.description": "{string}",
  "extensions.runtimes.customFunctions.namespace.name": "{string}",
  "extensions.runtimes.customFunctions.enums.values.name": "{string}",
  "extensions.runtimes.customFunctions.enums.values.tooltip": "{string}",
  "extensions.keyboardShortcuts.shortcuts.key.default": "{string}",
  "extensions.keyboardShortcuts.shortcuts.key.mac": "{string}",
  "extensions.keyboardShortcuts.shortcuts.key.web": "{string}",
  "extensions.keyboardShortcuts.shortcuts.key.windows": "{string}",
  "extensions.contextMenus.menus.controls.icons.url": "{string}",
  "extensions.contextMenus.menus.controls.label": "{string}",
  "extensions.contextMenus.menus.controls.supertip.title": "{string}",
  "extensions.contextMenus.menus.controls.supertip.description": "{string}",
  "extensions.contextMenus.menus.controls.items.icons.url": "{string}",
  "extensions.contextMenus.menus.controls.items.label": "{string}",
  "extensions.contextMenus.menus.controls.items.supertip.title": "{string}",
  "extensions.contextMenus.menus.controls.items.supertip.description": "{string}",
  "copilotAgents.customEngineAgents.disclaimer.text": "{string}",
  "description.features.title": "{string}",
  "description.features.description": "{string}"
}
```

```json
{
  "$schema": "http://json-schema.org/draft-04/schema#",
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "$schema": {
      "type": "string",
      "format": "uri"
    },
    "name.short": {
      "type": "string",
      "maxLength": 30,
      "$ref": "#/definitions/nonEmptyString"
    },
    "name.full": {
      "type": "string",
      "maxLength": 100,
      "$ref": "#/definitions/nonEmptyString"
    },
    "description.short": {
      "type": "string",
      "maxLength": 80,
      "$ref": "#/definitions/nonEmptyString"
    },
    "description.full": {
      "type": "string",
      "maxLength": 4000,
      "$ref": "#/definitions/nonEmptyString"
    },
    "localizationKeys": {
      "type": "object",
      "patternProperties": {
        "^\\[\\[[a-zA-Z_][a-zA-Z0-9_]*\\]\\]$": {
          "type": "string"
        }
      }
    }
  },
  "patternProperties": {
    "^staticTabs\\[([0-9]|1[0-5])\\]\\.name$": {
      "type": "string",
      "maxLength": 128
    },
    "^bots\\[0\\]\\.commandLists\\[[0-2]\\]\\.commands\\[([0-9]|1[0-1])\\]\\.title$": {
      "type": "string",
      "maxLength": 128
    },
    "^bots\\[0\\]\\.commandLists\\[[0-2]\\]\\.commands\\[([0-9]|1[0-1])\\]\\.description$": {
      "type": "string",
      "maxLength": 4000
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.title$": {
      "type": "string",
      "maxLength": 32
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.description$": {
      "type": "string",
      "maxLength": 128
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.title$": {
      "type": "string",
      "maxLength": 32
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.description$": {
      "type": "string",
      "maxLength": 128
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.value$": {
      "type": "string",
      "maxLength": 512
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.choices\\[[0-9]\\]\\.title$": {
      "type": "string",
      "maxLength": 128
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.taskInfo\\.title$": {
      "type": "string",
      "maxLength": 64
    },
    "^activities.activityTypes\\[\\b([0-9]|[1-8][0-9]|9[0-9]|1[01][0-9]|12[0-7])\\b]\\.description$": {
      "type": "string",
      "maxLength": 128
    },
    "^activities.activityTypes\\[\\b([0-9]|[1-8][0-9]|9[0-9]|1[01][0-9]|12[0-7])\\b]\\.templateText$": {
      "type": "string",
      "maxLength": 128
    },
    "^meetingExtensionDefinition.scenes\\[[0-9]\\]\\.name$": {
      "type": "string",
      "maxLength": 128
    },
    "^meetingExtensionDefinition.videoFilters\\[([0-9]|1[0-5])\\]\\.name$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.audienceClaimUrl$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.label$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.customMobileRibbonGroups\\[[0-9]\\]\\.label$": {
      "type": "string",
      "maxLength": 32
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.customMobileRibbonGroups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.icons\\[[0-8]\\]\\.url$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.icons\\[[0-7]\\]\\.url$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.label$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.icons\\[[0-7]\\]\\.url$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.label$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.supertip\\.title$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.supertip\\.description$": {
      "type": "string",
      "maxLength": 250
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.items\\[[1]?[0-9]\\]\\.icons\\[[0-7]\\]\\.url$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.items\\[[1]?[0-9]\\]\\.label$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.items\\[[1]?[0-9]\\]\\.supertip\\.title$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.items\\[[1]?[0-9]\\]\\.supertip\\.description$": {
      "type": "string",
      "maxLength": 250
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.code\\.page$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.code\\.script$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.actions\\[[1]?[0-9]\\]\\.displayName$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.alternates\\[[0-9]\\]\\.alternateIcons\\.icon\\.url$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.alternates\\[[0-9]\\]\\.alternateIcons\\.highResolutionIcon\\.url$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.getStartedMessages\\[[0-2]\\]\\.title$": {
      "type": "string",
      "maxLength": 125
    },
    "^extensions\\[[0]\\]\\.getStartedMessages\\[[0-2]\\]\\.description$": {
      "type": "string",
      "maxLength": 250
    },
    "^extensions\\[[0]\\]\\.getStartedMessages\\[[0-2]\\]\\.learnMoreUrl$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.contentRuntimes\\[[1]?[0-9]\\]\\.code\\.page$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.customFunctions\\.functions\\[[0-9]\\]\\.name$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.customFunctions\\.functions\\[[0-9]\\]\\.description$": {
      "type": "string",
      "maxLength": 1024
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.customFunctions\\.functions\\[[0-9]\\]\\.parameters\\[[0-9]\\]\\.name$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.customFunctions\\.functions\\[[0-9]\\]\\.parameters\\[[0-9]\\]\\.description$": {
      "type": "string",
      "maxLength": 512
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.customFunctions\\.namespace\\.name$": {
      "type": "string",
      "maxLength": 32
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.customFunctions\\.enums\\[[0-9]\\]\\.values\\[[0-9]\\]\\.name$": {
      "type": "string",
      "maxLength": 256
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.customFunctions\\.enums\\[[0-9]\\]\\.values\\[[0-9]\\]\\.tooltip$": {
      "type": "string",
      "maxLength": 256
    },
    "^extensions\\[[0]\\]\\.keyboardShortcuts\\[[0-9]\\]\\.shortcuts\\[[0-9]\\]\\.key\\.default$": {
      "type": "string",
      "maxLength": 32
    },
    "^extensions\\[[0]\\]\\.keyboardShortcuts\\[[0-9]\\]\\.shortcuts\\[[0-9]\\]\\.key\\.mac$": {
      "type": "string",
      "maxLength": 32
    },
    "^extensions\\[[0]\\]\\.keyboardShortcuts\\[[0-9]\\]\\.shortcuts\\[[0-9]\\]\\.key\\.web$": {
      "type": "string",
      "maxLength": 32
    },
    "^extensions\\[[0]\\]\\.keyboardShortcuts\\[[0-9]\\]\\.shortcuts\\[[0-9]\\]\\.key\\.windows$": {
      "type": "string",
      "maxLength": 32
    },
    "^extensions\\[[0]\\]\\.contextMenus\\[[0-9]\\]\\.menus\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.icons\\[[0-7]\\]\\.url$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.contextMenus\\[[0-9]\\]\\.menus\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.label": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.contextMenus\\[[0-9]\\]\\.menus\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.supertip\\.title": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.contextMenus\\[[0-9]\\]\\.menus\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.supertip\\.description": {
      "type": "string",
      "maxLength": 250
    },
    "^extensions\\[[0]\\]\\.contextMenus\\[[0-9]\\]\\.menus\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.items\\[[1]?[0-9]\\]\\.icons\\[[0-7]\\]\\.url": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.contextMenus\\[[0-9]\\]\\.menus\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.items\\[[1]?[0-9]\\]\\.label": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.contextMenus\\[[0-9]\\]\\.menus\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.items\\[[1]?[0-9]\\]\\.supertip\\.title": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.contextMenus\\[[0-9]\\]\\.menus\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.items\\[[1]?[0-9]\\]\\.supertip\\.description": {
      "type": "string",
      "maxLength": 250
    },
    "^copilotAgents\\.customEngineAgents\\[0\\]\\.disclaimer.text$": {
      "type": "string",
      "maxLength": 500
    },
    "^description\\.features\\[[0-2]\u002B\\]\\.title$": {
      "type": "string",
      "maxLength": 45
    },
    "^description\\.features\\[[0-2]\u002B\\]\\.description$": {
      "type": "string",
      "maxLength": 120
    }
  },
  "required": [
    "name.short",
    "description.short",
    "description.full"
  ],
  "definitions": {
    "nonEmptyString": {
      "type": "string",
      "pattern": "^(?![nN][uU][lL]{2}$)\\s*\\S.*"
    }
  }
}
```

- [Syntax](#tabpanel_2_syntax)
- [Schema](#tabpanel_2_schema)

```json
{
  "$schema": "{string}",
  "name.short": "{string}",
  "name.full": "{string}",
  "description.short": "{string}",
  "description.full": "{string}",
  "localizationKeys": {
    "^\[\[[a-zA-Z_][a-zA-Z0-9_]*\]\]$": "{string}"
  },
  "staticTabs.name": "{string}",
  "bots.commandLists.commands.title": "{string}",
  "bots.commandLists.commands.description": "{string}",
  "bots.commandLists.commands.prompt": "{string}",
  "composeExtensions.commands.title": "{string}",
  "composeExtensions.commands.description": "{string}",
  "composeExtensions.commands.parameters.title": "{string}",
  "composeExtensions.commands.parameters.description": "{string}",
  "composeExtensions.commands.parameters.value": "{string}",
  "composeExtensions.commands.parameters.choices.title": "{string}",
  "composeExtensions.commands.samplePrompts.text": "{string}",
  "composeExtensions.commands.taskInfo.title": "{string}",
  "activities.activityTypes.description": "{string}",
  "activities.activityTypes.templateText": "{string}",
  "meetingExtensionDefinition.scenes.name": "{string}",
  "extensions.audienceClaimUrl": "{string}",
  "extensions.ribbons.tabs.label": "{string}",
  "extensions.ribbons.tabs.customMobileRibbonGroups.label": "{string}",
  "extensions.ribbons.tabs.customMobileRibbonGroups.controls.icons.url": "{string}",
  "extensions.ribbons.tabs.customMobileRibbonGroups.controls.label": "{string}",
  "extensions.ribbons.tabs.groups.icons.url": "{string}",
  "extensions.ribbons.tabs.groups.label": "{string}",
  "extensions.ribbons.tabs.groups.controls.icons.url": "{string}",
  "extensions.ribbons.tabs.groups.controls.label": "{string}",
  "extensions.ribbons.tabs.groups.controls.supertip.title": "{string}",
  "extensions.ribbons.tabs.groups.controls.supertip.description": "{string}",
  "extensions.ribbons.tabs.groups.controls.items.icons.url": "{string}",
  "extensions.ribbons.tabs.groups.controls.items.label": "{string}",
  "extensions.ribbons.tabs.groups.controls.items.supertip.title": "{string}",
  "extensions.ribbons.tabs.groups.controls.items.supertip.description": "{string}",
  "extensions.ribbons.fixedControls.label": "{string}",
  "extensions.ribbons.fixedControls.supertip.title": "{string}",
  "extensions.ribbons.fixedControls.supertip.description": "{string}",
  "extensions.ribbons.spamPreProcessingDialog.title": "{string}",
  "extensions.ribbons.spamPreProcessingDialog.description": "{string}",
  "extensions.ribbons.spamPreProcessingDialog.spamFreeTextSectionTitle": "{string}",
  "extensions.ribbons.spamPreProcessingDialog.spamReportingOptions.title": "{string}",
  "extensions.ribbons.spamPreProcessingDialog.spamReportingOptions.options": "{string}",
  "extensions.ribbons.spamPreProcessingDialog.spamMoreInfo.text": "{string}",
  "extensions.ribbons.spamPreProcessingDialog.spamMoreInfo.url": "{string}",
  "extensions.runtimes.code.page": "{string}",
  "extensions.runtimes.code.script": "{string}",
  "extensions.runtimes.actions.displayName": "{string}",
  "extensions.runtimes.customFunctions.metadataUrl": "{string}",
  "extensions.runtimes.customFunctions.functions.name": "{string}",
  "extensions.runtimes.customFunctions.functions.description": "{string}",
  "extensions.runtimes.customFunctions.functions.parameters.name": "{string}",
  "extensions.runtimes.customFunctions.functions.parameters.description": "{string}",
  "extensions.runtimes.customFunctions.enums.values.name": "{string}",
  "extensions.runtimes.customFunctions.enums.values.tooltip": "{string}",
  "extensions.runtimes.customFunctions.namespace.name": "{string}",
  "extensions.keyboardShortcuts.shortcuts.key.default": "{string}",
  "extensions.keyboardShortcuts.shortcuts.key.mac": "{string}",
  "extensions.keyboardShortcuts.shortcuts.key.web": "{string}",
  "extensions.keyboardShortcuts.shortcuts.key.windows": "{string}",
  "extensions.alternates.alternateIcons.icon.url": "{string}",
  "extensions.alternates.alternateIcons.highResolutionIcon.url": "{string}",
  "extensions.getStartedMessages.title": "{string}",
  "extensions.getStartedMessages.description": "{string}",
  "extensions.getStartedMessages.learnMoreUrl": "{string}",
  "extensions.contentRuntimes.code.page": "{string}",
  "extensions.contextMenus.menus.controls.icons.url": "{string}",
  "extensions.contextMenus.menus.controls.label": "{string}",
  "extensions.contextMenus.menus.controls.supertip.title": "{string}",
  "extensions.contextMenus.menus.controls.supertip.description": "{string}",
  "extensions.contextMenus.menus.controls.items.icons.url": "{string}",
  "extensions.contextMenus.menus.controls.items.label": "{string}",
  "extensions.contextMenus.menus.controls.items.supertip.title": "{string}",
  "extensions.contextMenus.menus.controls.items.supertip.description": "{string}",
  "copilotAgents.customEngineAgents.disclaimer.text": "{string}",
  "agentConnectors.displayName": "{string}",
  "agentConnectors.description": "{string}",
  "description.features.title": "{string}",
  "description.features.description": "{string}"
}
```

```json
{
  "$schema": "http://json-schema.org/draft-04/schema#",
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "$schema": {
      "type": "string",
      "format": "uri"
    },
    "name.short": {
      "type": "string",
      "maxLength": 30,
      "$ref": "#/definitions/nonEmptyString"
    },
    "name.full": {
      "type": "string",
      "maxLength": 100,
      "$ref": "#/definitions/nonEmptyString"
    },
    "description.short": {
      "type": "string",
      "maxLength": 80,
      "$ref": "#/definitions/nonEmptyString"
    },
    "description.full": {
      "type": "string",
      "maxLength": 4000,
      "$ref": "#/definitions/nonEmptyString"
    },
    "localizationKeys": {
      "type": "object",
      "patternProperties": {
        "^\\[\\[[a-zA-Z_][a-zA-Z0-9_]*\\]\\]$": {
          "type": "string"
        }
      }
    }
  },
  "patternProperties": {
    "^staticTabs\\[([0-9]|1[0-5])\\]\\.name$": {
      "type": "string",
      "maxLength": 128
    },
    "^bots\\[0\\]\\.commandLists\\[[0-2]\\]\\.commands\\[([0-9]|1[0-1])\\]\\.title$": {
      "type": "string",
      "maxLength": 128
    },
    "^bots\\[0\\]\\.commandLists\\[[0-2]\\]\\.commands\\[([0-9]|1[0-1])\\]\\.description$": {
      "type": "string",
      "maxLength": 4000
    },
    "^bots\\[0\\]\\.commandLists\\[[0-2]\\]\\.commands\\[([0-9]|1[0-1])\\]\\.prompt$": {
      "type": "string",
      "maxLength": 4000
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.title$": {
      "type": "string",
      "maxLength": 32
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.description$": {
      "type": "string",
      "maxLength": 128
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.title$": {
      "type": "string",
      "maxLength": 32
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.description$": {
      "type": "string",
      "maxLength": 128
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.value$": {
      "type": "string",
      "maxLength": 512
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.choices\\[[0-9]\\]\\.title$": {
      "type": "string",
      "maxLength": 128
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.samplePrompts\\[[0-4]\\]\\.text$": {
      "type": "string",
      "maxLength": 128
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.taskInfo\\.title$": {
      "type": "string",
      "maxLength": 64
    },
    "^activities.activityTypes\\[\\b([0-9]|[1-8][0-9]|9[0-9]|1[01][0-9]|12[0-7])\\b]\\.description$": {
      "type": "string",
      "maxLength": 128
    },
    "^activities.activityTypes\\[\\b([0-9]|[1-8][0-9]|9[0-9]|1[01][0-9]|12[0-7])\\b]\\.templateText$": {
      "type": "string",
      "maxLength": 128
    },
    "^meetingExtensionDefinition.scenes\\[[0-9]\\]\\.name$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.audienceClaimUrl$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.label$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.customMobileRibbonGroups\\[[0-9]\\]\\.label$": {
      "type": "string",
      "maxLength": 32
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.customMobileRibbonGroups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.icons\\[[0-8]\\]\\.url$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.customMobileRibbonGroups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.label$": {
      "type": "string",
      "maxLength": 32
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.icons\\[[0-7]\\]\\.url$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.label$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.icons\\[[0-7]\\]\\.url$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.label$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.supertip\\.title$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.supertip\\.description$": {
      "type": "string",
      "maxLength": 250
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.items\\[[1]?[0-9]\\]\\.icons\\[[0-7]\\]\\.url$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.items\\[[1]?[0-9]\\]\\.label$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.items\\[[1]?[0-9]\\]\\.supertip\\.title$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.items\\[[1]?[0-9]\\]\\.supertip\\.description$": {
      "type": "string",
      "maxLength": 250
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.fixedControls\\[[1]?[0-9]\\]\\.label$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.fixedControls\\[[1]?[0-9]\\]\\.supertip\\.title$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.fixedControls\\[[1]?[0-9]\\]\\.supertip\\.description$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.spamPreProcessingDialog\\.title$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.spamPreProcessingDialog\\.description$": {
      "type": "string",
      "maxLength": 250
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.spamPreProcessingDialog\\.spamFreeTextSectionTitle$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.spamPreProcessingDialog\\.spamReportingOptions\\.title$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.spamPreProcessingDialog\\.spamReportingOptions\\.options\\[[0-4]\\]$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.spamPreProcessingDialog\\.spamMoreInfo\\.text$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.spamPreProcessingDialog\\.spamMoreInfo\\.url$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.code\\.page$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.code\\.script$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.actions\\[(1[0-4][0-9]|[1-9]?[0-9])\\]\\.displayName$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.customFunctions\\.metadataUrl$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.customFunctions\\.functions\\[[0-9]\\]\\.name$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.customFunctions\\.functions\\[[0-9]\\]\\.description$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.customFunctions\\.functions\\[[0-9]\\]\\.parameters\\[[0-9]\\]\\.name$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.customFunctions\\.functions\\[[0-9]\\]\\.parameters\\[[0-9]\\]\\.description$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.customFunctions\\.enums\\[[0-9]\\]\\.values\\[[0-9]\\]\\.name$": {
      "type": "string",
      "maxLength": 256
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.customFunctions\\.enums\\[[0-9]\\]\\.values\\[[0-9]\\]\\.tooltip$": {
      "type": "string",
      "maxLength": 256
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.customFunctions\\.namespace\\.name$": {
      "type": "string",
      "maxLength": 32
    },
    "^extensions\\[[0]\\]\\.keyboardShortcuts\\[[0-9]\\]\\.shortcuts\\[[0-9]\\]\\.key\\.default$": {
      "type": "string",
      "maxLength": 32
    },
    "^extensions\\[[0]\\]\\.keyboardShortcuts\\[[0-9]\\]\\.shortcuts\\[[0-9]\\]\\.key\\.mac$": {
      "type": "string",
      "maxLength": 32
    },
    "^extensions\\[[0]\\]\\.keyboardShortcuts\\[[0-9]\\]\\.shortcuts\\[[0-9]\\]\\.key\\.web$": {
      "type": "string",
      "maxLength": 32
    },
    "^extensions\\[[0]\\]\\.keyboardShortcuts\\[[0-9]\\]\\.shortcuts\\[[0-9]\\]\\.key\\.windows$": {
      "type": "string",
      "maxLength": 32
    },
    "^extensions\\[[0]\\]\\.alternates\\[[0-9]\\]\\.alternateIcons\\.icon\\.url$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.alternates\\[[0-9]\\]\\.alternateIcons\\.highResolutionIcon\\.url$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.getStartedMessages\\[[0-2]\\]\\.title$": {
      "type": "string",
      "maxLength": 125
    },
    "^extensions\\[[0]\\]\\.getStartedMessages\\[[0-2]\\]\\.description$": {
      "type": "string",
      "maxLength": 250
    },
    "^extensions\\[[0]\\]\\.getStartedMessages\\[[0-2]\\]\\.learnMoreUrl$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.contentRuntimes\\[[1]?[0-9]\\]\\.code\\.page$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.contextMenus\\[[0-9]\\]\\.menus\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.icons\\[[0-7]\\]\\.url$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.contextMenus\\[[0-9]\\]\\.menus\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.label": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.contextMenus\\[[0-9]\\]\\.menus\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.supertip\\.title": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.contextMenus\\[[0-9]\\]\\.menus\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.supertip\\.description": {
      "type": "string",
      "maxLength": 250
    },
    "^extensions\\[[0]\\]\\.contextMenus\\[[0-9]\\]\\.menus\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.items\\[[1]?[0-9]\\]\\.icons\\[[0-7]\\]\\.url": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.contextMenus\\[[0-9]\\]\\.menus\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.items\\[[1]?[0-9]\\]\\.label": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.contextMenus\\[[0-9]\\]\\.menus\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.items\\[[1]?[0-9]\\]\\.supertip\\.title": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.contextMenus\\[[0-9]\\]\\.menus\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.items\\[[1]?[0-9]\\]\\.supertip\\.description": {
      "type": "string",
      "maxLength": 250
    },
    "^copilotAgents.customEngineAgents\\[0\\]\\.disclaimer.text$": {
      "type": "string",
      "maxLength": 500
    },
    "^agentConnectors\\[[0-9]\\]\\.displayName$": {
      "type": "string",
      "maxLength": 128
    },
    "^agentConnectors\\[[0-9]\\]\\.description$": {
      "type": "string",
      "maxLength": 4000
    },
    "^description\\.features\\[[0-2]\u002B\\]\\.title$": {
      "type": "string",
      "maxLength": 45
    },
    "^description\\.features\\[[0-2]\u002B\\]\\.description$": {
      "type": "string",
      "maxLength": 120
    }
  },
  "required": [
    "name.short",
    "description.short",
    "description.full"
  ],
  "definitions": {
    "nonEmptyString": {
      "type": "string",
      "pattern": "^(?![nN][uU][lL]{2}$)\\s*\\S.*"
    }
  }
}
```

- [Syntax](#tabpanel_3_syntax)
- [Schema](#tabpanel_3_schema)

```json
{
  "$schema": "{string}",
  "name.short": "{string}",
  "name.full": "{string}",
  "description.short": "{string}",
  "description.full": "{string}",
  "localizationKeys": {
    "^\[\[[a-zA-Z_][a-zA-Z0-9_]*\]\]$": "{string}"
  },
  "staticTabs.name": "{string}",
  "bots.commandLists.commands.title": "{string}",
  "bots.commandLists.commands.description": "{string}",
  "composeExtensions.commands.title": "{string}",
  "composeExtensions.commands.description": "{string}",
  "composeExtensions.commands.parameters.title": "{string}",
  "composeExtensions.commands.parameters.description": "{string}",
  "composeExtensions.commands.parameters.value": "{string}",
  "composeExtensions.commands.parameters.choices.title": "{string}",
  "composeExtensions.commands.samplePrompts.text": "{string}",
  "composeExtensions.commands.taskInfo.title": "{string}",
  "^composeExtensions\[0\]\.commands\[[0-9]\]\.prompt$": "{string}",
  "activities.activityTypes.description": "{string}",
  "activities.activityTypes.templateText": "{string}",
  "meetingExtensionDefinition.scenes.name": "{string}",
  "extensions.audienceClaimUrl": "{string}",
  "extensions.ribbons.tabs.label": "{string}",
  "extensions.ribbons.tabs.customMobileRibbonGroups.label": "{string}",
  "extensions.ribbons.tabs.customMobileRibbonGroups.controls.icons.url": "{string}",
  "extensions.ribbons.tabs.customMobileRibbonGroups.controls.label": "{string}",
  "extensions.ribbons.tabs.groups.icons.url": "{string}",
  "extensions.ribbons.tabs.groups.label": "{string}",
  "extensions.ribbons.tabs.groups.controls.icons.url": "{string}",
  "extensions.ribbons.tabs.groups.controls.label": "{string}",
  "extensions.ribbons.tabs.groups.controls.supertip.title": "{string}",
  "extensions.ribbons.tabs.groups.controls.supertip.description": "{string}",
  "extensions.ribbons.tabs.groups.controls.items.icons.url": "{string}",
  "extensions.ribbons.tabs.groups.controls.items.label": "{string}",
  "extensions.ribbons.tabs.groups.controls.items.supertip.title": "{string}",
  "extensions.ribbons.tabs.groups.controls.items.supertip.description": "{string}",
  "extensions.ribbons.fixedControls.label": "{string}",
  "extensions.ribbons.fixedControls.supertip.title": "{string}",
  "extensions.ribbons.fixedControls.supertip.description": "{string}",
  "extensions.ribbons.spamPreProcessingDialog.title": "{string}",
  "extensions.ribbons.spamPreProcessingDialog.description": "{string}",
  "extensions.ribbons.spamPreProcessingDialog.spamFreeTextSectionTitle": "{string}",
  "extensions.ribbons.spamPreProcessingDialog.spamReportingOptions.title": "{string}",
  "extensions.ribbons.spamPreProcessingDialog.spamReportingOptions.options": "{string}",
  "extensions.ribbons.spamPreProcessingDialog.spamMoreInfo.text": "{string}",
  "extensions.ribbons.spamPreProcessingDialog.spamMoreInfo.url": "{string}",
  "extensions.runtimes.code.page": "{string}",
  "extensions.runtimes.code.script": "{string}",
  "extensions.runtimes.actions.displayName": "{string}",
  "extensions.runtimes.customFunctions.metadataUrl": "{string}",
  "extensions.runtimes.customFunctions.functions.name": "{string}",
  "extensions.runtimes.customFunctions.functions.description": "{string}",
  "extensions.runtimes.customFunctions.functions.parameters.name": "{string}",
  "extensions.runtimes.customFunctions.functions.parameters.description": "{string}",
  "extensions.runtimes.customFunctions.enums.values.name": "{string}",
  "extensions.runtimes.customFunctions.enums.values.tooltip": "{string}",
  "extensions.runtimes.customFunctions.namespace.name": "{string}",
  "extensions.keyboardShortcuts.shortcuts.key.default": "{string}",
  "extensions.keyboardShortcuts.shortcuts.key.mac": "{string}",
  "extensions.keyboardShortcuts.shortcuts.key.web": "{string}",
  "extensions.keyboardShortcuts.shortcuts.key.windows": "{string}",
  "extensions.alternates.alternateIcons.icon.url": "{string}",
  "extensions.alternates.alternateIcons.highResolutionIcon.url": "{string}",
  "extensions.getStartedMessages.title": "{string}",
  "extensions.getStartedMessages.description": "{string}",
  "extensions.getStartedMessages.learnMoreUrl": "{string}",
  "extensions.contentRuntimes.code.page": "{string}",
  "extensions.contextMenus.menus.controls.icons.url": "{string}",
  "extensions.contextMenus.menus.controls.label": "{string}",
  "extensions.contextMenus.menus.controls.supertip.title": "{string}",
  "extensions.contextMenus.menus.controls.supertip.description": "{string}",
  "extensions.contextMenus.menus.controls.items.icons.url": "{string}",
  "extensions.contextMenus.menus.controls.items.label": "{string}",
  "extensions.contextMenus.menus.controls.items.supertip.title": "{string}",
  "extensions.contextMenus.menus.controls.items.supertip.description": "{string}",
  "copilotAgents.customEngineAgents.disclaimer.text": "{string}",
  "agentConnectors.displayName": "{string}",
  "agentConnectors.description": "{string}",
  "description.features.title": "{string}",
  "description.features.description": "{string}"
}
```

```json
{
  "$schema": "http://json-schema.org/draft-04/schema#",
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "$schema": {
      "type": "string",
      "format": "uri"
    },
    "name.short": {
      "type": "string",
      "maxLength": 30,
      "$ref": "#/definitions/nonEmptyString"
    },
    "name.full": {
      "type": "string",
      "maxLength": 100,
      "$ref": "#/definitions/nonEmptyString"
    },
    "description.short": {
      "type": "string",
      "maxLength": 80,
      "$ref": "#/definitions/nonEmptyString"
    },
    "description.full": {
      "type": "string",
      "maxLength": 4000,
      "$ref": "#/definitions/nonEmptyString"
    },
    "localizationKeys": {
      "type": "object",
      "patternProperties": {
        "^\\[\\[[a-zA-Z_][a-zA-Z0-9_]*\\]\\]$": {
          "type": "string"
        }
      }
    }
  },
  "patternProperties": {
    "^staticTabs\\[([0-9]|1[0-5])\\]\\.name$": {
      "type": "string",
      "maxLength": 128
    },
    "^bots\\[0\\]\\.commandLists\\[[0-2]\\]\\.commands\\[([0-9]|1[0-1])\\]\\.title$": {
      "type": "string",
      "maxLength": 128
    },
    "^bots\\[0\\]\\.commandLists\\[[0-2]\\]\\.commands\\[([0-9]|1[0-1])\\]\\.description$": {
      "type": "string",
      "maxLength": 4000
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.title$": {
      "type": "string",
      "maxLength": 32
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.description$": {
      "type": "string",
      "maxLength": 128
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.title$": {
      "type": "string",
      "maxLength": 32
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.description$": {
      "type": "string",
      "maxLength": 128
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.value$": {
      "type": "string",
      "maxLength": 512
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.choices\\[[0-9]\\]\\.title$": {
      "type": "string",
      "maxLength": 128
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.samplePrompts\\[[0-4]\\]\\.text$": {
      "type": "string",
      "maxLength": 128
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.taskInfo\\.title$": {
      "type": "string",
      "maxLength": 64
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.prompt$": {
      "type": "string",
      "maxLength": 4000
    },
    "^activities.activityTypes\\[\\b([0-9]|[1-8][0-9]|9[0-9]|1[01][0-9]|12[0-7])\\b]\\.description$": {
      "type": "string",
      "maxLength": 128
    },
    "^activities.activityTypes\\[\\b([0-9]|[1-8][0-9]|9[0-9]|1[01][0-9]|12[0-7])\\b]\\.templateText$": {
      "type": "string",
      "maxLength": 128
    },
    "^meetingExtensionDefinition.scenes\\[[0-9]\\]\\.name$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.audienceClaimUrl$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.label$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.customMobileRibbonGroups\\[[0-9]\\]\\.label$": {
      "type": "string",
      "maxLength": 32
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.customMobileRibbonGroups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.icons\\[[0-8]\\]\\.url$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.customMobileRibbonGroups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.label$": {
      "type": "string",
      "maxLength": 32
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.icons\\[[0-7]\\]\\.url$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.label$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.icons\\[[0-7]\\]\\.url$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.label$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.supertip\\.title$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.supertip\\.description$": {
      "type": "string",
      "maxLength": 250
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.items\\[[1]?[0-9]\\]\\.icons\\[[0-7]\\]\\.url$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.items\\[[1]?[0-9]\\]\\.label$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.items\\[[1]?[0-9]\\]\\.supertip\\.title$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.items\\[[1]?[0-9]\\]\\.supertip\\.description$": {
      "type": "string",
      "maxLength": 250
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.fixedControls\\[[1]?[0-9]\\]\\.label$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.fixedControls\\[[1]?[0-9]\\]\\.supertip\\.title$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.fixedControls\\[[1]?[0-9]\\]\\.supertip\\.description$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.spamPreProcessingDialog\\.title$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.spamPreProcessingDialog\\.description$": {
      "type": "string",
      "maxLength": 250
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.spamPreProcessingDialog\\.spamFreeTextSectionTitle$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.spamPreProcessingDialog\\.spamReportingOptions\\.title$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.spamPreProcessingDialog\\.spamReportingOptions\\.options\\[[0-4]\\]$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.spamPreProcessingDialog\\.spamMoreInfo\\.text$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.spamPreProcessingDialog\\.spamMoreInfo\\.url$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.code\\.page$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.code\\.script$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.actions\\[(1[0-4][0-9]|[1-9]?[0-9])\\]\\.displayName$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.customFunctions\\.metadataUrl$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.customFunctions\\.functions\\[[0-9]\\]\\.name$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.customFunctions\\.functions\\[[0-9]\\]\\.description$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.customFunctions\\.functions\\[[0-9]\\]\\.parameters\\[[0-9]\\]\\.name$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.customFunctions\\.functions\\[[0-9]\\]\\.parameters\\[[0-9]\\]\\.description$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.customFunctions\\.enums\\[[0-9]\\]\\.values\\[[0-9]\\]\\.name$": {
      "type": "string",
      "maxLength": 256
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.customFunctions\\.enums\\[[0-9]\\]\\.values\\[[0-9]\\]\\.tooltip$": {
      "type": "string",
      "maxLength": 256
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.customFunctions\\.namespace\\.name$": {
      "type": "string",
      "maxLength": 32
    },
    "^extensions\\[[0]\\]\\.keyboardShortcuts\\[[0-9]\\]\\.shortcuts\\[[0-9]\\]\\.key\\.default$": {
      "type": "string",
      "maxLength": 32
    },
    "^extensions\\[[0]\\]\\.keyboardShortcuts\\[[0-9]\\]\\.shortcuts\\[[0-9]\\]\\.key\\.mac$": {
      "type": "string",
      "maxLength": 32
    },
    "^extensions\\[[0]\\]\\.keyboardShortcuts\\[[0-9]\\]\\.shortcuts\\[[0-9]\\]\\.key\\.web$": {
      "type": "string",
      "maxLength": 32
    },
    "^extensions\\[[0]\\]\\.keyboardShortcuts\\[[0-9]\\]\\.shortcuts\\[[0-9]\\]\\.key\\.windows$": {
      "type": "string",
      "maxLength": 32
    },
    "^extensions\\[[0]\\]\\.alternates\\[[0-9]\\]\\.alternateIcons\\.icon\\.url$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.alternates\\[[0-9]\\]\\.alternateIcons\\.highResolutionIcon\\.url$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.getStartedMessages\\[[0-2]\\]\\.title$": {
      "type": "string",
      "maxLength": 125
    },
    "^extensions\\[[0]\\]\\.getStartedMessages\\[[0-2]\\]\\.description$": {
      "type": "string",
      "maxLength": 250
    },
    "^extensions\\[[0]\\]\\.getStartedMessages\\[[0-2]\\]\\.learnMoreUrl$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.contentRuntimes\\[[1]?[0-9]\\]\\.code\\.page$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.contextMenus\\[[0-9]\\]\\.menus\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.icons\\[[0-7]\\]\\.url$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.contextMenus\\[[0-9]\\]\\.menus\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.label": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.contextMenus\\[[0-9]\\]\\.menus\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.supertip\\.title": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.contextMenus\\[[0-9]\\]\\.menus\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.supertip\\.description": {
      "type": "string",
      "maxLength": 250
    },
    "^extensions\\[[0]\\]\\.contextMenus\\[[0-9]\\]\\.menus\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.items\\[[1]?[0-9]\\]\\.icons\\[[0-7]\\]\\.url": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.contextMenus\\[[0-9]\\]\\.menus\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.items\\[[1]?[0-9]\\]\\.label": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.contextMenus\\[[0-9]\\]\\.menus\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.items\\[[1]?[0-9]\\]\\.supertip\\.title": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.contextMenus\\[[0-9]\\]\\.menus\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.items\\[[1]?[0-9]\\]\\.supertip\\.description": {
      "type": "string",
      "maxLength": 250
    },
    "^copilotAgents.customEngineAgents\\[0\\]\\.disclaimer.text$": {
      "type": "string",
      "maxLength": 500
    },
    "^agentConnectors\\[[0-9]\\]\\.displayName$": {
      "type": "string",
      "maxLength": 128
    },
    "^agentConnectors\\[[0-9]\\]\\.description$": {
      "type": "string",
      "maxLength": 4000
    },
    "^description\\.features\\[[0-2]\u002B\\]\\.title$": {
      "type": "string",
      "maxLength": 45
    },
    "^description\\.features\\[[0-2]\u002B\\]\\.description$": {
      "type": "string",
      "maxLength": 120
    }
  },
  "required": [
    "name.short",
    "description.short",
    "description.full"
  ],
  "definitions": {
    "nonEmptyString": {
      "type": "string",
      "pattern": "^(?![nN][uU][lL]{2}$)\\s*\\S.*"
    }
  }
}
```

- [Syntax](#tabpanel_4_syntax)
- [Schema](#tabpanel_4_schema)

```json
{
  "$schema": "{string}",
  "name.short": "{string}",
  "name.full": "{string}",
  "description.short": "{string}",
  "description.full": "{string}",
  "localizationKeys": {
    "^\[\[[a-zA-Z_][a-zA-Z0-9_]*\]\]$": "{string}"
  },
  "staticTabs.name": "{string}",
  "bots.commandLists.commands.title": "{string}",
  "bots.commandLists.commands.description": "{string}",
  "composeExtensions.commands.title": "{string}",
  "composeExtensions.commands.description": "{string}",
  "composeExtensions.commands.parameters.title": "{string}",
  "composeExtensions.commands.parameters.description": "{string}",
  "composeExtensions.commands.parameters.value": "{string}",
  "composeExtensions.commands.parameters.choices.title": "{string}",
  "composeExtensions.commands.samplePrompts.text": "{string}",
  "composeExtensions.commands.taskInfo.title": "{string}",
  "activities.activityTypes.description": "{string}",
  "activities.activityTypes.templateText": "{string}",
  "meetingExtensionDefinition.scenes.name": "{string}",
  "extensions.audienceClaimUrl": "{string}",
  "extensions.ribbons.tabs.label": "{string}",
  "extensions.ribbons.tabs.customMobileRibbonGroups.label": "{string}",
  "extensions.ribbons.tabs.customMobileRibbonGroups.controls.icons.url": "{string}",
  "extensions.ribbons.tabs.customMobileRibbonGroups.controls.label": "{string}",
  "extensions.ribbons.tabs.groups.icons.url": "{string}",
  "extensions.ribbons.tabs.groups.label": "{string}",
  "extensions.ribbons.tabs.groups.controls.icons.url": "{string}",
  "extensions.ribbons.tabs.groups.controls.label": "{string}",
  "extensions.ribbons.tabs.groups.controls.supertip.title": "{string}",
  "extensions.ribbons.tabs.groups.controls.supertip.description": "{string}",
  "extensions.ribbons.tabs.groups.controls.items.icons.url": "{string}",
  "extensions.ribbons.tabs.groups.controls.items.label": "{string}",
  "extensions.ribbons.tabs.groups.controls.items.supertip.title": "{string}",
  "extensions.ribbons.tabs.groups.controls.items.supertip.description": "{string}",
  "extensions.ribbons.fixedControls.label": "{string}",
  "extensions.ribbons.fixedControls.supertip.title": "{string}",
  "extensions.ribbons.fixedControls.supertip.description": "{string}",
  "extensions.ribbons.spamPreProcessingDialog.title": "{string}",
  "extensions.ribbons.spamPreProcessingDialog.description": "{string}",
  "extensions.ribbons.spamPreProcessingDialog.spamFreeTextSectionTitle": "{string}",
  "extensions.ribbons.spamPreProcessingDialog.spamReportingOptions.title": "{string}",
  "extensions.ribbons.spamPreProcessingDialog.spamReportingOptions.options": "{string}",
  "extensions.ribbons.spamPreProcessingDialog.spamMoreInfo.text": "{string}",
  "extensions.ribbons.spamPreProcessingDialog.spamMoreInfo.url": "{string}",
  "extensions.runtimes.code.page": "{string}",
  "extensions.runtimes.code.script": "{string}",
  "extensions.runtimes.actions.displayName": "{string}",
  "extensions.runtimes.customFunctions.metadataUrl": "{string}",
  "extensions.runtimes.customFunctions.functions.name": "{string}",
  "extensions.runtimes.customFunctions.functions.description": "{string}",
  "extensions.runtimes.customFunctions.functions.parameters.name": "{string}",
  "extensions.runtimes.customFunctions.functions.parameters.description": "{string}",
  "extensions.runtimes.customFunctions.enums.values.name": "{string}",
  "extensions.runtimes.customFunctions.enums.values.tooltip": "{string}",
  "extensions.runtimes.customFunctions.namespace.name": "{string}",
  "extensions.keyboardShortcuts.shortcuts.key.default": "{string}",
  "extensions.keyboardShortcuts.shortcuts.key.mac": "{string}",
  "extensions.keyboardShortcuts.shortcuts.key.web": "{string}",
  "extensions.keyboardShortcuts.shortcuts.key.windows": "{string}",
  "extensions.alternates.alternateIcons.icon.url": "{string}",
  "extensions.alternates.alternateIcons.highResolutionIcon.url": "{string}",
  "extensions.getStartedMessages.title": "{string}",
  "extensions.getStartedMessages.description": "{string}",
  "extensions.getStartedMessages.learnMoreUrl": "{string}",
  "extensions.contentRuntimes.code.page": "{string}",
  "extensions.contextMenus.menus.controls.icons.url": "{string}",
  "extensions.contextMenus.menus.controls.label": "{string}",
  "extensions.contextMenus.menus.controls.supertip.title": "{string}",
  "extensions.contextMenus.menus.controls.supertip.description": "{string}",
  "extensions.contextMenus.menus.controls.items.icons.url": "{string}",
  "extensions.contextMenus.menus.controls.items.label": "{string}",
  "extensions.contextMenus.menus.controls.items.supertip.title": "{string}",
  "extensions.contextMenus.menus.controls.items.supertip.description": "{string}",
  "copilotAgents.customEngineAgents.disclaimer.text": "{string}",
  "description.features.title": "{string}",
  "description.features.description": "{string}"
}
```

```json
{
  "$schema": "http://json-schema.org/draft-04/schema#",
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "$schema": {
      "type": "string",
      "format": "uri"
    },
    "name.short": {
      "type": "string",
      "maxLength": 30,
      "$ref": "#/definitions/nonEmptyString"
    },
    "name.full": {
      "type": "string",
      "maxLength": 100,
      "$ref": "#/definitions/nonEmptyString"
    },
    "description.short": {
      "type": "string",
      "maxLength": 80,
      "$ref": "#/definitions/nonEmptyString"
    },
    "description.full": {
      "type": "string",
      "maxLength": 4000,
      "$ref": "#/definitions/nonEmptyString"
    },
    "localizationKeys": {
      "type": "object",
      "patternProperties": {
        "^\\[\\[[a-zA-Z_][a-zA-Z0-9_]*\\]\\]$": {
          "type": "string"
        }
      }
    }
  },
  "patternProperties": {
    "^staticTabs\\[([0-9]|1[0-5])\\]\\.name$": {
      "type": "string",
      "maxLength": 128
    },
    "^bots\\[0\\]\\.commandLists\\[[0-2]\\]\\.commands\\[([0-9]|1[0-1])\\]\\.title$": {
      "type": "string",
      "maxLength": 128
    },
    "^bots\\[0\\]\\.commandLists\\[[0-2]\\]\\.commands\\[([0-9]|1[0-1])\\]\\.description$": {
      "type": "string",
      "maxLength": 4000
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.title$": {
      "type": "string",
      "maxLength": 32
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.description$": {
      "type": "string",
      "maxLength": 128
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.title$": {
      "type": "string",
      "maxLength": 32
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.description$": {
      "type": "string",
      "maxLength": 128
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.value$": {
      "type": "string",
      "maxLength": 512
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.choices\\[[0-9]\\]\\.title$": {
      "type": "string",
      "maxLength": 128
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.samplePrompts\\[[0-4]\\]\\.text$": {
      "type": "string",
      "maxLength": 128
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.taskInfo\\.title$": {
      "type": "string",
      "maxLength": 64
    },
    "^activities.activityTypes\\[\\b([0-9]|[1-8][0-9]|9[0-9]|1[01][0-9]|12[0-7])\\b]\\.description$": {
      "type": "string",
      "maxLength": 128
    },
    "^activities.activityTypes\\[\\b([0-9]|[1-8][0-9]|9[0-9]|1[01][0-9]|12[0-7])\\b]\\.templateText$": {
      "type": "string",
      "maxLength": 128
    },
    "^meetingExtensionDefinition.scenes\\[[0-9]\\]\\.name$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.audienceClaimUrl$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.label$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.customMobileRibbonGroups\\[[0-9]\\]\\.label$": {
      "type": "string",
      "maxLength": 32
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.customMobileRibbonGroups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.icons\\[[0-8]\\]\\.url$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.customMobileRibbonGroups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.label$": {
      "type": "string",
      "maxLength": 32
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.icons\\[[0-2]\\]\\.url$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.label$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.icons\\[[0-2]\\]\\.url$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.label$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.supertip\\.title$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.supertip\\.description$": {
      "type": "string",
      "maxLength": 250
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.items\\[[1]?[0-9]\\]\\.icons\\[[0-2]\\]\\.url$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.items\\[[1]?[0-9]\\]\\.label$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.items\\[[1]?[0-9]\\]\\.supertip\\.title$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.items\\[[1]?[0-9]\\]\\.supertip\\.description$": {
      "type": "string",
      "maxLength": 250
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.fixedControls\\[[1]?[0-9]\\]\\.label$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.fixedControls\\[[1]?[0-9]\\]\\.supertip\\.title$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.fixedControls\\[[1]?[0-9]\\]\\.supertip\\.description$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.spamPreProcessingDialog\\.title$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.spamPreProcessingDialog\\.description$": {
      "type": "string",
      "maxLength": 250
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.spamPreProcessingDialog\\.spamFreeTextSectionTitle$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.spamPreProcessingDialog\\.spamReportingOptions\\.title$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.spamPreProcessingDialog\\.spamReportingOptions\\.options\\[[0-4]\\]$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.spamPreProcessingDialog\\.spamMoreInfo\\.text$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.spamPreProcessingDialog\\.spamMoreInfo\\.url$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.code\\.page$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.code\\.script$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.actions\\[[1]?[0-9]\\]\\.displayName$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.customFunctions\\.metadataUrl$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.customFunctions\\.functions\\[[0-9]\\]\\.name$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.customFunctions\\.functions\\[[0-9]\\]\\.description$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.customFunctions\\.functions\\[[0-9]\\]\\.parameters\\[[0-9]\\]\\.name$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.customFunctions\\.functions\\[[0-9]\\]\\.parameters\\[[0-9]\\]\\.description$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.customFunctions\\.enums\\[[0-9]\\]\\.values\\[[0-9]\\]\\.name$": {
      "type": "string",
      "maxLength": 256
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.customFunctions\\.enums\\[[0-9]\\]\\.values\\[[0-9]\\]\\.tooltip$": {
      "type": "string",
      "maxLength": 256
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.customFunctions\\.namespace\\.name$": {
      "type": "string",
      "maxLength": 32
    },
    "^extensions\\[[0]\\]\\.keyboardShortcuts\\[[0-9]\\]\\.shortcuts\\[[0-9]\\]\\.key\\.default$": {
      "type": "string",
      "maxLength": 32
    },
    "^extensions\\[[0]\\]\\.keyboardShortcuts\\[[0-9]\\]\\.shortcuts\\[[0-9]\\]\\.key\\.mac$": {
      "type": "string",
      "maxLength": 32
    },
    "^extensions\\[[0]\\]\\.keyboardShortcuts\\[[0-9]\\]\\.shortcuts\\[[0-9]\\]\\.key\\.web$": {
      "type": "string",
      "maxLength": 32
    },
    "^extensions\\[[0]\\]\\.keyboardShortcuts\\[[0-9]\\]\\.shortcuts\\[[0-9]\\]\\.key\\.windows$": {
      "type": "string",
      "maxLength": 32
    },
    "^extensions\\[[0]\\]\\.alternates\\[[0-9]\\]\\.alternateIcons\\.icon\\.url$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.alternates\\[[0-9]\\]\\.alternateIcons\\.highResolutionIcon\\.url$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.getStartedMessages\\[[0-2]\\]\\.title$": {
      "type": "string",
      "maxLength": 125
    },
    "^extensions\\[[0]\\]\\.getStartedMessages\\[[0-2]\\]\\.description$": {
      "type": "string",
      "maxLength": 250
    },
    "^extensions\\[[0]\\]\\.getStartedMessages\\[[0-2]\\]\\.learnMoreUrl$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.contentRuntimes\\[[1]?[0-9]\\]\\.code\\.page$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.contextMenus\\[[0-9]\\]\\.menus\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.icons\\[[0-2]\\]\\.url": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.contextMenus\\[[0-9]\\]\\.menus\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.label": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.contextMenus\\[[0-9]\\]\\.menus\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.supertip\\.title": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.contextMenus\\[[0-9]\\]\\.menus\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.supertip\\.description": {
      "type": "string",
      "maxLength": 250
    },
    "^extensions\\[[0]\\]\\.contextMenus\\[[0-9]\\]\\.menus\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.items\\[[1]?[0-9]\\]\\.icons\\[[0-2]\\]\\.url": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.contextMenus\\[[0-9]\\]\\.menus\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.items\\[[1]?[0-9]\\]\\.label": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.contextMenus\\[[0-9]\\]\\.menus\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.items\\[[1]?[0-9]\\]\\.supertip\\.title": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.contextMenus\\[[0-9]\\]\\.menus\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.items\\[[1]?[0-9]\\]\\.supertip\\.description": {
      "type": "string",
      "maxLength": 250
    },
    "^copilotAgents.customEngineAgents\\[0\\]\\.disclaimer.text$": {
      "type": "string",
      "maxLength": 500
    },
    "^description\\.features\\[[0-2]\u002B\\]\\.title$": {
      "type": "string",
      "maxLength": 45
    },
    "^description\\.features\\[[0-2]\u002B\\]\\.description$": {
      "type": "string",
      "maxLength": 120
    }
  },
  "required": [
    "name.short",
    "description.short",
    "description.full"
  ],
  "definitions": {
    "nonEmptyString": {
      "type": "string",
      "pattern": "^(?![nN][uU][lL]{2}$)\\s*\\S.*"
    }
  }
}
```

- [Syntax](#tabpanel_5_syntax)
- [Schema](#tabpanel_5_schema)

```json
{
  "$schema": "{string}",
  "name.short": "{string}",
  "name.full": "{string}",
  "description.short": "{string}",
  "description.full": "{string}",
  "localizationKeys": {
    "^\[\[[a-zA-Z_][a-zA-Z0-9_]*\]\]$": "{string}"
  },
  "staticTabs.name": "{string}",
  "bots.commandLists.commands.title": "{string}",
  "bots.commandLists.commands.description": "{string}",
  "composeExtensions.commands.title": "{string}",
  "composeExtensions.commands.description": "{string}",
  "composeExtensions.commands.parameters.title": "{string}",
  "composeExtensions.commands.parameters.description": "{string}",
  "composeExtensions.commands.parameters.value": "{string}",
  "composeExtensions.commands.parameters.choices.title": "{string}",
  "composeExtensions.commands.samplePrompts.text": "{string}",
  "composeExtensions.commands.taskInfo.title": "{string}",
  "activities.activityTypes.description": "{string}",
  "activities.activityTypes.templateText": "{string}",
  "meetingExtensionDefinition.scenes.name": "{string}",
  "extensions.audienceClaimUrl": "{string}",
  "extensions.ribbons.tabs.label": "{string}",
  "extensions.ribbons.tabs.customMobileRibbonGroups.label": "{string}",
  "extensions.ribbons.tabs.customMobileRibbonGroups.controls.icons.url": "{string}",
  "extensions.ribbons.tabs.customMobileRibbonGroups.controls.label": "{string}",
  "extensions.ribbons.tabs.groups.icons.url": "{string}",
  "extensions.ribbons.tabs.groups.label": "{string}",
  "extensions.ribbons.tabs.groups.controls.icons.url": "{string}",
  "extensions.ribbons.tabs.groups.controls.label": "{string}",
  "extensions.ribbons.tabs.groups.controls.supertip.title": "{string}",
  "extensions.ribbons.tabs.groups.controls.supertip.description": "{string}",
  "extensions.ribbons.tabs.groups.controls.items.icons.url": "{string}",
  "extensions.ribbons.tabs.groups.controls.items.label": "{string}",
  "extensions.ribbons.tabs.groups.controls.items.supertip.title": "{string}",
  "extensions.ribbons.tabs.groups.controls.items.supertip.description": "{string}",
  "extensions.ribbons.fixedControls.label": "{string}",
  "extensions.ribbons.fixedControls.supertip.title": "{string}",
  "extensions.ribbons.fixedControls.supertip.description": "{string}",
  "extensions.ribbons.spamPreProcessingDialog.title": "{string}",
  "extensions.ribbons.spamPreProcessingDialog.description": "{string}",
  "extensions.ribbons.spamPreProcessingDialog.spamFreeTextSectionTitle": "{string}",
  "extensions.ribbons.spamPreProcessingDialog.spamReportingOptions.title": "{string}",
  "extensions.ribbons.spamPreProcessingDialog.spamReportingOptions.options": "{string}",
  "extensions.ribbons.spamPreProcessingDialog.spamMoreInfo.text": "{string}",
  "extensions.ribbons.spamPreProcessingDialog.spamMoreInfo.url": "{string}",
  "extensions.runtimes.code.page": "{string}",
  "extensions.runtimes.code.script": "{string}",
  "extensions.runtimes.customFunctions.metadataUrl": "{string}",
  "extensions.runtimes.customFunctions.functions.name": "{string}",
  "extensions.runtimes.customFunctions.functions.description": "{string}",
  "extensions.runtimes.customFunctions.functions.parameters.name": "{string}",
  "extensions.runtimes.customFunctions.functions.parameters.description": "{string}",
  "extensions.runtimes.customFunctions.namespace.name": "{string}",
  "extensions.runtimes.customFunctions.enums.values.name": "{string}",
  "extensions.runtimes.customFunctions.enums.values.tooltip": "{string}",
  "extensions.keyboardShortcuts.shortcuts.key.default": "{string}",
  "extensions.keyboardShortcuts.shortcuts.key.mac": "{string}",
  "extensions.keyboardShortcuts.shortcuts.key.web": "{string}",
  "extensions.keyboardShortcuts.shortcuts.key.windows": "{string}",
  "extensions.runtimes.actions.displayName": "{string}",
  "extensions.alternates.alternateIcons.icon.url": "{string}",
  "extensions.alternates.alternateIcons.highResolutionIcon.url": "{string}",
  "copilotAgents.customEngineAgents.disclaimer.text": "{string}",
  "extensions.getStartedMessages.title": "{string}",
  "extensions.getStartedMessages.description": "{string}",
  "extensions.getStartedMessages.learnMoreUrl": "{string}",
  "extensions.contentRuntimes.code.page": "{string}",
  "extensions.contextMenus.menus.controls.icons.url": "{string}",
  "extensions.contextMenus.menus.controls.label": "{string}",
  "extensions.contextMenus.menus.controls.supertip.title": "{string}",
  "extensions.contextMenus.menus.controls.supertip.description": "{string}",
  "extensions.contextMenus.menus.controls.items.icons.url": "{string}",
  "extensions.contextMenus.menus.controls.items.label": "{string}",
  "extensions.contextMenus.menus.controls.items.supertip.title": "{string}",
  "extensions.contextMenus.menus.controls.items.supertip.description": "{string}"
}
```

```json
{
  "$schema": "http://json-schema.org/draft-04/schema#",
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "$schema": {
      "type": "string",
      "format": "uri"
    },
    "name.short": {
      "type": "string",
      "maxLength": 30,
      "$ref": "#/definitions/nonEmptyString"
    },
    "name.full": {
      "type": "string",
      "maxLength": 100,
      "$ref": "#/definitions/nonEmptyString"
    },
    "description.short": {
      "type": "string",
      "maxLength": 80,
      "$ref": "#/definitions/nonEmptyString"
    },
    "description.full": {
      "type": "string",
      "maxLength": 4000,
      "$ref": "#/definitions/nonEmptyString"
    },
    "localizationKeys": {
      "type": "object",
      "patternProperties": {
        "^\\[\\[[a-zA-Z_][a-zA-Z0-9_]*\\]\\]$": {
          "type": "string"
        }
      }
    }
  },
  "patternProperties": {
    "^staticTabs\\[([0-9]|1[0-5])\\]\\.name$": {
      "type": "string",
      "maxLength": 128
    },
    "^bots\\[0\\]\\.commandLists\\[[0-2]\\]\\.commands\\[([0-9]|1[0-1])\\]\\.title$": {
      "type": "string",
      "maxLength": 128
    },
    "^bots\\[0\\]\\.commandLists\\[[0-2]\\]\\.commands\\[([0-9]|1[0-1])\\]\\.description$": {
      "type": "string",
      "maxLength": 4000
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.title$": {
      "type": "string",
      "maxLength": 32
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.description$": {
      "type": "string",
      "maxLength": 128
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.title$": {
      "type": "string",
      "maxLength": 32
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.description$": {
      "type": "string",
      "maxLength": 128
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.value$": {
      "type": "string",
      "maxLength": 512
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.choices\\[[0-9]\\]\\.title$": {
      "type": "string",
      "maxLength": 128
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.samplePrompts\\[[0-4]\\]\\.text$": {
      "type": "string",
      "maxLength": 128
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.taskInfo\\.title$": {
      "type": "string",
      "maxLength": 64
    },
    "^activities.activityTypes\\[\\b([0-9]|[1-8][0-9]|9[0-9]|1[01][0-9]|12[0-7])\\b]\\.description$": {
      "type": "string",
      "maxLength": 128
    },
    "^activities.activityTypes\\[\\b([0-9]|[1-8][0-9]|9[0-9]|1[01][0-9]|12[0-7])\\b]\\.templateText$": {
      "type": "string",
      "maxLength": 128
    },
    "^meetingExtensionDefinition.scenes\\[[0-9]\\]\\.name$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.audienceClaimUrl$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.label$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.customMobileRibbonGroups\\[[0-9]\\]\\.label$": {
      "type": "string",
      "maxLength": 32
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.customMobileRibbonGroups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.icons\\[[0-8]\\]\\.url$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.customMobileRibbonGroups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.label$": {
      "type": "string",
      "maxLength": 32
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.icons\\[[0-2]\\]\\.url$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.label$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.icons\\[[0-2]\\]\\.url$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.label$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.supertip\\.title$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.supertip\\.description$": {
      "type": "string",
      "maxLength": 250
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.items\\[[1]?[0-9]\\]\\.icons\\[[0-2]\\]\\.url$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.items\\[[1]?[0-9]\\]\\.label$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.items\\[[1]?[0-9]\\]\\.supertip\\.title$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.items\\[[1]?[0-9]\\]\\.supertip\\.description$": {
      "type": "string",
      "maxLength": 250
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.fixedControls\\[[1]?[0-9]\\]\\.label$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.fixedControls\\[[1]?[0-9]\\]\\.supertip\\.title$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.fixedControls\\[[1]?[0-9]\\]\\.supertip\\.description$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.spamPreProcessingDialog\\.title$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.spamPreProcessingDialog\\.description$": {
      "type": "string",
      "maxLength": 250
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.spamPreProcessingDialog\\.spamFreeTextSectionTitle$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.spamPreProcessingDialog\\.spamReportingOptions\\.title$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.spamPreProcessingDialog\\.spamReportingOptions\\.options\\[[0-4]\\]$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.spamPreProcessingDialog\\.spamMoreInfo\\.text$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.spamPreProcessingDialog\\.spamMoreInfo\\.url$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.code\\.page$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.code\\.script$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.customFunctions\\.metadataUrl$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.customFunctions\\.functions\\[[0-9]\\]\\.name$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.customFunctions\\.functions\\[[0-9]\\]\\.description$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.customFunctions\\.functions\\[[0-9]\\]\\.parameters\\[[0-9]\\]\\.name$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.customFunctions\\.functions\\[[0-9]\\]\\.parameters\\[[0-9]\\]\\.description$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.customFunctions\\.namespace\\.name$": {
      "type": "string",
      "maxLength": 32
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.customFunctions\\.enums\\[[0-9]\\]\\.values\\[[0-9]\\]\\.name$": {
      "type": "string",
      "maxLength": 256
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.customFunctions\\.enums\\[[0-9]\\]\\.values\\[[0-9]\\]\\.tooltip$": {
      "type": "string",
      "maxLength": 256
    },
    "^extensions\\[[0]\\]\\.keyboardShortcuts\\[[0-9]\\]\\.shortcuts\\[[0-9]\\]\\.key\\.default$": {
      "type": "string",
      "maxLength": 32
    },
    "^extensions\\[[0]\\]\\.keyboardShortcuts\\[[0-9]\\]\\.shortcuts\\[[0-9]\\]\\.key\\.mac$": {
      "type": "string",
      "maxLength": 32
    },
    "^extensions\\[[0]\\]\\.keyboardShortcuts\\[[0-9]\\]\\.shortcuts\\[[0-9]\\]\\.key\\.web$": {
      "type": "string",
      "maxLength": 32
    },
    "^extensions\\[[0]\\]\\.keyboardShortcuts\\[[0-9]\\]\\.shortcuts\\[[0-9]\\]\\.key\\.windows$": {
      "type": "string",
      "maxLength": 32
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.actions\\[[1]?[0-9]\\]\\.displayName$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.alternates\\[[0-9]\\]\\.alternateIcons\\.icon\\.url$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.alternates\\[[0-9]\\]\\.alternateIcons\\.highResolutionIcon\\.url$": {
      "type": "string",
      "maxLength": 2048
    },
    "^copilotAgents.customEngineAgents\\[0\\]\\.disclaimer.text$": {
      "type": "string",
      "maxLength": 500
    },
    "^extensions\\[[0]\\]\\.getStartedMessages\\[[0-2]\\]\\.title$": {
      "type": "string",
      "maxLength": 125
    },
    "^extensions\\[[0]\\]\\.getStartedMessages\\[[0-2]\\]\\.description$": {
      "type": "string",
      "maxLength": 250
    },
    "^extensions\\[[0]\\]\\.getStartedMessages\\[[0-2]\\]\\.learnMoreUrl$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.contentRuntimes\\[[1]?[0-9]\\]\\.code\\.page$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.contextMenus\\[[0-9]\\]\\.menus\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.icons\\[[0-2]\\]\\.url": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.contextMenus\\[[0-9]\\]\\.menus\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.label": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.contextMenus\\[[0-9]\\]\\.menus\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.supertip\\.title": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.contextMenus\\[[0-9]\\]\\.menus\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.supertip\\.description": {
      "type": "string",
      "maxLength": 250
    },
    "^extensions\\[[0]\\]\\.contextMenus\\[[0-9]\\]\\.menus\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.items\\[[1]?[0-9]\\]\\.icons\\[[0-2]\\]\\.url": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.contextMenus\\[[0-9]\\]\\.menus\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.items\\[[1]?[0-9]\\]\\.label": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.contextMenus\\[[0-9]\\]\\.menus\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.items\\[[1]?[0-9]\\]\\.supertip\\.title": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.contextMenus\\[[0-9]\\]\\.menus\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.items\\[[1]?[0-9]\\]\\.supertip\\.description": {
      "type": "string",
      "maxLength": 250
    }
  },
  "required": [
    "name.short",
    "description.short",
    "description.full"
  ],
  "definitions": {
    "nonEmptyString": {
      "type": "string",
      "pattern": "^(?![nN][uU][lL]{2}$)\\s*\\S.*"
    }
  }
}
```

- [Syntax](#tabpanel_6_syntax)
- [Schema](#tabpanel_6_schema)

```json
{
  "$schema": "{string}",
  "name.short": "{string}",
  "name.full": "{string}",
  "description.short": "{string}",
  "description.full": "{string}",
  "localizationKeys": {
    "^\[\[[a-zA-Z_][a-zA-Z0-9_]*\]\]$": "{string}"
  },
  "staticTabs.name": "{string}",
  "bots.commandLists.commands.title": "{string}",
  "bots.commandLists.commands.description": "{string}",
  "composeExtensions.commands.title": "{string}",
  "composeExtensions.commands.description": "{string}",
  "composeExtensions.commands.parameters.title": "{string}",
  "composeExtensions.commands.parameters.description": "{string}",
  "composeExtensions.commands.parameters.value": "{string}",
  "composeExtensions.commands.parameters.choices.title": "{string}",
  "composeExtensions.commands.samplePrompts.text": "{string}",
  "composeExtensions.commands.taskInfo.title": "{string}",
  "activities.activityTypes.description": "{string}",
  "activities.activityTypes.templateText": "{string}",
  "meetingExtensionDefinition.scenes.name": "{string}",
  "extensions.audienceClaimUrl": "{string}",
  "extensions.ribbons.tabs.label": "{string}",
  "extensions.ribbons.tabs.customMobileRibbonGroups.label": "{string}",
  "extensions.ribbons.tabs.customMobileRibbonGroups.controls.icons.url": "{string}",
  "extensions.ribbons.tabs.customMobileRibbonGroups.controls.label": "{string}",
  "extensions.ribbons.tabs.groups.icons.url": "{string}",
  "extensions.ribbons.tabs.groups.label": "{string}",
  "extensions.ribbons.tabs.groups.controls.icons.url": "{string}",
  "extensions.ribbons.tabs.groups.controls.label": "{string}",
  "extensions.ribbons.tabs.groups.controls.supertip.title": "{string}",
  "extensions.ribbons.tabs.groups.controls.supertip.description": "{string}",
  "extensions.ribbons.tabs.groups.controls.items.icons.url": "{string}",
  "extensions.ribbons.tabs.groups.controls.items.label": "{string}",
  "extensions.ribbons.tabs.groups.controls.items.supertip.title": "{string}",
  "extensions.ribbons.tabs.groups.controls.items.supertip.description": "{string}",
  "extensions.ribbons.fixedControls.label": "{string}",
  "extensions.ribbons.fixedControls.supertip.title": "{string}",
  "extensions.ribbons.fixedControls.supertip.description": "{string}",
  "extensions.ribbons.spamPreProcessingDialog.title": "{string}",
  "extensions.ribbons.spamPreProcessingDialog.description": "{string}",
  "extensions.ribbons.spamPreProcessingDialog.spamFreeTextSectionTitle": "{string}",
  "extensions.ribbons.spamPreProcessingDialog.spamReportingOptions.title": "{string}",
  "extensions.ribbons.spamPreProcessingDialog.spamReportingOptions.options": "{string}",
  "extensions.ribbons.spamPreProcessingDialog.spamMoreInfo.text": "{string}",
  "extensions.ribbons.spamPreProcessingDialog.spamMoreInfo.url": "{string}",
  "extensions.runtimes.code.page": "{string}",
  "extensions.runtimes.code.script": "{string}",
  "extensions.runtimes.customFunctions.metadataUrl": "{string}",
  "extensions.runtimes.customFunctions.functions.name": "{string}",
  "extensions.runtimes.customFunctions.functions.description": "{string}",
  "extensions.runtimes.customFunctions.functions.parameters.name": "{string}",
  "extensions.runtimes.customFunctions.functions.parameters.description": "{string}",
  "extensions.runtimes.customFunctions.namespace.name": "{string}",
  "extensions.keyboardShortcuts.shortcuts.key.default": "{string}",
  "extensions.keyboardShortcuts.shortcuts.key.mac": "{string}",
  "extensions.keyboardShortcuts.shortcuts.key.web": "{string}",
  "extensions.keyboardShortcuts.shortcuts.key.windows": "{string}",
  "extensions.runtimes.actions.displayName": "{string}",
  "extensions.alternates.alternateIcons.icon.url": "{string}",
  "extensions.alternates.alternateIcons.highResolutionIcon.url": "{string}",
  "copilotAgents.customEngineAgents.disclaimer.text": "{string}",
  "extensions.getStartedMessages.title": "{string}",
  "extensions.getStartedMessages.description": "{string}",
  "extensions.getStartedMessages.learnMoreUrl": "{string}",
  "extensions.contentRuntimes.code.page": "{string}",
  "extensions.contextMenus.menus.controls.icons.url": "{string}",
  "extensions.contextMenus.menus.controls.label": "{string}",
  "extensions.contextMenus.menus.controls.supertip.title": "{string}",
  "extensions.contextMenus.menus.controls.supertip.description": "{string}",
  "extensions.contextMenus.menus.controls.items.icons.url": "{string}",
  "extensions.contextMenus.menus.controls.items.label": "{string}",
  "extensions.contextMenus.menus.controls.items.supertip.title": "{string}",
  "extensions.contextMenus.menus.controls.items.supertip.description": "{string}"
}
```

```json
{
  "$schema": "http://json-schema.org/draft-04/schema#",
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "$schema": {
      "type": "string",
      "format": "uri"
    },
    "name.short": {
      "type": "string",
      "maxLength": 30,
      "$ref": "#/definitions/nonEmptyString"
    },
    "name.full": {
      "type": "string",
      "maxLength": 100,
      "$ref": "#/definitions/nonEmptyString"
    },
    "description.short": {
      "type": "string",
      "maxLength": 80,
      "$ref": "#/definitions/nonEmptyString"
    },
    "description.full": {
      "type": "string",
      "maxLength": 4000,
      "$ref": "#/definitions/nonEmptyString"
    },
    "localizationKeys": {
      "type": "object",
      "patternProperties": {
        "^\\[\\[[a-zA-Z_][a-zA-Z0-9_]*\\]\\]$": {
          "type": "string"
        }
      }
    }
  },
  "patternProperties": {
    "^staticTabs\\[([0-9]|1[0-5])\\]\\.name$": {
      "type": "string",
      "maxLength": 128
    },
    "^bots\\[0\\]\\.commandLists\\[[0-2]\\]\\.commands\\[([0-9]|1[0-1])\\]\\.title$": {
      "type": "string",
      "maxLength": 128
    },
    "^bots\\[0\\]\\.commandLists\\[[0-2]\\]\\.commands\\[([0-9]|1[0-1])\\]\\.description$": {
      "type": "string",
      "maxLength": 4000
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.title$": {
      "type": "string",
      "maxLength": 32
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.description$": {
      "type": "string",
      "maxLength": 128
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.title$": {
      "type": "string",
      "maxLength": 32
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.description$": {
      "type": "string",
      "maxLength": 128
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.value$": {
      "type": "string",
      "maxLength": 512
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.choices\\[[0-9]\\]\\.title$": {
      "type": "string",
      "maxLength": 128
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.samplePrompts\\[[0-4]\\]\\.text$": {
      "type": "string",
      "maxLength": 128
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.taskInfo\\.title$": {
      "type": "string",
      "maxLength": 64
    },
    "^activities.activityTypes\\[\\b([0-9]|[1-8][0-9]|9[0-9]|1[01][0-9]|12[0-7])\\b]\\.description$": {
      "type": "string",
      "maxLength": 128
    },
    "^activities.activityTypes\\[\\b([0-9]|[1-8][0-9]|9[0-9]|1[01][0-9]|12[0-7])\\b]\\.templateText$": {
      "type": "string",
      "maxLength": 128
    },
    "^meetingExtensionDefinition.scenes\\[[0-9]\\]\\.name$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.audienceClaimUrl$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.label$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.customMobileRibbonGroups\\[[0-9]\\]\\.label$": {
      "type": "string",
      "maxLength": 32
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.customMobileRibbonGroups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.icons\\[[0-8]\\]\\.url$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.customMobileRibbonGroups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.label$": {
      "type": "string",
      "maxLength": 32
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.icons\\[[0-2]\\]\\.url$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.label$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.icons\\[[0-2]\\]\\.url$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.label$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.supertip\\.title$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.supertip\\.description$": {
      "type": "string",
      "maxLength": 250
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.items\\[[1]?[0-9]\\]\\.icons\\[[0-2]\\]\\.url$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.items\\[[1]?[0-9]\\]\\.label$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.items\\[[1]?[0-9]\\]\\.supertip\\.title$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.items\\[[1]?[0-9]\\]\\.supertip\\.description$": {
      "type": "string",
      "maxLength": 250
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.fixedControls\\[[1]?[0-9]\\]\\.label$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.fixedControls\\[[1]?[0-9]\\]\\.supertip\\.title$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.fixedControls\\[[1]?[0-9]\\]\\.supertip\\.description$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.spamPreProcessingDialog\\.title$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.spamPreProcessingDialog\\.description$": {
      "type": "string",
      "maxLength": 250
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.spamPreProcessingDialog\\.spamFreeTextSectionTitle$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.spamPreProcessingDialog\\.spamReportingOptions\\.title$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.spamPreProcessingDialog\\.spamReportingOptions\\.options\\[[0-4]\\]$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.spamPreProcessingDialog\\.spamMoreInfo\\.text$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.spamPreProcessingDialog\\.spamMoreInfo\\.url$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.code\\.page$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.code\\.script$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.customFunctions\\.metadataUrl$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.customFunctions\\.functions\\[[0-9]\\]\\.name$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.customFunctions\\.functions\\[[0-9]\\]\\.description$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.customFunctions\\.functions\\[[0-9]\\]\\.parameters\\[[0-9]\\]\\.name$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.customFunctions\\.functions\\[[0-9]\\]\\.parameters\\[[0-9]\\]\\.description$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.customFunctions\\.namespace\\.name$": {
      "type": "string",
      "maxLength": 32
    },
    "^extensions\\[[0]\\]\\.keyboardShortcuts\\[[0-9]\\]\\.shortcuts\\[[0-9]\\]\\.key\\.default$": {
      "type": "string",
      "maxLength": 32
    },
    "^extensions\\[[0]\\]\\.keyboardShortcuts\\[[0-9]\\]\\.shortcuts\\[[0-9]\\]\\.key\\.mac$": {
      "type": "string",
      "maxLength": 32
    },
    "^extensions\\[[0]\\]\\.keyboardShortcuts\\[[0-9]\\]\\.shortcuts\\[[0-9]\\]\\.key\\.web$": {
      "type": "string",
      "maxLength": 32
    },
    "^extensions\\[[0]\\]\\.keyboardShortcuts\\[[0-9]\\]\\.shortcuts\\[[0-9]\\]\\.key\\.windows$": {
      "type": "string",
      "maxLength": 32
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.actions\\[[1]?[0-9]\\]\\.displayName$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.alternates\\[[0-9]\\]\\.alternateIcons\\.icon\\.url$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.alternates\\[[0-9]\\]\\.alternateIcons\\.highResolutionIcon\\.url$": {
      "type": "string",
      "maxLength": 2048
    },
    "^copilotAgents.customEngineAgents\\[0\\]\\.disclaimer.text$": {
      "type": "string",
      "maxLength": 500
    },
    "^extensions\\[[0]\\]\\.getStartedMessages\\[[0-2]\\]\\.title$": {
      "type": "string",
      "maxLength": 125
    },
    "^extensions\\[[0]\\]\\.getStartedMessages\\[[0-2]\\]\\.description$": {
      "type": "string",
      "maxLength": 250
    },
    "^extensions\\[[0]\\]\\.getStartedMessages\\[[0-2]\\]\\.learnMoreUrl$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.contentRuntimes\\[[1]?[0-9]\\]\\.code\\.page$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.contextMenus\\[[0-9]\\]\\.menus\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.icons\\[[0-2]\\]\\.url": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.contextMenus\\[[0-9]\\]\\.menus\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.label": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.contextMenus\\[[0-9]\\]\\.menus\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.supertip\\.title": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.contextMenus\\[[0-9]\\]\\.menus\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.supertip\\.description": {
      "type": "string",
      "maxLength": 250
    },
    "^extensions\\[[0]\\]\\.contextMenus\\[[0-9]\\]\\.menus\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.items\\[[1]?[0-9]\\]\\.icons\\[[0-2]\\]\\.url": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.contextMenus\\[[0-9]\\]\\.menus\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.items\\[[1]?[0-9]\\]\\.label": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.contextMenus\\[[0-9]\\]\\.menus\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.items\\[[1]?[0-9]\\]\\.supertip\\.title": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.contextMenus\\[[0-9]\\]\\.menus\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.items\\[[1]?[0-9]\\]\\.supertip\\.description": {
      "type": "string",
      "maxLength": 250
    }
  },
  "required": [
    "name.short",
    "description.short",
    "description.full"
  ],
  "definitions": {
    "nonEmptyString": {
      "type": "string",
      "pattern": "^(?![nN][uU][lL]{2}$)\\s*\\S.*"
    }
  }
}
```

- [Syntax](#tabpanel_7_syntax)
- [Schema](#tabpanel_7_schema)

```json
{
  "$schema": "{string}",
  "name.short": "{string}",
  "name.full": "{string}",
  "description.short": "{string}",
  "description.full": "{string}",
  "localizationKeys": {
    "^\[\[[a-zA-Z_][a-zA-Z0-9_]*\]\]$": "{string}"
  },
  "staticTabs.name": "{string}",
  "bots.commandLists.commands.title": "{string}",
  "bots.commandLists.commands.description": "{string}",
  "composeExtensions.commands.title": "{string}",
  "composeExtensions.commands.description": "{string}",
  "composeExtensions.commands.parameters.title": "{string}",
  "composeExtensions.commands.parameters.description": "{string}",
  "composeExtensions.commands.parameters.value": "{string}",
  "composeExtensions.commands.parameters.choices.title": "{string}",
  "composeExtensions.commands.samplePrompts.text": "{string}",
  "composeExtensions.commands.taskInfo.title": "{string}",
  "activities.activityTypes.description": "{string}",
  "activities.activityTypes.templateText": "{string}",
  "meetingExtensionDefinition.scenes.name": "{string}",
  "extensions.audienceClaimUrl": "{string}",
  "extensions.ribbons.tabs.label": "{string}",
  "extensions.ribbons.tabs.customMobileRibbonGroups.label": "{string}",
  "extensions.ribbons.tabs.customMobileRibbonGroups.controls.icons.url": "{string}",
  "extensions.ribbons.tabs.customMobileRibbonGroups.controls.label": "{string}",
  "extensions.ribbons.tabs.groups.icons.url": "{string}",
  "extensions.ribbons.tabs.groups.label": "{string}",
  "extensions.ribbons.tabs.groups.controls.icons.url": "{string}",
  "extensions.ribbons.tabs.groups.controls.label": "{string}",
  "extensions.ribbons.tabs.groups.controls.supertip.title": "{string}",
  "extensions.ribbons.tabs.groups.controls.supertip.description": "{string}",
  "extensions.ribbons.tabs.groups.controls.items.icons.url": "{string}",
  "extensions.ribbons.tabs.groups.controls.items.label": "{string}",
  "extensions.ribbons.tabs.groups.controls.items.supertip.title": "{string}",
  "extensions.ribbons.tabs.groups.controls.items.supertip.description": "{string}",
  "extensions.ribbons.fixedControls.label": "{string}",
  "extensions.ribbons.fixedControls.supertip.title": "{string}",
  "extensions.ribbons.fixedControls.supertip.description": "{string}",
  "extensions.ribbons.spamPreProcessingDialog.title": "{string}",
  "extensions.ribbons.spamPreProcessingDialog.description": "{string}",
  "extensions.ribbons.spamPreProcessingDialog.spamFreeTextSectionTitle": "{string}",
  "extensions.ribbons.spamPreProcessingDialog.spamReportingOptions.title": "{string}",
  "extensions.ribbons.spamPreProcessingDialog.spamReportingOptions.options": "{string}",
  "extensions.ribbons.spamPreProcessingDialog.spamMoreInfo.text": "{string}",
  "extensions.ribbons.spamPreProcessingDialog.spamMoreInfo.url": "{string}",
  "extensions.runtimes.code.page": "{string}",
  "extensions.runtimes.code.script": "{string}",
  "extensions.runtimes.customFunctions.functions.name": "{string}",
  "extensions.runtimes.customFunctions.functions.description": "{string}",
  "extensions.runtimes.customFunctions.functions.parameters.name": "{string}",
  "extensions.runtimes.customFunctions.functions.parameters.description": "{string}",
  "extensions.runtimes.customFunctions.namespace.name": "{string}",
  "extensions.keyboardShortcuts.shortcuts.key.default": "{string}",
  "extensions.keyboardShortcuts.shortcuts.key.mac": "{string}",
  "extensions.keyboardShortcuts.shortcuts.key.web": "{string}",
  "extensions.keyboardShortcuts.shortcuts.key.windows": "{string}",
  "extensions.runtimes.actions.displayName": "{string}",
  "extensions.alternates.alternateIcons.icon.url": "{string}",
  "extensions.alternates.alternateIcons.highResolutionIcon.url": "{string}",
  "copilotAgents.customEngineAgents.disclaimer.text": "{string}",
  "extensions.getStartedMessages.title": "{string}",
  "extensions.getStartedMessages.description": "{string}",
  "extensions.getStartedMessages.learnMoreUrl": "{string}",
  "extensions.contentRuntimes.code.page": "{string}",
  "extensions.contextMenus.menus.controls.icons.url": "{string}",
  "extensions.contextMenus.menus.controls.label": "{string}",
  "extensions.contextMenus.menus.controls.supertip.title": "{string}",
  "extensions.contextMenus.menus.controls.supertip.description": "{string}",
  "extensions.contextMenus.menus.controls.items.icons.url": "{string}",
  "extensions.contextMenus.menus.controls.items.label": "{string}",
  "extensions.contextMenus.menus.controls.items.supertip.title": "{string}",
  "extensions.contextMenus.menus.controls.items.supertip.description": "{string}"
}
```

```json
{
  "$schema": "http://json-schema.org/draft-04/schema#",
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "$schema": {
      "type": "string",
      "format": "uri"
    },
    "name.short": {
      "type": "string",
      "maxLength": 30,
      "$ref": "#/definitions/nonEmptyString"
    },
    "name.full": {
      "type": "string",
      "maxLength": 100,
      "$ref": "#/definitions/nonEmptyString"
    },
    "description.short": {
      "type": "string",
      "maxLength": 80,
      "$ref": "#/definitions/nonEmptyString"
    },
    "description.full": {
      "type": "string",
      "maxLength": 4000,
      "$ref": "#/definitions/nonEmptyString"
    },
    "localizationKeys": {
      "type": "object",
      "patternProperties": {
        "^\\[\\[[a-zA-Z_][a-zA-Z0-9_]*\\]\\]$": {
          "type": "string"
        }
      }
    }
  },
  "patternProperties": {
    "^staticTabs\\[([0-9]|1[0-5])\\]\\.name$": {
      "type": "string",
      "maxLength": 128
    },
    "^bots\\[0\\]\\.commandLists\\[[0-2]\\]\\.commands\\[[0-9]\\]\\.title$": {
      "type": "string",
      "maxLength": 128
    },
    "^bots\\[0\\]\\.commandLists\\[[0-2]\\]\\.commands\\[[0-9]\\]\\.description$": {
      "type": "string",
      "maxLength": 4000
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.title$": {
      "type": "string",
      "maxLength": 32
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.description$": {
      "type": "string",
      "maxLength": 128
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.title$": {
      "type": "string",
      "maxLength": 32
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.description$": {
      "type": "string",
      "maxLength": 128
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.value$": {
      "type": "string",
      "maxLength": 512
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.choices\\[[0-9]\\]\\.title$": {
      "type": "string",
      "maxLength": 128
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.samplePrompts\\[[0-4]\\]\\.text$": {
      "type": "string",
      "maxLength": 128
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.taskInfo\\.title$": {
      "type": "string",
      "maxLength": 64
    },
    "^activities.activityTypes\\[\\b([0-9]|[1-8][0-9]|9[0-9]|1[01][0-9]|12[0-7])\\b]\\.description$": {
      "type": "string",
      "maxLength": 128
    },
    "^activities.activityTypes\\[\\b([0-9]|[1-8][0-9]|9[0-9]|1[01][0-9]|12[0-7])\\b]\\.templateText$": {
      "type": "string",
      "maxLength": 128
    },
    "^meetingExtensionDefinition.scenes\\[[0-9]\\]\\.name$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.audienceClaimUrl$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.label$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.customMobileRibbonGroups\\[[0-9]\\]\\.label$": {
      "type": "string",
      "maxLength": 32
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.customMobileRibbonGroups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.icons\\[[0-8]\\]\\.url$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.customMobileRibbonGroups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.label$": {
      "type": "string",
      "maxLength": 32
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.icons\\[[0-2]\\]\\.url$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.label$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.icons\\[[0-2]\\]\\.url$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.label$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.supertip\\.title$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.supertip\\.description$": {
      "type": "string",
      "maxLength": 250
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.items\\[[1]?[0-9]\\]\\.icons\\[[0-2]\\]\\.url$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.items\\[[1]?[0-9]\\]\\.label$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.items\\[[1]?[0-9]\\]\\.supertip\\.title$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.items\\[[1]?[0-9]\\]\\.supertip\\.description$": {
      "type": "string",
      "maxLength": 250
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.fixedControls\\[[1]?[0-9]\\]\\.label$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.fixedControls\\[[1]?[0-9]\\]\\.supertip\\.title$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.fixedControls\\[[1]?[0-9]\\]\\.supertip\\.description$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.spamPreProcessingDialog\\.title$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.spamPreProcessingDialog\\.description$": {
      "type": "string",
      "maxLength": 250
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.spamPreProcessingDialog\\.spamFreeTextSectionTitle$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.spamPreProcessingDialog\\.spamReportingOptions\\.title$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.spamPreProcessingDialog\\.spamReportingOptions\\.options\\[[0-4]\\]$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.spamPreProcessingDialog\\.spamMoreInfo\\.text$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.spamPreProcessingDialog\\.spamMoreInfo\\.url$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.code\\.page$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.code\\.script$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.customFunctions\\.functions\\[[0-9]\\]\\.name$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.customFunctions\\.functions\\[[0-9]\\]\\.description$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.customFunctions\\.functions\\[[0-9]\\]\\.parameters\\[[0-9]\\]\\.name$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.customFunctions\\.functions\\[[0-9]\\]\\.parameters\\[[0-9]\\]\\.description$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.customFunctions\\.namespace\\.name$": {
      "type": "string",
      "maxLength": 32
    },
    "^extensions\\[[0]\\]\\.keyboardShortcuts\\[[0-9]\\]\\.shortcuts\\[[0-9]\\]\\.key\\.default$": {
      "type": "string",
      "maxLength": 32
    },
    "^extensions\\[[0]\\]\\.keyboardShortcuts\\[[0-9]\\]\\.shortcuts\\[[0-9]\\]\\.key\\.mac$": {
      "type": "string",
      "maxLength": 32
    },
    "^extensions\\[[0]\\]\\.keyboardShortcuts\\[[0-9]\\]\\.shortcuts\\[[0-9]\\]\\.key\\.web$": {
      "type": "string",
      "maxLength": 32
    },
    "^extensions\\[[0]\\]\\.keyboardShortcuts\\[[0-9]\\]\\.shortcuts\\[[0-9]\\]\\.key\\.windows$": {
      "type": "string",
      "maxLength": 32
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.actions\\[[1]?[0-9]\\]\\.displayName$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.alternates\\[[0-9]\\]\\.alternateIcons\\.icon\\.url$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.alternates\\[[0-9]\\]\\.alternateIcons\\.highResolutionIcon\\.url$": {
      "type": "string",
      "maxLength": 2048
    },
    "^copilotAgents.customEngineAgents\\[0\\]\\.disclaimer.text$": {
      "type": "string",
      "maxLength": 500
    },
    "^extensions\\[[0]\\]\\.getStartedMessages\\[[0-2]\\]\\.title$": {
      "type": "string",
      "maxLength": 125
    },
    "^extensions\\[[0]\\]\\.getStartedMessages\\[[0-2]\\]\\.description$": {
      "type": "string",
      "maxLength": 250
    },
    "^extensions\\[[0]\\]\\.getStartedMessages\\[[0-2]\\]\\.learnMoreUrl$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.contentRuntimes\\[[1]?[0-9]\\]\\.code\\.page$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.contextMenus\\[[0-9]\\]\\.menus\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.icons\\[[0-2]\\]\\.url": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.contextMenus\\[[0-9]\\]\\.menus\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.label": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.contextMenus\\[[0-9]\\]\\.menus\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.supertip\\.title": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.contextMenus\\[[0-9]\\]\\.menus\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.supertip\\.description": {
      "type": "string",
      "maxLength": 250
    },
    "^extensions\\[[0]\\]\\.contextMenus\\[[0-9]\\]\\.menus\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.items\\[[1]?[0-9]\\]\\.icons\\[[0-2]\\]\\.url": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.contextMenus\\[[0-9]\\]\\.menus\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.items\\[[1]?[0-9]\\]\\.label": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.contextMenus\\[[0-9]\\]\\.menus\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.items\\[[1]?[0-9]\\]\\.supertip\\.title": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.contextMenus\\[[0-9]\\]\\.menus\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.items\\[[1]?[0-9]\\]\\.supertip\\.description": {
      "type": "string",
      "maxLength": 250
    }
  },
  "required": [
    "name.short",
    "description.short",
    "description.full"
  ],
  "definitions": {
    "nonEmptyString": {
      "type": "string",
      "pattern": "^(?![nN][uU][lL]{2}$)\\s*\\S.*"
    }
  }
}
```

- [Syntax](#tabpanel_8_syntax)
- [Schema](#tabpanel_8_schema)

```json
{
  "$schema": "{string}",
  "name.short": "{string}",
  "name.full": "{string}",
  "description.short": "{string}",
  "description.full": "{string}",
  "localizationKeys": {
    "^\[\[[a-zA-Z_][a-zA-Z0-9_]*\]\]$": "{string}"
  },
  "staticTabs.name": "{string}",
  "bots.commandLists.commands.title": "{string}",
  "bots.commandLists.commands.description": "{string}",
  "composeExtensions.commands.title": "{string}",
  "composeExtensions.commands.description": "{string}",
  "composeExtensions.commands.parameters.title": "{string}",
  "composeExtensions.commands.parameters.description": "{string}",
  "composeExtensions.commands.parameters.value": "{string}",
  "composeExtensions.commands.parameters.choices.title": "{string}",
  "composeExtensions.commands.samplePrompts.text": "{string}",
  "composeExtensions.commands.taskInfo.title": "{string}",
  "activities.activityTypes.description": "{string}",
  "activities.activityTypes.templateText": "{string}",
  "meetingExtensionDefinition.scenes.name": "{string}",
  "extensions.audienceClaimUrl": "{string}",
  "extensions.ribbons.tabs.label": "{string}",
  "extensions.ribbons.tabs.customMobileRibbonGroups.label": "{string}",
  "extensions.ribbons.tabs.customMobileRibbonGroups.controls.icons.url": "{string}",
  "extensions.ribbons.tabs.customMobileRibbonGroups.controls.label": "{string}",
  "extensions.ribbons.tabs.groups.icons.url": "{string}",
  "extensions.ribbons.tabs.groups.label": "{string}",
  "extensions.ribbons.tabs.groups.controls.icons.url": "{string}",
  "extensions.ribbons.tabs.groups.controls.label": "{string}",
  "extensions.ribbons.tabs.groups.controls.supertip.title": "{string}",
  "extensions.ribbons.tabs.groups.controls.supertip.description": "{string}",
  "extensions.ribbons.tabs.groups.controls.items.icons.url": "{string}",
  "extensions.ribbons.tabs.groups.controls.items.label": "{string}",
  "extensions.ribbons.tabs.groups.controls.items.supertip.title": "{string}",
  "extensions.ribbons.tabs.groups.controls.items.supertip.description": "{string}",
  "extensions.ribbons.fixedControls.label": "{string}",
  "extensions.ribbons.fixedControls.supertip.title": "{string}",
  "extensions.ribbons.fixedControls.supertip.description": "{string}",
  "extensions.ribbons.spamPreProcessingDialog.title": "{string}",
  "extensions.ribbons.spamPreProcessingDialog.description": "{string}",
  "extensions.ribbons.spamPreProcessingDialog.spamFreeTextSectionTitle": "{string}",
  "extensions.ribbons.spamPreProcessingDialog.spamReportingOptions.title": "{string}",
  "extensions.ribbons.spamPreProcessingDialog.spamReportingOptions.options": "{string}",
  "extensions.ribbons.spamPreProcessingDialog.spamMoreInfo.text": "{string}",
  "extensions.ribbons.spamPreProcessingDialog.spamMoreInfo.url": "{string}",
  "extensions.runtimes.code.page": "{string}",
  "extensions.runtimes.code.script": "{string}",
  "extensions.runtimes.actions.displayName": "{string}",
  "extensions.alternates.alternateIcons.icon.url": "{string}",
  "extensions.alternates.alternateIcons.highResolutionIcon.url": "{string}",
  "copilotAgents.customEngineAgents.disclaimer.text": "{string}"
}
```

```json
{
  "$schema": "http://json-schema.org/draft-04/schema#",
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "$schema": {
      "type": "string",
      "format": "uri"
    },
    "name.short": {
      "type": "string",
      "maxLength": 30,
      "$ref": "#/definitions/nonEmptyString"
    },
    "name.full": {
      "type": "string",
      "maxLength": 100,
      "$ref": "#/definitions/nonEmptyString"
    },
    "description.short": {
      "type": "string",
      "maxLength": 80,
      "$ref": "#/definitions/nonEmptyString"
    },
    "description.full": {
      "type": "string",
      "maxLength": 4000,
      "$ref": "#/definitions/nonEmptyString"
    },
    "localizationKeys": {
      "type": "object",
      "patternProperties": {
        "^\\[\\[[a-zA-Z_][a-zA-Z0-9_]*\\]\\]$": {
          "type": "string"
        }
      }
    }
  },
  "patternProperties": {
    "^staticTabs\\[([0-9]|1[0-5])\\]\\.name$": {
      "type": "string",
      "maxLength": 128
    },
    "^bots\\[0\\]\\.commandLists\\[[0-2]\\]\\.commands\\[[0-9]\\]\\.title$": {
      "type": "string",
      "maxLength": 128
    },
    "^bots\\[0\\]\\.commandLists\\[[0-2]\\]\\.commands\\[[0-9]\\]\\.description$": {
      "type": "string",
      "maxLength": 4000
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.title$": {
      "type": "string",
      "maxLength": 32
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.description$": {
      "type": "string",
      "maxLength": 128
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.title$": {
      "type": "string",
      "maxLength": 32
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.description$": {
      "type": "string",
      "maxLength": 128
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.value$": {
      "type": "string",
      "maxLength": 512
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.choices\\[[0-9]\\]\\.title$": {
      "type": "string",
      "maxLength": 128
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.samplePrompts\\[[0-4]\\]\\.text$": {
      "type": "string",
      "maxLength": 128
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.taskInfo\\.title$": {
      "type": "string",
      "maxLength": 64
    },
    "^activities.activityTypes\\[\\b([0-9]|[1-8][0-9]|9[0-9]|1[01][0-9]|12[0-7])\\b]\\.description$": {
      "type": "string",
      "maxLength": 128
    },
    "^activities.activityTypes\\[\\b([0-9]|[1-8][0-9]|9[0-9]|1[01][0-9]|12[0-7])\\b]\\.templateText$": {
      "type": "string",
      "maxLength": 128
    },
    "^meetingExtensionDefinition.scenes\\[[0-9]\\]\\.name$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.audienceClaimUrl$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.label$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.customMobileRibbonGroups\\[[0-9]\\]\\.label$": {
      "type": "string",
      "maxLength": 32
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.customMobileRibbonGroups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.icons\\[[0-8]\\]\\.url$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.customMobileRibbonGroups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.label$": {
      "type": "string",
      "maxLength": 32
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.icons\\[[0-2]\\]\\.url$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.label$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.icons\\[[0-2]\\]\\.url$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.label$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.supertip\\.title$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.supertip\\.description$": {
      "type": "string",
      "maxLength": 250
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.items\\[[1]?[0-9]\\]\\.icons\\[[0-2]\\]\\.url$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.items\\[[1]?[0-9]\\]\\.label$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.items\\[[1]?[0-9]\\]\\.supertip\\.title$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.items\\[[1]?[0-9]\\]\\.supertip\\.description$": {
      "type": "string",
      "maxLength": 250
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.fixedControls\\[[1]?[0-9]\\]\\.label$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.fixedControls\\[[1]?[0-9]\\]\\.supertip\\.title$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.fixedControls\\[[1]?[0-9]\\]\\.supertip\\.description$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.spamPreProcessingDialog\\.title$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.spamPreProcessingDialog\\.description$": {
      "type": "string",
      "maxLength": 250
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.spamPreProcessingDialog\\.spamFreeTextSectionTitle$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.spamPreProcessingDialog\\.spamReportingOptions\\.title$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.spamPreProcessingDialog\\.spamReportingOptions\\.options\\[[0-4]\\]$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.spamPreProcessingDialog\\.spamMoreInfo\\.text$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.spamPreProcessingDialog\\.spamMoreInfo\\.url$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.code\\.page$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.code\\.script$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.actions\\[[1]?[0-9]\\]\\.displayName$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.alternates\\[[0-9]\\]\\.alternateIcons\\.icon\\.url$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.alternates\\[[0-9]\\]\\.alternateIcons\\.highResolutionIcon\\.url$": {
      "type": "string",
      "maxLength": 2048
    },
    "^copilotAgents.customEngineAgents\\[0\\]\\.disclaimer.text$": {
      "type": "string",
      "maxLength": 500
    }
  },
  "required": [
    "name.short",
    "description.short",
    "description.full"
  ],
  "definitions": {
    "nonEmptyString": {
      "type": "string",
      "pattern": "^(?![nN][uU][lL]{2}$)\\s*\\S.*"
    }
  }
}
```

- [Syntax](#tabpanel_9_syntax)
- [Schema](#tabpanel_9_schema)

```json
{
  "$schema": "{string}",
  "name.short": "{string}",
  "name.full": "{string}",
  "description.short": "{string}",
  "description.full": "{string}",
  "localizationKeys": {
    "^\[\[[a-zA-Z_][a-zA-Z0-9_]*\]\]$": "{string}"
  },
  "staticTabs.name": "{string}",
  "bots.commandLists.commands.title": "{string}",
  "bots.commandLists.commands.description": "{string}",
  "composeExtensions.commands.title": "{string}",
  "composeExtensions.commands.description": "{string}",
  "composeExtensions.commands.parameters.title": "{string}",
  "composeExtensions.commands.parameters.description": "{string}",
  "composeExtensions.commands.parameters.value": "{string}",
  "composeExtensions.commands.parameters.choices.title": "{string}",
  "composeExtensions.commands.samplePrompts.text": "{string}",
  "composeExtensions.commands.taskInfo.title": "{string}",
  "activities.activityTypes.description": "{string}",
  "activities.activityTypes.templateText": "{string}",
  "meetingExtensionDefinition.scenes.name": "{string}",
  "extensions.audienceClaimUrl": "{string}",
  "extensions.ribbons.tabs.label": "{string}",
  "extensions.ribbons.tabs.customMobileRibbonGroups.label": "{string}",
  "extensions.ribbons.tabs.customMobileRibbonGroups.controls.icons.url": "{string}",
  "extensions.ribbons.tabs.customMobileRibbonGroups.controls.label": "{string}",
  "extensions.ribbons.tabs.groups.icons.url": "{string}",
  "extensions.ribbons.tabs.groups.label": "{string}",
  "extensions.ribbons.tabs.groups.controls.icons.url": "{string}",
  "extensions.ribbons.tabs.groups.controls.label": "{string}",
  "extensions.ribbons.tabs.groups.controls.supertip.title": "{string}",
  "extensions.ribbons.tabs.groups.controls.supertip.description": "{string}",
  "extensions.ribbons.tabs.groups.controls.items.icons.url": "{string}",
  "extensions.ribbons.tabs.groups.controls.items.label": "{string}",
  "extensions.ribbons.tabs.groups.controls.items.supertip.title": "{string}",
  "extensions.ribbons.tabs.groups.controls.items.supertip.description": "{string}",
  "extensions.ribbons.fixedControls.label": "{string}",
  "extensions.ribbons.fixedControls.supertip.title": "{string}",
  "extensions.ribbons.fixedControls.supertip.description": "{string}",
  "extensions.ribbons.spamPreProcessingDialog.title": "{string}",
  "extensions.ribbons.spamPreProcessingDialog.description": "{string}",
  "extensions.ribbons.spamPreProcessingDialog.spamFreeTextSectionTitle": "{string}",
  "extensions.ribbons.spamPreProcessingDialog.spamReportingOptions.title": "{string}",
  "extensions.ribbons.spamPreProcessingDialog.spamReportingOptions.options": "{string}",
  "extensions.ribbons.spamPreProcessingDialog.spamMoreInfo.text": "{string}",
  "extensions.ribbons.spamPreProcessingDialog.spamMoreInfo.url": "{string}",
  "extensions.runtimes.code.page": "{string}",
  "extensions.runtimes.code.script": "{string}",
  "extensions.runtimes.actions.displayName": "{string}",
  "extensions.alternates.alternateIcons.icon.url": "{string}",
  "extensions.alternates.alternateIcons.highResolutionIcon.url": "{string}"
}
```

```json
{
  "$schema": "http://json-schema.org/draft-04/schema#",
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "$schema": {
      "type": "string",
      "format": "uri"
    },
    "name.short": {
      "type": "string",
      "maxLength": 30,
      "$ref": "#/definitions/nonEmptyString"
    },
    "name.full": {
      "type": "string",
      "maxLength": 100,
      "$ref": "#/definitions/nonEmptyString"
    },
    "description.short": {
      "type": "string",
      "maxLength": 80,
      "$ref": "#/definitions/nonEmptyString"
    },
    "description.full": {
      "type": "string",
      "maxLength": 4000,
      "$ref": "#/definitions/nonEmptyString"
    },
    "localizationKeys": {
      "type": "object",
      "patternProperties": {
        "^\\[\\[[a-zA-Z_][a-zA-Z0-9_]*\\]\\]$": {
          "type": "string"
        }
      }
    }
  },
  "patternProperties": {
    "^staticTabs\\[([0-9]|1[0-5])\\]\\.name$": {
      "type": "string",
      "maxLength": 128
    },
    "^bots\\[0\\]\\.commandLists\\[[0-2]\\]\\.commands\\[[0-9]\\]\\.title$": {
      "type": "string",
      "maxLength": 128
    },
    "^bots\\[0\\]\\.commandLists\\[[0-2]\\]\\.commands\\[[0-9]\\]\\.description$": {
      "type": "string",
      "maxLength": 4000
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.title$": {
      "type": "string",
      "maxLength": 32
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.description$": {
      "type": "string",
      "maxLength": 128
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.title$": {
      "type": "string",
      "maxLength": 32
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.description$": {
      "type": "string",
      "maxLength": 128
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.value$": {
      "type": "string",
      "maxLength": 512
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.choices\\[[0-9]\\]\\.title$": {
      "type": "string",
      "maxLength": 128
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.samplePrompts\\[[0-4]\\]\\.text$": {
      "type": "string",
      "maxLength": 128
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.taskInfo\\.title$": {
      "type": "string",
      "maxLength": 64
    },
    "^activities.activityTypes\\[\\b([0-9]|[1-8][0-9]|9[0-9]|1[01][0-9]|12[0-7])\\b]\\.description$": {
      "type": "string",
      "maxLength": 128
    },
    "^activities.activityTypes\\[\\b([0-9]|[1-8][0-9]|9[0-9]|1[01][0-9]|12[0-7])\\b]\\.templateText$": {
      "type": "string",
      "maxLength": 128
    },
    "^meetingExtensionDefinition.scenes\\[[0-9]\\]\\.name$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.audienceClaimUrl$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.label$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.customMobileRibbonGroups\\[[0-9]\\]\\.label$": {
      "type": "string",
      "maxLength": 32
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.customMobileRibbonGroups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.icons\\[[0-8]\\]\\.url$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.customMobileRibbonGroups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.label$": {
      "type": "string",
      "maxLength": 32
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.icons\\[[0-2]\\]\\.url$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.label$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.icons\\[[0-2]\\]\\.url$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.label$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.supertip\\.title$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.supertip\\.description$": {
      "type": "string",
      "maxLength": 250
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.items\\[[1]?[0-9]\\]\\.icons\\[[0-2]\\]\\.url$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.items\\[[1]?[0-9]\\]\\.label$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.items\\[[1]?[0-9]\\]\\.supertip\\.title$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.items\\[[1]?[0-9]\\]\\.supertip\\.description$": {
      "type": "string",
      "maxLength": 250
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.fixedControls\\[[1]?[0-9]\\]\\.label$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.fixedControls\\[[1]?[0-9]\\]\\.supertip\\.title$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.fixedControls\\[[1]?[0-9]\\]\\.supertip\\.description$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.spamPreProcessingDialog\\.title$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.spamPreProcessingDialog\\.description$": {
      "type": "string",
      "maxLength": 250
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.spamPreProcessingDialog\\.spamFreeTextSectionTitle$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.spamPreProcessingDialog\\.spamReportingOptions\\.title$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.spamPreProcessingDialog\\.spamReportingOptions\\.options\\[[0-4]\\]$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.spamPreProcessingDialog\\.spamMoreInfo\\.text$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.spamPreProcessingDialog\\.spamMoreInfo\\.url$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.code\\.page$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.code\\.script$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.actions\\[[1]?[0-9]\\]\\.displayName$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.alternates\\[[0-9]\\]\\.alternateIcons\\.icon\\.url$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.alternates\\[[0-9]\\]\\.alternateIcons\\.highResolutionIcon\\.url$": {
      "type": "string",
      "maxLength": 2048
    }
  },
  "required": [
    "name.short",
    "description.short",
    "description.full"
  ],
  "definitions": {
    "nonEmptyString": {
      "type": "string",
      "pattern": "^(?![nN][uU][lL]{2}$)\\s*\\S.*"
    }
  }
}
```

- [Syntax](#tabpanel_10_syntax)
- [Schema](#tabpanel_10_schema)

```json
{
  "$schema": "{string}",
  "name.short": "{string}",
  "name.full": "{string}",
  "description.short": "{string}",
  "description.full": "{string}",
  "localizationKeys": {
    "^\[\[[a-zA-Z_][a-zA-Z0-9_]*\]\]$": "{string}"
  },
  "staticTabs.name": "{string}",
  "bots.commandLists.commands.title": "{string}",
  "bots.commandLists.commands.description": "{string}",
  "composeExtensions.commands.title": "{string}",
  "composeExtensions.commands.description": "{string}",
  "composeExtensions.commands.parameters.title": "{string}",
  "composeExtensions.commands.parameters.description": "{string}",
  "composeExtensions.commands.parameters.value": "{string}",
  "composeExtensions.commands.parameters.choices.title": "{string}",
  "composeExtensions.commands.samplePrompts.text": "{string}",
  "composeExtensions.commands.taskInfo.title": "{string}",
  "activities.activityTypes.description": "{string}",
  "activities.activityTypes.templateText": "{string}",
  "meetingExtensionDefinition.scenes.name": "{string}",
  "extensions.audienceClaimUrl": "{string}",
  "extensions.ribbons.tabs.label": "{string}",
  "extensions.ribbons.tabs.customMobileRibbonGroups.label": "{string}",
  "extensions.ribbons.tabs.customMobileRibbonGroups.controls.icons.url": "{string}",
  "extensions.ribbons.tabs.customMobileRibbonGroups.controls.label": "{string}",
  "extensions.ribbons.tabs.groups.icons.url": "{string}",
  "extensions.ribbons.tabs.groups.label": "{string}",
  "extensions.ribbons.tabs.groups.controls.icons.url": "{string}",
  "extensions.ribbons.tabs.groups.controls.label": "{string}",
  "extensions.ribbons.tabs.groups.controls.supertip.title": "{string}",
  "extensions.ribbons.tabs.groups.controls.supertip.description": "{string}",
  "extensions.ribbons.tabs.groups.controls.items.icons.url": "{string}",
  "extensions.ribbons.tabs.groups.controls.items.label": "{string}",
  "extensions.ribbons.tabs.groups.controls.items.supertip.title": "{string}",
  "extensions.ribbons.tabs.groups.controls.items.supertip.description": "{string}",
  "extensions.ribbons.fixedControls.label": "{string}",
  "extensions.ribbons.fixedControls.supertip.title": "{string}",
  "extensions.ribbons.fixedControls.supertip.description": "{string}",
  "extensions.ribbons.spamPreProcessingDialog.title": "{string}",
  "extensions.ribbons.spamPreProcessingDialog.description": "{string}",
  "extensions.ribbons.spamPreProcessingDialog.spamFreeTextSectionTitle": "{string}",
  "extensions.ribbons.spamPreProcessingDialog.spamReportingOptions.title": "{string}",
  "extensions.ribbons.spamPreProcessingDialog.spamReportingOptions.options": "{string}",
  "extensions.ribbons.spamPreProcessingDialog.spamMoreInfo.text": "{string}",
  "extensions.ribbons.spamPreProcessingDialog.spamMoreInfo.url": "{string}",
  "extensions.runtimes.code.page": "{string}",
  "extensions.runtimes.code.script": "{string}",
  "extensions.runtimes.actions.displayName": "{string}",
  "extensions.alternates.alternateIcons.icon.url": "{string}",
  "extensions.alternates.alternateIcons.highResolutionIcon.url": "{string}"
}
```

```json
{
  "$schema": "http://json-schema.org/draft-04/schema#",
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "$schema": {
      "type": "string",
      "format": "uri"
    },
    "name.short": {
      "type": "string",
      "maxLength": 30
    },
    "name.full": {
      "type": "string",
      "maxLength": 100
    },
    "description.short": {
      "type": "string",
      "maxLength": 80
    },
    "description.full": {
      "type": "string",
      "maxLength": 4000
    },
    "localizationKeys": {
      "type": "object",
      "patternProperties": {
        "^\\[\\[[a-zA-Z_][a-zA-Z0-9_]*\\]\\]$": {
          "type": "string"
        }
      }
    }
  },
  "patternProperties": {
    "^staticTabs\\[([0-9]|1[0-5])\\]\\.name$": {
      "type": "string",
      "maxLength": 128
    },
    "^bots\\[0\\]\\.commandLists\\[[0-2]\\]\\.commands\\[[0-9]\\]\\.title$": {
      "type": "string",
      "maxLength": 32
    },
    "^bots\\[0\\]\\.commandLists\\[[0-2]\\]\\.commands\\[[0-9]\\]\\.description$": {
      "type": "string",
      "maxLength": 128
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.title$": {
      "type": "string",
      "maxLength": 32
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.description$": {
      "type": "string",
      "maxLength": 128
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.title$": {
      "type": "string",
      "maxLength": 32
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.description$": {
      "type": "string",
      "maxLength": 128
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.value$": {
      "type": "string",
      "maxLength": 512
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.choices\\[[0-9]\\]\\.title$": {
      "type": "string",
      "maxLength": 128
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.samplePrompts\\[[0-4]\\]\\.text$": {
      "type": "string",
      "maxLength": 128
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.taskInfo\\.title$": {
      "type": "string",
      "maxLength": 64
    },
    "^activities.activityTypes\\[\\b([0-9]|[1-8][0-9]|9[0-9]|1[01][0-9]|12[0-7])\\b]\\.description$": {
      "type": "string",
      "maxLength": 128
    },
    "^activities.activityTypes\\[\\b([0-9]|[1-8][0-9]|9[0-9]|1[01][0-9]|12[0-7])\\b]\\.templateText$": {
      "type": "string",
      "maxLength": 128
    },
    "^meetingExtensionDefinition.scenes\\[[0-9]\\]\\.name$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.audienceClaimUrl$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.label$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.customMobileRibbonGroups\\[[0-9]\\]\\.label$": {
      "type": "string",
      "maxLength": 32
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.customMobileRibbonGroups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.icons\\[[0-8]\\]\\.url$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.customMobileRibbonGroups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.label$": {
      "type": "string",
      "maxLength": 32
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.icons\\[[0-2]\\]\\.url$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.label$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.icons\\[[0-2]\\]\\.url$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.label$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.supertip\\.title$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.supertip\\.description$": {
      "type": "string",
      "maxLength": 250
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.items\\[[1]?[0-9]\\]\\.icons\\[[0-2]\\]\\.url$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.items\\[[1]?[0-9]\\]\\.label$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.items\\[[1]?[0-9]\\]\\.supertip\\.title$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.items\\[[1]?[0-9]\\]\\.supertip\\.description$": {
      "type": "string",
      "maxLength": 250
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.fixedControls\\[[1]?[0-9]\\]\\.label$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.fixedControls\\[[1]?[0-9]\\]\\.supertip\\.title$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.fixedControls\\[[1]?[0-9]\\]\\.supertip\\.description$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.spamPreProcessingDialog\\.title$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.spamPreProcessingDialog\\.description$": {
      "type": "string",
      "maxLength": 250
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.spamPreProcessingDialog\\.spamFreeTextSectionTitle$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.spamPreProcessingDialog\\.spamReportingOptions\\.title$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.spamPreProcessingDialog\\.spamReportingOptions\\.options\\[[0-4]\\]$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.spamPreProcessingDialog\\.spamMoreInfo\\.text$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.spamPreProcessingDialog\\.spamMoreInfo\\.url$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.code\\.page$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.code\\.script$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.actions\\[[1]?[0-9]\\]\\.displayName$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.alternates\\[[0-9]\\]\\.alternateIcons\\.icon\\.url$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.alternates\\[[0-9]\\]\\.alternateIcons\\.highResolutionIcon\\.url$": {
      "type": "string",
      "maxLength": 2048
    }
  },
  "required": [
    "name.short",
    "name.full",
    "description.short",
    "description.full"
  ]
}
```

- [Syntax](#tabpanel_11_syntax)
- [Schema](#tabpanel_11_schema)

```json
{
  "$schema": "{string}",
  "name.short": "{string}",
  "name.full": "{string}",
  "description.short": "{string}",
  "description.full": "{string}",
  "localizationKeys": {
    "^\[\[[a-zA-Z_][a-zA-Z0-9_]*\]\]$": "{string}"
  },
  "staticTabs.name": "{string}",
  "bots.commandLists.commands.title": "{string}",
  "bots.commandLists.commands.description": "{string}",
  "composeExtensions.commands.title": "{string}",
  "composeExtensions.commands.description": "{string}",
  "composeExtensions.commands.parameters.title": "{string}",
  "composeExtensions.commands.parameters.description": "{string}",
  "composeExtensions.commands.parameters.value": "{string}",
  "composeExtensions.commands.parameters.choices.title": "{string}",
  "composeExtensions.commands.samplePrompts.text": "{string}",
  "composeExtensions.commands.taskInfo.title": "{string}",
  "activities.activityTypes.description": "{string}",
  "activities.activityTypes.templateText": "{string}",
  "meetingExtensionDefinition.scenes.name": "{string}",
  "extensions.audienceClaimUrl": "{string}",
  "extensions.ribbons.tabs.label": "{string}",
  "extensions.ribbons.tabs.customMobileRibbonGroups.label": "{string}",
  "extensions.ribbons.tabs.customMobileRibbonGroups.controls.icons.url": "{string}",
  "extensions.ribbons.tabs.customMobileRibbonGroups.controls.label": "{string}",
  "extensions.ribbons.tabs.groups.icons.url": "{string}",
  "extensions.ribbons.tabs.groups.label": "{string}",
  "extensions.ribbons.tabs.groups.controls.icons.url": "{string}",
  "extensions.ribbons.tabs.groups.controls.label": "{string}",
  "extensions.ribbons.tabs.groups.controls.supertip.title": "{string}",
  "extensions.ribbons.tabs.groups.controls.supertip.description": "{string}",
  "extensions.ribbons.tabs.groups.controls.items.icons.url": "{string}",
  "extensions.ribbons.tabs.groups.controls.items.label": "{string}",
  "extensions.ribbons.tabs.groups.controls.items.supertip.title": "{string}",
  "extensions.ribbons.tabs.groups.controls.items.supertip.description": "{string}",
  "extensions.runtimes.code.page": "{string}",
  "extensions.runtimes.code.script": "{string}",
  "extensions.runtimes.actions.displayName": "{string}",
  "extensions.alternates.alternateIcons.icon.url": "{string}",
  "extensions.alternates.alternateIcons.highResolutionIcon.url": "{string}"
}
```

```json
{
  "$schema": "http://json-schema.org/draft-04/schema#",
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "$schema": {
      "type": "string",
      "format": "uri"
    },
    "name.short": {
      "type": "string",
      "maxLength": 30
    },
    "name.full": {
      "type": "string",
      "maxLength": 100
    },
    "description.short": {
      "type": "string",
      "maxLength": 80
    },
    "description.full": {
      "type": "string",
      "maxLength": 4000
    },
    "localizationKeys": {
      "type": "object",
      "patternProperties": {
        "^\\[\\[[a-zA-Z_][a-zA-Z0-9_]*\\]\\]$": {
          "type": "string"
        }
      }
    }
  },
  "patternProperties": {
    "^staticTabs\\[([0-9]|1[0-5])\\]\\.name$": {
      "type": "string",
      "maxLength": 128
    },
    "^bots\\[0\\]\\.commandLists\\[[0-2]\\]\\.commands\\[[0-9]\\]\\.title$": {
      "type": "string",
      "maxLength": 32
    },
    "^bots\\[0\\]\\.commandLists\\[[0-2]\\]\\.commands\\[[0-9]\\]\\.description$": {
      "type": "string",
      "maxLength": 128
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.title$": {
      "type": "string",
      "maxLength": 32
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.description$": {
      "type": "string",
      "maxLength": 128
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.title$": {
      "type": "string",
      "maxLength": 32
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.description$": {
      "type": "string",
      "maxLength": 128
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.value$": {
      "type": "string",
      "maxLength": 512
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.choices\\[[0-9]\\]\\.title$": {
      "type": "string",
      "maxLength": 128
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.samplePrompts\\[[0-4]\\]\\.text$": {
      "type": "string",
      "maxLength": 128
    },
    "^composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.taskInfo\\.title$": {
      "type": "string",
      "maxLength": 64
    },
    "^activities.activityTypes\\[\\b([0-9]|[1-8][0-9]|9[0-9]|1[01][0-9]|12[0-7])\\b]\\.description$": {
      "type": "string",
      "maxLength": 128
    },
    "^activities.activityTypes\\[\\b([0-9]|[1-8][0-9]|9[0-9]|1[01][0-9]|12[0-7])\\b]\\.templateText$": {
      "type": "string",
      "maxLength": 128
    },
    "^meetingExtensionDefinition.scenes\\[[0-9]\\]\\.name$": {
      "type": "string",
      "maxLength": 128
    },
    "^extensions\\[[0]\\]\\.audienceClaimUrl$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.label$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.customMobileRibbonGroups\\[[0-9]\\]\\.label$": {
      "type": "string",
      "maxLength": 32
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.customMobileRibbonGroups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.icons\\[[0-8]\\]\\.url$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.customMobileRibbonGroups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.label$": {
      "type": "string",
      "maxLength": 32
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.icons\\[[0-2]\\]\\.url$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.label$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.icons\\[[0-2]\\]\\.url$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.label$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.supertip\\.title$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.supertip\\.description$": {
      "type": "string",
      "maxLength": 250
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.items\\[[1]?[0-9]\\]\\.icons\\[[0-2]\\]\\.url$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.items\\[[1]?[0-9]\\]\\.label$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.items\\[[1]?[0-9]\\]\\.supertip\\.title$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.ribbons\\[[0-9]\\]\\.tabs\\[[1]?[0-9]\\]\\.groups\\[[0-9]\\]\\.controls\\[[1]?[0-9]\\]\\.items\\[[1]?[0-9]\\]\\.supertip\\.description$": {
      "type": "string",
      "maxLength": 250
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.code\\.page$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.code\\.script$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.runtimes\\[[1]?[0-9]\\]\\.actions\\[[1]?[0-9]\\]\\.displayName$": {
      "type": "string",
      "maxLength": 64
    },
    "^extensions\\[[0]\\]\\.alternates\\[[0-9]\\]\\.alternateIcons\\.icon\\.url$": {
      "type": "string",
      "maxLength": 2048
    },
    "^extensions\\[[0]\\]\\.alternates\\[[0-9]\\]\\.alternateIcons\\.highResolutionIcon\\.url$": {
      "type": "string",
      "maxLength": 2048
    }
  },
  "required": [
    "name.short",
    "name.full",
    "description.short",
    "description.full"
  ]
}
```

## Properties

#### $schema

The https:// URL referencing the JSON Schema for the manifest.

**Type**  
string

**Required**  
—

**Constraints**  


**Supported values**  


#### name.short

This property specifies a localized value for the [name.short](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-name?view=m365-app-1.30#short) property. The short display name for the app. It replaces the corresponding string from the app manifest with the value provided here.

**Type**  
string

**Required**  
✅

**Constraints**  


**Supported values**  
The string value must not be 'null' \(case insensitive\) and must not be empty or whitespace only.

#### name.short

This property specifies a localized value for the [name.short](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-name?view=m365-app-1.30#short) property. The short display name for the app. It replaces the corresponding string from the app manifest with the value provided here.

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 30.

**Supported values**  


#### name.full

This property specifies a localized value for the [name.full](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-name?view=m365-app-1.30#full) property. The full name of the app. It replaces the corresponding string from the app manifest with the value provided here.

**Type**  
string

**Required**  
—

**Constraints**  


**Supported values**  
The string value must not be 'null' \(case insensitive\) and must not be empty or whitespace only.

#### name.full

This property specifies a localized value for the [name.full](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-name?view=m365-app-1.30#full) property. The full name of the app. It replaces the corresponding string from the app manifest with the value provided here.

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 100.

**Supported values**  


#### description.short

This property specifies a localized value for the [description.short](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-description?view=m365-app-1.30#short) property. A short description of the app, used when space is limited. It replaces the corresponding string from the app manifest with the value provided here.

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 80

**Supported values**  
The string value must not be 'null' \(case insensitive\) and must not be empty or whitespace only.

#### description.short

This property specifies a localized value for the [description.short](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-description?view=m365-app-1.30#short) property. A short description of the app, used when space is limited. It replaces the corresponding string from the app manifest with the value provided here.

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 80.

**Supported values**  


#### description.full

This property specifies a localized value for the [description.full](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-description?view=m365-app-1.30#full) property. The full description of the app. It replaces the corresponding string from the app manifest with the value provided here.

**Type**  
string

**Required**  
✅

**Constraints**  


**Supported values**  
The string value must not be 'null' \(case insensitive\) and must not be empty or whitespace only.

#### description.full

This property specifies a localized value for the [description.full](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-description?view=m365-app-1.30#full) property. The full description of the app. It replaces the corresponding string from the app manifest with the value provided here.

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 4000.

**Supported values**  


#### localizationKeys

Represents custom tokenized keys for localized strings in agents. Each key is represented by a property name that matches a regular expression \(with the following format: `^\[\[[a-zA-Z_][a-zA-Z0-9_]*\]\]$`\) and the value provides the localized string value.

```json
"localizationKeys": {
    "DA_Name": "Agent de Communications",
    "DA_Description": "Un assistant pour les professionnels de la communication et des relations publiques chez Contoso."
}
```

For more information, see [localize your agent](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/localize-agents).

**Type**  
object

**Required**  
—

**Constraints**  


**Supported values**  


#### staticTabs.name

This property specifies a localized value for the [staticTabs.name](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-static-tabs?view=m365-app-1.30#name-property) property. The property name should be a JSON path expression in the following form: `staticTabs[0-15].name`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 128.

**Supported values**  


#### bots.commandLists.commands.title

This property specifies a localized value for the [bots.commandLists.commands.title](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-command-lists-commands?view=m365-app-1.30#title-property) property. The property name should be a JSON path expression in the following form: `bots[0].commandLists[0-2].commands[0-11].title`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 128.

**Supported values**  


#### bots.commandLists.commands.title

This property specifies a localized value for the [bots.commandLists.commands.title](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-command-lists-commands?view=m365-app-1.30#title-property) property. The property name should be a JSON path expression in the following form: `bots[0].commandLists[0-2].commands[0-9].title`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 128.

**Supported values**  


#### bots.commandLists.commands.title

This property specifies a localized value for the [bots.commandLists.commands.title](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-command-lists-commands?view=m365-app-1.30#title-property) property. The property name should be a JSON path expression in the following form: `bots[0].commandLists[0-2].commands[0-9].title`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 32.

**Supported values**  


#### bots.commandLists.commands.description

This property specifies a localized value for the [bots.commandLists.commands.description](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-command-lists-commands?view=m365-app-1.30#description-property) property. The property name should be a JSON path expression in the following form: `bots[0].commandLists[0-2].commands[0-11].description`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 4000.

**Supported values**  


#### bots.commandLists.commands.description

This property specifies a localized value for the [bots.commandLists.commands.description](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-command-lists-commands?view=m365-app-1.30#description-property) property. The property name should be a JSON path expression in the following form: `bots[0].commandLists[0-2].commands[0-9].description`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 4000.

**Supported values**  


#### bots.commandLists.commands.description

This property specifies a localized value for the [bots.commandLists.commands.description](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-command-lists-commands?view=m365-app-1.30#description-property) property. The property name should be a JSON path expression in the following form: `bots[0].commandLists[0-2].commands[0-9].description`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 128.

**Supported values**  


#### composeExtensions.commands.title

This property specifies a localized value for the [composeExtensions.commands.title](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-compose-extensions-commands?view=m365-app-1.30#title-property) property. The property name should be a JSON path expression in the following form: `composeExtensions[0].commands[0-9].title`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 32.

**Supported values**  


#### composeExtensions.commands.description

This property specifies a localized value for the [composeExtensions.commands.description](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-compose-extensions-commands?view=m365-app-1.30#description-property) property. The property name should be a JSON path expression in the following form: `composeExtensions[0].commands[0-9].description`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 128.

**Supported values**  


#### composeExtensions.commands.parameters.title

This property specifies a localized value for the [composeExtensions.commands.parameters.title](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-compose-extensions-commands-parameters?view=m365-app-1.30#title-property) property. The property name should be a JSON path expression in the following form: `composeExtensions[0].commands[0-9].parameters[0-4].title`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 32.

**Supported values**  


#### composeExtensions.commands.parameters.description

This property specifies a localized value for the [composeExtensions.commands.parameters.description](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-compose-extensions-commands-parameters?view=m365-app-1.30#description-property) property. The property name should be a JSON path expression in the following form: `composeExtensions[0].commands[0-9].parameters[0-4].description`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 128.

**Supported values**  


#### composeExtensions.commands.parameters.value

This property specifies a localized value for the [composeExtensions.commands.parameters.value](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-compose-extensions-commands-parameters?view=m365-app-1.30#value-property) property. The property name should be a JSON path expression in the following form: `composeExtensions[0].commands[0-9].parameters[0-4].value`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 512.

**Supported values**  


#### composeExtensions.commands.parameters.choices.title

This property specifies a localized value for the [composeExtensions.commands.parameters.choices.title](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-compose-extensions-commands-parameters-choices?view=m365-app-1.30#title-property) property. The property name should be a JSON path expression in the following form: `composeExtensions[0].commands[0-9].parameters[0-4].choices[0-9].title`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 128.

**Supported values**  


#### composeExtensions.commands.taskInfo.title

This property specifies a localized value for the [composeExtensions.commands.taskInfo.title](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/task-info?view=m365-app-1.30#title-property) property. The property name should be a JSON path expression in the following form: `composeExtensions[0].commands[0-9].taskInfo.title`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 64.

**Supported values**  


#### activities.activityTypes.description

This property specifies a localized value for the [activities.activityTypes.description](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-activities-activity-types?view=m365-app-1.30#description-property) property. The property name should be a JSON path expression in the following form: `activities.activityTypes[0-127].description`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 128.

**Supported values**  


#### activities.activityTypes.templateText

This property specifies a localized value for the [activities.activityTypes.templateText](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-activities-activity-types?view=m365-app-1.30#templateText-property) property. The property name should be a JSON path expression in the following form: `activities.activityTypes[0-127].templateText`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 128.

**Supported values**  


#### meetingExtensionDefinition.scenes.name

This property specifies a localized value for the [meetingExtensionDefinition.scenes.name](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-meeting-extension-definition-scenes?view=m365-app-1.30#name-property) property. The property name should be a JSON path expression in the following form: `meetingExtensionDefinition.scenes[0-4].name`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 128.

**Supported values**  


#### meetingExtensionDefinition.videoFilters.name

This property specifies a localized value for the [meetingExtensionDefinition.videoFilters.name](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-meeting-extension-definition-video-filters?view=m365-app-1.30#name-property) property. The property name should be a JSON path expression in the following form: `meetingExtensionDefinition.videoFilters[0-31].name`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 128.

**Supported values**  


#### extensions.audienceClaimUrl

This property specifies a localized value for the [extensions.audienceClaimUrl](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/element-extensions?view=m365-app-1.30#audienceClaimUrl-property) property. The property name should be a JSON path expression in the following form: `extensions[0].audienceClaimUrl`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 2048.

**Supported values**  


#### extensions.ribbons.tabs.label

This property specifies a localized value for the [extensions.ribbons.tabs.label](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-array-tabs-item?view=m365-app-1.30#label-property) property. The property name should be a JSON path expression in the following form: `extensions[0].ribbons[0-19].tabs[0-19].label`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 64.

**Supported values**  


#### extensions.ribbons.tabs.customMobileRibbonGroups.label

This property specifies a localized value for the [extensions.ribbons.tabs.customMobileRibbonGroups.label](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-custom-mobile-group-item?view=m365-app-1.30#label-property) property. The property name should be a JSON path expression in the following form: `extensions[0].ribbons[0-19].tabs[0-19].customMobileRibbonGroups[0-9].label`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 32.

**Supported values**  


#### extensions.ribbons.tabs.customMobileRibbonGroups.controls.icons.url

This property specifies a localized value for the [extensions.ribbons.tabs.customMobileRibbonGroups.controls.icons.url](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-custom-mobile-icon?view=m365-app-1.30#url-property) property. The property name should be a JSON path expression in the following form: `extensions[0].ribbons[0-19].tabs[0-19].customMobileRibbonGroups[0-9].controls[0-19].icons[0-8].url`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 2048.

**Supported values**  


#### extensions.ribbons.tabs.groups.icons.url

This property specifies a localized value for the [extensions.ribbons.tabs.groups.icons.url](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-icon?view=m365-app-1.30#url-property) property. The property name should be a JSON path expression in the following form: `extensions[0].ribbons[0-19].tabs[0-19].groups[0-9].icons[0-7].url`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 2048.

**Supported values**  


#### extensions.ribbons.tabs.groups.icons.url

This property specifies a localized value for the [extensions.ribbons.tabs.groups.icons.url](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-icon?view=m365-app-1.30#url-property) property. The property name should be a JSON path expression in the following form: `extensions[0].ribbons[0-19].tabs[0-19].groups[0-9].icons[0-2].url`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 2048.

**Supported values**  


#### extensions.ribbons.tabs.groups.label

This property specifies a localized value for the [extensions.ribbons.tabs.groups.label](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-custom-tab-groups-item?view=m365-app-1.30#label-property) property. The property name should be a JSON path expression in the following form: `extensions[0].ribbons[0-19].tabs[0-19].groups[0-9].label`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 64.

**Supported values**  


#### extensions.ribbons.tabs.groups.controls.icons.url

This property specifies a localized value for the [extensions.ribbons.tabs.groups.controls.icons.url](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-icon?view=m365-app-1.30#url-property) property. The property name should be a JSON path expression in the following form: `extensions[0].ribbons[0-19].tabs[0-19].groups[0-9].controls[0-19].icons[0-7].url`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 2048.

**Supported values**  


#### extensions.ribbons.tabs.groups.controls.icons.url

This property specifies a localized value for the [extensions.ribbons.tabs.groups.controls.icons.url](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-icon?view=m365-app-1.30#url-property) property. The property name should be a JSON path expression in the following form: `extensions[0].ribbons[0-19].tabs[0-19].groups[0-9].controls[0-19].icons[0-2].url`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 2048.

**Supported values**  


#### extensions.ribbons.tabs.groups.controls.label

This property specifies a localized value for the [extensions.ribbons.tabs.groups.controls.label](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-custom-group-controls-item?view=m365-app-1.30#label-property) property. The property name should be a JSON path expression in the following form: `extensions[0].ribbons[0-19].tabs[0-19].groups[0-9].controls[0-19].label`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 64.

**Supported values**  


#### extensions.ribbons.tabs.groups.controls.supertip.title

This property specifies a localized value for the [extensions.ribbons.tabs.groups.controls.supertip.title](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-super-tool-tip?view=m365-app-1.30#title-property) property. The property name should be a JSON path expression in the following form: `extensions[0].ribbons[0-19].tabs[0-19].groups[0-9].controls[0-19].supertip.title`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 64.

**Supported values**  


#### extensions.ribbons.tabs.groups.controls.supertip.description

This property specifies a localized value for the [extensions.ribbons.tabs.groups.controls.supertip.description](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-super-tool-tip?view=m365-app-1.30#description-property) property. The property name should be a JSON path expression in the following form: `extensions[0].ribbons[0-19].tabs[0-19].groups[0-9].controls[0-19].supertip.description`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 250.

**Supported values**  


#### extensions.ribbons.tabs.groups.controls.items.icons.url

This property specifies a localized value for the [extensions.ribbons.tabs.groups.controls.items.icons.url](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-icon?view=m365-app-1.30#url-property) property. The property name should be a JSON path expression in the following form: `extensions[0].ribbons[0-19].tabs[0-19].groups[0-9].controls[0-19].items[0-29].icons[0-7].url`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 2048.

**Supported values**  


#### extensions.ribbons.tabs.groups.controls.items.icons.url

This property specifies a localized value for the [extensions.ribbons.tabs.groups.controls.items.icons.url](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-icon?view=m365-app-1.30#url-property) property. The property name should be a JSON path expression in the following form: `extensions[0].ribbons[0-19].tabs[0-19].groups[0-9].controls[0-19].items[0-29].icons[0-2].url`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 2048.

**Supported values**  


#### extensions.ribbons.tabs.groups.controls.items.icons.url

This property specifies a localized value for the [extensions.ribbons.tabs.groups.controls.items.icons.url](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-icon?view=m365-app-1.30#url-property) property. The property name should be a JSON path expression in the following form: `extensions[0].ribbons[0-19].tabs[0-19].groups[0-9].controls[0-19].items[0-19].icons[0-2].url`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 2048.

**Supported values**  


#### extensions.ribbons.tabs.groups.controls.items.label

This property specifies a localized value for the [extensions.ribbons.tabs.groups.controls.items.label](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-custom-control-menu-item?view=m365-app-1.30#label-property) property. The property name should be a JSON path expression in the following form: `extensions[0].ribbons[0-19].tabs[0-19].groups[0-9].controls[0-19].items[0-29].label`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 64.

**Supported values**  


#### extensions.ribbons.tabs.groups.controls.items.label

This property specifies a localized value for the [extensions.ribbons.tabs.groups.controls.items.label](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-custom-control-menu-item?view=m365-app-1.30#label-property) property. The property name should be a JSON path expression in the following form: `extensions[0].ribbons[0-19].tabs[0-19].groups[0-9].controls[0-19].items[0-19].label`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 64.

**Supported values**  


#### extensions.ribbons.tabs.groups.controls.items.supertip.title

This property specifies a localized value for the [extensions.ribbons.tabs.groups.controls.items.supertip.title](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-super-tool-tip?view=m365-app-1.30#title-property) property. The property name should be a JSON path expression in the following form: `extensions[0].ribbons[0-19].tabs[0-19].groups[0-9].controls[0-19].items[0-29].supertip.title`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 64.

**Supported values**  


#### extensions.ribbons.tabs.groups.controls.items.supertip.title

This property specifies a localized value for the [extensions.ribbons.tabs.groups.controls.items.supertip.title](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-super-tool-tip?view=m365-app-1.30#title-property) property. The property name should be a JSON path expression in the following form: `extensions[0].ribbons[0-19].tabs[0-19].groups[0-9].controls[0-19].items[0-19].supertip.title`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 64.

**Supported values**  


#### extensions.ribbons.tabs.groups.controls.items.supertip.description

This property specifies a localized value for the [extensions.ribbons.tabs.groups.controls.items.supertip.description](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-super-tool-tip?view=m365-app-1.30#description-property) property. The property name should be a JSON path expression in the following form: `extensions[0].ribbons[0-19].tabs[0-19].groups[0-9].controls[0-19].items[0-29].supertip.description`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 250.

**Supported values**  


#### extensions.ribbons.tabs.groups.controls.items.supertip.description

This property specifies a localized value for the [extensions.ribbons.tabs.groups.controls.items.supertip.description](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-super-tool-tip?view=m365-app-1.30#description-property) property. The property name should be a JSON path expression in the following form: `extensions[0].ribbons[0-19].tabs[0-19].groups[0-9].controls[0-19].items[0-19].supertip.description`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 250.

**Supported values**  


#### extensions.runtimes.code.page

This property specifies a localized value for the [extensions.runtimes.code.page](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-runtime-code?view=m365-app-1.30#page-property) property. The property name should be a JSON path expression in the following form: `extensions[0].runtimes[0-19].code.page`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 2048.

**Supported values**  


#### extensions.runtimes.code.script

This property specifies a localized value for the [extensions.runtimes.code.script](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-runtime-code?view=m365-app-1.30#script-property) property. The property name should be a JSON path expression in the following form: `extensions[0].runtimes[0-19].code.script`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 2048.

**Supported values**  


#### extensions.runtimes.actions.displayName

This property specifies a localized value for the [extensions.runtimes.actions.displayName](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-runtimes-actions-item?view=m365-app-1.30#displayName-property) property. The property name should be a JSON path expression in the following form: `extensions[0].runtimes[0-19].actions[0-149].displayName`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 64.

**Supported values**  


#### extensions.runtimes.actions.displayName

This property specifies a localized value for the [extensions.runtimes.actions.displayName](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-runtimes-actions-item?view=m365-app-1.30#displayName-property) property. The property name should be a JSON path expression in the following form: `extensions[0].runtimes[0-19].actions[0-19].displayName`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 64.

**Supported values**  


#### extensions.alternates.alternateIcons.icon.url

This property specifies a localized value for the [extensions.alternates.alternateIcons.icon.url](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-icon?view=m365-app-1.30#url-property) property. The property name should be a JSON path expression in the following form: `extensions[0].alternates[0-9].alternateIcons.icon.url`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 2048.

**Supported values**  


#### extensions.alternates.alternateIcons.highResolutionIcon.url

This property specifies a localized value for the [extensions.alternates.alternateIcons.highResolutionIcon.url](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-icon?view=m365-app-1.30#url-property) property. The property name should be a JSON path expression in the following form: `extensions[0].alternates[0-9].alternateIcons.highResolutionIcon.url`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 2048.

**Supported values**  


#### extensions.getStartedMessages.title

This property specifies a localized value for the [extensions.getStartedMessages.title](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-get-started-message-array?view=m365-app-1.30#title-property) property. The property name should be a JSON path expression in the following form: `extensions[0].getStartedMessages[0-2].title`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 125.

**Supported values**  


#### extensions.getStartedMessages.description

This property specifies a localized value for the [extensions.getStartedMessages.description](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-get-started-message-array?view=m365-app-1.30#description-property) property. The property name should be a JSON path expression in the following form: `extensions[0].getStartedMessages[0-2].description`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 250.

**Supported values**  


#### extensions.getStartedMessages.learnMoreUrl

This property specifies a localized value for the [extensions.getStartedMessages.learnMoreUrl](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-get-started-message-array?view=m365-app-1.30#learnMoreUrl-property) property. The property name should be a JSON path expression in the following form: `extensions[0].getStartedMessages[0-2].learnMoreUrl`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 2048.

**Supported values**  


#### extensions.contentRuntimes.code.page

This property specifies a localized value for the [extensions.contentRuntimes.code.page](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-runtime-code?view=m365-app-1.30#page-property) property. The property name should be a JSON path expression in the following form: `extensions[0].contentRuntimes[].code.page`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 2048.

**Supported values**  


#### extensions.runtimes.customFunctions.functions.name

This property specifies a localized value for the [extensions.runtimes.customFunctions.functions.name](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-function?view=m365-app-1.30#name-property) property. The property name should be a JSON path expression in the following form: `extensions[0].runtimes[0-19].customFunctions.functions[0-19999].name`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 64.

**Supported values**  


#### extensions.runtimes.customFunctions.functions.description

This property specifies a localized value for the [extensions.runtimes.customFunctions.functions.description](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-function?view=m365-app-1.30#description-property) property. The property name should be a JSON path expression in the following form: `extensions[0].runtimes[0-19].customFunctions.functions[0-19999].description`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 1024.

**Supported values**  


#### extensions.runtimes.customFunctions.functions.description

This property specifies a localized value for the [extensions.runtimes.customFunctions.functions.description](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-function?view=m365-app-1.30#description-property) property. The property name should be a JSON path expression in the following form: `extensions[0].runtimes[0-19].customFunctions.functions[0-19999].description`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 128.

**Supported values**  


#### extensions.runtimes.customFunctions.functions.parameters.name

This property specifies a localized value for the [extensions.runtimes.customFunctions.functions.parameters.name](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-function-parameter?view=m365-app-1.30#name-property) property. The property name should be a JSON path expression in the following form: `extensions[0].runtimes[0-19].customFunctions.functions[0-19999].parameters[0-127].name`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 64.

**Supported values**  


#### extensions.runtimes.customFunctions.functions.parameters.description

This property specifies a localized value for the [extensions.runtimes.customFunctions.functions.parameters.description](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-function-parameter?view=m365-app-1.30#description-property) property. The property name should be a JSON path expression in the following form: `extensions[0].runtimes[0-19].customFunctions.functions[0-19999].parameters[0-127].description`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 512.

**Supported values**  


#### extensions.runtimes.customFunctions.functions.parameters.description

This property specifies a localized value for the [extensions.runtimes.customFunctions.functions.parameters.description](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-function-parameter?view=m365-app-1.30#description-property) property. The property name should be a JSON path expression in the following form: `extensions[0].runtimes[0-19].customFunctions.functions[0-19999].parameters[0-127].description`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 128.

**Supported values**  


#### extensions.runtimes.customFunctions.namespace.name

This property specifies a localized value for the [extensions.runtimes.customFunctions.namespace.name](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-custom-functions-namespace?view=m365-app-1.30#name-property) property. The property name should be a JSON path expression in the following form: `extensions[0].runtimes[0-19].customFunctions.namespace.name`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 32.

**Supported values**  


#### extensions.runtimes.customFunctions.enums.values.name

This property specifies a localized value for the [extensions.runtimes.customFunctions.enums.values.name](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/enum-values?view=m365-app-1.30#name-property) property. The property name should be a JSON path expression in the following form: `extensions[0].runtimes[0-19].customFunctions.enums[0-255].values[].name`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 256.

**Supported values**  


#### extensions.runtimes.customFunctions.enums.values.name

This property specifies a localized value for the [extensions.runtimes.customFunctions.enums.values.name](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/enum-values?view=m365-app-1.30#name-property) property. The property name should be a JSON path expression in the following form: `extensions[0].runtimes[0-19].customFunctions.enums[0-19999].values[].name`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 256.

**Supported values**  


#### extensions.runtimes.customFunctions.enums.values.tooltip

This property specifies a localized value for the [extensions.runtimes.customFunctions.enums.values.tooltip](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/enum-values?view=m365-app-1.30#tooltip-property) property. The property name should be a JSON path expression in the following form: `extensions[0].runtimes[0-19].customFunctions.enums[0-255].values[].tooltip`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 256.

**Supported values**  


#### extensions.runtimes.customFunctions.enums.values.tooltip

This property specifies a localized value for the [extensions.runtimes.customFunctions.enums.values.tooltip](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/enum-values?view=m365-app-1.30#tooltip-property) property. The property name should be a JSON path expression in the following form: `extensions[0].runtimes[0-19].customFunctions.enums[0-19999].values[].tooltip`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 256.

**Supported values**  


#### extensions.keyboardShortcuts.shortcuts.key.default

This property specifies a localized value for the [extensions.keyboardShortcuts.shortcuts.key.default](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-key-combination?view=m365-app-1.30#default-property) property. The property name should be a JSON path expression in the following form: `extensions[0].keyboardShortcuts[0-9].shortcuts[0-19999].key.default`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 32.

**Supported values**  


#### extensions.keyboardShortcuts.shortcuts.key.mac

This property specifies a localized value for the [extensions.keyboardShortcuts.shortcuts.key.mac](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-key-combination?view=m365-app-1.30#mac-property) property. The property name should be a JSON path expression in the following form: `extensions[0].keyboardShortcuts[0-9].shortcuts[0-19999].key.mac`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 32.

**Supported values**  


#### extensions.keyboardShortcuts.shortcuts.key.web

This property specifies a localized value for the [extensions.keyboardShortcuts.shortcuts.key.web](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-key-combination?view=m365-app-1.30#web-property) property. The property name should be a JSON path expression in the following form: `extensions[0].keyboardShortcuts[0-9].shortcuts[0-19999].key.web`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 32.

**Supported values**  


#### extensions.keyboardShortcuts.shortcuts.key.windows

This property specifies a localized value for the [extensions.keyboardShortcuts.shortcuts.key.windows](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-key-combination?view=m365-app-1.30#windows-property) property. The property name should be a JSON path expression in the following form: `extensions[0].keyboardShortcuts[0-9].shortcuts[0-19999].key.windows`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 32.

**Supported values**  


#### extensions.contextMenus.menus.controls.icons.url

This property specifies a localized value for the [extensions.contextMenus.menus.controls.icons.url](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-icon?view=m365-app-1.30#url-property) property. The property name should be a JSON path expression in the following form: `extensions[0].contextMenus[].menus[].controls[].icons[0-7].url`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 2048.

**Supported values**  


#### extensions.contextMenus.menus.controls.icons.url

This property specifies a localized value for the [extensions.contextMenus.menus.controls.icons.url](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-icon?view=m365-app-1.30#url-property) property. The property name should be a JSON path expression in the following form: `extensions[0].contextMenus[].menus[].controls[].icons[0-2].url`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 2048.

**Supported values**  


#### extensions.contextMenus.menus.controls.label

This property specifies a localized value for the [extensions.contextMenus.menus.controls.label](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-custom-group-controls-item?view=m365-app-1.30#label-property) property. The property name should be a JSON path expression in the following form: `extensions[0].contextMenus[].menus[].controls[].label`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 64.

**Supported values**  


#### extensions.contextMenus.menus.controls.supertip.title

This property specifies a localized value for the [extensions.contextMenus.menus.controls.supertip.title](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-super-tool-tip?view=m365-app-1.30#title-property) property. The property name should be a JSON path expression in the following form: `extensions[0].contextMenus[].menus[].controls[].supertip.title`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 64.

**Supported values**  


#### extensions.contextMenus.menus.controls.supertip.description

This property specifies a localized value for the [extensions.contextMenus.menus.controls.supertip.description](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-super-tool-tip?view=m365-app-1.30#description-property) property. The property name should be a JSON path expression in the following form: `extensions[0].contextMenus[].menus[].controls[].supertip.description`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 250.

**Supported values**  


#### extensions.contextMenus.menus.controls.items.icons.url

This property specifies a localized value for the [extensions.contextMenus.menus.controls.items.icons.url](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-icon?view=m365-app-1.30#url-property) property. The property name should be a JSON path expression in the following form: `extensions[0].contextMenus[].menus[].controls[].items[0-29].icons[0-7].url`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 2048.

**Supported values**  


#### extensions.contextMenus.menus.controls.items.icons.url

This property specifies a localized value for the [extensions.contextMenus.menus.controls.items.icons.url](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-icon?view=m365-app-1.30#url-property) property. The property name should be a JSON path expression in the following form: `extensions[0].contextMenus[].menus[].controls[].items[0-29].icons[0-2].url`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 2048.

**Supported values**  


#### extensions.contextMenus.menus.controls.items.icons.url

This property specifies a localized value for the [extensions.contextMenus.menus.controls.items.icons.url](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-icon?view=m365-app-1.30#url-property) property. The property name should be a JSON path expression in the following form: `extensions[0].contextMenus[].menus[].controls[].items[0-19].icons[0-2].url`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 2048.

**Supported values**  


#### extensions.contextMenus.menus.controls.items.label

This property specifies a localized value for the [extensions.contextMenus.menus.controls.items.label](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-custom-control-menu-item?view=m365-app-1.30#label-property) property. The property name should be a JSON path expression in the following form: `extensions[0].contextMenus[].menus[].controls[].items[0-29].label`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 64.

**Supported values**  


#### extensions.contextMenus.menus.controls.items.label

This property specifies a localized value for the [extensions.contextMenus.menus.controls.items.label](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-custom-control-menu-item?view=m365-app-1.30#label-property) property. The property name should be a JSON path expression in the following form: `extensions[0].contextMenus[].menus[].controls[].items[0-19].label`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 64.

**Supported values**  


#### extensions.contextMenus.menus.controls.items.supertip.title

This property specifies a localized value for the [extensions.contextMenus.menus.controls.items.supertip.title](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-super-tool-tip?view=m365-app-1.30#title-property) property. The property name should be a JSON path expression in the following form: `extensions[0].contextMenus[].menus[].controls[].items[0-29].supertip.title`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 64.

**Supported values**  


#### extensions.contextMenus.menus.controls.items.supertip.title

This property specifies a localized value for the [extensions.contextMenus.menus.controls.items.supertip.title](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-super-tool-tip?view=m365-app-1.30#title-property) property. The property name should be a JSON path expression in the following form: `extensions[0].contextMenus[].menus[].controls[].items[0-19].supertip.title`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 64.

**Supported values**  


#### extensions.contextMenus.menus.controls.items.supertip.description

This property specifies a localized value for the [extensions.contextMenus.menus.controls.items.supertip.description](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-super-tool-tip?view=m365-app-1.30#description-property) property. The property name should be a JSON path expression in the following form: `extensions[0].contextMenus[].menus[].controls[].items[0-29].supertip.description`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 250.

**Supported values**  


#### extensions.contextMenus.menus.controls.items.supertip.description

This property specifies a localized value for the [extensions.contextMenus.menus.controls.items.supertip.description](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-super-tool-tip?view=m365-app-1.30#description-property) property. The property name should be a JSON path expression in the following form: `extensions[0].contextMenus[].menus[].controls[].items[0-19].supertip.description`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 250.

**Supported values**  


#### copilotAgents.customEngineAgents.disclaimer.text

This property specifies a localized value for the [copilotAgents.customEngineAgents.disclaimer.text](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-copilot-agents-custom-engine-agents-disclaimer?view=m365-app-1.30#text-property) property. The property name should be a JSON path expression in the following form: `copilotAgents.customEngineAgents[0].disclaimer.text`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 500.

**Supported values**  


#### description.features.title

This property specifies a localized value for the [description.features.title](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-description-features?view=m365-app-1.30#title-property) property. The property name should be a JSON path expression in the following form: `description.features[0-2].title`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 45.

**Supported values**  


#### description.features.description

This property specifies a localized value for the [description.features.description](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-description-features?view=m365-app-1.30#description-property) property. The property name should be a JSON path expression in the following form: `description.features[0-2].description`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 120.

**Supported values**  


#### bots.commandLists.commands.prompt

This property specifies a localized value for the [bots.commandLists.commands.prompt](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-command-lists-commands?view=m365-app-1.30#prompt-property) property. The property name should be a JSON path expression in the following form: `bots[0].commandLists[0-2].commands[0-11].prompt`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 4000.

**Supported values**  


#### composeExtensions.commands.samplePrompts.text

This property specifies a localized value for the [composeExtensions.commands.samplePrompts.text](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-compose-extensions-commands-sample-prompts?view=m365-app-1.30#text-property) property. The property name should be a JSON path expression in the following form: `composeExtensions[0].commands[0-9].samplePrompts[0-4].text`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 128.

**Supported values**  


#### extensions.ribbons.tabs.customMobileRibbonGroups.controls.label

This property specifies a localized value for the [extensions.ribbons.tabs.customMobileRibbonGroups.controls.label](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-custom-mobile-control-button-item?view=m365-app-1.30#label-property) property. The property name should be a JSON path expression in the following form: `extensions[0].ribbons[0-19].tabs[0-19].customMobileRibbonGroups[0-9].controls[0-19].label`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 32.

**Supported values**  


#### extensions.ribbons.fixedControls.label

This property specifies a localized value for the [extensions.ribbons.fixedControls.label](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-array-fixed-control-item?view=m365-app-1.30#label-property) property. The property name should be a JSON path expression in the following form: `extensions[0].ribbons[0-19].fixedControls[0].label`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 64.

**Supported values**  


#### extensions.ribbons.fixedControls.label

This property specifies a localized value for the [extensions.ribbons.fixedControls.label](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-array-fixed-control-item?view=m365-app-1.30#label-property) property. The property name should be a JSON path expression in the following form: `extensions[0].ribbons[0-19].fixedControls[].label`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 64.

**Supported values**  


#### extensions.ribbons.fixedControls.supertip.title

This property specifies a localized value for the [extensions.ribbons.fixedControls.supertip.title](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-super-tool-tip?view=m365-app-1.30#title-property) property. The property name should be a JSON path expression in the following form: `extensions[0].ribbons[0-19].fixedControls[0].supertip.title`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 64.

**Supported values**  


#### extensions.ribbons.fixedControls.supertip.title

This property specifies a localized value for the [extensions.ribbons.fixedControls.supertip.title](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-super-tool-tip?view=m365-app-1.30#title-property) property. The property name should be a JSON path expression in the following form: `extensions[0].ribbons[0-19].fixedControls[].supertip.title`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 64.

**Supported values**  


#### extensions.ribbons.fixedControls.supertip.description

This property specifies a localized value for the [extensions.ribbons.fixedControls.supertip.description](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-super-tool-tip?view=m365-app-1.30#description-property) property. The property name should be a JSON path expression in the following form: `extensions[0].ribbons[0-19].fixedControls[0].supertip.description`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 128.

**Supported values**  


#### extensions.ribbons.fixedControls.supertip.description

This property specifies a localized value for the [extensions.ribbons.fixedControls.supertip.description](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-super-tool-tip?view=m365-app-1.30#description-property) property. The property name should be a JSON path expression in the following form: `extensions[0].ribbons[0-19].fixedControls[].supertip.description`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 128.

**Supported values**  


#### extensions.ribbons.spamPreProcessingDialog.title

This property specifies a localized value for the [extensions.ribbons.spamPreProcessingDialog.title](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-spam-pre-processing-dialog?view=m365-app-1.30#title-property) property. The property name should be a JSON path expression in the following form: `extensions[0].ribbons[0-19].spamPreProcessingDialog.title`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 128.

**Supported values**  


#### extensions.ribbons.spamPreProcessingDialog.description

This property specifies a localized value for the [extensions.ribbons.spamPreProcessingDialog.description](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-spam-pre-processing-dialog?view=m365-app-1.30#description-property) property. The property name should be a JSON path expression in the following form: `extensions[0].ribbons[0-19].spamPreProcessingDialog.description`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 250.

**Supported values**  


#### extensions.ribbons.spamPreProcessingDialog.spamFreeTextSectionTitle

This property specifies a localized value for the [extensions.ribbons.spamPreProcessingDialog.spamFreeTextSectionTitle](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-spam-pre-processing-dialog?view=m365-app-1.30#spamFreeTextSectionTitle-property) property. The property name should be a JSON path expression in the following form: `extensions[0].ribbons[0-19].spamPreProcessingDialog.spamFreeTextSectionTitle`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 128.

**Supported values**  


#### extensions.ribbons.spamPreProcessingDialog.spamReportingOptions.title

This property specifies a localized value for the [extensions.ribbons.spamPreProcessingDialog.spamReportingOptions.title](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-spam-pre-processing-dialog-spam-reporting-options?view=m365-app-1.30#title-property) property. The property name should be a JSON path expression in the following form: `extensions[0].ribbons[0-19].spamPreProcessingDialog.spamReportingOptions.title`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 128.

**Supported values**  


#### extensions.ribbons.spamPreProcessingDialog.spamReportingOptions.options

This property specifies a localized value for the [extensions.ribbons.spamPreProcessingDialog.spamReportingOptions.options](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-spam-pre-processing-dialog-spam-reporting-options?view=m365-app-1.30#options-property) property. The property name should be a JSON path expression in the following form: `extensions[0].ribbons[0-19].spamPreProcessingDialog.spamReportingOptions.options[]`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 128.

**Supported values**  


#### extensions.ribbons.spamPreProcessingDialog.spamMoreInfo.text

This property specifies a localized value for the [extensions.ribbons.spamPreProcessingDialog.spamMoreInfo.text](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-spam-pre-processing-dialog-spam-more-info?view=m365-app-1.30#text-property) property. The property name should be a JSON path expression in the following form: `extensions[0].ribbons[0-19].spamPreProcessingDialog.spamMoreInfo.text`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 128.

**Supported values**  


#### extensions.ribbons.spamPreProcessingDialog.spamMoreInfo.url

This property specifies a localized value for the [extensions.ribbons.spamPreProcessingDialog.spamMoreInfo.url](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-spam-pre-processing-dialog-spam-more-info?view=m365-app-1.30#url-property) property. The property name should be a JSON path expression in the following form: `extensions[0].ribbons[0-19].spamPreProcessingDialog.spamMoreInfo.url`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 2048.

**Supported values**  


#### extensions.runtimes.customFunctions.metadataUrl

This property specifies a localized value for the [extensions.runtimes.customFunctions.metadataUrl](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-custom-functions?view=m365-app-1.30#metadataUrl-property) property. The property name should be a JSON path expression in the following form: `extensions[0].runtimes[0-19].customFunctions.metadataUrl`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 2048.

**Supported values**  


#### agentConnectors.displayName

This property specifies a localized value for the [agentConnectors.displayName](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-connectors?view=m365-app-1.30#displayName-property) property. The property name should be a JSON path expression in the following form: `agentConnectors[0-9].displayName`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 128.

**Supported values**  


#### agentConnectors.description

This property specifies a localized value for the [agentConnectors.description](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-connectors?view=m365-app-1.30#description-property) property. The property name should be a JSON path expression in the following form: `agentConnectors[0-9].description`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 4000.

**Supported values**  


## Remarks

The JSON schema uses regular expression to define how the localization file should be structured. For instance, it defines the pattern property for `staticTabs` as:

```json
    "patternProperties": {
      "^staticTabs\\[([0-9]|1[0-5])\\]\\.name$": {
        "type": "string",
        "maxLength": 128
      },
    }
```

- `^` asserts the start of the string, followed by the property `staticTab`.
- `\\[` and `\\]\\` are escape characters for the square brackets.
- `([0-9]|1[0-5])` means any digit between 0-15 is allowed.
- `$` asserts the end of the string.

This allows up to 15 string translations of the `staticTabs.name` property at a max length of 128 characters, as shown in the following example for Spanish:

```json
{
  "staticTabs[0].name": "Editeur de manifest",
  "staticTabs[1].name": "Editeur de cartes",
  "staticTabs[2].name": "Bibliothèque de contrôles",
}
```

## Examples

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.Localization.schema.json",
  "name.short": "Le App",
  "name.full": "App pour Microsoft Teams",
  "description.short": "Créez d'excellentes applications pour Microsoft Teams avec App.",
  "description.full": "Créez de nouvelles applications Microsoft Teams, concevez et prévisualisez des cartes bot, et explorez la documentation avec App.",
  "staticTabs[0].name": "Editeur de manifest",
  "staticTabs[1].name": "Editeur de cartes",
  "staticTabs[2].name": "Bibliothèque de contrôles",
  "bots[0].commandLists[0].commands[0].title": "chercher",
  "bots[0].commandLists[0].commands[0].description": "Rechercher la documentation Teams pertinente"
}
```
