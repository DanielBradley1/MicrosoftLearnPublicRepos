<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/callrecords-api-overview?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-03-18 -->

# Working with the call records API in Microsoft Graph

Call records provide usage and diagnostic information about the calls and online meetings that occur within your organization when using Microsoft Teams or Skype for Business. You can use the call records APIs to subscribe to call records, list call records, and look up call records by IDs. A call record is created after a call or meeting ends and the record is retained for 30 days.

The call records API is defined in the OData sub-namespace, `microsoft.graph.callRecords`.

## Key resource types

| Resource | Methods |
| :--- | :--- |
| [callRecord](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-callrecord?view=graph-rest-1.0) | [List callRecords](https://learn.microsoft.com/en-us/graph/api/callrecords-cloudcommunications-list-callrecords?view=graph-rest-1.0)  <br>[Get callRecord](https://learn.microsoft.com/en-us/graph/api/callrecords-callrecord-get?view=graph-rest-1.0) |
| [directRoutingLogRow](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-directroutinglogrow?view=graph-rest-1.0) | [getDirectRoutingCalls](https://learn.microsoft.com/en-us/graph/api/callrecords-callrecord-getdirectroutingcalls?view=graph-rest-1.0) |
| [participant](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-participant?view=graph-rest-1.0) | [List participants\_v2](https://learn.microsoft.com/en-us/graph/api/callrecords-callrecord-list-participants_v2?view=graph-rest-1.0) |
| [pstnCallLogRow](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-pstncalllogrow?view=graph-rest-1.0) | [getPstnCalls](https://learn.microsoft.com/en-us/graph/api/callrecords-callrecord-getpstncalls?view=graph-rest-1.0) |
| [segment](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-segment?view=graph-rest-1.0) | [List sessions](https://learn.microsoft.com/en-us/graph/api/callrecords-callrecord-list-sessions?view=graph-rest-1.0)  <br>[Get callRecord](https://learn.microsoft.com/en-us/graph/api/callrecords-callrecord-get?view=graph-rest-1.0) |
| [session](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-session?view=graph-rest-1.0) | [List sessions](https://learn.microsoft.com/en-us/graph/api/callrecords-callrecord-list-sessions?view=graph-rest-1.0)  <br>[Get callRecord](https://learn.microsoft.com/en-us/graph/api/callrecords-callrecord-get?view=graph-rest-1.0) |

## Call record structure

The [callRecord](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-callrecord?view=graph-rest-1.0) entity represents a single peer-to-peer call or a group call between multiple [participants](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-participant?view=graph-rest-1.0), sometimes referred to as an online meeting.

A peer-to-peer call contains a single [session](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-session?view=graph-rest-1.0) between the two participants in the call. Group calls contain one or more **session** entities. In a group call, each **session** is between the participant and a service endpoint.

Each **session** contains one or more [segment](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-segment?view=graph-rest-1.0) entities. A **segment** represents a media link between two [endpoints](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-endpoint?view=graph-rest-1.0). For most calls, only one **segment** will be present for each **session**, however sometimes there may be one or more intermediate **endpoints**.

![Image of a the data structure representing a complete call record](https://learn.microsoft.com/en-us/graph/images/callrecords-structure.png)

In the diagram above, the numbers denote how many children of each type can be present. For example, a 1..N relationship between a **callRecord** and a **session** means one **callRecord** instance can contain one or more **session** instances. Similarly, a 1..N relationship between a **segment** and a **media** means one **segment** instance can contain one or more [media](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-media?view=graph-rest-1.0) streams.

## PSTN and direct routing logs

The [pstnCallLogRow](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-pstncalllogrow?view=graph-rest-1.0) and [directRoutingLogRow](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-directroutinglogrow?view=graph-rest-1.0) resources only include information about calls that utilize public switched telephone network \(PSTN\) infrastructure. This information can be useful to understand the usage of calling products in your organization. However, these resources may only reflect a portion of a larger call or meeting experience. For example, a log row include information about a user who places a PSTN call to join an online meeting, but doesn't include information about other participants in that online meeting. Because a log row is also only a subset of call record information, the ID for a particular log row can't be used to fetch a [callRecord](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-callrecord?view=graph-rest-1.0) object.

## Related content

- [Set up change notifications that include resource data](https://learn.microsoft.com/en-us/graph/api/resources/change-notifications-api-overview)
