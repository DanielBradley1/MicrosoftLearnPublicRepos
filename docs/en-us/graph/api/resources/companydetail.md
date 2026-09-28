<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/companydetail?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-08-08 -->

# companyDetail resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents information about companies related to entities within their [profile](https://learn.microsoft.com/en-us/graph/api/resources/profile?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| address | [physicalAddress](https://learn.microsoft.com/en-us/graph/api/resources/physicaladdress?view=graph-rest-beta) | Address of the company. |
| companyCode | String | Legal entity number of the company or its subdivision. For information on how to set the value for the **companyCode**, see [profileSourceAnnotation](https://learn.microsoft.com/en-us/graph/api/resources/profilesourceannotation?view=graph-rest-beta). |
| costCenter | String | The cost center associated with the company or department. |
| department | String | Department Name within a company. |
| displayName | String | Company name. |
| division | String | The division within the company. |
| officeLocation | String | Office Location of the person referred to. |
| pronunciation | String | Pronunciation guide for the company name. |
| secondaryDepartment | String | Secondary Department Name within a company. |
| webUrl | String | Link to the company home page. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "address": {"@odata.type": "microsoft.graph.physicalAddress"},
  "companyCode": "String",
  "costCenter": "String",
  "department": "String",
  "displayName": "String",
  "division": "String",
  "officeLocation": "String",
  "pronunciation": "String",
  "secondaryDepartment": "String",
  "webUrl": "String"
}
```
