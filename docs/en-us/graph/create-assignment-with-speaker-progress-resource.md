<!-- Source: https://learn.microsoft.com/en-us/graph/create-assignment-with-speaker-progress-resource -->
<!-- Sitemap-Last-Modified: 2025-07-21 -->

# Create an assignment with a Speaker Progress resource

This article describes how to create an assignment with a [Speaker Progress resource](https://learn.microsoft.com/en-us/graph/api/resources/educationspeakerprogressresource).

## Create a new assignment

An assignment represents a task or unit of work assigned to a student or team member in a class as part of their study. You can use the [Create educationAssignment](https://learn.microsoft.com/en-us/graph/api/educationclass-post-assignment) API to create a new assignment for the class.

## Add a Speaker Progress resource

You can use the [Create educationAssignmentResource](https://learn.microsoft.com/en-us/graph/api/educationassignment-post-resources?tabs=http#example-8-create-an-educationspeakerprogressresource) API to create and attach a Speaker Progress resource to an assignment. This operation requires you to provide an [educationSpeakerProgressResource](https://learn.microsoft.com/en-us/graph/api/resources/educationspeakerprogressresource) in the request body.

## Get the Speaker Progress resource

Retrieve the Speaker Progress resource you created by calling the [Get educationAssignmentResource](https://learn.microsoft.com/en-us/graph/api/educationassignmentresource-get) API using the resource ID obtained in the previous step.

To view all resources associated with a specific assignment, use the [List assignment resources](https://learn.microsoft.com/en-us/graph/api/educationassignment-list-resources) API.

## Permissions

The teacher role is required to add a Speaker Progress resource to assignments.
