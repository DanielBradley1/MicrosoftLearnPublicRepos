<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyenforcementaction?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-07 -->

# lifecyclePolicyEnforcementAction resource type

Namespace: microsoft.graph.identityGovernance

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the abstract base type for the action applied to an identity that becomes non-compliant with a lifecycle policy. This type is configured in the **enforcementAction** property of a [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-beta).

You can't create instances of this abstract type directly. Instead, use one of the following derived types:

- [deleteOnlyEnforcementAction](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-deleteonlyenforcementaction?view=graph-rest-beta)
- [disableOnlyEnforcementAction](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-disableonlyenforcementaction?view=graph-rest-beta)
- [disableThenDeleteEnforcementAction](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-disablethendeleteenforcementaction?view=graph-rest-beta)

Instances are differentiated by the **@odata.type** property. This is an abstract type.

## Properties

None.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.lifecyclePolicyEnforcementAction"
}
```
