<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/signinfrequencysessioncontrol?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# signInFrequencySessionControl resource type

Namespace: microsoft.graph

Session control to enforce sign-in frequency. Inherits from [conditionalAccessSessionControl](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesssessioncontrol?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| authenticationType | signInFrequencyAuthenticationType | The possible values are `primaryAndSecondaryAuthentication`, `secondaryAuthentication`, `unknownFutureValue`. This property isn't required when using **frequencyInterval** with the value of `timeBased`. |
| frequencyInterval | signInFrequencyInterval | The possible values are `timeBased`, `everyTime`, `unknownFutureValue`. Sign-in frequency of `everyTime` is available for risky users, risky sign-ins, and Intune device enrollment. For more information, see [Require reauthentication every time](https://aka.ms/RequireReauthentication). |
| isEnabled | Boolean | Specifies whether the session control is enabled. |
| type | signinFrequencyType | The possible values are: `days`, `hours`. |
| value | Int32 | The number of `days` or `hours`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "isEnabled":true,
  "type": "String",
  "value": 1024,
  "authenticationType": "String",
  "frequencyInterval": "String"
}
```
