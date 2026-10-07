<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/build-declarative-agents-add-knowledge -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# Add knowledge sources to a declarative agent created with Microsoft 365 Agents Toolkit

You can control the knowledge available to your agent for generating responses with knowledge sources from the web and your Microsoft 365 organizational data. For a full list of the knowledge sources available, see [Add knowledge sources to your declarative agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/knowledge-sources).

Important

This guide assumes you have completed the [Create declarative agents by using Microsoft 365 Agents Toolkit and JSON](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/build-declarative-agents) tutorial.

## Add web search to the agent

Adding web search to your agent allows it to search the web to generate answers. You can optionally scope the knowledge to specific websites.

1. Open the `appPackage/declarativeAgent.json` file and add the `capabilities` array with the following content.

   ```json
   "capabilities": [
     {
       "name": "WebSearch"
     }
   ]
   ```


   For more information, see [Web search object](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-manifest-1.8#web-search-object).

2. Select **Provision** in the **Lifecycle** pane of Microsoft 365 Agents Toolkit.

The declarative agent has access to web content to generate its answers after you reload the page.

![A screenshot showing a response from the declarative agent that contains web content](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/build-da/ttk/web-content.png)

## Add a SharePoint site to the agent

You can add files in OneDrive or the contents of SharePoint sites as a knowledge source.

1. Open the `appPackage/declarativeAgent.json` file and add the following value to the `capabilities` array, replacing `https://contoso.sharepoint.com/sites/ProductSupport` with a SharePoint site URL in your Microsoft 365 organization.

   ```json
   {
     "name": "OneDriveAndSharePoint",
     "items_by_url": [
       {
         "url": "https://contoso.sharepoint.com/sites/ProductSupport"
       }
     ]
   }
   ```


   For more information, see [OneDrive and SharePoint object](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-manifest-1.8#onedrive-and-sharepoint-object).


   Note


   - URLs should be full path to SharePoint items \(site, document library, folder, or file\). You can use the "Copy direct link" option in SharePoint to get the full path or files and folders. Right-click on the file or folder and select **Details**. Navigate to **Path** and select the copy icon.
   - Not specifying the `items_by_url` array \(or the alternative `items_by_sharepoint_ids` array\) causes all OneDrive and SharePoint content in your Microsoft 365 organization that is available to the logged in user to be available to the agent.

2. Select **Provision** in the **Lifecycle** pane of Agents Toolkit.

The declarative agent has access to OneDrive and SharePoint content to generate its answers after you reload the page.

![A screenshot showing a response from the declarative agent that contains SharePoint and OneDrive content](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/build-da/ttk/sharepoint-onedrive-content.png)

## Add Teams messages to the agent

1. Open the `appPackage/declarativeAgent.json` file and add the following value to the `capabilities` array, replacing `https://teams.microsoft.com/l/team/...` with a Teams channel or team URL from your organization.

   ```json
   {
     "name": "TeamsMessages",
     "urls": [
       {
         "url": "https://teams.microsoft.com/l/team/..."
       }
     ]
   }
   ```


   For more information, see [Microsoft Teams messages object](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-manifest-1.8#microsoft-teams-messages-object).


   Note


   - The URL in the `url` property must be a well-formed link to a Teams chat, team, or meeting chat.
   - Not specifying the `urls` array causes all Teams channels, teams, meetings, 1:1 chat, and group chats in your Microsoft 365 organization that is available to the logged in user to be available to the agent.

2. Select **Provision** in the **Lifecycle** pane of Agents Toolkit.

The declarative agent has access to Teams data to generate its answers after you reload the page.

![A screenshot showing a response from the declarative agent that contains Teams content](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/build-da/ttk/teams-content.png)

## Add people knowledge to the agent

The people knowledge source allows you to scope your agent to answer questions about individuals in an organization.

1. Open the `appPackage/declarativeAgent.json` file and add the `People` entry to the `capabilities` array.

   ```json
   {
     "name": "People"
   }
   ```


   For more information, see [People object](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-manifest-1.8#people-object).

2. Select **Provision** in the **Lifecycle** pane of Agents Toolkit.

The declarative agent has access to people knowledge after you reload the page.

![A screenshot showing a response from the declarative agent that contains people knowledge](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/build-da/ttk/people-content.png)

## Add email messages to the agent

The email knowledge source allows you to scope your agent to use email from the user's mailbox or a shared mailbox to answer queries.

1. Open the `appPackage/declarativeAgent.json` file and add the `Email` entry to the `capabilities` array.

   ```json
   {
     "name": "Email",
     "folders": [
       {
         "folder_id": "inbox"
       }
     ]
   }
   ```


   For more information, see [Email object](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-manifest-1.8#email-object).


   Note


   - This example accesses the user of the agent's mailbox. To access a shared mailbox instead, add the optional `shared_mailbox` property set to the email address of the shared mailbox.
   - The `folders` array limits the mailbox access to specific folders. To access the entire mailbox, omit the `folders` array.

2. Select **Provision** in the **Lifecycle** pane of Agents Toolkit.

The declarative agent has access to email knowledge after you reload the page.

![A screenshot showing a response from the declarative agent that contains email knowledge](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/build-da/ttk/email-content.png)

## Add a Copilot connector to the agent

Adding a [Copilot connector](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/overview-copilot-connector) makes the items ingested by that connector available to the agent as a knowledge source.

1. Open the `appPackage/declarativeAgent.json` file and add the following value to the `capabilities` array, replacing `policieslocal` with a valid Copilot connector ID in your Microsoft 365 organization. For more information about how to find Copilot connector IDs, see [Retrieve capability IDs for the declarative agent manifest](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-capabilities-ids#copilot-connectors).

   ```json
   {
     "name": "GraphConnectors",
     "connections": [
       {
         "connection_id": "policieslocal"
       }
     ]
   }
   ```


   For more information, see [Copilot connectors object](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-manifest-1.8#copilot-connectors-object).


   Note


   - Not specifying the `connections` array causes all Copilot connectors content in your Microsoft 365 organization that is available to the logged in user to be available to the agent.

2. Select **Provision** in the **Lifecycle** pane of Agents Toolkit.

The declarative agent has access to Copilot connectors content to generate its answers after you reload the page.

![A screenshot showing a response from the declarative agent that contains Copilot connector content](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/build-da/ttk/graph-connector-content.png)

## Next step

[Add capabilities and custom actions to a declarative agent created with Microsoft 365 Agents Toolkit](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/build-declarative-agents-add-capabilities)
