<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-service?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-01-16 -->

# service resource type

Namespace: microsoft.graph.cloudLicensing

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a specific service granted by an individual [usageRight](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-usageright?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| assignableTo | [microsoft.graph.cloudLicensing.assigneeTypes](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-service?view=graph-rest-beta#assigneetypes-values) | Identifies the types of directory objects to which the service can be assigned. The possible values are: `none`, `user`, `group`, `device`, `unknownFutureValue`.  <br>  <br>The **assigneeTypes** property is a multi-valued enumeration and the property can contain multiple values in a comma-separated list. |
| planId | Guid | The unique identifier of the service plan that is equal to the **servicePlanId** property on the related [servicePlanInfo](https://learn.microsoft.com/en-us/graph/api/resources/serviceplaninfo?view=graph-rest-beta) objects. |
| planName | String | The name of the service plan that is equal to the **servicePlanName** property on the related [servicePlanInfo](https://learn.microsoft.com/en-us/graph/api/resources/serviceplaninfo?view=graph-rest-beta) objects. |

### assigneeTypes values

| Member | Description |
| :--- | :--- |
| none | No flags are enabled; this service can't be assigned. |
| user | If enabled, this service can be assigned directly to users. |
| group | If enabled, this service can be assigned to groups. |
| device | If enabled, this service can be assigned directly to devices. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudLicensing.service",
  "assignableTo": "String",
  "planId": "Guid",
  "planName": "String"
}
```
