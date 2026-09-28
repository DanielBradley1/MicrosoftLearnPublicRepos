<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/relyingpartydetailedsummary?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# relyingPartyDetailedSummary resource type

Namespace: microsoft.graph

Represents the summary of AD FS relying parties' information on daily, weekly, or monthly frequency.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get relying party detailed summary](https://learn.microsoft.com/en-us/graph/api/reportroot-getrelyingpartydetailedsummary?view=graph-rest-1.0) | [relyingPartyDetailedSummary](https://learn.microsoft.com/en-us/graph/api/resources/relyingpartydetailedsummary?view=graph-rest-1.0) collection | Get a summary of AD FS relying parties information. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| failedSignInCount | Int64 | Number of failed sign ins on AD FS in the period specified.  <br>  <br>Supports `$orderby`, `$filter` \(`eq`\). |
| id | String | Unique identifier for the report. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| migrationStatus | migrationStatus | Indicates whether the app can be easily moved to Entra ID. The possible values are: `ready`, `needsReview`, `additionalStepsRequired`, `unknownFutureValue`.  <br>  <br>Supports `$orderby`, `$filter` \(`eq`\). |
| migrationValidationDetails | [keyValuePair](https://learn.microsoft.com/en-us/graph/api/resources/keyvaluepair?view=graph-rest-1.0) collection | Specifies all the validations checks done on applications config details. |
| relyingPartyId | String | Identifies the relying party to this federation service. It's used when issuing claims to the relying party.  <br>  <br>Supports `$orderby`, `$filter` \(`eq`\). |
| relyingPartyName | String | Name of the relying party's website or other entity on the Internet that uses an identity provider to authenticate a user who wants to log in.  <br>  <br>Supports `$orderby`, `$filter` \(`eq`\). |
| replyUrls | String collection | Specifies where the relying party expects to receive the token. |
| serviceId | String | Uniquely identifies the Active Directory forest.  <br>  <br>Supports `$orderby`, `$filter` \(`eq`\). |
| signInSuccessRate | Double | Calculated as `Number of successful / (Number of successful + Number of failed sign ins)` or `successfulSignInCount / totalSignInCount` on AD FS in the period specified.  <br>  <br>Supports `$orderby`, `$filter` \(`eq`\). |
| successfulSignInCount | Int64 | Number of successful sign ins on AD FS.  <br>  <br>Supports `$orderby`, `$filter` \(`eq`\). |
| totalSignInCount | Int64 | Number of successful + failed sign ins on AD FS in the period specified.  <br>  <br>Supports `$orderby`, `$filter` \(`eq`\). |
| uniqueUserCount | Int64 | Number of unique users that signed into the application.  <br>  <br>Supports `$orderby`, `$filter` \(`eq`\). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.relyingPartyDetailedSummary",
  "id": "String (identifier)",
  "relyingPartyId": "String",
  "serviceId": "String",
  "relyingPartyName": "String",
  "successfulSignInCount": "Integer",
  "failedSignInCount": "Integer",
  "totalSignInCount": "Integer",
  "signInSuccessRate": "Double",
  "uniqueUserCount": "Integer",
  "migrationStatus": "String",
  "migrationValidationDetails": [
    {
      "@odata.type": "microsoft.graph.keyValuePair"
    }
  ],
  "replyUrls": [
    "String"
  ]
}
```
