<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iprogressui--showmessage-method -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# IProgressUI::ShowMessage method

In Configuration Manager, the `ShowMessage` method displays customizable dialog box.

## Syntax

```
[IDL]
HRESULT ShowMessage(
     BSTR pszText,
     BSTR pszCaption,
     ULONG uType
);
```

### Parameters

#### `pszText`

Data type: `BSTR`

Qualifiers: \[in\]

The text displayed in the message box body.

#### `pszCaption`

Data type: `BSTR`

Qualifiers: \[in\]

The text displayed in the message box windows header.

#### `uType`

Data type: `ULONG`

Qualifiers: \[in\]

The value corresponding to one of the following possible values for the buttons:

- 0 - Ok
- 1 - Ok/Cancel
- 2 - Abort/Retry/Ignore
- 3 - Yes/No/Cancel
- 4 - Yes/No
- 5 - Retry/Cancel
- 6 - Cancel/Try Again/Continue

## Return values

An `HRESULT` code. Possible values include, but aren't limited to, the following value. There are no `HRESULT` values returned that are specific to this method.

S\_OK The method succeeded.

To evaluate the user's response to the message box, use the [IProgressUI::ShowMessageEx](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iprogressui--showmessageex-method) method.

## See also

- [OS deployment client COM automation classes](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/operating-system-deployment-client-com-automation-classes)
- [IProgressUI interface](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iprogressui-interface)
- [About reporting Configuration Manager custom action progress](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/about-reporting-configuration-manager-custom-action-progress)
- [How to use task sequence variables in a running Configuration Manager task sequence](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-use-task-sequence-variables-in-a-running-task-sequence)
