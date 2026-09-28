<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-privateaccessdetails?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-04-11 -->

# privateAccessDetails resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents details about private access in a network transaction or connection.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| accessType | microsoft.graph.networkaccess.accessType | Type of accessed application. Access type options: QuickAccess, PrivateAccess. |
| appSegmentId | String | The unique identifier for Application segment ID from Azure AD. |
| connectionStatus | microsoft.graph.networkaccess.connectionStatus | Status of a connection. Status options: Open, Active, Closed. |
| connectorId | String | Private access connector ID. |
| connectorIp | String | Private access connector IP address. |
| connectorName | String | Private access connector name. |
| processingRegion | String | Region where the request was processed by the backend service. |
| thirdPartyTokenDetails | [microsoft.graph.networkaccess.thirdPartyTokenDetails](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-thirdpartytokendetails?view=graph-rest-beta) | Details about third-party tokens used in the transaction. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.privateAccessDetails",
  "connectorId": "String",
  "connectorName": "String",
  "connectorIp": "String",
  "connectionStatus": "String",
  "accessType": "String",
  "processingRegion": "String",
  "thirdPartyTokenDetails": {
    "@odata.type": "microsoft.graph.networkaccess.thirdPartyTokenDetails"
  },
  "appSegmentId": "String"
}
```
