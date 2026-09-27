<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/osd/deploy-use/use-software-center-to-deploy-windows-over-the-network -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# Use Software Center to deploy Windows over the network with Configuration Manager

*Applies to: Configuration Manager \(current branch\)*

You can make a task sequence that installs an OS available in Software Center. A user can run a task sequence from Software Center for the following OS deployment scenarios:

- [Refresh an existing computer with a new version of Windows](https://learn.microsoft.com/en-us/intune/configmgr/osd/deploy-use/refresh-an-existing-computer-with-a-new-version-of-windows)
- [Upgrade Windows to the latest version](https://learn.microsoft.com/en-us/intune/configmgr/osd/deploy-use/upgrade-windows-to-the-latest-version)
- [Create a task sequence for non-OS deployments](https://learn.microsoft.com/en-us/intune/configmgr/osd/deploy-use/create-a-task-sequence-for-non-operating-system-deployments)

Complete the steps in one of those OS deployment scenarios. Then use the following sections to prepare for deployments that are available in Software Center.

## Deploy the task sequence

Deploy the task sequence to a target collection. For more information, see [Deploy a task sequence](https://learn.microsoft.com/en-us/intune/configmgr/osd/deploy-use/deploy-a-task-sequence).

On the **Deployment Settings** page of the deployment, for the **Make available to the following** setting, select one of the following options:

- Only Configuration Manager Clients
- Configuration Manager clients, media and PXE

Also configure whether the deployment is required or available:

- Required deployment: Required deployments make the task sequence available in Software Center. It automatically starts at the configured deadline.
- Available deployment: The task sequence is available in Software Center, and a user can install it on demand.

After you create the deployment, clients in the target collection will show the task sequence in Software Center.

Note

If multiple users are signed in on the device, task sequence deployments might not appear in Software Center until other users are signed out.

## Next steps

[User experiences for OS deployment](https://learn.microsoft.com/en-us/intune/configmgr/osd/understand/user-experience#software-center)
