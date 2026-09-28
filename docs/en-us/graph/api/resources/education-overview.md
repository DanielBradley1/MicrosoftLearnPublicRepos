<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/education-overview?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-01-17 -->

# Working with education APIs in Microsoft Graph

The education APIs in Microsoft Graph enhance Microsoft 365 resources and data with information that is relevant for education scenarios, including schools, students, teachers, classes, and enrollments. This makes it easy for you to build solutions that integrate with educational resources.

The education APIs include rostering resources and assignments resources that you can use to interact with the rostering services in Microsoft Teams. You can use these resources to manage a school roster.

## Authorization

To call the education APIs in Microsoft Graph, your app will need to acquire an access token. For details about access tokens, see [Get access tokens to call Microsoft Graph](https://learn.microsoft.com/en-us/graph/auth/). Your app will also need the appropriate permissions. For more information, see [Education permissions](https://learn.microsoft.com/en-us/graph/permissions-reference#education-permissions).

### App permissions to enable school IT admins to consent

To deploy apps that are integrated with the Education APIs in Microsoft Graph, school IT admins must first grant consent to the permissions requested by the app. This consent has to be granted only once, unless the permissions change. After the admin consents, the app is provisioned for all users in the tenant.

To show a consent dialog box, use the following REST call.

```http
GET https://login.microsoftonline.com/{tenant}/adminconsent?
client_id={clientId}&state=12345&redirect_uri={redirectUrl}
```

| Parameter | Description |
| :--- | :--- |
| Tenant | Tenant ID of the school. Use the full ID, which includes onmicrosoft.com. |
| clientId | Client ID of the app. |
| redirectUrl | App redirect URL. |

## Rostering

The rostering APIs enable you to extract data from a school's Microsoft 365 tenant provisioned with [Microsoft School Data Sync](https://sds.microsoft.com/). These APIs provide access to information about schools, sections, teachers, students, and rosters. The APIs support both app-only \(sync\) scenarios, and app + user \(interactive\) scenarios. The APIs that support interactive scenarios enforce region-appropriate RBAC policies based on the user role calling the API. This provides a consistent API and minimal policy surface, regardless of the administrative configuration within tenants. In addition, the APIs also provide education-specific permissions to ensure that the right user has access to the data.

You can use the rostering APIs to enable an app user to know:

- Who I am
- What classes I attend or teach
- What I need to do and by when

The rostering APIs provide the following key resources:

- [educationSchool](https://learn.microsoft.com/en-us/graph/api/resources/educationschool?view=graph-rest-1.0) - Represents the school.
- [educationClass](https://learn.microsoft.com/en-us/graph/api/resources/educationclass?view=graph-rest-1.0) - Represents a class within a school.
- [educationTerm](https://learn.microsoft.com/en-us/graph/api/resources/educationterm?view=graph-rest-1.0) - Represents a designated portion of the academic year.
- [educationTeacher](https://learn.microsoft.com/en-us/graph/api/resources/educationteacher?view=graph-rest-1.0) - Represents a user with the primary role of 'Teacher'.
- [educationStudent](https://learn.microsoft.com/en-us/graph/api/resources/educationstudent?view=graph-rest-1.0) - Represents a user with the primary role of 'student'.

The rostering APIs support the following scenarios:

- [List all schools](https://learn.microsoft.com/en-us/graph/api/educationschool-list?view=graph-rest-1.0)
- [List schools in which a class is taught](https://learn.microsoft.com/en-us/graph/api/educationclass-list-schools?view=graph-rest-1.0)
- [List schools for a user](https://learn.microsoft.com/en-us/graph/api/educationuser-list-schools?view=graph-rest-1.0)
- [Get all classes](https://learn.microsoft.com/en-us/graph/api/educationclass-list?view=graph-rest-1.0)
- [Get classes in a school](https://learn.microsoft.com/en-us/graph/api/educationschool-list-classes?view=graph-rest-1.0)
- [List classes for a user](https://learn.microsoft.com/en-us/graph/api/educationuser-list-classes?view=graph-rest-1.0)
- [Add classes to a school](https://learn.microsoft.com/en-us/graph/api/educationschool-post-classes?view=graph-rest-1.0)
- [Get students and teachers for a class](https://learn.microsoft.com/en-us/graph/api/educationclass-list-members?view=graph-rest-1.0)
- [Add members to a class](https://learn.microsoft.com/en-us/graph/api/educationclass-post-members?view=graph-rest-1.0)
- [List teachers for a class](https://learn.microsoft.com/en-us/graph/api/educationclass-list-teachers?view=graph-rest-1.0)
- [Get users in a school](https://learn.microsoft.com/en-us/graph/api/educationschool-list-users?view=graph-rest-1.0)

## Assignments

You can use the assignment-related education APIs to integrate with assignments in Microsoft Teams. Microsoft Teams in Microsoft 365 for Education is based on the same education APIs, and provides a use case for what you can do with the APIs. Your app can use these APIs to interact with assignments throughout the assignment lifecycle.

The assignment APIs provide the following key resources:

- [educationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/educationassignment?view=graph-rest-1.0) - The core object of the assignments API. Represents a task or unit of work assigned to a student or team member in a class as part of their study.
- [educationSubmission](https://learn.microsoft.com/en-us/graph/api/resources/educationsubmission?view=graph-rest-1.0) - Represents the resources that an individual \(or group\) submits for an assignment and the associated grade and feedback for that assignment.
- [educationResource](https://learn.microsoft.com/en-us/graph/api/resources/educationresource?view=graph-rest-1.0) - Represents the learning object that is being assigned or submitted. An **educationResource** is associated with an **educationAssignment** and/or an **educationSubmission**.

The assignment APIs support the following scenarios:

- [Create assignment](https://learn.microsoft.com/en-us/graph/api/educationclass-post-assignments?view=graph-rest-1.0)
- [Publish assignment](https://learn.microsoft.com/en-us/graph/api/educationassignment-publish?view=graph-rest-1.0)
- [Create assignment resource](https://learn.microsoft.com/en-us/graph/api/educationassignment-post-resources?view=graph-rest-1.0)
- [Create submission resource](https://learn.microsoft.com/en-us/graph/api/educationsubmission-post-resources?view=graph-rest-1.0)
- [Submit assignment](https://learn.microsoft.com/en-us/graph/api/educationsubmission-submit?view=graph-rest-1.0)
- [Unsubmit assignment](https://learn.microsoft.com/en-us/graph/api/educationsubmission-unsubmit?view=graph-rest-1.0)
- [Return grades and feedback to student](https://learn.microsoft.com/en-us/graph/api/educationsubmission-return?view=graph-rest-1.0)
- [Get assignment details](https://learn.microsoft.com/en-us/graph/api/educationuser-list-assignments?view=graph-rest-1.0)

The following are some common use cases for the assignment-related education APIs.

| Use case | Description | See also |
| :--- | :--- | :--- |
| Create assignments | An external system can create an assignment for the class and attach resources to the assignment. | [Create assignment](https://learn.microsoft.com/en-us/graph/api/educationassignment-post-resources?view=graph-rest-1.0) |
| Read assignment information | An analytics application can get information about assignments and student submissions, including dates and grades. | [Get assignment](https://learn.microsoft.com/en-us/graph/api/educationassignment-get?view=graph-rest-1.0) |
| Track student submissions | Your app can provide a teacher dashboard that shows how many submissions from students need to be graded. | [Submission resource](https://learn.microsoft.com/en-us/graph/api/resources/educationsubmission?view=graph-rest-1.0) |

## Next steps

Use the Microsoft Graph education APIs to build education solutions that access school rosters. To learn more:

- Explore the resources and methods that are most helpful to your scenario.
- Try the API in the [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer).
