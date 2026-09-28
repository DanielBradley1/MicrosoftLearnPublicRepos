<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/agent-essentials/agent-lifecycle/agent-upload-agents -->
<!-- Sitemap-Last-Modified: 2026-09-09 -->

# Upload Microsoft Copilot custom agents

Copilot controls in Microsoft 365 admin center provide a way to upload a custom agent so that you can manage it from your organization's agent inventory.

To upload an agent, the agent must be contained in a ZIP packet file. The ZIP file contains resources, such as manifest files, configuration files, icons, branding, and embedded knowledge files.

Your Copilot agent ZIP file can be downloaded from Copilot Studio by selecting **Agents** > *the name of your agent* > **Channels**. Select the channel you use to publish, such as **Teams and Microsoft Copilot**. Select **Availability options** > **Download .zip**.

Note

The ZIP packet file \(.zip\) can also be used to share agents. For more information, see [Sideload agents for personal use](https://learn.microsoft.com/en-us/microsoft-365/copilot/agent-essentials/agent-policies/agent-sideload).

To upload an agent as a ZIP packet file to the Microsoft 365 admin center:

1. Open Copilot controls in [Microsoft 365 admin center](https://admin.microsoft.com/) in your browser.
2. Select **Agents** > **Upload custom agent**.
3. Select **Choose File** to find and select the agent ZIP file. The ZIP file is validated.
4. Verify the agent's name, icon, and host products. Then, select **Next**.
5. Select the assigned users. Then, select **Next**.

   Note

   You can select a small audience for testing purposes. For instance, select **Just me**, or a single test group to narrow the availability of the agent.
6. Review the agent's permissions and capabilities. Then, select **Next**.
7. Select **Finish deployment** to review and finish the agent's deployment.

[![Screenshot of deploying a new agent within M365 Copilot controls.](https://learn.microsoft.com/en-us/microsoft-365/copilot/agent-essentials/media/m365-agents-admin-guide/agent-deploy-new.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/agent-essentials/media/m365-agents-admin-guide/agent-deploy-new.png#lightbox)

To manage, assign, and publish the agent, see [Assign and deploy agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/agent-essentials/agent-lifecycle/agent-deploy).
