<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-sensorcandidateactivationconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-16 -->

# sensorCandidateActivationConfiguration resource type

Namespace: microsoft.graph.security

Represents the configuration for a Microsoft Defender for Identity sensor that is ready to be activated.

Inherits from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/security-sensorcandidateactivationconfiguration-get?view=graph-rest-1.0) | [microsoft.graph.security.sensorCandidateActivationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/security-sensorcandidateactivationconfiguration?view=graph-rest-1.0) | Read the properties and relationships of sensor candidate activation mode object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/security-identitycontainer-post-sensorcandidateactivationconfiguration?view=graph-rest-1.0) | [microsoft.graph.security.sensorCandidateActivationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/security-sensorcandidateactivationconfiguration?view=graph-rest-1.0) | Update the activation mode of a sensor candidate activation mode object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| activationMode | microsoft.graph.security.sensorCandidateActivationMode | The mode for activating sensor candidates. The possible values are: `manual`, `automated`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.sensorCandidateActivationConfiguration",
  "activationMode": "String"
}
```
