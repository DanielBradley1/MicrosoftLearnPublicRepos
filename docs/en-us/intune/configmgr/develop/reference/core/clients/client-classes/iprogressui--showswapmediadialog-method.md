<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iprogressui--showswapmediadialog-method -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# IProgressUI::ShowSwapMediaDialog method

In Configuration Manager, the `ShowSwapMediaDialog` method displays message box to prompt a user to swap media.

## Syntax

```
[IDL]
HRESULT ShowSwapMediaDialog(
     BSTR pszTaskSequenceName,
     ULONG uMediaNumber
);
```

### Parameters

#### `pszTaskSequenceName`

Data type: `BSTR`

Qualifiers: \[in\]

Pointer to the name of the task sequence that is currently running. The value can be retrieved from the `_SMSTSPackageName` environment variable.

#### `uMediaNumber`

Data type: `ULONG`

Qualifiers: \[in\]

The value of the media item to be swapped by the user.

## Return values

An `HRESULT` code. Possible values include, but aren't limited to, the following value. There are no `HRESULT` values returned that are specific to this method.

S\_OK The method succeeded.

## See also

- [OS deployment client COM automation classes](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/operating-system-deployment-client-com-automation-classes)
- [IProgressUI interface](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iprogressui-interface)
- [About reporting Configuration Manager custom action progress](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/about-reporting-configuration-manager-custom-action-progress)
- [How to use task sequence variables in a running Configuration Manager task sequence](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-use-task-sequence-variables-in-a-running-task-sequence)
