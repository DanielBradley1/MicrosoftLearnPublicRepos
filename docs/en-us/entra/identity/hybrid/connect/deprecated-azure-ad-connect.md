<!-- Source: https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/deprecated-azure-ad-connect -->
<!-- Sitemap-Last-Modified: 2025-07-17 -->

# Using a deprecated version of Microsoft Entra Connect

You may have received a notification email that says that your [Microsoft Entra Connect version is deprecated](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/whatis-azure-ad-connect-v2) and no longer supported. Or, you may have read a portal recommendation about upgrading your Microsoft Entra Connect version. What is next?

Important

Instead of upgrading to the latest version of Microsoft Entra Connect, see if cloud sync is right for you. For more information, evaluate your options using the [supported sync scenarios comparison](https://learn.microsoft.com/en-us/entra/identity/hybrid/common-scenarios)

Using a deprecated and unsupported version of Microsoft Entra Connect isn't recommended and not supported. Deprecated and unsupported versions of Microsoft Entra Connect may **unexpectedly stop working**. In these instances, you may need to install the latest version of Microsoft Entra Connect as your only remedy to restore your sync process.

We regularly update Microsoft Entra Connect with [newer versions](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/reference-connect-version-history). The new versions have bug fixes, performance improvements, new functionality, and security fixes, so it's important to stay up to date.

## How to replace your deprecated version

If you're still using a deprecated and unsupported version of Microsoft Entra Connect, here's what you should do:

1. Verify which version you should install. Most customers no longer need Microsoft Entra Connect and can now use [Microsoft Entra Connect cloud sync](https://learn.microsoft.com/en-us/azure/active-directory/cloud-sync/what-is-cloud-sync). Cloud sync is the next generation of sync tools to provision users and groups from AD into Microsoft Entra ID. It features a lightweight agent and is fully managed from the cloud – and it upgrades to newer versions automatically, so you never have to worry about upgrading again!
2. If you're not yet eligible for Microsoft Entra Connect cloud sync, please follow this [link to download](https://www.microsoft.com/download/details.aspx?id=47594) and install the latest version of Microsoft Entra Connect. In most cases, upgrading to the latest version will only take a few moments. For more information, see [Upgrading Microsoft Entra Connect from a previous version.](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/how-to-upgrade-previous-version).

## Next steps

- [What is Microsoft Entra Connect V2?](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/whatis-azure-ad-connect-v2)
- [Microsoft Entra Connect cloud sync](https://learn.microsoft.com/en-us/azure/active-directory/cloud-sync/what-is-cloud-sync)
- [Microsoft Entra Connect version history](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/reference-connect-version-history)
