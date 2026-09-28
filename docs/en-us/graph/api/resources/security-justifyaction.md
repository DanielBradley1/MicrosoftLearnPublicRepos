<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-justifyaction?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# justifyAction resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Indicates that a justification is required for the specified operation. The [evaluateApplication](https://learn.microsoft.com/en-us/graph/api/security-sensitivitylabel-evaluateapplication?view=graph-rest-beta), [evaluateClassificationResults](https://learn.microsoft.com/en-us/graph/api/security-sensitivitylabel-evaluateclassificationresults?view=graph-rest-beta), or [evaluateRemoval](https://learn.microsoft.com/en-us/graph/api/security-sensitivitylabel-evaluateremoval?view=graph-rest-beta) APIs might return the **justifyAction**. Justification is provided via [labelingOptions](https://learn.microsoft.com/en-us/graph/api/resources/security-labelingoptions?view=graph-rest-beta). The previous call should be repeated, but with the **downgradeJustification** property of **labelingOptions** set with a justification message, provided via user input or application logic.

Inherits from [informationProtectionAction](https://learn.microsoft.com/en-us/graph/api/resources/security-informationprotectionaction?view=graph-rest-beta).

## Properties

None.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.justifyAction"
}
```
