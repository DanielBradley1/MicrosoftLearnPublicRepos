<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/viva-learning-api-overview?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-01 -->

# Use the employee learning API to integrate with Viva Learning

Viva Learning is a centralized employee learning hub in Microsoft Teams that lets employees integrate learning and building skills into their work day. In Viva Learning, teams can discover, share, recommend, and learn from content libraries provided by both their organization and partners. They can quickly access assigned or recently completed learning content, and do all of this without leaving Microsoft Teams.

The employee learning API in Microsoft Graph enables apps to make content from a Learning Management System \(LMS\) or learning provider available in Viva Learning. Use the following resources to integrate with Viva Learning:

- [Learning provider](https://learn.microsoft.com/en-us/graph/api/resources/learningprovider?view=graph-rest-1.0) to manage learning providers, including registering and deleting providers.
- [Learning content](https://learn.microsoft.com/en-us/graph/api/resources/learningcontent?view=graph-rest-1.0) to upload and manage learning content metadata from your LMS or learning provider in Viva Learning.
- [Learning course activities](https://learn.microsoft.com/en-us/graph/api/resources/learningcourseactivity?view=graph-rest-1.0) to upload and manage learner course activity records from your LMS or learning provider in Viva Learning.

## How do integrations work?

As administrators, you can integrate your content and learner records \(employee assignments and completed course records\) from your LMS or learning provider with Viva Learning, by using out-of-the-box integrations where Viva Learning can pull content metadata and learning records from your LMS or learning provider. You can also [use the employee learning API](#use-cases-for-the-employee-learning-api-in-microsoft-graph) in Microsoft Graph to push content metadata from your LMS or learning provider into Viva Learning.

When the content metadata, employee assignments, and their completed course records are uploaded to Viva Learning, they appear in Viva Learning in the following locations:

- When the content metadata is synchronized, the content appears on the home page under the **Browse courses** – **Providers** section.
- When the learning course activities are synchronized, assignments, recommendations, and self-learning course records appear on the **My Learning** tab. Based on progression, the status will move from **In Progress** to **Completed**.

The learning course activities for the learners can be discovered outside of Viva Learning via APIs.

## Authorization

With the appropriate delegated or application [employee learning permissions](https://learn.microsoft.com/en-us/graph/permissions-reference#employee-learning-permissions), your app can use the employee learning API to manage learning providers and their content for a learning hub in a tenant. For more information about access tokens, app registration, and delegated and application permissions, see [Authentication and authorization basics](https://learn.microsoft.com/en-us/graph/auth/auth-concepts).

## Use cases for the employee learning API in Microsoft Graph

Use the employee learning APIs to do the following:

- Manage learning providers:

  - [Register a provider with Viva Learning](https://learn.microsoft.com/en-us/graph/api/employeeexperience-post-learningproviders?view=graph-rest-1.0), provide a display name, square logo that is displayed on a learning content card, and a long logo that is displayed in the **Details** page, which is required for the provider content to show up in Viva Learning. The returned registration ID can be used to make the subsequent calls for content ingestion.
  - [Get the details about a provider](https://learn.microsoft.com/en-us/graph/api/learningprovider-get?view=graph-rest-1.0) in Viva Learning for a specific **registrationId**.
  - [Get the list of provider registrations](https://learn.microsoft.com/en-us/graph/api/employeeexperience-list-learningproviders?view=graph-rest-1.0) in Viva Learning for a tenant.
  - [Delete a registration](https://learn.microsoft.com/en-us/graph/api/employeeexperience-delete-learningproviders?view=graph-rest-1.0) of a provider in Viva Learning.

- Create and manage learning content:

  - [Push content metadata](https://learn.microsoft.com/en-us/graph/api/learningcontent-update?view=graph-rest-1.0) to Viva Learning to make content available within Viva Learning for consumption by users.
  - [Get a list of the metadata of a provider's ingested content](https://learn.microsoft.com/en-us/graph/api/learningprovider-list-learningcontents?view=graph-rest-1.0) by using the **registrationId** of a provider.
  - [Get the specified metadata of a provider's ingested content](https://learn.microsoft.com/en-us/graph/api/learningcontent-get?view=graph-rest-1.0) in Viva Learning.
  - [Delete the specfied metadata of a provider's ingested content](https://learn.microsoft.com/en-us/graph/api/learningprovider-delete-learningcontents?view=graph-rest-1.0).

- Create and manage learning course activity:

  - [Get the list of the courses for a user](https://learn.microsoft.com/en-us/graph/api/learningcourseactivity-list?view=graph-rest-1.0)
  - [Create a new learning course activity](https://learn.microsoft.com/en-us/graph/api/employeeexperienceuser-post-learningcourseactivities?view=graph-rest-1.0) in Viva Learning.
  - [Get details of learning course activity](https://learn.microsoft.com/en-us/graph/api/learningcourseactivity-get?view=graph-rest-1.0) by using **learningCourseActivityId**.
  - [Update details of learning course activity](https://learn.microsoft.com/en-us/graph/api/learningcourseactivity-update?view=graph-rest-1.0) by using **learningCourseActivityId**.
  - [Delete learning course activity](https://learn.microsoft.com/en-us/graph/api/learningcourseactivity-delete?view=graph-rest-1.0)

## Next steps

- [Enable employee learning using the collaborative capabilities in Teams](https://learn.microsoft.com/en-us/graph/teams-concept-overview#enable-employee-learning-using-the-collaborative-capabilities-in-teams).
- Try the employee learning API in the [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer).
