<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/idcmsdk-interface -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# IDCMSDK Interface

The `IDCMSDK` interface, in Configuration Manager, represents the Desired Configuration Management SDK and defines methods used to perform operations on baseline configuration items. The interface inherits from `IDispatch`.

## In This Section

The following table lists the methods in the `IDCMSDK` interface.

| Method | Description |
| --- | --- |
| [IDCMSDK::EvaluateBaseline](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/idcmsdk--evaluatebaseline-method) | Runs discover operation for the provided configuration item ID. |
| [IDCMSDK::GetAssignedBaselines](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/idcmsdk--getassignedbaselines-method) | Retrieves the assigned baseline configuration items. |
| [IDCMSDK::GetBaselineComplianceReport](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/idcmsdk--getbaselinecompliancereport-method) | Retrieves the cached discovery report for the specified configuration item baseline. |
| [IDCMSDK::GetBaselineInfo](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/idcmsdk--getbaselineinfo-method) | Retrieves the configuration item information for the specified configuration item baseline. |
| [IDCMSDK::SetEvaluationCallback](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/idcmsdk--setevaluationcallback-method) | Retrieves an existing evaluation job by ID. |

## UUID

The UUID for `IDCMSDK` is 08595CA8-6A42-4ce1-A1D6-8B6C2811A555.

## See Also

[Compliance Settings \(DCM\) Client Interfaces](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/compliance-settings--dcm--client-interfaces) [IDCMAgentCallback Interface](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/idcmagentcallback-interface)
