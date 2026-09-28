<!-- Source: https://learn.microsoft.com/en-us/graph/tutorials/php-extend-app -->
<!-- Sitemap-Last-Modified: 2025-06-11 -->

# Extend PHP apps with more Microsoft Graph APIs

In this article, you add your own Microsoft Graph capabilities to the application you created in [Build PHP apps with Microsoft Graph](https://learn.microsoft.com/en-us/graph/tutorials/php). For example, you might want to add a code snippet from Microsoft Graph [documentation](https://learn.microsoft.com/en-us/graph/api/overview) or [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer), or code that you created. This section is optional.

## Update the app

1. Add the following code to the `GraphHelper` class.

   ```php
   public static function makeGraphCall(): void {
       // INSERT YOUR CODE HERE
   }
   ```

2. Replace the empty `makeGraphCall` function in **main.php** with the following.

   ```php
   function makeGraphCall(): void {
       try {
           GraphHelper::makeGraphCall();
       } catch (Exception $e) {
           print(PHP_EOL.'Error making Graph call'.PHP_EOL.PHP_EOL);
       }
   }
   ```

## Choose an API

Find an API in Microsoft Graph you'd like to try. For example, the [Create event](https://learn.microsoft.com/en-us/graph/api/user-post-events) API. You can use one of the examples in the API documentation, or create your own API request.

## Configure permissions

Check the **Permissions** section of the reference documentation for your chosen API to see which authentication methods are supported. Some APIs don't support app-only, or personal Microsoft accounts, for example.

- To call an API with user authentication \(if the API supports user \(delegated\) authentication\), add the required permission scope in **.env**.
- To call an API with app-only authentication, see the [app-only authentication](https://learn.microsoft.com/en-us/graph/tutorials/php-app-only) tutorial.

## Add your code

Add your code into the `makeGraphCall` function in **GraphHelper.php**.

## Related content

Now that you have a working app that calls Microsoft Graph, you can experiment and add new features.

- Learn how to use [app-only authentication](https://learn.microsoft.com/en-us/graph/tutorials/php-app-only) with the Microsoft Graph PHP SDK.
- Visit the [Overview of Microsoft Graph](https://learn.microsoft.com/en-us/graph/overview) to see all of the data you can access with Microsoft Graph.

### PHP Samples

- [Laravel web app](https://github.com/microsoftgraph/msgraph-training-phpapp)
