<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/workflow -->
<!-- Sitemap-Last-Modified: 2025-02-27 -->

# Integrate Microsoft 365 for the web with document workflow processes

Warning

This documentation is for an upcoming feature and might undergo dramatic changes prior to final release. Pre-release features are available in the [Test environment](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/build-test-ship/environments#test-environment) only.

Hosts can integrate Microsoft 365 for the web into workflow processes, so that users can work with UI directly in Microsoft 365 for the web to manage documents in a workflow.

For example, consider a host that caters to customers in the education field. The host can provide a way for students to submit documents as part of an assignment. With the Microsoft 365 for the web workflow features, hosts can configure Microsoft 365 for the web to display a **Submit** button directly in the Microsoft 365 for the web UI that, when activated, displays host-specific UI letting the student submit the document.

## Supporting workflows in Microsoft 365 for the web

In Microsoft 365 for the web, documents that are a part of workflows display a button that replaces the **Share** button. The button's text is specific to the [WorkflowType](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-other#workflowtype).

| [WorkflowType](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-other#workflowtype) | Microsoft 365 for the web workflow button text |
| --- | --- |
| Assign | Manage Assignment |
| Submit | Turn In |

Important

In Microsoft 365 for the web, the *Assign* and *Submit* workflow types are mutually exclusive. Only one of the two workflow types should be set for a given document session.

Much like **Share**, when clicked, the workflow button can either navigate to a URL in a new browser tab or window or send a message to the [host frame](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/glossary#host-page).

To navigate to a URL, set the [WorkflowUrl](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-other#workflowurl) property to the URL to which Microsoft 365 for the web should navigate.

To post a message to the host frame instead, set the [WorkflowPostMessage](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/customization#workflowpostmessage) property to `true`. When clicked, Microsoft 365 for the web sends the `UI_Workflow` message to the host frame. The message includes the type of workflow that the document is a part of.

Tip

Microsoft 365 for the web always saves the latest copy of the document to the host when the workflow UI is activated. This ensures that the host always has the latest copy of the document to use in the workflow.

## Important considerations

WOPI clients, including Microsoft 365 for the web, aren't designed to understand what the workflow is and how it behaves. In other words, when you use the [WorkflowUrl](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-other#workflowurl) or [WorkflowPostMessage](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/customization#workflowpostmessage) properties, Microsoft 365 for the web displays the workflow button and behaves appropriately when triggered. But if, for example, you want to prevent a user from submitting the same document multiple times, you must handle that in your own UI. In other words, Microsoft 365 for the web and other WOPI clients don't know anything about the workflow process except that a document is a part of a workflow and to display the appropriate UI. This provides a WOPI host great flexibility in their workflows, but the host is also responsible for managing the workflow as a whole.
