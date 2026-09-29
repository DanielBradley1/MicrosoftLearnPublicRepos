<!-- Source: https://learn.microsoft.com/en-us/defender-cloud-apps/api-discovery-list-categories -->
<!-- Sitemap-Last-Modified: 2024-10-23 -->

# List continuous report categories - cloud discovery API

Run the POST request to fetch a list of categories associated with a continuous report.

## HTTP request

```rest
POST api/v1/discovery/discovered_apps/categories/
```

## Request BODY parameters

| Parameter | Description |
| --- | --- |
| filters \(*optional*\) | Filter objects with all the search filters for the request by category id |
| sortDirection \(*optional*\) | The sorting direction. Possible values are: `asc` and `desc` |
| sortField \(*optional*\) | Fields used to sort entities. Possible values are:  <br>- **score**: The total number of apps in this category |
| skip \(*optional*\) | Skips the specified number of records |
| limit \(*optional*\) | Maximum number of records returned by the request |
| streamId | Filter records by continuous report ID |
| timeFrame \(*optional*\) | Filter records by the number of days since the continuous report was last used |

## Example

### Request

Here is an example of the request.

```rest
curl -XPOST -H "Authorization:Token <your_token_key>" -H "Content-Type: application/json" "https://<tenant_id>.<tenant_region>.portal.cloudappsecurity.com/api/v1/discovery/discovered_apps/categories/" -d '{
  "filters": {
    // some filters
  },
  "skip": 5,
  "limit": 10,
  "streamId": <continuous_report_id>
}'
```

### Response

Returns a list of app tags in JSON format.

```json
[
  {
    "id": "SAASDB_CATEGORY_PRODUCT_DESIGN",
    "total": 2
  }
]
```

The response object defines the following properties.

| Field name | Field type | Field description |
| --- | --- | --- |
| id | string | The id of the category |
| total | int | The total number of services in the category |

## Supported log types

The following category IDs are currently supported:

| ID | Name |
| --- | --- |
| SAASDB\_CATEGORY\_ACCOUNTING\_AND\_FINANCE | Accounting and finance |
| SAASDB\_CATEGORY\_ADVERTISING | Advertising |
| SAASDB\_CATEGORY\_ALL | All categories |
| SAASDB\_CATEGORY\_BUSINESS\_INTELLIGENCE | Business intelligence |
| SAASDB\_CATEGORY\_BUSINESS\_MANAGEMENT | Business management |
| SAASDB\_CATEGORY\_CLOUD\_COMPUTING\_PLATFORM | Cloud computing platform |
| SAASDB\_CATEGORY\_CLOUD\_STORAGE | Cloud storage |
| SAASDB\_CATEGORY\_CODE\_HOSTING | Code hosting |
| SAASDB\_CATEGORY\_COLLABORATION | Collaboration |
| SAASDB\_CATEGORY\_COMMUNICATIONS | Communications |
| SAASDB\_CATEGORY\_CONSUMER | Consumer |
| SAASDB\_CATEGORY\_CONTENT\_MANAGEMENT | Content management |
| SAASDB\_CATEGORY\_CONTENT\_SHARING | Content sharing |
| SAASDB\_CATEGORY\_CRM | CRM |
| SAASDB\_CATEGORY\_CUSTOMER\_SUPPORT | Customer support |
| SAASDB\_CATEGORY\_DATA\_ANALYTICS | Data analytics |
| SAASDB\_CATEGORY\_DEVELOPMENT\_TOOLS | Development tools |
| SAASDB\_CATEGORY\_ECOMMERCE | E-commerce |
| SAASDB\_CATEGORY\_EDUCATION | Education |
| SAASDB\_CATEGORY\_FORUMS | Forums |
| SAASDB\_CATEGORY\_GENERATIVE\_AI | Generative AI |
| SAASDB\_CATEGORY\_HEALTH | Health |
| SAASDB\_CATEGORY\_HOSTING\_SERVICES | Hosting services |
| SAASDB\_CATEGORY\_HUMAN\_RESOURCE\_MANAGEMENT | Human-resource management |
| SAASDB\_CATEGORY\_INTERNET\_OF\_THINGS | Internet of Things |
| SAASDB\_CATEGORY\_IT\_SERVICES | IT services |
| SAASDB\_CATEGORY\_MARKETING | Marketing |
| SAASDB\_CATEGORY\_MEDIA | Media |
| SAASDB\_CATEGORY\_NEWS\_AND\_ENTERTAINMENT | News and entertainment |
| SAASDB\_CATEGORY\_ONLINE\_MEETINGS | Online meetings |
| SAASDB\_CATEGORY\_OPERATIONS\_MANAGEMENT | Operations management |
| SAASDB\_CATEGORY\_PERSONAL\_INSTANT\_MESSAGING | Personal instant messaging |
| SAASDB\_CATEGORY\_PRODUCT\_DESIGN | Product design |
| SAASDB\_CATEGORY\_PRODUCTIVITY | Productivity |
| SAASDB\_CATEGORY\_PROJECT\_MANAGEMENT | Project management |
| SAASDB\_CATEGORY\_PROPERTY\_MANAGEMENT | Property management |
| SAASDB\_CATEGORY\_SALES | Sales |
| SAASDB\_CATEGORY\_SECURITY | Security |
| SAASDB\_CATEGORY\_SOCIAL\_NETWORK | Social network |
| SAASDB\_CATEGORY\_SUPLLY\_CHAIN\_AND\_LOGISTICS | Supply chain and logistics |
| SAASDB\_CATEGORY\_TIME\_TRACKING | Time tracking |
| SAASDB\_CATEGORY\_TRANSPORTATION\_AND\_TRAVEL | Transportation and travel |
| SAASDB\_CATEGORY\_UNCLASSIFIED | Unclassified |
| SAASDB\_CATEGORY\_VENDOR\_MANAGEMENT\_SYSTEM | Vendor management system |
| SAASDB\_CATEGORY\_WEB\_ANALYTICS | Web analytics |
| SAASDB\_CATEGORY\_WEBMAIL | Webmail |
| SAASDB\_CATEGORY\_WEBSITE\_MONITORING | Website monitoring |
| SAASDB\_SUBCATEGORY\_INSURANCE\_AND\_INVESTMENTS | Accounting and finance |

If you run into any problems, we're here to help. To get assistance or support for your product issue, please [open a support ticket](https://learn.microsoft.com/en-us/defender-xdr/contact-defender-support).
