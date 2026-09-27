<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iprogressui--showerrordialog-method -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# IProgressUI::ShowErrorDialog method

In Configuration Manager, the `ShowErrorDialog` method displays customizable error information in a dialog box.

## Syntax

```
[IDL]
HRESULT ShowErrorDialog(
     BSTR pszOrgName,
     BSTR pszTaskSequenceName,
     BSTR pszCustomTitle,
     BSTR pszErrorMessage,
     ULONG uErrorCode,
     ULONG uTimeoutInSeconds,
     ULONG uWillReboot,
     BSTR pszTaskSequenceStepName
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

Pointer to the text for a custom message that replaces the default title text displayed in the error dialog box. Pass an empty string if there's no custom message to show. The value can be obtained from the `_SMSTSCustomProgressDialogMessage` environment variable.

#### `pszErrorMessage`

Data type: `BSTR`

Qualifiers: \[in\]

Pointer to the text for the custom message that's displayed in the error dialog box. Pass an empty string if there's no custom message to show. The default text includes the text from `pszTaskSequenceName`, `pszTaskSequenceStepName`, and `uErrorCode`. It changes depending on which values are specified.

#### `uErrorCode`

Data type: `ULONG`

Qualifiers: \[in\]

Pointer to the return code of the last step that failed. The value can be obtained from the `_SMSTSLastActionRetCode` environment variable. If no custom text for `pszErrorMessage` is specified, `uErrorCode` will be displayed in [Microsoft system error code](https://learn.microsoft.com/en-us/windows/desktop/debug/system-error-codes) format.

#### `uTimeoutInSeconds`

Data type: `ULONG`

Qualifiers: \[in\]

Pointer to the value for the number of seconds the dialog box is displayed before closing. The value can be obtained from the `SMSTSErrorDialogTimeout` environment variable, which isn't configured in the task sequence by default. If an empty string is specified for `uTimeoutInSeconds` and `SMSTSErrorDialogTimeout` isn't specified, a default of 900 seconds will be used.

#### `bWillReboot`

Data type: `ULONG`

Qualifiers: \[in\]

Boolean value. It indicates whether the task sequence will restart the computer when the dialog is closed or the timeout expires.

#### `pszTaskSequenceStepName`

Data type: `BSTR`

Qualifiers: \[in\]

Pointer to the text for name of the step name that will be displayed in the default `pszErrorMessage` text. The value can be retrieved from the `_SMSTSLastActionName` environment variable.

## Return values

An `HRESULT` code. Possible values include, but aren't limited to, the following value. There are no `HRESULT` values returned that are specific to this method.

S\_OK The method succeeded.

## See also

- [OS deployment client COM automation classes](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/operating-system-deployment-client-com-automation-classes)
- [IProgressUI interface](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iprogressui-interface)
- [About reporting Configuration Manager custom action progress](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/about-reporting-configuration-manager-custom-action-progress)
- [How to use task sequence variables in a running Configuration Manager task sequence](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-use-task-sequence-variables-in-a-running-task-sequence)
