<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/remote-control/prerequisites-for-remote-control -->
<!-- Sitemap-Last-Modified: 2023-02-22 -->

# Prerequisites for remote control in Configuration Manager

*Applies to: Configuration Manager \(current branch\)*

Remote control in Configuration Manager has external dependencies and dependencies in the product.

## Dependencies external to Configuration Manager

To help improve performance, install the most up-to-date video driver on client devices.

You can't use Configuration Manager remote control to remotely administer client computers that run versions of the Configuration Manager client earlier than current branch.

Note

No Windows services are required as an external dependency for remote control.

### Supported operating systems for the remote control viewer

The remote control viewer is supported on all operating systems that are supported for the Configuration Manager console. For information, see [Supported configurations for Configuration Manager consoles](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/configs/supported-operating-systems-consoles).

The following OS versions don't support the remote control viewer, but they do support the remote control client:

- Windows Embedded
- Windows Embedded for Point of Service \(POS\)
- Windows Fundamentals for Legacy PCs

## Configuration Manager dependencies

### Enable remote control

By default, remote control isn't enabled when you install Configuration Manager. For more information about how to enable and configure remote control, see [Configure remote control](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/remote-control/configuring-remote-control).

### Reporting

Before you can run reports for remote control, install the reporting services point site system role. For more information, see [Introduction to reporting](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/introduction-to-reporting).

### Security permissions

- To access collection resources and to start a remote control session from the Configuration Manager console, your account needs the **Read**, **Read Resource**, and **Remote Control** permissions for the **Collection** object.
- The **Remote Tools Operator** security role includes the permissions that are required to manage remote control in Configuration Manager.
- Permitted viewers must be given permission to use remote control by adding these users to the **Permitted viewers of Remote Control and Remote Assistance** list in the **Remote Tools** client settings.

For more information, see [Configure role-based administration](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/configure-role-based-administration).

### Remote clients

Remote tools aren't supported for clients that are connected remotely. For example, you can't remote control a client that communicates with the site through a cloud management gateway \(CMG\). For more information about the network ports required for remote tools, see [Ports used in Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/hierarchy/ports#BKMK_PortsConsole-Client).

Tip

For tenant-attached devices, remote tools are available in the Microsoft Intune admin center. For more information, see [Support for remote tools](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/supported-configurations#bkmk_note3).

## Next steps

[Configure remote control](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/remote-control/configuring-remote-control)
