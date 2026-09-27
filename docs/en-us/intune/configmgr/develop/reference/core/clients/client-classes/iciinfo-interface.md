<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iciinfo-interface -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# ICIINFO Interface

The `ICIINFO` interface, in Configuration Manager, can represent the properties of a configuration item which has been downloaded and stored by the Desired Configuration Management client or the properties of a baseline configuration item in a Desired Configuration Management Agent job in the client data store. In both cases, the configuration item is either a \(top level/root\) baseline or a Software Updates configuration item.

The interface inherits from `IUnknown`.

## In This Section

The following table lists the methods in the `ICIINFO` interface.

| Term | Definition |
| --- | --- |
| [ICIINFO::GetCategory](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iciinfo--getcategory-method) | Gets a localized category name by index and the group name of the category. |
| [ICIINFO::GetCategoryCount](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iciinfo--getcategorycount-method) | Gets the count of categories applied to the configuration item. |
| [ICIINFO::GetCIPresence](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iciinfo--getcipresence-method) | Gets the current presence for the configuration item. |
| [ICIINFO::GetContextInfo](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iciinfo--getcontextinfo-method) | Gets the context information by name from the configuration item. |
| [ICIINFO::GetDependantPackages](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iciinfo--getdependantpackages-method) | Gets dependent package information for the configuration item. |
| [ICIINFO::GetDetailedComplianceInfo](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iciinfo--getdetailedcomplianceinfo-method) | Gets detailed compliance information from the last compliance evaluation run for the configuration item. |
| [ICIINFO::GetEvalState](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iciinfo--getevalstate-method) | Gets the current evaluation state of the configuration item. |
| [ICIINFO::GetId](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iciinfo--getid-method) | Gets the ID of the configuration item. |
| [ICIINFO::GetJobState](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iciinfo--getjobstate-method) | Gets the current operational job state of the configuration item that is part of a job or task. |
| [ICIINFO::GetLastEvalTime](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iciinfo--getlastevaltime-method) | Gets the last evaluation time for the configuration item. |
| [ICIINFO::GetProperty](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iciinfo--getproperty-method) | Gets a named property value from the configuration item. |
| [ICIINFO::GetSdmTypeName](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iciinfo--getsdmtypename-method) | Gets the fully qualified name of a root configuration item. |
| [ICIINFO::GetVersion](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iciinfo--getversion-method) | Gets the version of the configuration item. |

## Remarks

To obtain this interface, the application calls the [IDCMSDK Interface](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/idcmsdk-interface). The application calls the [IDCMAgentCallback Interface](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/idcmagentcallback-interface) interface to respond to agent calls.

## UUID

The UUID for `ICIINFO` is ACF43B8E-23A2-4923-B421-CB918FC5CA1F.

## See Also

[Compliance Settings \(DCM\) Client Interfaces](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/compliance-settings--dcm--client-interfaces) [IDCMSDK Interface](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/idcmsdk-interface) [IDCMAgentCallback Interface](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/idcmagentcallback-interface)
