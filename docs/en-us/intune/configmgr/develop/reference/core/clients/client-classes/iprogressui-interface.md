<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iprogressui-interface -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# IProgressUI interface

The `IProgressUI` automation interface in Configuration Manager represents the user interface that allows custom actions to report progress to the OS deployment task sequencing environment.

## Methods for this interface

| Term | Definition |
| --- | --- |
| [IProgressUI::CloseProgressDialog](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iprogressui--closeprogressdialog-method) | Closes open instances of `IProgressUI` |
| [IProgressUI::ShowActionProgress](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iprogressui--showactionprogress-method) | Displays custom action progress information in a dialog box while the custom action is running. |
| [IProgressUI::ShowErrorDialog](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iprogressui--showerrordialog-method) | Displays customizable error information in a dialog box. |
| [IProgressUI::ShowMessage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iprogressui--showmessage-method) | Displays customizable dialog box. |
| [IProgressUI::ShowMessageEx](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iprogressui--showmessageex-method) | Displays customizable dialog box and captures an integer result variable. |
| [IProgressUI::ShowRebootDialog](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iprogressui--showrebootdialog-method) | Displays customizable reboot warning dialog box. |
| [IProgressUI::ShowSwapMediaDialog](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iprogressui--showswapmediadialog-method) | Displays message box to prompt a user to swap media. |
| [IProgressUI::ShowTSProgress](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iprogressui--showtsprogress-method) | Displays custom task sequence progress information in a dialog box. |

## Remarks

The GUID for `IProgressUI` is B64D758A-01C2-4bf0-9F17-621EFB9CF697.

## See also

- [OS deployment client COM automation classes](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/operating-system-deployment-client-com-automation-classes)
- [ProgressUI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/progressui-client-com-automation-class)
- [About reporting Configuration Manager custom action progress](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/about-reporting-configuration-manager-custom-action-progress)
