<!-- Source: https://learn.microsoft.com/en-us/graph/tutorials/java-app-only-extend-app -->
<!-- Sitemap-Last-Modified: 2025-06-11 -->

# Extend Java apps that use app-only authentication with more Microsoft Graph APIs

In this article, you add your own Microsoft Graph capabilities to the application you created in [Build Java apps with Microsoft Graph and app-only authentication](https://learn.microsoft.com/en-us/graph/tutorials/java-app-only). For example, you might want to add a code snippet from Microsoft Graph [documentation](https://learn.microsoft.com/en-us/graph/api/overview) or [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer), or code that you created.

## Update the app

1. Open **Graph.java** and add the following function to the `Graph` class.

   ```java
   public static void makeGraphCall() {
       // INSERT YOUR CODE HERE
   }
   ```

2. Replace the empty `MakeGraphCallAsync` function in **App.java** with the following.

   ```java
   private static void makeGraphCall() {
       try {
           Graph.makeGraphCall();
       } catch (Exception e) {
           System.out.println("Error making Graph call");
           System.out.println(e.getMessage());
       }
   }
   ```

## Choose an API

Find an API in Microsoft Graph you'd like to try. For example, the [Create event](https://learn.microsoft.com/en-us/graph/api/user-post-events) API. You can use one of the examples in the API documentation, or you can customize an API request in Graph Explorer and use the generated snippet.

## Configure permissions

Check the **Permissions** section of the reference documentation for your chosen API to see which authentication methods are supported. Some APIs don't support app-only, or personal Microsoft accounts, for example.

- To call an API with user authentication \(if the API supports user \(delegated\) authentication\), see the [user \(delegated\) authentication](https://learn.microsoft.com/en-us/graph/tutorials/java) tutorial.
- To call an API with app-only authentication \(if the API supports it\), add the required permission scope in the Microsoft Entra admin center.

## Add your code

Copy your code into the `makeGraphCallAsync` function in **Graph.java**. If you're copying a snippet from documentation or Graph Explorer, be sure to rename the `GraphServiceClient` to `_appClient`.

## Related content

Now that you have a working app that calls Microsoft Graph, you can experiment and add new features.

- Learn how to use [user \(delegated\) authentication](https://learn.microsoft.com/en-us/graph/tutorials/java) with the Microsoft Graph Java SDK.
- Visit the [Overview of Microsoft Graph](https://learn.microsoft.com/en-us/graph/overview) to see all of the data you can access with Microsoft Graph.

### Java samples

- [Android app](https://github.com/microsoftgraph/msgraph-training-android)
- [Change notifications](https://github.com/microsoftgraph/java-spring-webhooks-sample)
