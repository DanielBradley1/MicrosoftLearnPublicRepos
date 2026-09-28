<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/justifyaction?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# justifyAction resource type \(deprecated\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

The Information Protection labels API is deprecated and will stop returning data on January 1, 2023. Please use the new [informationProtection](https://learn.microsoft.com/en-us/graph/api/resources/security-informationprotection?view=graph-rest-beta&preserve-view=true), [sensitivityLabel](https://learn.microsoft.com/en-us/graph/api/resources/security-sensitivitylabel?view=graph-rest-beta&preserve-view=true), and associated resources.

Indicates that a justification is required for the specified operation. The [evaluateApplication](https://learn.microsoft.com/en-us/graph/api/informationprotectionlabel-evaluateapplication?view=graph-rest-beta), [evaluateClassificationResults](https://learn.microsoft.com/en-us/graph/api/informationprotectionlabel-evaluateclassificationresults?view=graph-rest-beta), or [evaluateRemoval](https://learn.microsoft.com/en-us/graph/api/informationprotectionlabel-evaluateremoval?view=graph-rest-beta) APIs may return **justifyAction**. Justification is provided via [labelingOptions](https://learn.microsoft.com/en-us/graph/api/resources/labelingoptions?view=graph-rest-beta). The previous call should be repeated, but with the **downgradeJustification** property of **labelingOptions** set with a justification message, provided via user input or application logic.

## Properties

None

## JSON representation

The following JSON representation shows the resource type.

```json
{
  
}
```
