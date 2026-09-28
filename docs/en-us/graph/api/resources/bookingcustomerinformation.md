<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/bookingcustomerinformation?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# bookingCustomerInformation resource type

Namespace: microsoft.graph

Registers the customer properties for an appointment. An appointment will contain a list of customer information and each unit will indicate the properties of a customer who is part of that appointment.

Inherits from [bookingCustomerInformationBase](https://learn.microsoft.com/en-us/graph/api/resources/bookingcustomerinformationbase?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| customerId | String | The ID of the **bookingCustomer** for this appointment. If no ID is specified when an appointment is created, then a new **bookingCustomer** object is created. Once set, you should consider the **customerId** immutable. |
| customQuestionAnswers | [bookingQuestionAnswer](https://learn.microsoft.com/en-us/graph/api/resources/bookingquestionanswer?view=graph-rest-1.0) collection | It consists of the list of custom questions and answers given by the customer as part of the appointment |
| emailAddress | String | The SMTP address of the [bookingCustomer](https://learn.microsoft.com/en-us/graph/api/resources/bookingcustomer?view=graph-rest-1.0) who is booking the appointment |
| location | [location](https://learn.microsoft.com/en-us/graph/api/resources/location?view=graph-rest-1.0) | Represents location information for the bookingCustomer who is booking the appointment. |
| name | String | The customer's name. |
| notes | String | Notes from the customer associated with this appointment. You can get the value only when reading this **bookingAppointment** by its ID. You can set this property only when initially creating an appointment with a new customer. After that point, the value is computed from the customer represented by the **customerId**. |
| phone | String | The customer's phone number. |
| timeZone | String | The time zone of the customer. For a list of possible values, see [dateTimeTimeZone](https://learn.microsoft.com/en-us/graph/api/resources/datetimetimezone?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.bookingCustomerInformation",
  "customerId": "String",
  "customQuestionAnswers": [
    {
      "@odata.type": "microsoft.graph.bookingQuestionAnswer"
    }
  ],
  "emailAddress": "String",
  "location": {
    "@odata.type": "microsoft.graph.location"
  },
  "name": "String",
  "notes": "String",
  "phone": "String",
  "timeZone": "String"
}
```
