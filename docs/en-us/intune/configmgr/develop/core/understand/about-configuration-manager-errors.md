<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors -->
<!-- Sitemap-Last-Modified: 2024-01-05 -->

# About Configuration Manager Errors

In Configuration Manager, when a Configuration Manager error occurs it's either a Windows Management Instrumentation \(WMI\) or an SMS Provider error.

A WMI error is reported in an instance of \_\_ExtendedStatus. An SMS Provider error is reported in an instance of `SMS_ExtendedStatus`.

How you process an error depends on the programming language that you're using.

## Error Handling with WMI

In VBScript the error object `Number` property is non-zero if an error occurs during synchronous operation. Typically, you check this value after making changes to, or querying, the SMS Provider. In an asynchronous operation you receive an error object of the `OnCompleted` callback function.

After you get the error object instance, you can check the \_\_Class property to determine the origin of the error. WMI creates an instance of \_\_ExtendedStatus for WMI errors, and the SMS Provider creates an instance of `SMS_ExtendedStatus` for SMS Provider errors. `SMS_ExtendedStatus` is derived from \_\_ExtendedStatus. The details of an SMS Provider error can also be found in SMSProv.log.

For more information about handling synchronous errors, see [How to Handle Configuration Manager Synchronous Errors by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-handle-configuration-manager-synchronous-errors-by-using-wmi).

For more information about handling asynchronous errors, see [How to Handle Configuration Manager Asynchronous Errors by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-handle-configuration-manager-asynchronous-errors-by-using-wmi).

## Error Handling with the Managed SMS Provider

To handle Configuration Manager errors by using the managed SMS Provider, you catch the Configuration Manager-specific exceptions.

| Exception | Description |
| --- | --- |
| `SmsQueryException` | `SmsQueryException` is raised when a Configuration Manager query error occurs. It provides exception information specific to Configuration Manager \(`SMS_ExtendedStatus`\) and also encapsulates any WMI exceptions raised.  <br>  <br>`SmsQueryException.ErrorCode` maps to the equivalent System.ManagementException exception code.  <br>  <br>`SmsQueryException.ExtendStatusCode` maps to the SMS Provider error code raised in `SMS_ExtendedStatus.ErrorCode`. |
| `SmsConnectionException` | `SmsConnectionException` is raised when the connection to WMI is lost. |
| `SmsException` | `SmsException` is the base class from which `SmsQueryException` and `SmsConnectionException` derive. It's never raised but can be caught to catch both `SmsQueryException` and `SmsConnectionException`. |

### Accessing the \_\_ExtendedStatus and the SMS\_ExtendedStatus objects

Because the \_\_ExtendedStatus and `SMS_ExtendedStatus` aren't wrapped by the managed SMS Provider, you must use the System.Management ManagedException object.

If you don't need access to the error WMI objects, you can get access to an exception details string in SMSException.Details.

For more information about handling synchronous exceptions, see [How to Handle Configuration Manager Synchronous Errors by Using Managed Code](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-handle-configuration-manager-synchronous-errors-by-using-managed-code).

For more information about handling asynchronous exceptions, see [How to Handle Configuration Manager Asynchronous Errors by Using Managed Code](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-handle-configuration-manager-asynchronous-errors-by-using-managed-code).

## See Also

[About errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors)

[How to Handle Configuration Manager Synchronous Errors by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-handle-configuration-manager-synchronous-errors-by-using-wmi)

[How to Handle Configuration Manager Asynchronous Errors by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-handle-configuration-manager-asynchronous-errors-by-using-wmi)

[Configuration Manager Asynchronous Errors by Using Managed Code](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-handle-configuration-manager-asynchronous-errors-by-using-managed-code)

[How to Handle Configuration Manager Synchronous Errors by Using Managed Code](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-handle-configuration-manager-synchronous-errors-by-using-managed-code)
