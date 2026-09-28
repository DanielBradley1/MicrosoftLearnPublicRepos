<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/verifiablecredentialrequired?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# verifiableCredentialRequired resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Verifiable credential requirements status indicating that credentials verification is required and returns the information required to initiate the credential verification process. Used for the **verifiableCredentialRequirementStatus** property of [access package assignment request requirements](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentrequestrequirements?view=graph-rest-beta).

Inherits from [verifiableCredentialRequirementStatus](https://learn.microsoft.com/en-us/graph/api/resources/verifiablecredentialrequirementstatus?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| expiryDateTime | DateTimeOffset | When the presentation request will expire and a new one will need to be generated. |
| url | String | A URL that launches the digital wallet and starts the presentation process. You can present this URL to the user if they can't scan the QR code. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.verifiableCredentialRequired",
  "expiryDateTime": "String (timestamp)",
  "url": "String"
}
```
