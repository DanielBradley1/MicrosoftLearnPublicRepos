<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/core/understand/interoperability-client -->
<!-- Sitemap-Last-Modified: 2025-05-08 -->

# Use the Configuration Manager client software for extended interoperability with future versions of a Current Branch site

*Applies to: Configuration Manager \(current branch\)*

Business requirements might not allow you to regularly update the Configuration Manager client on some devices. For example, you need to follow change management policies, or the device is mission-critical. Accommodate these needs by installing a new client for long-term use, called the extended interoperability client \(EIC\). Only use the EIC for specific devices that can't be frequently updated, like kiosk or point-of-sale devices. Continue to use [automatic client upgrade](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/upgrade/upgrade-clients-for-windows-computers#bkmk_autoupdate) for most of your clients.

## How it works

Typically, when you install a new [in-console update](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/install-in-console-updates) for Configuration Manager, clients automatically update their client software so they can use those new features. With this scenario, you still update to the current branch receiving the new features and updates. Most devices update the Configuration Manager client software with each version update you install. However, on a subset of critical systems that you don't want to receive client software updates, you install the extended interoperability client. These clients don't install new client software until you explicitly deploy a new version of the client software to them.

## Supported versions

For more information on the current supported versions, see [Support for Configuration Manager current branch versions](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/updates#supported-versions).

Tip

The EIC is supported for the client versions which are still in the supported list of Configuration Manager versions. For example, when Configuration Manager 2503 is the latest CB version, EIC supported client version can be on 2403.

Plan to update the extended interoperability client on devices that you manage with the current branch before support for the client expires. To do so, download a new version of the client from Microsoft, and then deploy that updated client software to your devices that use the current extended interoperability client.

## How to use the EIC

1. Add these devices to a collection, and exclude that collection from automatic client upgrades. For more information, see [How to exclude clients from upgrade](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/upgrade/exclude-clients-windows).
2. Obtain a supported version of the EIC from the `\SMSSETUP\Client` folder of the Configuration Manager update installation media. Make sure that you copy the entire contents of the folder.
3. Manually install the EIC on those devices. For more information, see [Manually install the client](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/deploy/deploy-clients-to-windows-computers#BKMK_Manual).

## Limitations

- Updates for the extended interoperability client software aren't available by using in-console updates. For more information on how to update the EIC, see [How to upgrade an excluded client](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/upgrade/exclude-clients-windows#how-to-upgrade-an-excluded-client).
- The EIC only supports the following features:

  - Software updates
  - Hardware and software inventory
  - Packages and programs

## Next steps

[How to exclude clients from upgrade](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/upgrade/exclude-clients-windows)

To make sure that clients are installed correctly on the devices you want, see [How to monitor clients](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/monitor-clients).
