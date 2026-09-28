<!-- Source: https://learn.microsoft.com/en-us/graph/download-resources-from-assignment -->
<!-- Sitemap-Last-Modified: 2024-11-07 -->

# Download all resources from a set of assignments

This article describes how to use Microsoft Graph to download all SharePoint resources from a set of assignments at the end of a grade period. This can be helpful for end-of-year archiving or for reviewing feedback given to students.

> **Note:** You can use [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer) to test the APIs mentioned in this article.

## Get class assignment information

Assignment information is linked to a class. You can use the [Get educationAssignment](https://learn.microsoft.com/en-us/graph/api/educationassignment-get) API to get information about class assignments. You can then use the [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters) to customize the response.

## Get assignment and submission resource information

Assignments and submissions are an important part in the interaction between teachers and students. You can use the following APIs to get information about assignment and submission resources:

- [Get educationAssignmentResource](https://learn.microsoft.com/en-us/graph/api/educationassignmentresource-get) to retrieve the properties of an [education assignment resource](https://learn.microsoft.com/en-us/graph/api/resources/educationassignmentresource) associated with an assignment.
- [Get educationSubmissionResource](https://learn.microsoft.com/en-us/graph/api/educationsubmissionresource-get) to retrieve the properties of a specific resource associated with a [submission](https://learn.microsoft.com/en-us/graph/api/resources/educationsubmissionresource).

## Get submission feedback information

The education API in Microsoft Graph uses feedback resource folders as a destination for feedback files. To get details about the user's submission feedback, see [Upload feedback files for education submissions](https://learn.microsoft.com/en-us/graph/education-upload-feedback-resource-overview).

You can use the [List outcomes](https://learn.microsoft.com/en-us/graph/api/educationsubmission-list-outcomes) API to get a list of education outcome objects.

## Download files from SharePoint

Before you can download the SharePoint resources, you need the **driveId** and **itemId** that are related to each assignment resource. You can use the [List educationAssignmentResources](https://learn.microsoft.com/en-us/graph/api/educationassignment-list-resources) response object to extract information about the corresponding **driveId** and **itemId** from the **fileUrl** property.

You can then use the [Download file](https://learn.microsoft.com/en-us/graph/api/driveitem-get-content) API to download the contents of the file from SharePoint. Note that only [driveItems](https://learn.microsoft.com/en-us/graph/api/resources/driveitem) with the **file** property can be downloaded.

Alternatively, you can download the files from a JavaScript app. For details, see [Downloading files in JavaScript apps](https://learn.microsoft.com/en-us/graph/api/driveitem-get-content#downloading-files-in-javascript-apps).
