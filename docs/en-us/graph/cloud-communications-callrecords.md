<!-- Source: https://learn.microsoft.com/en-us/graph/cloud-communications-callrecords -->
<!-- Sitemap-Last-Modified: 2024-11-07 -->

# Call records

Call records provide usage and diagnostic information about the calls and online meetings that occur within your organization when using Microsoft Teams or Skype for Business. Usage and diagnostic data can be consumed to produce custom reporting for your business to help monitor adoption or to troubleshoot call quality issues.

Organizations can subscribe to changes to call records using the Microsoft Graph [change notifications](https://learn.microsoft.com/en-us/graph/api/resources/change-notifications-api-overview) capability, allowing them to build near-real-time reports from the data or to alert on certain scenarios like emergency calls.

Important

Use discretion when granting the CallRecords.Read.All permission to applications. Call records can provide insights into the operation of your business, and therefore can be a target for malicious actors. Only grant this permission to applications you trust to meet your data protection requirements.

## Subscribe to call records

Organizations and partners often have their own tooling for generating reports about calls and online meetings. Using webhooks, they can receive a continuous feed of call records as they are created. This push model enables organizations and partners to build their own real-time reporting solutions. A call record and its respective notification are created after a call or meeting ends. For more information, see [Get change notifications for Microsoft Teams call records](https://learn.microsoft.com/en-us/graph/changenotifications-for-callrecords).

## Look up a call record by its call ID

Applications can retrieve a [call record](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-callrecord) by its ID. This ID can be determined from a webhook notification, a [list](https://learn.microsoft.com/en-us/graph/api/callrecords-cloudcommunications-list-callrecords) of available call records, or retrieved from administrative tools. A call record is generated after a call concludes and the record is retained for 30 days.

## Get call record reports

Organizations that use Microsoft Teams to connect to the public switched telephone network \(PSTN\) usually want to track this usage to understand the associated costs. The [getPstnCalls](https://learn.microsoft.com/en-us/graph/api/callrecords-callrecord-getpstncalls) and [getDirectRoutingCalls](https://learn.microsoft.com/en-us/graph/api/callrecords-callrecord-getdirectroutingcalls) functions return a projection of [call record](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-callrecord) data in a tabular format.

## Related content

- [Call records permissions](https://learn.microsoft.com/en-us/graph/permissions-reference)
- [Teams API overview](https://learn.microsoft.com/en-us/graph/teams-concept-overview)
