<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/industrydata-industrydatarun?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# industryDataRun resource type

Namespace: microsoft.graph.industryData

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an ephemeral run that contains data for all subordinate activities performed by the system. Industry data automates a run every 12 hours. Each of these operations is represented by an **industryDataRun** resource. All flows that are active at the time of the run start are included in the run. The individual flows are represented by an [industryDataRunActivity](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-industrydatarunactivity?view=graph-rest-beta) resource.

During a run, the data supplied is validated, bringing in good data to the data lake and flagging bad data. For more information about data validation, see [Validation rules and descriptions](https://learn.microsoft.com/en-us/schooldatasync/validation-rules-and-descriptions). To determine the health of the data, it goes through data matching and validation rules to help safeguard required and optional data. Good data goes into the data lake. Data that doesn't pass validation is identified as errors or warnings and isn't sent to the data lake. The following list shows possible results for a run:

- `running`: Run is actively running.
- `completed`: Run completed without any errors or warnings.
- `completedWithErrors`: Run completed but errors were found. Error is a record where the required data didn't pass a data matching and/or validation rule and therefore, was removed and not sent to the data lake.
- `completedWithWarnings`: Run completed but only warnings were found. Warning is a value on a record where optional data didn't pass a data matching and/or validation rule. The value was removed but the record was sent to the data lake.
- `failed`: Run canceled by the system.

For details about how statistics can assist with health and monitoring a run group, see [industryDataRun: getStatistics](https://learn.microsoft.com/en-us/graph/api/industrydata-industrydatarun-getstatistics?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/industrydata-industrydatarun-list?view=graph-rest-beta) | [microsoft.graph.industryData.industryDataRun](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-industrydatarun?view=graph-rest-beta) collection | Get a list of the [industryDataRun](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-industrydatarun?view=graph-rest-beta) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/industrydata-industrydatarun-get?view=graph-rest-beta) | [microsoft.graph.industryData.industryDataRun](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-industrydatarun?view=graph-rest-beta) | Read the properties and relationships of an [industryDataRun](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-industrydatarun?view=graph-rest-beta) object. |
| [Get statistics](https://learn.microsoft.com/en-us/graph/api/industrydata-industrydatarun-getstatistics?view=graph-rest-beta) | [microsoft.graph.industryData.industryDataRunStatistics](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-industrydatarunstatistics?view=graph-rest-beta) | Calculate statistics for a run group. |
| [Start](https://learn.microsoft.com/en-us/graph/api/industrydata-industrydatarun-start?view=graph-rest-beta) | None | Start a new [industryDataRun](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-industrydatarun?view=graph-rest-beta). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| blockingError | [publicError](https://learn.microsoft.com/en-us/graph/api/resources/publicerror?view=graph-rest-beta) | An error object to diagnose critical failures in the run. |
| displayName | String | The name of the run for rendering in a user interface. |
| endDateTime | DateTimeOffset | The date and time when the run finished or null if the run is still in-progress. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on `Jan 1, 2014 is 2014-01-01T00:00:00Z`. |
| startDateTime | DateTimeOffset | The date and time when the run started. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on `Jan 1, 2014 is 2014-01-01T00:00:00Z`. |
| status | microsoft.graph.industryData.industryDataRunStatus | The current status of the run. The possible values are: `running`, `failed`, `completed`, `completedWithErrors`, `completedWithWarnings`, `unknownFutureValue`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| activities | [microsoft.graph.industryData.industryDataRunActivity](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-industrydatarunactivity?view=graph-rest-beta) collection | The set of activities performed during the run. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.industryData.industryDataRun",
  "blockingError": {
    "@odata.type": "microsoft.graph.publicError"
  },
  "displayName": "String",
  "endDateTime": "String (timestamp)",
  "startDateTime": "String (timestamp)",
  "status": "String"
}
```
