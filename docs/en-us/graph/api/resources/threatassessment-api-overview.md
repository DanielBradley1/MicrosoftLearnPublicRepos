<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/threatassessment-api-overview?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-13 -->

# Use the Microsoft Graph threat assessment API

The Microsoft Graph threat assessment API helps organizations to assess the threat received by any user in a tenant. This empowers customers to report spam emails, phishing URLs or malware attachments they receive to Microsoft. The policy check result and rescan result can help tenant administrators understand the threat scanning verdict and adjust their organizational policy.

## Authorization

Microsoft Graph controls access to resources via permissions. You must specify the permissions you need in order to access threat assessment resources. Typically, you specify permissions in the Microsoft Entra admin center. For more information, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference) and [Threat assessment permissions](https://learn.microsoft.com/en-us/graph/permissions-reference#threat-assessment-permissions).

## Common use cases

The Microsoft Graph threat assessment API provides methods to list, create, and get threat assessment requests and retrieve the assessment results.

| Use cases | REST resources | See also |
| :--- | :--- | :--- |
| List, create, and get threat assessment requests | [threatAssessmentRequest](https://learn.microsoft.com/en-us/graph/api/resources/threatassessmentrequest?view=graph-rest-1.0)  <br>[mailAssessmentRequest](https://learn.microsoft.com/en-us/graph/api/resources/mailassessmentrequest?view=graph-rest-1.0)  <br>[emailFileAssessmentRequest](https://learn.microsoft.com/en-us/graph/api/resources/emailfileassessmentrequest?view=graph-rest-1.0)  <br>[fileAssessmentRequest](https://learn.microsoft.com/en-us/graph/api/resources/fileassessmentrequest?view=graph-rest-1.0)  <br>[urlAssessmentRequest](https://learn.microsoft.com/en-us/graph/api/resources/urlassessmentrequest?view=graph-rest-1.0)  <br> | [Create threatAssessmentRequest](https://learn.microsoft.com/en-us/graph/api/informationprotection-post-threatassessmentrequests?view=graph-rest-1.0)  <br>[Get threatAssessmentRequest](https://learn.microsoft.com/en-us/graph/api/threatassessmentrequest-get?view=graph-rest-1.0)  <br>[List threatAssessmentRequest](https://learn.microsoft.com/en-us/graph/api/informationprotection-list-threatassessmentrequests?view=graph-rest-1.0) |
| Get threat assessment results | [threatAssessmentResult](https://learn.microsoft.com/en-us/graph/api/resources/threatassessmentresult?view=graph-rest-1.0) | [Get threatAssessmentResult](https://learn.microsoft.com/en-us/graph/api/threatassessmentrequest-get?view=graph-rest-1.0#example-5-expand-threat-assessment-results-for-a-request) |

## Next steps

Threat assessment resources and APIs can open up new ways for you to engage with users and manage their experiences with Microsoft Graph. To learn more:

- Drill down on the [methods](https://learn.microsoft.com/en-us/graph/api/resources/threatassessmentrequest?view=graph-rest-1.0#methods), [properties](https://learn.microsoft.com/en-us/graph/api/resources/threatassessmentrequest?view=graph-rest-1.0#properties), and [relationships](https://learn.microsoft.com/en-us/graph/api/resources/threatassessmentrequest?view=graph-rest-1.0#relationships) of the [threat assessment request](https://learn.microsoft.com/en-us/graph/api/resources/threatassessmentrequest?view=graph-rest-1.0) and [threat asessment result](https://learn.microsoft.com/en-us/graph/api/resources/threatassessmentresult?view=graph-rest-1.0) resources.
- Try the API in the [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer).
