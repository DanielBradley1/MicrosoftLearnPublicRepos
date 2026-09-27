<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/manage/how-to-determine-advertisement-status -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# How to Determine Advertisement Status

To determine advertisement status in Configuration Manager, you can use the queries described in this section.

Note

These queries query the status messages directly and might take some time to complete because there can be many status messages.

For more information about using these queries, see [How to Perform a Synchronous Configuration Manager Query by Using Managed Code](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-perform-a-synchronous-configuration-manager-query-by-using-managed-code) and [How to Perform a Synchronous Configuration Manager Query by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-perform-a-synchronous-configuration-manager-query-by-using-wmi).

For more queries about advertisement status and summarization, you can use [SMS\_ClientAdvertisementStatus Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_clientadvertisementstatus-server-wmi-class) and [SMS\_ClientAdvertisementSummary Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_clientadvertisementsummary-server-wmi-class).

## Queries

### Client Program Install

The following query returns the clients that have successfully installed a program. You need to check for both message identifiers because the program can report status with an exit code \(10008\) or an install status MIF file \(10009\).

```
' Returns clients that have successful installed a program
SELECT msg.MachineName, msg.SiteCode, ad.ProgramName
FROM SMS_StatusMessage msg
     JOIN SMS_StatMsgAttributes attr ON msg.RecordID = attr.RecordID
     JOIN SMS_Advertisement ad ON attr.AttributeValue = ad.AdvertisementID
WHERE msg.Component = "Software Distribution"
AND   (msg.MessageID = 10008 or msg.MessageID = 10009)
AND   attr.AttributeID = 401
ORDER BY ad.ProgramName
```

### Clients That Have Installed a Specific Advertised Program

This query returns the clients that have successfully installed a specific advertised program.

```
' Returns clients that have successfully installed a specific advertised program
SELECT msg.MachineName, msg.SiteCode
FROM SMS_StatusMessage msg
     JOIN SMS_StatMsgAttributes attr ON msg.RecordID = attr.RecordID
WHERE msg.Component = "Software Distribution"
and   (msg.MessageID = 10008 or msg.MessageID = 10009)
and   attr.AttributeID = 401
and   attr.AttributeValue = "<AdvertisementID>"
```

### Clients That Have Not Installed a Specific Advertised Program

The previous queries show which clients successfully installed an advertised program. Determining which collection members have not installed the advertised program can be more involved if the advertisement specified subcollections. The following query determines which clients of the **All Systems** \(SMS00001\) collection \(substitute your collection member class for SMS\_CM\_RES\_COLL\_SMS00001\) have not installed the advertised program. If the advertisement specified subcollections, the query must be run for each subcollection.

```
' Returns which clients of a collection have not installed the advertised program
SELECT Name
FROM SMS_CM_RES_COLL_SMS00001
WHERE NOT Name IN (SELECT msg.MachineName
FROM SMS_StatusMessage msg
     JOIN SMS_StatMsgAttributes attr ON msg.RecordID = attr.RecordID
WHERE msg.Component = "Software Distribution"
AND   (msg.MessageID = 10008 or msg.MessageID = 10009)
AND   attr.AttributeID = 401
AND   attr.AttributeValue = "<AdvertisementID>")
```

## See Also

[How to Perform an Asynchronous Configuration Manager Query by Using Managed Code](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-perform-an-asynchronous-query-by-using-managed-code) [How to Perform a Synchronous Configuration Manager Query by Using Managed Code](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-perform-a-synchronous-configuration-manager-query-by-using-managed-code) [How to Perform an Asynchronous Configuration Manager Query by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-perform-an-asynchronous-configuration-manager-query-by-using-wmi) [How to Perform a Synchronous Configuration Manager Query by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-perform-a-synchronous-configuration-manager-query-by-using-wmi) [SMS\_StatusMessage Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/sms_statusmessage-server-wmi-class) [SMS\_StatMsgAttributes Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/sms_statmsgattributes-server-wmi-class) [Calling Configuration Manager Code Snippets](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/calling-code-snippets)
