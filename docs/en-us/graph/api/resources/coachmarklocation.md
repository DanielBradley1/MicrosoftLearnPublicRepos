<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/coachmarklocation?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-03-06 -->

# coachmarkLocation resource type

Namespace: microsoft.graph

Represents details about a coachmark location.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| length | Int32 | Length of coachmark. |
| offset | Int32 | Offset of coachmark. |
| type | [coachmarkLocationType](#coachmarklocationtype-values) | Type of coachmark location. The possible values are: `unknown`, `fromEmail`, `subject`, `externalTag`, `displayName`, `messageBody`, `unknownFutureValue`. |

### coachmarkLocationType values

| Member | Description |
| :--- | :--- |
| unknown | Coachmark location type as unknown. |
| fromEmail | Coachmark from email address. |
| subject | Coachmark from email subject. |
| externalTag | Coachmark from external tag. |
| displayName | Coachmark from display name. |
| messageBody | Coachmark from email body. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
    "@odata.type": "#microsoft.graph.coachmarkLocation",
    "offset": "Int32",
    "length": "Int32",
    "type": "String"
}
```
