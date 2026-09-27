<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iprogressui--closeprogressdialog-method -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# IProgressUI::CloseProgressDialog method

In Configuration Manager, the `CloseProgressDialog` method closes open instances of `IProgressUI`.

## Syntax

```
[IDL]
HRESULT CloseProgressDialog();
```

## Parameters

None

## Return values

An `HRESULT` code. Possible values include, but aren't limited to, the following value. There are no `HRESULT` values returned that are specific to this method.

S\_OK The method succeeded.

## See also

- [OS deployment client COM automation classes](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/operating-system-deployment-client-com-automation-classes)
- [IProgressUI interface](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iprogressui-interface)
- [About reporting Configuration Manager custom action progress](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/about-reporting-configuration-manager-custom-action-progress)
- [How to use task sequence variables in a running Configuration Manager task sequence](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-use-task-sequence-variables-in-a-running-task-sequence)
