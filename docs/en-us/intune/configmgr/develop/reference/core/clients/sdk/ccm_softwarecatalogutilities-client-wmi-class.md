<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/ccm_softwarecatalogutilities-client-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# CCM\_SoftwareCatalogUtilities Client WMI Class

The `CCM_SoftwareCatalogUtilities` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that provides a set of utility methods to assist in processing software updates.

Important

The software update client side SDK will only return set of updates which are deployed to client from Configuration Manager site server, and are applicable, and are yet to be installed on the client.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class CCM_SoftwareCatalogUtilities :
{
};
```

## Methods

The following table lists the methods in the `CCM_SoftwareCatalogUtilities` class.

- [ApplyPolicyEx Method in Class CCM\_SoftwareCatalogUtilities](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/applypolicyex-method-in-class-ccm_softwarecatalogutilities)
- [GetClientVersion Method in Class CCM\_SoftwareCatalogUtilities](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/getclientversion-method-in-class-ccm_softwarecatalogutilities)
- [GetDeviceId Method in Class CCM\_SoftwareCatalogUtilities](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/getdeviceid-method-in-class-ccm_softwarecatalogutilities)
- [GetPolicyState Method in Class CCM\_SoftwareCatalogUtilities](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/getpolicystate-method-in-class-ccm_softwarecatalogutilities)
- [GetPortalUrlValue Method in Class CCM\_SoftwareCatalogUtilities](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/getportalurlvalue-method-in-class-ccm_softwarecatalogutilities)
- [VerifySignature Method in Class CCM\_SoftwareCatalogUtilities](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/verifysignature-method-in-class-ccm_softwarecatalogutilities)

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
