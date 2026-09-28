<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/ipapplicationsegment?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-23 -->

# ipApplicationSegment resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the segment configurations that are allowed for an **on-premises nonweb application** published through Microsoft Entra application proxy and accessed via non-HTTP protocols.

Inherits from [applicationSegment](https://learn.microsoft.com/en-us/graph/api/resources/applicationsegment?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/onpremisespublishingprofile-list-applicationsegments?view=graph-rest-beta) | [ipApplicationSegment](https://learn.microsoft.com/en-us/graph/api/resources/ipapplicationsegment?view=graph-rest-beta) collection | Get a list of the [ipApplicationSegment](https://learn.microsoft.com/en-us/graph/api/resources/ipapplicationsegment?view=graph-rest-beta) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/onpremisespublishingprofile-post-applicationsegments?view=graph-rest-beta) | [ipApplicationSegment](https://learn.microsoft.com/en-us/graph/api/resources/ipapplicationsegment?view=graph-rest-beta) | Create a new [ipApplicationSegment](https://learn.microsoft.com/en-us/graph/api/resources/ipapplicationsegment?view=graph-rest-beta) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/ipapplicationsegment-get?view=graph-rest-beta) | [ipApplicationSegment](https://learn.microsoft.com/en-us/graph/api/resources/ipapplicationsegment?view=graph-rest-beta) | Read the properties and relationships of an [ipApplicationSegment](https://learn.microsoft.com/en-us/graph/api/resources/ipapplicationsegment?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/ipapplicationsegment-update?view=graph-rest-beta) | [ipApplicationSegment](https://learn.microsoft.com/en-us/graph/api/resources/ipapplicationsegment?view=graph-rest-beta) | Update the properties of an [ipApplicationSegment](https://learn.microsoft.com/en-us/graph/api/resources/ipapplicationsegment?view=graph-rest-beta) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/onpremisespublishingprofile-delete-applicationsegments?view=graph-rest-beta) | None | Delete an [ipApplicationSegment](https://learn.microsoft.com/en-us/graph/api/resources/ipapplicationsegment?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| destinationHost | String | Either the IP address, IP range, or FQDN of the **applicationSegment**, with or without wildcards. |
| destinationType | privateNetworkDestinationType | The possible values are: `ipAddress`, `ipRange`, `ipRangeCidr`, `fqdn`, `dnsSuffix`, `unknownFutureValue`. |
| id | String | Identifier for the application segment. Inherited from [applicationSegment](https://learn.microsoft.com/en-us/graph/api/resources/applicationsegment?view=graph-rest-beta). |
| port \(deprecated\) | Int32 | Port supported for the application segment. **DO NOT USE**. |
| ports | String collection | List of ports supported for the application segment. |
| protocol | privateNetworkProtocol | Indicates the protocol of the network traffic acquired for the application segment. The possible values are: `tcp`, `udp`, `unknownFutureValue`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| application | [application](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-beta) | The on-premises nonweb application published through Microsoft Entra application proxy. Expanded by default and supports `$expand`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.ipApplicationSegment",
  "id": "String (identifier)",
  "destinationHost": "String",
  "destinationType": "String",
  "port": "Integer",
  "ports": [
    "String"
  ],
  "protocol": "String"
}
```
