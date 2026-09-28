<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/hybridagentupdaterconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# hybridAgentUpdaterConfiguration resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

A tenant admin can configure for each onPremisesPublishingProfile the time window during which agents can receive updates or defer updates to the agents. The **hybridAgentUpdaterConfiguration** specified for an [onPremisesPublishingProfile](https://learn.microsoft.com/en-us/graph/api/resources/onpremisespublishingprofile?view=graph-rest-beta) is applicable to all the agents within that onPremisesPublishingProfile.

For example, for the agents in onPremisesPublishingProfile of type "provisioning" the steps could be as below.

1. Tenant administrator can configure to not receive any updates to the Provisioning agents for the next n days.
2. Tenant administrator can configure an update window\(start and end time\) during which the agents can receive updates.
3. Tenant administrator can enable allowUpdateConfigurationOverride which overrides the updater configuration for Provisioning agents and allows them to receive the next available update.

The DateTime/Time information specified in the updater configuration will be converted to the local timezone reported by the agent during evaluation.

The update of the agent follows the below priority list

1. If allowUpdateConfigurationOverride is set to true the updater configuration set by the tenant will be skipped and the agent will receive an update when the next version of the agent is available \(priority 1\).
2. If the defer update is set, the agent won't be updated until the defer update date time \(priority 2\).
3. If the update window is set, the agent is updated only during that time window in a 24 hour day \(priority 3\).
4. If no valid updater configuration is set by the tenant, the agent will receive an update when the next version of the agent is available

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| allowUpdateConfigurationOverride | Boolean | Indicates if updater configuration will be skipped and the agent will receive an update when the next version of the agent is available. |
| deferUpdateDateTime | DateTimeOffset | The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z` |
| updateWindow | [updateWindow](https://learn.microsoft.com/en-us/graph/api/resources/updatewindow?view=graph-rest-beta) | The time window during which the agent can receive updates. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "allowUpdateConfigurationOverride": true,
  "deferUpdateDateTime": "String (timestamp)",
  "updateWindow": {"@odata.type": "microsoft.graph.updateWindow"}
}
```
