<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-ipaddress?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# ipAddress resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

An IP address \(Internet Protocol address\) is a unique numerical label assigned to each device connected to a computer network that uses the Internet Protocol for communication. It serves as an identifier for the device within the network and allows it to send and receive data over the internet. An IP address consists of a series of numbers, separated by periods, such as "192.168.0.1".

Inherits from [microsoft.graph.networkaccess.ruleDestination](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-ruledestination?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| value | String | Defines the IP address used in a destination for a rule. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.ipAddress",
  "value": "String"
}
```
