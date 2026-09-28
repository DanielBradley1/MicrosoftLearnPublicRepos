<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/bookingbusiness?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-10-09 -->

# bookingBusiness resource type

Namespace: microsoft.graph

Represents a business in Microsoft Bookings. This is the top level object in the Microsoft Bookings API. It contains business information and related business objects such as appointments, customers, services, and staff members.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/bookingbusiness-list?view=graph-rest-1.0) | [bookingBusiness](https://learn.microsoft.com/en-us/graph/api/resources/bookingbusiness?view=graph-rest-1.0) collection | Get a collection of **bookingBusiness** objects in the tenant. |
| [Create](https://learn.microsoft.com/en-us/graph/api/bookingbusiness-post-bookingbusinesses?view=graph-rest-1.0) | [bookingBusiness](https://learn.microsoft.com/en-us/graph/api/resources/bookingbusiness?view=graph-rest-1.0) | Create a new Microsoft Bookings business. |
| [Get](https://learn.microsoft.com/en-us/graph/api/bookingbusiness-get?view=graph-rest-1.0) | [bookingBusiness](https://learn.microsoft.com/en-us/graph/api/resources/bookingbusiness?view=graph-rest-1.0) | Read properties and relationships of a **bookingBusiness** object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/bookingbusiness-update?view=graph-rest-1.0) | [bookingBusiness](https://learn.microsoft.com/en-us/graph/api/resources/bookingbusiness?view=graph-rest-1.0) | Update the properties of a **bookingBusiness** object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/bookingbusiness-delete?view=graph-rest-1.0) | None | Delete a **bookingBusiness** object. |
| [Create bookingAppointment](https://learn.microsoft.com/en-us/graph/api/bookingbusiness-post-appointments?view=graph-rest-1.0) | [bookingAppointment](https://learn.microsoft.com/en-us/graph/api/resources/bookingappointment?view=graph-rest-1.0) | Create a new **bookingAppointment** by posting to the appointments collection. |
| [List appointments](https://learn.microsoft.com/en-us/graph/api/bookingbusiness-list-appointments?view=graph-rest-1.0) | [bookingAppointment](https://learn.microsoft.com/en-us/graph/api/resources/bookingappointment?view=graph-rest-1.0) collection | Get a **bookingAppointment** object collection. |
| [Create bookingCustomer](https://learn.microsoft.com/en-us/graph/api/bookingbusiness-post-customers?view=graph-rest-1.0) | [bookingCustomer](https://learn.microsoft.com/en-us/graph/api/resources/bookingcustomer?view=graph-rest-1.0) | Create a new **bookingCustomer** by posting to the customers collection. |
| [List customers](https://learn.microsoft.com/en-us/graph/api/bookingbusiness-list-customers?view=graph-rest-1.0) | [bookingCustomer](https://learn.microsoft.com/en-us/graph/api/resources/bookingcustomer?view=graph-rest-1.0) collection | Get a **bookingCustomer** object collection. |
| [Create bookingService](https://learn.microsoft.com/en-us/graph/api/bookingbusiness-post-services?view=graph-rest-1.0) | [bookingService](https://learn.microsoft.com/en-us/graph/api/resources/bookingservice?view=graph-rest-1.0) | Create a new **bookingService** by posting to the services collection. |
| [List services](https://learn.microsoft.com/en-us/graph/api/bookingbusiness-list-services?view=graph-rest-1.0) | [bookingService](https://learn.microsoft.com/en-us/graph/api/resources/bookingservice?view=graph-rest-1.0) collection | Get a **bookingService** object collection. |
| [Create bookingStaffMember](https://learn.microsoft.com/en-us/graph/api/bookingbusiness-post-staffmembers?view=graph-rest-1.0) | [bookingStaffMember](https://learn.microsoft.com/en-us/graph/api/resources/bookingstaffmember?view=graph-rest-1.0) | Create a new **bookingStaffMember** by posting to the staffMembers collection. |
| [List staffMembers](https://learn.microsoft.com/en-us/graph/api/bookingbusiness-list-staffmembers?view=graph-rest-1.0) | [bookingStaffMember](https://learn.microsoft.com/en-us/graph/api/resources/bookingstaffmember?view=graph-rest-1.0) collection | Get a **bookingStaffMember** object collection. |
| [List customQuestions](https://learn.microsoft.com/en-us/graph/api/bookingbusiness-list-customquestions?view=graph-rest-1.0) | [bookingCustomQuestion](https://learn.microsoft.com/en-us/graph/api/resources/bookingcustomquestion?view=graph-rest-1.0) collection | Get the **bookingCustomQuestion** resources from the **customQuestions** navigation property. |
| [Create bookingCustomQuestion](https://learn.microsoft.com/en-us/graph/api/bookingbusiness-post-customquestions?view=graph-rest-1.0) | [bookingCustomQuestion](https://learn.microsoft.com/en-us/graph/api/resources/bookingcustomquestion?view=graph-rest-1.0) | Create a new **bookingCustomQuestion** object. |
| [List calendarView](https://learn.microsoft.com/en-us/graph/api/bookingbusiness-list-calendarview?view=graph-rest-1.0) | [bookingAppointment](https://learn.microsoft.com/en-us/graph/api/resources/bookingappointment?view=graph-rest-1.0) collection | Get the collection of **bookingAppointment** objects that occurs in the specified date range. |
| [Publish](https://learn.microsoft.com/en-us/graph/api/bookingbusiness-publish?view=graph-rest-1.0) | None | Make the scheduling page of this business available to external customers. Set the **isPublished** property to `true`, and **publicUrl** property to the URL of the scheduling page. |
| [Unpublish](https://learn.microsoft.com/en-us/graph/api/bookingbusiness-unpublish?view=graph-rest-1.0) | None | Make the scheduling page of this business not available to external customers. Set the **isPublished** property to `false`, and the **publicUrl** property to `null`. |
| [Get staff availability](https://learn.microsoft.com/en-us/graph/api/bookingbusiness-getstaffavailability?view=graph-rest-1.0) | [staffAvailabilityItem](https://learn.microsoft.com/en-us/graph/api/resources/staffavailabilityitem?view=graph-rest-1.0) collection | Get the availability information of staff members of a Microsoft Bookings calendar. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| address | [physicalAddress](https://learn.microsoft.com/en-us/graph/api/resources/physicaladdress?view=graph-rest-1.0) | The street address of the business. The **address** property, together with **phone** and **webSiteUrl**, appear in the footer of a business scheduling page. The attribute **type** of physicalAddress is not supported in v1.0. Internally we map the addresses to the type `others`. |
| bookingPageSettings | [bookingPageSettings](https://learn.microsoft.com/en-us/graph/api/resources/bookingpagesettings?view=graph-rest-1.0) | Settings for the published booking page. |
| businessHours | [bookingWorkHours](https://learn.microsoft.com/en-us/graph/api/resources/bookingworkhours?view=graph-rest-1.0) collection | The hours of operation for the business. |
| businessType | String | The type of business. |
| createdDateTime | DateTimeOffset | The date, time, and time zone when the booking business was created. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| defaultCurrencyIso | String | The code for the currency that the business operates in on Microsoft Bookings. |
| displayName | String | The name of the business, which interfaces with customers. This name appears at the top of the business scheduling page. |
| email | String | The email address for the business. |
| id | String | A unique programmatic identifier for the business. Read-only. |
| isPublished | Boolean | The scheduling page has been made available to external customers. Use the **publish** and **unpublish** actions to set this property. Read-only. |
| languageTag | String | The language of the self-service booking page. |
| lastUpdatedDateTime | DateTimeOffset | The date, time, and time zone when the booking business was last updated. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| phone | String | The telephone number for the business. The **phone** property, together with **address** and **webSiteUrl**, appear in the footer of a business scheduling page. |
| publicUrl | String | The URL for the scheduling page, which is set after you [publish](https://learn.microsoft.com/en-us/graph/api/bookingbusiness-publish?view=graph-rest-1.0) or [unpublish](https://learn.microsoft.com/en-us/graph/api/bookingbusiness-unpublish?view=graph-rest-1.0) the page. Read-only. |
| schedulingPolicy | [bookingSchedulingPolicy](https://learn.microsoft.com/en-us/graph/api/resources/bookingschedulingpolicy?view=graph-rest-1.0) | Specifies how bookings can be created for this business. |
| webSiteUrl | String | The URL of the business web site. The **webSiteUrl** property, together with **address**, **phone**, appear in the footer of a business scheduling page. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| appointments | [bookingAppointment](https://learn.microsoft.com/en-us/graph/api/resources/bookingappointment?view=graph-rest-1.0) collection | All the appointments of this business. Read-only. Nullable. |
| calendarView | [bookingAppointment](https://learn.microsoft.com/en-us/graph/api/resources/bookingappointment?view=graph-rest-1.0) collection | The set of appointments of this business in a specified date range. Read-only. Nullable. |
| customers | [bookingCustomer](https://learn.microsoft.com/en-us/graph/api/resources/bookingcustomer?view=graph-rest-1.0) collection | All the customers of this business. Read-only. Nullable. |
| customQuestions | [bookingCustomQuestion](https://learn.microsoft.com/en-us/graph/api/resources/bookingcustomquestion?view=graph-rest-1.0) collection | All the custom questions of this business. Read-only. Nullable. |
| services | [bookingService](https://learn.microsoft.com/en-us/graph/api/resources/bookingservice?view=graph-rest-1.0) collection | All the services offered by this business. Read-only. Nullable. |
| staffMembers | [bookingStaffMember](https://learn.microsoft.com/en-us/graph/api/resources/bookingstaffmember?view=graph-rest-1.0) collection | All the staff members that provide services in this business. Read-only. Nullable. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.bookingBusiness",
  "address": {"@odata.type": "microsoft.graph.physicalAddress"},
  "bookingPageSettings": {"@odata.type": "microsoft.graph.bookingPageSettings"},
  "businessHours": [{"@odata.type": "microsoft.graph.bookingWorkHours"}],
  "businessType": "String",
  "createdDateTime": "String (timestamp)",
  "defaultCurrencyIso": "String",
  "displayName": "String",
  "email": "String",
  "id": "String (identifier)",
  "isPublished": "Boolean",
  "languageTag": "String",
  "lastUpdatedDateTime": "String (timestamp)",
  "phone": "String",
  "publicUrl": "String",
  "schedulingPolicy": {"@odata.type": "microsoft.graph.bookingSchedulingPolicy"},
  "webSiteUrl": "String"
}
```
