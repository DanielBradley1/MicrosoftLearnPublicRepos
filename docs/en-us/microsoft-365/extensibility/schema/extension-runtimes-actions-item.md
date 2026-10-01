<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-runtimes-actions-item?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# extensionRuntimesActionsItem object

Specifies the set of actions supported by this runtime. An action is either running a JavaScript function or opening a view such as a task pane.

Properties that reference this object type:

- [root.extensions.runtimes.actions](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-runtimes-array?view=m365-app-1.30#actions-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "id": "{string}",
  "type": "executeFunction | openPage | executeDataFunction",
  "displayName": "{string}",
  "pinnable": {boolean},
  "view": "{string}",
  "multiselect": {boolean},
  "supportsNoItemContext": {boolean},
  "taskpane": {
    "preferredWidth": {number}
  }
}
```

```json
{
  "type": "object",
  "properties": {
    "id": {
      "type": "string",
      "description": "Identifier for this action. Maximum length is 64 characters. This value is passed to the code file.",
      "maxLength": 64
    },
    "type": {
      "type": "string",
      "enum": [
        "executeFunction",
        "openPage",
        "executeDataFunction"
      ],
      "description": "executeFunction: Run a script function without waiting for it to finish. openPage: Open a page in a view. executeDataFunction: invoke command and retrieve data."
    },
    "displayName": {
      "type": "string",
      "description": "Display name of the action. Maximum length is 64 characters.",
      "maxLength": 64
    },
    "pinnable": {
      "type": "boolean",
      "description": "Specifies that a task pane supports pinning, which keeps the task pane open when the user changes the selection."
    },
    "view": {
      "type": "string",
      "description": "View where the page should be opened. Maximum length is 64 characters.  ",
      "maxLength": 64
    },
    "multiselect": {
      "type": "boolean",
      "description": "Whether allows the action to have multiple selection.",
      "default": false
    },
    "supportsNoItemContext": {
      "type": "boolean",
      "description": "Whether allows task pane add-ins to activate without the Reading Pane enabled or a message selected. ",
      "default": false
    },
    "taskpane": {
      "type": "object",
      "description": "Configuration for the task pane opened by this action.",
      "properties": {
        "preferredWidth": {
          "type": "number",
          "description": "Specifies the preferred initial width of the task pane in CSS pixels. This value is treated as a hint and may be adjusted or ignored by the host. User-resized widths always take precedence. Must be a positive number.",
          "minimum": 0,
          "exclusiveMinimum": true
        }
      },
      "additionalProperties": false
    }
  },
  "additionalProperties": false,
  "required": [
    "id",
    "type"
  ]
}
```

- [Syntax](#tabpanel_2_syntax)
- [Schema](#tabpanel_2_schema)

```json
{
  "id": "{string}",
  "type": "executeFunction | openPage | executeDataFunction",
  "displayName": "{string}",
  "pinnable": {boolean},
  "view": "{string}",
  "multiselect": {boolean},
  "supportsNoItemContext": {boolean}
}
```

```json
{
  "type": "object",
  "properties": {
    "id": {
      "type": "string",
      "description": "Identifier for this action. Maximum length is 64 characters. This value is passed to the code file.",
      "maxLength": 64
    },
    "type": {
      "type": "string",
      "enum": [
        "executeFunction",
        "openPage",
        "executeDataFunction"
      ],
      "description": "executeFunction: Run a script function without waiting for it to finish. openPage: Open a page in a view. executeDataFunction: invoke command and retrieve data."
    },
    "displayName": {
      "type": "string",
      "description": "Display name of the action. Maximum length is 64 characters.",
      "maxLength": 64
    },
    "pinnable": {
      "type": "boolean",
      "description": "Specifies that a task pane supports pinning, which keeps the task pane open when the user changes the selection."
    },
    "view": {
      "type": "string",
      "description": "View where the page should be opened. Maximum length is 64 characters.  ",
      "maxLength": 64
    },
    "multiselect": {
      "type": "boolean",
      "description": "Whether allows the action to have multiple selection.",
      "default": false
    },
    "supportsNoItemContext": {
      "type": "boolean",
      "description": "Whether allows task pane add-ins to activate without the Reading Pane enabled or a message selected. ",
      "default": false
    }
  },
  "additionalProperties": false,
  "required": [
    "id",
    "type"
  ]
}
```

- [Syntax](#tabpanel_3_syntax)
- [Schema](#tabpanel_3_schema)

```json
{
  "id": "{string}",
  "type": "executeFunction | openPage",
  "displayName": "{string}",
  "pinnable": {boolean},
  "view": "{string}",
  "multiselect": {boolean},
  "supportsNoItemContext": {boolean}
}
```

```json
{
  "type": "object",
  "properties": {
    "id": {
      "type": "string",
      "description": "Identifier for this action. Maximum length is 64 characters. This value is passed to the code file.",
      "maxLength": 64
    },
    "type": {
      "type": "string",
      "enum": [
        "executeFunction",
        "openPage"
      ],
      "description": "executeFunction: Run a script function without waiting for it to finish. openPate: Open a page in a view."
    },
    "displayName": {
      "type": "string",
      "description": "Display name of the action. Maximum length is 64 characters.",
      "maxLength": 64
    },
    "pinnable": {
      "type": "boolean",
      "description": "Specifies that a task pane supports pinning, which keeps the task pane open when the user changes the selection."
    },
    "view": {
      "type": "string",
      "description": "View where the page should be opened. Maximum length is 64 characters.  ",
      "maxLength": 64
    },
    "multiselect": {
      "type": "boolean",
      "description": "Whether allows the action to have multiple selection.",
      "default": false
    },
    "supportsNoItemContext": {
      "type": "boolean",
      "description": "Whether allows task pane add-ins to activate without the Reading Pane enabled or a message selected. ",
      "default": false
    }
  },
  "additionalProperties": false,
  "required": [
    "id",
    "type"
  ]
}
```

## Properties

#### id

Specifies the ID for the action.

Tip

When the `type` value is `executeFunction` or `executeDataFunction`, the ID used here is is passed to the [code file](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-runtimes-array?view=m365-app-1.30#code-property). In that file, the ID is mapped to a specific JavaScript function by a call of [Office.action.associate](https://learn.microsoft.com/en-us/javascript/api/office/office.actions#office-office-actions-associate-member\(1\)) in the code file. In most cases, you can just use the same string as the actual name of the function. But the code file can also have branching logic that maps different functions onto the action ID depending on which branch is taken. In that case, consider using a more generic action ID, but be as descriptive as possible. If possible, avoid uninformative action IDs such as "action".

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 64.

**Supported values**  


#### type

Specifies the type of action. The following are the possible values.

- `openPage`: Opens a page in a task pane.
- `executeFunction`: Runs a JavaScript function, usually invoked by a button, menu item, or keyboard shortcut. For more information, see [Create add-in commands](https://learn.microsoft.com/en-us/office/dev/add-ins/develop/create-addin-commands-unified-manifest).
- `executeDataFunction`: Runs a JavaScript function that is invoked by a Copilot agent.

Note

- Once the user starts an action of type `executeFunction`, the runtime in which it executes times out after five minutes if the function hasn't completed by then.
- Once the user starts an action of type `executeDataFunction`, the runtime in which it executes times out after two minutes if the function hasn't completed by then.
- Outlook [Mailbox](https://learn.microsoft.com/en-us/javascript/api/requirement-sets/outlook/preview-requirement-set/office.context.mailbox#events) and [Item](https://learn.microsoft.com/en-us/javascript/api/requirement-sets/outlook/preview-requirement-set/office.context.mailbox.item#events) event handlers can't be registered in `executeFunction` or `executeDataFunction` actions. Only functions invoked from a task pane can do this.

**Type**  
string

**Required**  
✅

**Constraints**  


**Supported values**  
Allowed values: `executeFunction`, `openPage`, `executeDataFunction`.

#### type

Specifies the type of action. The following are the possible values.

- `openPage`: Opens a page in a task pane.
- `executeFunction`: Runs a JavaScript function, usually invoked by a button, menu item, or keyboard shortcut. For more information, see [Create add-in commands](https://learn.microsoft.com/en-us/office/dev/add-ins/develop/create-addin-commands-unified-manifest).
- `executeDataFunction`: Runs a JavaScript function that is invoked by a Copilot agent.

Note

- Once the user starts an action of type `executeFunction`, the runtime in which it executes times out after five minutes if the function hasn't completed by then.
- Once the user starts an action of type `executeDataFunction`, the runtime in which it executes times out after two minutes if the function hasn't completed by then.
- Outlook [Mailbox](https://learn.microsoft.com/en-us/javascript/api/requirement-sets/outlook/preview-requirement-set/office.context.mailbox#events) and [Item](https://learn.microsoft.com/en-us/javascript/api/requirement-sets/outlook/preview-requirement-set/office.context.mailbox.item#events) event handlers can't be registered in `executeFunction` or `executeDataFunction` actions. Only functions invoked from a task pane can do this.

**Type**  
string

**Required**  
✅

**Constraints**  


**Supported values**  
Allowed values: `executeFunction`, `openPage`.

#### type

Specifies the type of action. The following are the possible values.

- `openPage`: Opens a page in a task pane.
- `executeFunction`: Runs a JavaScript function, usually invoked by a button, menu item, or keyboard shortcut. For more information, see [Create add-in commands](https://learn.microsoft.com/en-us/office/dev/add-ins/develop/create-addin-commands-unified-manifest).

Note

- Once the user starts an action of type `executeFunction`, the runtime in which it executes times out after five minutes if the function hasn't completed by then.
- Outlook [Mailbox](https://learn.microsoft.com/en-us/javascript/api/requirement-sets/outlook/preview-requirement-set/office.context.mailbox#events) and [Item](https://learn.microsoft.com/en-us/javascript/api/requirement-sets/outlook/preview-requirement-set/office.context.mailbox.item#events) event handlers can't be registered in `executeFunction` actions. Only functions invoked from a task pane can do this.

**Type**  
string

**Required**  
✅

**Constraints**  


**Supported values**  
Allowed values: `executeFunction`, `openPage`.

#### displayName

If the add-in includes a custom keyboard shortcut to invoke the action, this property specifies a description of a shortcut in a dialog that reports a conflict between the custom shortcut and a shortcut built into Office or installed with another add-in. This property is *not* the label of a button or a menu item that invokes the action \(which is configured with `tabs.groups.controls.label`\).

This property is localizable. For more information, see the [localization schema](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/loc-schema/root?view=m365-app-1.30).

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 64.

**Supported values**  


#### pinnable

Specifies that a task pane supports pinning, which keeps the task pane open when the user changes the selection.

This property is used only when `actions.type` is `openPage`. For more information, see [Implement a pinnable task pane in Outlook](https://learn.microsoft.com/en-us/office/dev/add-ins/outlook/pinnable-taskpane).

Important

Pinning a task pane is currently only supported for Microsoft 365 subscribers using the following:

- Modern Outlook on the web
- [new Outlook on Windows](https://support.microsoft.com/office/656bb8d9-5a60-49b2-a98b-ba7822bc7627)
- Outlook 2016 or later on Windows \(Version 1612 \(Build 7628.1000\) or later\)
- Outlook on Mac \(Version 16.13 \(18050300\) or later\)

**Type**  
boolean

**Required**  
—

**Constraints**  


**Supported values**  


#### view

Specifies a descriptive name for the task pane container; for example, "MainAppDashboard".

This property is used only when `actions.type` is `openPage`. When you have multiple `openPage` actions, use a different `view` if you want an independent pane for each. Use the same `view` for different pages that share the same pane. When users choose an action of type `openPage` that shares the same `view`, the pane container will remain open, but the contents of the pane will be replaced with the corresponding `runtimes.code.page`.

Note

The `view` property isn't supported in Outlook.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 64.

**Supported values**  


#### multiselect

Specifies whether the end user can select multiple email messages, and apply the action to all of them.

This property is only supported in Outlook add-ins, and only when the `extensions.ribbons.contexts` array includes `mailRead` or `mailCompose`. To learn more about item multi-select, see [Activate your Outlook add-in on multiple messages](https://learn.microsoft.com/en-us/office/dev/add-ins/outlook/item-multi-select).

**Type**  
boolean

**Required**  
—

**Constraints**  


**Supported values**  
Default value: `False`.

#### supportsNoItemContext

Enables task pane add-ins to activate without the reading pane enabled or a message selected.

This property is only supported in Outlook add-ins, and only when the `extensions.ribbons.contexts` array includes `mailRead`. To learn more, see [Activate your Outlook add-in without the Reading Pane enabled or a message selected](https://learn.microsoft.com/en-us/office/dev/add-ins/outlook/contextless).

Note

In Outlook on the web and new Outlook on Windows, an add-in won't activate if the Reading Pane is hidden or a message isn't first selected. To learn more, see [Feature support in Outlook on the web and new Outlook on Windows](https://learn.microsoft.com/en-us/office/dev/add-ins/outlook/contextless#feature-support-in-outlook-on-the-web-and-new-outlook-on-windows).

**Type**  
boolean

**Required**  
—

**Constraints**  


**Supported values**  
Default value: `False`.

#### taskpane

Configuration for the task pane opened by this action.

**Type**  
[taskpane](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-runtimes-actions-item-taskpane?view=m365-app-1.30)

**Required**  
—

**Constraints**  


**Supported values**  


## Examples

```json
{
    "extensions": [
        {
          "runtimes": [
            {
              "actions": [
                {
                  "id": "ShowTaskPane",
                  "type": "openPage",
                  "view": "MainAppDashboard"
                },
                {
                  "id": "InsertText",
                  "type": "executeFunction"
                },
                {
                  "id": "DeleteTableHeader",
                  "type": "executeFunction"
                }
              ]
            }
          ],
        }
    ]
}
```
