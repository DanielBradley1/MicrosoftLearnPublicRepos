<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/subjectrightsrequeststage?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# subjectRightsRequestStage enum type

Namespace: microsoft.graph

Represents the stage of a subject rights request. This enumeration is used by multiple resources.

The following table lists the members of an [evolvable enumeration](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations). Use the `Prefer: include-unknown-enum-members` request header to get the following values in this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `approval`.

## Members

| Member | Description |
| :--- | :--- |
| contentRetrieval | The stage where content is being retrieved for the subject rights request.  <br>  <br>Applies to: **stage** property of [subjectRightsRequestHistory](https://learn.microsoft.com/en-us/graph/api/resources/subjectrightsrequesthistory?view=graph-rest-1.0) and [subjectRightsRequestStageDetail](https://learn.microsoft.com/en-us/graph/api/resources/subjectrightsrequeststagedetail?view=graph-rest-1.0) |
| contentReview | The stage where content is being reviewed for the subject rights request.  <br>  <br>Applies to: **stage** property of [subjectRightsRequestHistory](https://learn.microsoft.com/en-us/graph/api/resources/subjectrightsrequesthistory?view=graph-rest-1.0) and [subjectRightsRequestStageDetail](https://learn.microsoft.com/en-us/graph/api/resources/subjectrightsrequeststagedetail?view=graph-rest-1.0) |
| generateReport | The stage where a report is being generated for the subject rights request.  <br>  <br>Applies to: **stage** property of [subjectRightsRequestHistory](https://learn.microsoft.com/en-us/graph/api/resources/subjectrightsrequesthistory?view=graph-rest-1.0) and [subjectRightsRequestStageDetail](https://learn.microsoft.com/en-us/graph/api/resources/subjectrightsrequeststagedetail?view=graph-rest-1.0) |
| contentDeletion | The stage where content is being deleted as part of the subject rights request.  <br>  <br>Applies to: **stage** property of [subjectRightsRequestHistory](https://learn.microsoft.com/en-us/graph/api/resources/subjectrightsrequesthistory?view=graph-rest-1.0) and [subjectRightsRequestStageDetail](https://learn.microsoft.com/en-us/graph/api/resources/subjectrightsrequeststagedetail?view=graph-rest-1.0) |
| caseResolved | The stage where the subject rights request case has been resolved.  <br>  <br>Applies to: **stage** property of [subjectRightsRequestHistory](https://learn.microsoft.com/en-us/graph/api/resources/subjectrightsrequesthistory?view=graph-rest-1.0) and [subjectRightsRequestStageDetail](https://learn.microsoft.com/en-us/graph/api/resources/subjectrightsrequeststagedetail?view=graph-rest-1.0) |
| contentEstimate | The stage where content is being estimated for the subject rights request.  <br>  <br>Applies to: **stage** property of [subjectRightsRequestHistory](https://learn.microsoft.com/en-us/graph/api/resources/subjectrightsrequesthistory?view=graph-rest-1.0) and [subjectRightsRequestStageDetail](https://learn.microsoft.com/en-us/graph/api/resources/subjectrightsrequeststagedetail?view=graph-rest-1.0) |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use.  <br>  <br>Applies to: **stage** property of [subjectRightsRequestHistory](https://learn.microsoft.com/en-us/graph/api/resources/subjectrightsrequesthistory?view=graph-rest-1.0) and [subjectRightsRequestStageDetail](https://learn.microsoft.com/en-us/graph/api/resources/subjectrightsrequeststagedetail?view=graph-rest-1.0) |
| approval | The stage where the subject rights request is awaiting approval.  <br>  <br>Applies to: **stage** property of [subjectRightsRequestHistory](https://learn.microsoft.com/en-us/graph/api/resources/subjectrightsrequesthistory?view=graph-rest-1.0) and [subjectRightsRequestStageDetail](https://learn.microsoft.com/en-us/graph/api/resources/subjectrightsrequeststagedetail?view=graph-rest-1.0) |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.subjectRightsRequestStage"
}
```
