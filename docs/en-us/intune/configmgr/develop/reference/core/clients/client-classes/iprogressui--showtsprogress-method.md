<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iprogressui--showtsprogress-method -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# IProgressUI::ShowTSProgress method

In Configuration Manager, the `ShowTSProgress` method displays custom task sequence progress information in a dialog box.

## Syntax

```
[IDL]
HRESULT ShowActionProgress(
     BSTR pszOrgName,
     BSTR pszTaskSequenceName,
     BSTR pszCustomTitle,
     BSTR pszCurrentAction,
     ULONG uStep,
     ULONG uMaxStep,
);
```

### Parameters

#### `pszOrgName`

Data type: `BSTR`

Qualifiers: \[in\]

Pointer to the organization name that is shown in the progress dialog box. The value can be retrieved from the `_SMSTSOrgName` environment variable.

#### `pszTaskSequenceName`

Data type: `BSTR`

Qualifiers: \[in\]

Pointer to the name of the task sequence that is currently running. The value can be retrieved from the `_SMSTSPackageName` environment variable.

#### `pszCustomTitle`

Data type: `BSTR`

Qualifiers: \[in\]

Pointer to the text for a custom message that replaces the default title text displayed in the progress dialog box. Pass an empty string if there's no custom message to show. The value can be obtained from the `_SMSTSCustomProgressDialogMessage` environment variable.

#### `pszCurrentAction`

Data type: `BSTR`

Qualifiers: \[in\]

Pointer to the name of the current task sequence step. The value can be obtained from the `_SMSTSCurrentActionName` environment variable.

#### `uStep`

Data type: `ULONG`

Qualifiers: \[in\]

The current task sequence step number. The value can be obtained from the `SMSTSNextInstructionPointer` environment variable.

#### `uMaxStep`

Data type: `ULONG`

Qualifiers: \[in\]

The total number of steps in the task sequence. The value can be obtained from the `_SMSTSInstructionTableSize` environment variable.

## Return values

An `HRESULT` code. Possible values include, but aren't limited to, the following value. There are no `HRESULT` values returned that are specific to this method.

S\_OK The method succeeded.

## See also

- [OS deployment client COM automation classes](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/operating-system-deployment-client-com-automation-classes)
- [IProgressUI interface](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iprogressui-interface)
- [About reporting Configuration Manager custom action progress](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/about-reporting-configuration-manager-custom-action-progress)
- [How to use task sequence variables in a running Configuration Manager task sequence](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-use-task-sequence-variables-in-a-running-task-sequence)
