<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-kubernetesserviceport?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# kubernetesServicePort resource type

Namespace: microsoft.graph.security

Represents a Kubernetes service port object that is reported as part of a [microsoft.graph.security.kubernetesServiceEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-kubernetesserviceevidence?view=graph-rest-1.0) entity.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| appProtocol | String | The application protocol for this port. |
| name | String | The name of this port within the service. |
| nodePort | Int32 | The port on each node on which this service is exposed when the type is either `NodePort` or `LoadBalancer`. |
| port | Int32 | The port that this service exposes. |
| protocol | [microsoft.graph.security.containerPortProtocol](#containerportprotocol-values) | The protocol name. The possible values are: `udp`, `tcp`, `sctp`, `unknownFutureValue`. |
| targetPort | String | The name or number of the port to access on the pods targeted by the service. The port number must be in the range `1` to `65535`. The name must be an `IANA_SVC_NAME`. |

### containerPortProtocol values

| Member | Description |
| :--- | :--- |
| udp | User Datagram Protocol. |
| tcp | Transmission Control Protocol. |
| sctp | Stream Control Transmission Protocol. |
| unknownFutureValue | Evolvable enumeration sentinel value. Do not use. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
    "@odata.type": "#microsoft.graph.security.kubernetesServicePort",
    "appProtocol": "String",
    "name": "String",
    "nodePort": "Int32",
    "port": "Int32",
    "protocol": "String",
    "targetPort": "String"
}
```
