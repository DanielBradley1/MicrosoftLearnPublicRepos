<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/publish -->
<!-- Sitemap-Last-Modified: 2026-05-13 -->

# Publish the Employee Self-Service agent to your organization

Publishing the Employee Self-Service agent makes it available to your users. Currently, the Employee Self-Service agent supports publishing to Copilot Business Chat.

| Role | Activities to perform | Configuration area |
| --- | --- | --- |
| Environment Maker/ Owner of the Employee Self-Service agent | - Deploy customization solution to target environment  <br>- Set up authentication  <br>- Publish the Employee Self-Service agent | Microsoft Copilot Studio |
| Administrator | - Approve the Employee Self-Service agent publish request  <br>- Deploy it to selected users | Microsoft admin center |
| Business stakeholders/ champions | Identify test users | N/A |

## Deploy customization solution to TEST / UAT / PROD as Managed Solution

Terms to know:

- **UAT** - User acceptance testing
- **PROD** - Production

Steps:

1. Go to the **Solutions** page in Copilot Studio.
2. Select the ellipsis \(**...**\) and choose **Export Solution** for the preferred solution that you set when preparing environments.
3. Before you export the solution, it needs to be published or deployed using the Azure DevOps CI/CD pipelines. This article covers the manual publishing option. See [the Power Platform documentation](https://learn.microsoft.com/en-us/power-platform/alm/pipelines) to understand the Azure DevOps CI/CD pipeline deployment.
4. Select **Publish** to publish all customizations.
5. Select **Next** to export the solution.
6. Specify the version number. We recommend you export as **Managed** if the solution deploys to another nondev environment.
7. You can see the export status on the **Solutions** page. The status banner updates when the export completes.
8. Select **Download** to download the exported solution and save it in a preferred folder.

   Important

   \[No edits are allowed in the downloaded package, as they cause the upload to fail.\]
9. Choose the desired Power Platform environment to deploy and test this exported solution.
10. Ensure all the dependencies required for customization are already available in the target environment. If the dependencies aren't available, imports fail. The following dependencies need to be installed in the desired environment:

    1. The Employee Self-Service agent
    2. Any third-party external system solution packages used in customization

11. Select **Solutions** options from the left navigation pane within the Power Platform environment you selected.
12. Select the **Import Solution** option to import the file you downloaded in step 9.
13. Select the downloaded file using the **Browse** button in the right pane.

## Set up authentication

The Employee Self-Service agent is designed to run on Teams channels and Microsoft Copilot channels.

Important

Microsoft Copilot channel isn't available for the Employee Self-Service agent while using options other than **Authenticate with Microsoft**.

By default, the Employee Self-Service agent uses Microsoft Entra authentication. Therefore, the default option is **Authenticate with Microsoft**.

If your organization needs to use a different identity provider than Microsoft Entra, then you need to choose the **Authenticate manually** option and provide the following information:

- Service provider
- Client ID
- Client secret
- Token exchange URL \(required for single sign-on\)
- Tenant ID

## Review end-user consent experience for SSO-enabled connectors \(optional\)

When employees use the Employee Self‑Service agent for the first time, end users might be prompted to provide consent to SSO‑enabled Power Platform connectors when interacting with the agent.

If your organization prefers to avoid this end‑user consent prompt during onboarding, you can request that this experience be disabled at the environment level before production rollout.

Note

This setting isn't currently available as a self‑service configuration. Customers who prefer to disable this per-user consent prompt can request to have the feature disabled. To file this request:

1. Submit a support request through the Microsoft 365 admin center.
2. In your request, specify that you want to disable the SSO consent form for the Employee Self-Service agent and authorize the connection on behalf of all users.
3. Once the request is received, Microsoft Support guides you through the process of making configuration changes for all connectors in the environment.

Reviewing this option ahead of rollout can help ensure a smoother onboarding experience for end users.

## Publish the Employee Self-Service agent

Note

If your organization's Teams app deployment has its own application lifecycle management/ DevOps process in place for deploying and testing new apps, you can side-load apps into the Teams app store using the **Download.zip** option. Consult your organization's Teams app deployment policies and work with your Teams administrators.

1. Open the **Employee Self-Service** agent in Copilot Studio.
2. Verify the customizations from the imported solution are in place.
3. Select **Channels** in the top navigation bar.
4. Choose **Microsoft Teams**.
5. Select **Edit details** in the details pane for Microsoft Teams. Then check **Make agent available in Microsoft Copilot.**
6. Select the **Availability options** button. Then choose whether to share the agent to everyone in your organization or only to a specific set of users. We recommend you start with a small group of pilot users who can test and provide feedback on the configurations.
7. Choose whether to send email invitations to selected users. You can also choose to show users that this agent is built within Power Platform.
8. Select **Submit for admin approval** to send the Employee Self-Service agent Teams app to your administrator.
9. Confirm your submission.

## Approve the Employee Self-Service agent in Integrated apps as an admin

Approval is the final step to deploy the Employee Self-Service agent to your users through Integrated apps.

1. Sign in to the Microsoft admin center as an administrator with access to Integrated apps.
2. Select **Integrated apps** under **Settings**. You see a notification to approve the published agent.
3. Select **Review request**.
4. Select the appropriate actions to publish the Employee Self-Service agent.
5. Confirm publish or update for the app.
6. Select the **Employee Self-Service agent** from the list of Integrated apps.
7. Select **Deploy app**. Then choose the set of users you want to deploy the app to.

## Workaround if publishing takes more than 48 hours

1. Follow the steps until #6 in the [Publish the Employee Self-Service agent](#publish-the-employee-self-service-agent) section.
2. Use the **Download.zip** option to download the agent manifest.
3. Follow the steps until #2 in the [Approve the Employee Self-Service agent in Integrated apps section](#approve-the-employee-self-service-agent-in-integrated-apps-as-an-admin).
4. Upload the download manifest file from the previous step and follow the rest of the process in the [Approve the Employee Self-Service agent in Integrated apps as an admin](#approve-the-employee-self-service-agent-in-integrated-apps-as-an-admin) section.

Tip

[Run FlightCheck](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/commands-reference#flightcheck-readiness-check) one final time before you submit for admin approval. Proactively validating authentication, channel, and SSO connector configuration here helps prevent publish failures and the 48-hour republishing wait.

## Publishing checklist

| Role | Verification steps | Result |
| --- | --- | --- |
| Environment Maker | 1. Use the **Copy link** option to get the link to the Employee Self-Service agent.  <br>2. Paste the link into a browser.  <br>3. This link redirects to the Teams interface for the Employee Self-Service agent, which provides a link for Microsoft Copilot Chat.  <br>This action is an option to mitigate any publishing lags. | Pass/Fail |

You need to follow the publishing steps again if any of these steps fail.

## Manage Employee Self-Service agent availability

Currently, the Employee Self-Service agent is designed to operate within **Microsoft Copilot**.

While the agent might appear in the **Microsoft Teams app** after publishing, it isn't supported in the standalone Teams experience. Users who access it from Teams might encounter errors or broken functionality.

To provide a better experience for your users, you can:

- **Redirect users from Teams to Copilot**  
  Create a topic in Copilot Studio that detects Teams access and displays a redirect message.
- **Block the agent in Teams**  
  Use the Teams admin center to prevent it from appearing in Teams.

### Redirect users from Microsoft Teams to Microsoft Copilot

You can create a topic in Copilot Studio that detects when the agent is launched from the Microsoft Teams channel. The topic displays a redirect message guiding users to Microsoft Copilot.

When a user opens the agent from Teams, the message appears as follows:

Note

**Looking for the Employee Self-Service Agent? You're almost there!**

1. Open Copilot Business Chat \(BizChat\): [https://www.microsoft365.com/chat](https://www.microsoft365.com/chat).
2. In the left pane, select **Agents**.
3. Choose **All agents** if the agent isn't immediately visible.

**Employee Self-Service** is in the list.

### To create the redirect topic

1. Open the Employee Self-Service agent in Copilot Studio.
2. Select **Topics**.
3. Select **+ Add a topic** → **From blank**.
4. Name the topic \(for example, `Redirect from Teams`\).
5. Paste the following:

   ```yaml
   kind: AdaptiveDialog
   beginDialog:
     kind: OnActivity
     id: main
     condition: =System.Activity.ChannelId = "msteams"
     priority: -1
     actions:
       - kind: SendActivity
         id: sendActivity_dT0g9y
         activity: |
           **Looking for the Employee Self-Service Agent? You're almost there!**
           1. Open https://www.microsoft365.com/chat (BizChat).
           2. In the left pane, select **Agents**.
           3. Choose **All agents** if the agent isn't immediately visible.
           4. You'll find **Employee Self-Service** in the list.
       - kind: EndConversation
         id: aCWPQ6
       - kind: CancelAllDialogs
         id: gd9GgV
   ```

6. Save the topic.
7. Test by opening the agent from Teams in the Copilot Studio test pane.

Note

Update the message if your tenant uses a different agent name.

### Optional: Deep link to the agent

To link directly to the agent:

1. Copy the link from Copilot \(**... → Share**\).
2. Replace the URL in the topic message.

Note

[Auto-pinning](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/agent-registry#manage-pinning-of-agents) is recommended.

### Block the Employee Self-Service agent in Microsoft Teams

To prevent access from Teams:

1. Block the agent in the Teams admin center.
2. This action removes it from discovery and usage in Teams.

To learn more, see [Agent and app governance](https://learn.microsoft.com/en-us/microsoftteams/manage-apps#agent-and-app-governance).

Important

Blocking the agent in Teams doesn't affect availability in Microsoft Copilot. Users can still access it via Copilot Business Chat.

## Uninstall the Employee Self-Service agent

### Core Employee Self-Service agent

Follow these steps if you need to uninstall and delete the Employee Self-Service agent:

1. Sign in to Copilot Studio.
2. Select the environment where the Employee Self-Service agent is installed and needs to be uninstalled.
3. Select **Agents** from the left navigation.
4. Select the respective vertical agent installed for Employee Self-Service agent.
5. Delete all the dependencies, such as knowledge source configuration and other customizations applied, before deleting the solution itself. Otherwise the solution can't be deleted. [Learn more](https://learn.microsoft.com/en-us/power-platform/alm/removing-dependencies) about removing dependencies in Power Platform.
6. In the Employee Self-Service agent page, select the ellipsis \(**...**\) in the upper right pane next to **Test**.
7. Select the **Delete** option from the dropdown. A popup window appears directing you to Power Apps Solutions.
8. Select **Go to Power Apps Solutions**.
9. Identify the **Preferred solution** that you set up during the [installation](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/install) stage for saving customizations in the agent.
10. In the solutions page, select the vertical ellipsis in the context menu and choose **Delete**.
11. Choose **Delete** in the confirmation dialog.

### External systems integration packages

1. Open **Solutions**.

   1. Select the ellipsis \(**...**\) in the left pane of Copilot Studio.
   2. Select **Solutions**.

2. Locate the **Managed external systems integrated packages** option.

   1. Select the **Managed** tab to find the packages you need to uninstall.

3. **Initiate uninstallation**

   1. Select the ellipsis \(**...**\) associated with the external system integration solution.
   2. Select **Uninstall** to start the uninstallation process.

4. Check for **uninstallation errors**.

   1. If the uninstallation fails, a failure message appears at the top of the screen.
   2. Expand the error message to see the detailed reason for the failure.

5. **Identify dependencies**.

   1. The error message may indicate that dependencies vary from environment variables to bot components that need to be delinked before the external systems integration solution can be deleted.

6. Access **external systems integration package details**.

   1. Select the external systems integration package to open its detailed view.

7. View **Environmental Variable Dependencies**

   1. Select **Environmental variables** within the external systems integration packages.
   2. Select **View dependencies** for each variable.

8. **Remove dependencies**

   1. Identify the variables with dependencies and remove these dependencies.
   2. Once all dependencies are removed, retry the uninstallation.
