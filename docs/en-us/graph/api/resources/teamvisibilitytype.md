<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamvisibilitytype?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-19 -->

# teamVisibilityType enum type

Describes the visibility of a [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0).

## Members

| Member | Value | Description |
| :--- | :--- | :--- |
| private | 0 | Anyone can see the team but only the owner can add a user to the team. |
| public | 1 | Anyone can join the team. |
| hiddenMembership | 2 | Only the administrators \(global, company, user, and helpdesk\) can view the members of a team.  <br>Owner permissions are required to join a team. |
