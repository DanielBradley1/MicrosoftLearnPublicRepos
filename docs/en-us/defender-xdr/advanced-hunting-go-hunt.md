<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-go-hunt -->
<!-- Sitemap-Last-Modified: 2026-07-02 -->

# Quickly hunt for entity or event information with go hunt

With the *go hunt* action, you can quickly investigate events and various entity types using powerful query-based [advanced hunting](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview) capabilities. The *go hunt* action automatically runs an advanced hunting query to find relevant information about the selected event or entity.

The *go hunt* action is available in various sections of Microsoft Defender XDR. The *go hunt* action appears once event or entity details are displayed. For example, you can use the *go hunt* option from the following sections:

- In the [incident summary page](https://learn.microsoft.com/en-us/defender-xdr/investigate-incidents#summary), you can review details about users, devices, and many other entities associated with an incident. As you select an entity, you get additional information and the various actions you could take on that entity. In the example below, a mailbox is selected, showing details about the mailbox and the option to hunt for more information about the mailbox.

  [![The Mailboxes page with the Go hunt option in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/media/advanced-hunting-go-hunt/go-hunt-1-incident.png)](https://learn.microsoft.com/en-us/defender-xdr/media/advanced-hunting-go-hunt/go-hunt-1-incident.png#lightbox)
- In the incident page, you can also access a list of entities under the **Evidence** tab. Selecting one of those entities provides an option to quickly hunt for information about that entity.

  [![The Go hunt option for a piece of evidence in the Incident page in Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/media/advanced-hunting-go-hunt/go-hunt-2-entity.png)](https://learn.microsoft.com/en-us/defender-xdr/media/advanced-hunting-go-hunt/go-hunt-2-entity.png#lightbox)
- When viewing the timeline for a device, you can select an event in the timeline to view additional information about that event. Once an event is selected, you get the option to hunt for other relevant events in advanced hunting.

  [![The Hunt for related events option on an event's page in the Timelines tab in Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/media/advanced-hunting-go-hunt/go-hunt-3-event.png)](https://learn.microsoft.com/en-us/defender-xdr/media/advanced-hunting-go-hunt/go-hunt-3-event.png#lightbox)

Selecting **Go hunt** or **Hunt for related events** passes different queries, depending on whether you've selected an entity or an event.

## Query for entity information

You can use *go hunt* to query for information about a user, device, or any other type of entity; the query checks all relevant schema tables for any events involving that entity to return information. To keep the results manageable, the query is:

- scoped to around the same time period as the earliest activity in the past 30 days that involves the entity
- associated with the incident that includes the entity.

Here is an example of the go hunt query for a device:

```kusto
let selectedTimestamp = datetime(2020-06-02T02:06:47.1167157Z);
let deviceName = "fv-az770.example.com";
let deviceId = "device-guid";
search in (DeviceLogonEvents, DeviceProcessEvents, DeviceNetworkEvents, DeviceFileEvents, DeviceRegistryEvents, DeviceImageLoadEvents, DeviceEvents, DeviceImageLoadEvents, IdentityLogonEvents, IdentityQueryEvents)
Timestamp between ((selectedTimestamp - 1h) .. (selectedTimestamp + 1h))
and DeviceName == deviceName
// or RemoteDeviceName == deviceName
// or DeviceId == deviceId
| take 100
```

### Supported entity types

You can use the *go hunt* option after selecting any of these entity types:

- Devices
- Email clusters
- Emails
- Files
- Groups
- IP addresses
- Mailboxes
- Users
- URLs

## Query for event information

When using *go hunt* to query for information about a timeline event, the query checks all relevant schema tables for other events around the time of the selected event. For example, the following query lists events in various schema tables that occurred around the same time period on the same device:

```kusto
// List relevant events 30 minutes before and after selected LogonAttempted event
let selectedEventTimestamp = datetime(2020-06-04T01:29:09.2496688Z);
search in (DeviceFileEvents, DeviceProcessEvents, DeviceEvents, DeviceRegistryEvents, DeviceNetworkEvents, DeviceImageLoadEvents, DeviceLogonEvents)
    Timestamp between ((selectedEventTimestamp - 30m) .. (selectedEventTimestamp + 30m))
    and DeviceId == "079ecf9c5798d249128817619606c1c47369eb3e"
| sort by Timestamp desc
| extend Relevance = iff(Timestamp == selectedEventTimestamp, "Selected event", iff(Timestamp < selectedEventTimestamp, "Earlier event", "Later event"))
| project-reorder Relevance
```

## Adjust the generated hunt query

With some knowledge of the [advanced hunting query language](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-query-language), you can adjust the query to your preference. For example, you can adjust the `Timestamp between` line, which determines the size of the time window:

```kusto
Timestamp between ((selectedTimestamp - 1h) .. (selectedTimestamp + 1h))
```

In addition to modifying the query to get more relevant results, you can also:

- [View the results as charts](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-query-results#view-query-results-as-a-table-or-chart)
- [Create a custom detection rule](https://learn.microsoft.com/en-us/defender-xdr/custom-detection-rules)

Note

Some tables in this article might not be available in Microsoft Defender for Endpoint. [Turn on Microsoft Defender](https://learn.microsoft.com/en-us/defender-xdr/m365d-enable) to hunt for threats using more data sources. You can move your advanced hunting workflows from Microsoft Defender for Endpoint to Microsoft Defender by following the steps in [Migrate advanced hunting queries from Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-migrate-from-mde).

## Related content

- [Advanced hunting overview](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview)
- [Learn the query language](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-query-language)
- [Work with query results](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-query-results)
- [Custom detection rules](https://learn.microsoft.com/en-us/defender-xdr/custom-detection-rules)

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender XDR Tech Community](https://techcommunity.microsoft.com/t5/microsoft-365-defender/bd-p/MicrosoftThreatProtection).
