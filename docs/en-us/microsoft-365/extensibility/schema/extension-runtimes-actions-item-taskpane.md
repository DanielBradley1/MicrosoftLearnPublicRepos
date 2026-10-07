<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-runtimes-actions-item-taskpane?view=m365-app-prev -->
<!-- Sitemap-Last-Modified: 2026-10-01 -->

# extensionRuntimesActionsItem.taskpane object

Configuration for the task pane opened by this action.

Properties that reference this object type:

- [root.extensions.runtimes.actions.taskpane](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-runtimes-actions-item?view=m365-app-prev#taskpane-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "preferredWidth": {number}
}
```

```json
{
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
```

## Properties

#### preferredWidth

Specifies the preferred initial width of the task pane in CSS pixels. This value is treated as a hint and may be adjusted or ignored by the host. User-resized widths always take precedence. Must be a positive number.

**Type**  
number

**Required**  
—

**Constraints**  


**Supported values**
