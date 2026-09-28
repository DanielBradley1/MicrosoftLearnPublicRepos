<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-configurationmanageractiondeliverystatus?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# configurationManagerActionDeliveryStatus enum type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Delivery state of Configuration Manager device action

## Members

| Member | Value | Description |
| :--- | :--- | :--- |
| unknown | 0 | Pending to deliver the action to ConfigurationManager |
| pendingDelivery | 1 | Pending to deliver the action to ConfigurationManager |
| deliveredToConnectorService | 2 | Action is sent to ConfigurationManager Connector service \(cloud\) |
| failedToDeliverToConnectorService | 3 | Failed to send the action to ConfigurationManager Connector service \(cloud\) |
| deliveredToOnPremisesServer | 4 | Action is delivered to ConfigurationManager on-prem server |
