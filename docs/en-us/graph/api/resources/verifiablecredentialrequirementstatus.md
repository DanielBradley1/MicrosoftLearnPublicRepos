<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/verifiablecredentialrequirementstatus?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# verifiableCredentialRequirementStatus resource type

Namespace: microsoft.graph

Represents the status of processing the verifiable credential requirement for an access package request. This is an abstract type that's inherited by:

- [verifiableCredentialRequired](https://learn.microsoft.com/en-us/graph/api/resources/verifiablecredentialrequired?view=graph-rest-beta)
- [verifiableCredentialRetrieved](https://learn.microsoft.com/en-us/graph/api/resources/verifiablecredentialretrieved?view=graph-rest-beta)
- [verifiableCredentialVerified](https://learn.microsoft.com/en-us/graph/api/resources/verifiablecredentialverified?view=graph-rest-beta)

At any instance, the actual status of the processing is represented by one of the derived types.

In entitlement management, the derived types of this object are configured in the **verifiableCredentialRequirementStatus** property of [accessPackageAssignmentRequestRequirements](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentrequestrequirements?view=graph-rest-beta).

## Properties

None.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.verifiableCredentialRequirementStatus"
}
```
