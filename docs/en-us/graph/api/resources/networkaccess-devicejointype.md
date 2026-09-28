<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-devicejointype?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-04 -->

# deviceJoinType enum type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the Microsoft Entra device join type for a device participating in a network [connection](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-connection?view=graph-rest-beta) in Global Secure Access.

## Members

| Member | Description |
| :--- | :--- |
| none | No specific device join type. Indicates a regular, non-BYOD scenario. |
| microsoftEntraJoined | The device is joined to Microsoft Entra ID. |
| microsoftEntraRegistered | The device is registered with Microsoft Entra ID \(typically BYOD\). |
| unknownFutureValue | Evolvable enumeration sentinel value. |
