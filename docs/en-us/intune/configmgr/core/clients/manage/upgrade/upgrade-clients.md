<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/upgrade/upgrade-clients -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# Upgrade clients in Configuration Manager

*Applies to: Configuration Manager \(current branch\)*

You can use different methods to upgrade the Configuration Manager client software on Windows computers and Mac computers. Here are the advantages and disadvantages of each method.

Tip

If you are upgrading your server infrastructure from System Center 2012 Configuration Manager, before upgrading the Configuration Manager clients, complete the server upgrades including installing all current branch updates. This process makes sure that you'll have the most recent version of the client software.

## Group Policy installation

Supported client platform: **Windows**

Advantages:

- Doesn't require computers to be discovered before the client can be upgraded.
- Can be used for new client installations or for upgrades.
- Computers can read client installation properties that have been published to Active Directory Domain Services.
- Doesn't require you to configure and maintain an installation account for the intended client computer.

Disadvantages:

- Can cause high network traffic if you're upgrading many clients.
- If you don't extend the Active Directory schema for Configuration Manager, use [Group Policy settings](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/deploy/deploy-clients-to-windows-computers#BKMK_ClientGP). These settings add client installation properties to computers in your site.

## Logon script installation

Supported client platform: **Windows**

Advantages:

- Doesn't require computers to be discovered before the client can be installed.
- Can be used for new client installations or for upgrades.
- Supports using command-line properties for CCMSetup.

Disadvantages:

- Can cause high network traffic if you're upgrading many clients in a short time.
- Can take a long time to upgrade all client computers if users don't frequently sign in to the network.

For more information, see [How to install clients by using logon scripts](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/deploy/deploy-clients-to-windows-computers#BKMK_ClientLogonScript).

## Manual installation

Supported client platform: **Windows**, **macOS**

Advantages:

- Doesn't require computers to be discovered before the client can be upgraded.
- Can be useful for testing purposes.
- Supports using command-line properties for CCMSetup.

Disadvantages:

- No automation, so can be time consuming.

For more information, see the following articles:

- [How to install clients manually](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/deploy/deploy-clients-to-windows-computers#BKMK_Manual)
- [How to upgrade clients on Mac computers](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/upgrade/upgrade-clients-on-mac-computers)

## Upgrade installation \(application management\)

Supported client platform: **Windows**

Advantages:

- Supports using command-line properties for CCMSetup.

Disadvantages:

- Can cause high network traffic if you distribute the client to large collections.
- Can only be used to upgrade the client software on computers that have been discovered and assigned to the site.

For more information, see [How to install clients by using a package and program](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/deploy/deploy-clients-to-windows-computers#BKMK_ClientApp).

## Automatic client upgrade

Supported client platform: **Windows**

Advantages:

- Because of the randomization over the specified period, only auto-upgrade is suitable for large-scale client upgrades. Other methods are either too slow on large scale, or don't have randomization.

  Note

  Client piloting isn't good for large scale as it doesn't randomize at all.
- Can be used to automatically keep clients in your site at the latest version.
- Requires minimal administration.

Disadvantages:

- Can only be used to upgrade the client software and can't be used to install a new client.
- Applies to all clients in the hierarchy that are assigned to a site. Can't be scoped by collection.
- Limited scheduling options.

For more information, see [How to upgrade clients for Windows computers](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/upgrade/upgrade-clients-for-windows-computers).

## Client testing

Supported client platform: **Windows**

Advantages:

- Can be used to test new client versions in a smaller pre-production collection.
- When testing is complete, clients in pre-production are promoted to production and automatically upgraded across the Configuration Manager site.

Disadvantages:

- Can only be used to upgrade the client software and can't be used to install a new client.

For more information, see [How to test client upgrades in a pre-production collection](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/upgrade/test-client-upgrades).

## Next steps

[How to test client upgrades in a pre-production collection](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/upgrade/test-client-upgrades)

[How to exclude clients from upgrade](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/upgrade/exclude-clients-windows)

[How to upgrade clients for Windows computers](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/upgrade/upgrade-clients-for-windows-computers)
