<!-- Source: https://learn.microsoft.com/en-us/graph/tutorials/powershell-extend-app -->
<!-- Sitemap-Last-Modified: 2025-06-11 -->

# Extend PowerShell scripts with additional Microsoft Graph APIs

In this article you will add your own Microsoft Graph capabilities to the application you created in [Build PowerShell scripts with Microsoft Graph](https://learn.microsoft.com/en-us/graph/tutorials/powershell). For example, you might want to add a code snippet from Microsoft Graph [documentation](https://learn.microsoft.com/en-us/graph/api/overview) or [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer), or code that you created.

## Choose an API

Find an API in Microsoft Graph you'd like to try. For example, the [Create event](https://learn.microsoft.com/en-us/graph/api/user-post-events) API. You can use one of the examples in the API documentation, customize an API request in Graph Explorer and use the generated snippet, or use the `Find-MgGraphCommand` command to find the corresponding command.

For example, one of the API endpoints to create an event is `POST /users/{id | userPrincipalName}/events`. You can use this to find the corresponding PowerShell command.

```powershell
PS > Find-MgGraphCommand -Uri "/users/{id | userPrincipalName}/events" -Method "POST"

   APIVersion: v1.0

Command         Module   Method URI                     OutputType           Permissions           Variants
-------         ------   ------ ---                     ----------           -----------           --------
New-MgUserEvent Calendar POST   /users/{user-id}/events IMicrosoftGraphEvent {Calendars.ReadWrite} {Create1, CreateExp…

   APIVersion: beta

Command         Module   Method URI                     OutputType            Permissions           Variants
-------         ------   ------ ---                     ----------            -----------           --------
New-MgUserEvent Calendar POST   /users/{user-id}/events IMicrosoftGraphEvent1 {Calendars.ReadWrite} {Create, CreateExp…
```

The output indicates that the `New-MgUserEvent` command is the corresponding command.

## Configure permissions

Check the **Permissions** section of the reference documentation for your chosen API to see which authentication methods are supported. Some APIs don't support user \(delegated\) authentication, or personal Microsoft accounts, for example.

Disconnect the current session \(`Disconnect-MgGraph`\) and reconnect with the required permission in the `-Scopes` parameter.

Tip

Using the `-ForceRefresh` parameter with the `Connect-MgGraph` command ensures that newly configured permissions are applied.

## Run the command

Now that you are connected with the required permissions, run your chosen command.

## Related content

Now that you have a working app that calls Microsoft Graph, you can experiment and add new features.

- Learn how to use [app-only authentication](https://learn.microsoft.com/en-us/graph/tutorials/powershell-app-only) with the Microsoft Graph PowerShell SDK.
- Visit the [Overview of Microsoft Graph](https://learn.microsoft.com/en-us/graph/overview) to see all of the data you can access with Microsoft Graph.
