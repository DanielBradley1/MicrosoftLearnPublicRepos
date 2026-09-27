<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/install-site-system-roles -->
<!-- Sitemap-Last-Modified: 2025-09-16 -->

# Install site system roles for Configuration Manager

*Applies to: Configuration Manager \(current branch\)*

There are two methods in the Configuration Manager console to install site system roles:

- **Add Site System Roles**: Add site system roles to an existing site system server in the site.
- **Create Site System Server**: Specify a new server as a site system server, and then install one or more roles. This method is the same as the **Add Site System Roles**, except for the first page. You first specify the name of the server and the site in which you want to install it.

Tip

A best practice for security and operational resilience is to keep site system roles separate from the site server, rather than colocate them on the same computer. When you install a role on a remote computer, Configuration Manager adds the computer account of the remote computer to a local group on the site server.

When you install the site on a domain controller, the group on the site server is a domain group instead of a local group. In this case, the remote site system role doesn't immediately work. The site system server needs to restart, or you refresh the Kerberos ticket for the remote server's computer account. For more information, see [Accounts used](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/hierarchy/accounts).

Before it installs the site system role, Configuration Manager checks the destination computer to make sure it meets the prerequisites for the selected roles.

By default, when Configuration Manager installs a site system role, it installs files on the first available NTFS-formatted disk drive that has the most available free disk space. To prevent Configuration Manager from installing on specific drives, before you install the site system server, create an empty file named **NO\_SMS\_ON\_DRIVE.SMS** in the root of the drive.

Configuration Manager uses the **site system installation account** to install roles. You specify this account when you install the role. By default, this account is the local system account of the site server computer. You can specify a domain user account as the site system installation account. For more information, see [Accounts - Site system installation account](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/hierarchy/accounts#site-system-installation-account).

## Install roles on an existing site system server

1. In the Configuration Manager console, go to the **Administration** workspace. Expand **Site Configuration**, and select the **Servers and Site System Roles** node. Select the existing site system server on which you want to install new site system roles.
2. In the ribbon, on the **Home** tab, in the **Server** group, select **Add Site System Roles**.
3. On the **General** page, review the settings.

   Tip

   To access the site system role from the internet, make sure that you specify an internet fully qualified domain name \(FQDN\).
4. On the **Proxy** page, if roles on this server require an internet proxy, then specify settings for a proxy server. For more information, see [Proxy server support](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/network/proxy-server-support).
5. On the **System Role Selection** page, select the site system roles that you want to add.
6. Complete the wizard. Additional pages can appear for specific roles. For more information, see [Configuration options for site system roles](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/configuration-options-for-site-system-roles).

Tip

The Windows PowerShell cmdlet, **New-CMSiteSystemServer**, performs the same function as this procedure. For more information, see [New-CMSiteSystemServer](https://learn.microsoft.com/en-us/powershell/module/configurationmanager/new-cmsitesystemserver).

## Install roles on a new site system server

1. In the Configuration Manager console, go to the **Administration** workspace. Expand **Site Configuration**, and select the **Servers and Site System Roles** node.
2. In the ribbon, on the **Home** tab, in the **Create** group, select **Create Site System Server**.
3. On the **General** page, specify the general settings for the site system.

   Tip

   To access the new site system role from the internet, make sure that you specify an internet FQDN.
4. On the **Proxy** page, if roles on this server require an internet proxy, then specify settings for a proxy server. For more information, see [Proxy server support](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/network/proxy-server-support).
5. On the **System Role Selection** page, select the site system roles that you want to add.
6. Complete the wizard. Additional pages can appear for specific roles. For more information, see [Configuration options for site system roles](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/configuration-options-for-site-system-roles).

Tip

The Windows PowerShell cmdlet, **New-CMSiteSystemServer**, performs the same function as this procedure. For more information, see [New-CMSiteSystemServer](https://learn.microsoft.com/en-us/powershell/module/configurationmanager/new-cmsitesystemserver).

## Next steps

- [Configuration options for site system roles](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/configuration-options-for-site-system-roles)
- [Remove role](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/install/uninstall-sites-and-hierarchies#bkmk_role)
