<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ipxeauthclass-interface -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# IPxeAuthClass Interface

The `IPxeAuthClass` automation interface, in Configuration Manager, enables configuration of a PXE service point by serializing certificate information in the form that is required for the [SubmitRegistrationRecord Method in Class SMS\_Site](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/submitregistrationrecord-method-in-class-sms_site). This interface inherits from `IDispatch`.

## In This Section

| Term | Definition |
| --- | --- |
| [IPxeAuthClass::CreateIdentity Method](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ipxeauthclass--createidentity-method) | Creates a PXE certificate identity used in the client configuration file. |
| [IPxeAuthClass::ReadIdentity Method](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ipxeauthclass--readidentity-method) | Reads a PXE certificate identity from the client configuration file. |

## Remarks

The UUID for `IPxeAuthClass` is 2BCF9AFE-C441-4f69-A943-08A4C4EAAE5B.

## See Also

[PxeAuthClass Client COM Automation Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/pxeauthclass-client-com-automation-class) [About Operating System Deployment Site Role Configuration](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/about-operating-system-deployment-site-role-configuration)
