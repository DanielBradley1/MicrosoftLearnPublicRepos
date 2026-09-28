<!-- Source: https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/how-to-automatic-upgrade -->
<!-- Sitemap-Last-Modified: 2025-04-09 -->

# Microsoft Entra Connect cloud provisioning agent: Automatic upgrade

Making sure your Microsoft Entra Connect cloud provisioning agent installation is always up to date is easy with the automatic upgrade feature.

The agent is installed here: "Program files\\Azure AD Connect Provisioning Agent\\AADConnectProvisioningAgent.exe"

To verify your version, right-click the executable and select properties and then details.

![Agent file version](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/media/how-to-automatic-upgrade/agent-1.png)

The agent updater is installed here: "Program files\\Azure AD Connect Provisioning Agent Updater\\AzureADConnectAgentUpdater.exe"

To verify your version, right-click the executable and select properties and then details.

![Agent updater version](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/media/how-to-automatic-upgrade/agent-2.png)

## Uninstall the agent

To remove the agent, go to **Uninstall or change a program** and uninstall the following:

- **Microsoft Entra Connect Agent Updater**
- **Microsoft Entra Provisioning Agent**
- **Microsoft Entra Provisioning Agent Package**

![Agent removal](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/media/how-to-automatic-upgrade/agent-3.png)

## Next steps

- [What is provisioning?](https://learn.microsoft.com/en-us/entra/identity/hybrid/what-is-provisioning)
- [What is Microsoft Entra Cloud Sync?](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/what-is-cloud-sync)
