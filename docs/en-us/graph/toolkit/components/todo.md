<!-- Source: https://learn.microsoft.com/en-us/graph/toolkit/components/todo -->
<!-- Sitemap-Last-Modified: 2025-09-04 -->

# To Do component in Microsoft Graph Toolkit

Caution

The Microsoft Graph Toolkit is deprecated. The retirement period begins September 1, 2025, with full retirement planned for August 28, 2026. Developers should migrate to using the Microsoft Graph SDKs or other supported Microsoft Graph tools for building web experiences. For more information, see the [deprecation announcement](https://devblogs.microsoft.com/microsoft365dev/microsoft-graph-toolkit-retirement/).

The To Do component is used to enable the signed-in user to view, add, remove, complete, and/or edit tasks from Microsoft To Do using the To Do API in Microsoft Graph.

## Example

The following example displays the signed-in user's Microsoft To Do tasks using the `mgt-todo` component. You can use the code editor to see how [properties](#properties) change the behavior of the component.

- [HTML](#tabpanel_1_html)
- [React](#tabpanel_1_react)

<iframe src="https://mgt.dev/iframe.html?id=components-mgt-todo-html--todos&amp;source=docs" data-linktype="external" height="500"></iframe>

[Open this example in mgt.dev](https://mgt.dev/?path=/story/components-mgt-todo-html--todos&source=docs).

<iframe src="https://mgt.dev/iframe.html?id=components-mgt-todo-react--todos&amp;source=docs" data-linktype="external" height="500"></iframe>

[Open this example in mgt.dev](https://mgt.dev/?path=/story/components-mgt-todo-react--todos&source=docs).

## Properties

You can use the following attributes and properties to customize the component.

| Attribute | Property | Description |
| --- | --- | --- |
| read-only | readOnly | A Boolean to set the task interface to be read only \(no adding or removing tasks\). Default is `false`. |
| initial-id="folder\_id" | initialId | A string ID to set the initially displayed folder to the provided ID. |
| target-id="folder\_id" | targetId | A string ID to lock the tasks interface to the provided folder ID. |
| N/A | isNewTaskVisible | Determines whether new task view is visible at render. |
| N/A | taskFilter | An optional function to filter which tasks are shown to the user. |

The following example shows only tasks from the folder with ID *12345* and does not allow the user to create new tasks.

```html
<mgt-todo read-only initial-id="12345"></mgt-todo>
```

## Custom CSS variables

The `mgt-todo` component defines the following CSS custom properties.

```html
<mgt-todo class="todo"></mgt-todo>
```

```css
.todo {
    --task-new-cancel-button-color: blue;
    --task-detail-color: purple;
    --task-color: black;
    --task-background-color: white;
    --task-complete-background-color: grey;
    --task-date-input-active-color: blue;
    --task-date-input-hover-color: green;
    --task-background-color-hover: grey;
    --task-box-shadow: 0 0 10px 0 rgba(0, 0, 0, 0.2);
    --task-border: 1px solid black;
    --task-border-completed: 1px solid grey;
    --task-radio-background-color: green;
}
```

To learn more, see [styling components](https://learn.microsoft.com/en-us/graph/toolkit/customize-components/style).

## Events

The following events are fired from the component.

| Event | When is it emitted | Custom data | Cancelable | Bubbles | Works with custom template |
| --- | --- | --- | :---: | :---: | :---: |
| `taskClick` | Fires when the user clicks or taps on a task | Selected [task](https://github.com/microsoftgraph/microsoft-graph-toolkit/blob/66a5bbb6591e6260e95dbc00c0d06bcbe8dcef38/packages/mgt-components/src/components/mgt-todo/graph.todo.ts#L41) | No | No | No |

For more information about handling events, see [events](https://learn.microsoft.com/en-us/graph/toolkit/customize-components/events).

## Templates

The `todo` component supports several [templates](https://learn.microsoft.com/en-us/graph/toolkit/customize-components/templates) that allow you to replace certain parts of the component. To specify a template, include a `<template>` element inside a component and set the `data-type` to one of the following values.

| Data type | Data context | Description |
| --- | --- | --- |
| task | task: a To Do task object | Replaces the whole default task. |
| task-details | task: a To Do task object | Template replaces the details section of the task. |

The following example defines a template for the tasks component.

```html
<mgt-todo>
    <template data-type="task-details">
        <div>
            Importance Level: {{task.importance}}
        </div>
    </template>
</mgt-todo>
```

## Microsoft Graph permissions

This control uses the following Microsoft Graph APIs and permissions. For each API called, the user must have at least one of the listed permissions.

| Configuration | Permission | API |
| --- | --- | --- |
| `targetId` or `initialId` set | Tasks.Read, Tasks.ReadWrite | [/me/todo/lists/${listId}](https://learn.microsoft.com/en-us/graph/api/todotasklist-get?tabs=http), [/me/todo/lists/{todoTaskListId}/tasks](https://learn.microsoft.com/en-us/graph/api/todotasklist-list-tasks) |
| `targetId` not set | Tasks.Read, Tasks.ReadWrite | [/me/todo/lists](https://learn.microsoft.com/en-us/graph/api/todo-list-lists?tabs=http), [/me/todo/lists/{todoTaskListId}/tasks](https://learn.microsoft.com/en-us/graph/api/todotasklist-list-tasks) |
| create, update or delete task | Tasks.ReadWrite | [/me/todo/lists/{todoTaskListId}/tasks/{taskId}](https://learn.microsoft.com/en-us/graph/api/todotask-get) |

## Authentication

The todo component uses the global authentication provider described in the [authentication documentation](https://learn.microsoft.com/en-us/graph/toolkit/providers/providers).

## Cache

The `mgt-todo` component doesn't cache any data.

## Localization

The control exposes the following variables that can be localized. For more information, see [Localizing components](https://learn.microsoft.com/en-us/graph/toolkit/customize-components/localization).

| String name | Default value |
| --- | --- |
| cancelNewTaskSubtitle | `Cancel` |
| newTaskPlaceholder | `Add a task` |
| newTaskLabel | `New Task Input` |
| addTaskButtonSubtitle | `Add` |
| deleteTaskLabel | `Delete Task` |
| dueDate | `Due date` |
| newTaskDateInputLabel | `New Task Date Input` |
| newTaskNameInputLabel | `New Task Name Input` |
| cancelAddingTask | `Cancel adding a new task` |
