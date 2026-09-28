<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/verifiablecredentialretrieved?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# verifiableCredentialRetrieved resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the status where a service requires a verifiable credential to be presented and the user has retrieved the presentation request. Inherits from [verifiableCredentialRequirementStatus](https://learn.microsoft.com/en-us/graph/api/resources/verifiablecredentialrequirementstatus?view=graph-rest-beta). Used for the **verifiableCredentialRequirementStatus** property of [access package assignment request requirements](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentrequestrequirements?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| expiryDateTime | DateTimeOffset | The specific date and time that the presentation request will expire and a new one will need to be generated. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.verifiableCredentialRetrieved",
  "expiryDateTime": "String (timestamp)"
}
```
