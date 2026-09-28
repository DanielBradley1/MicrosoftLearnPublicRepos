<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/educationalactivitydetail?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-04-18 -->

# educationalActivityDetail resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents more detail about an undergraduate, graduate, postgraduate degree, or other educational activity for a user and is used within an [educationalActivity](https://learn.microsoft.com/en-us/graph/api/resources/educationalactivity?view=graph-rest-beta) resource.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| abbreviation | String | Shortened name of the degree or program, for example, `PhD` and `MBA`. |
| activities | String collection | Extracurricular activities undertaken alongside the program. |
| awards | String collection | Any awards or honors associated with the program. |
| description | String | Short description of the program provided by the user. |
| displayName | String | Long-form name of the program that the user provided. |
| fieldsOfStudy | String collection | Majors and minors associated with the program, if applicable. |
| grade | String | The final grade, class, grade point average \(GPA\), or score. |
| notes | String | More notes provided by the user. |
| webUrl | String | Link to the degree or program page. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "abbreviation": "String",
  "activities": ["String"],
  "awards": ["String"],
  "description": "String",
  "displayName": "String",
  "fieldsOfStudy": ["String"],
  "grade": "String",
  "notes": "String",
  "webUrl": "String"
}
```
