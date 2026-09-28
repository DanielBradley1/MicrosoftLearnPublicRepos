<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowexecutiontriggeroperator?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-09-02 -->

# workflowExecutionTriggerOperator resource type

Namespace: microsoft.graph.identityGovernance

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an abstract operator used by a [timeBasedAttributeTriggerV2](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-timebasedattributetriggerv2?view=graph-rest-beta) to evaluate a user's date attribute. This type can't be instantiated directly.

Configure this type in the **operator** property of [timeBasedAttributeTriggerV2](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-timebasedattributetriggerv2?view=graph-rest-beta).

The following type is derived from this type:

- [workflowTriggerTimeBasedOperator](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowtriggertimebasedoperator?view=graph-rest-beta)

The type of an operator is differentiated by its `@odata.type` property.

## Properties

None.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.workflowExecutionTriggerOperator"
}
```
