<!-- Source: https://learn.microsoft.com/en-us/entra/msal/android/architect-your-mobile-app -->
<!-- Sitemap-Last-Modified: 2024-02-07 -->

# Architecting your mobile app

## Introduction

Whether you're building a small app for users inside your organization or the next SaaS hit, you'll want to be conscious of how to integrate Identity into your app. This article will focus on the various app architectures available in the Microsoft identity platform, highlighting ease of development, ability to scale, and speed of operations all while maintaining a strong security posture.

Before diving into the technical details, there's some key principles to keep in mind:

- Users expect operations to be quick and convey system status.
- The quality, speed, and coherence of interactions are critical to user engagement in Mobile.
- Operationally speaking, mobile apps are generally accompanied by other clients \(Web apps, Desktop apps\).

## Basics

The Microsoft identity platform is built on open standards including OpenId Connect and OAuth2.0. The architectures discussed will focus on the most commons topologies these protocols support. Each section will walk through the basic layout, procs and cons of each architecture, and the best practices and links to getting started with that layout.

## Architectures

- Standalone Mobile app
- Mobile app + Service
- Mobile app + Serverless

### Architecture 0: Standalone Mobile app

No matter what architecture you ultimately pick, the goal is to build a great mobile app that delivers seamless experiences to your users. The simplest manifestation of this is a standalone mobile app that performs all API requests directly from the user's device.

![standalone](https://user-images.githubusercontent.com/6620414/47383067-a7a90a80-d6b8-11e8-9c00-a47cd81f19db.png)

In this architecture, the code running on the device is responsible for everything including sign in, calling APIs, aggregating and applying meaning to the data, and presenting experiences to the user. This architecture does not exclude using a dedicated service, but focuses on the majority of API calls being executed by the Mobile app.

#### Pros + Cons

##### Pros

- Simple to develop and maintain.
- Reduces the complexity of handling user data.

  - There are data privacy and regulatory implications when data passes through a service.

- Can build trust with users who are privacy conscious.

  - User data never needs to leave the device.
  - User data is more distributed in that it's only being gathered and used on the user's device.

##### Cons

- Significantly more network requests and data over the network.

  - Many user's have limited data plans.
  - Users may be in low-network conditions that make it more difficult to handle large amounts of data being sent to the device.

- Reduces the capability for telemetry and diagnostics of user behavior.
- Reduces the capability to process large amounts of data for insights and personalized expereinces.

  - Your app may want to perform several Microsoft Graph API calls and feed this into a Machine Learning service to provide more personalized experiences. This may be computationally intense for a mobile device.

#### Best Practices

If you've chosen to use MSAL to integrate and build a standalone app architecture, there are very few best practices your app will be missing. MSAL automatically renews refresh tokens, handles most unique Microsoft Entra scenarios \(like Multi-factor Auth, SSO, and Conditional Access\), and caching/managing accounts + tokens.

In addition to what MSAL does automatically, an app may also consider the following practices:

- MSAL + Identity

  - Use MSAL to get an Access Token right before you make an API call.
  - Do not look inside the Access token in your client app, these can change at any time.

    - If you need information about the user, you can perform a request to [Microsoft Graph /me](https://developer.microsoft.com/en-us/graph/docs/api-reference/v1.0/resources/users).

  - Always attempt `acquireTokenSilent(...)` requests before `acquireToken(...)`.

- Network requests

  - Research the API you're requesting data from and handle all error conditions.

    - Most Microsoft APIs support and may throw HTTP 400, 401, 403, and 429.

  - Try to use asynchronous requests where possible.
  - If you know you will need to make an API call, do it in advance to minimize waiting time.
  - For blocking requests, convey the current status through a visual cue.

#### Getting started with a Standalone Mobile app

The [MSAL.Android getting started sample](https://github.com/Azure-Samples/active-directory-android-native-v2) uses a standalone Mobile app architecture.

For more help, feel free to create a [Github issue](https://github.com/AzureAD/microsoft-authentication-library-for-android/issues) or post on [StackOverflow with tag `azure-active-directory`](https://stackoverflow.com/questions/ask).

### Architecture 1.0: Mobile app + Service

Building a mobile app that delivers an amazing user experience at scale will likely want to consider using a Mobile app + Service architecture. This architecture introduces some new challenges, but is a great option for apps trying to deliver cutting-edge experiences that run seamlessly on mobile.

![AppServer](https://user-images.githubusercontent.com/6620414/47393467-6e7e9380-d6d4-11e8-80c0-66bc332f2a78.png)

In this architecture, your Mobile app is responsible for signing in the user and get authorization, but defers API calls and data aggregation to a Service. There are several manifestations of this architecture, we'll focus on using the `On-behalf-of` flow in our service which will make all requests in the context of a user.

#### Pros + Cons

##### Pros

- Easily extensible to other clients you may build \(more platforms, web app, other services\).

  - Forcing function to define shared data model for requests, ensuring some amount of consistency across experiences.

- Minimizes network requests and data passing to your user's device.
- Allows for more computationally intensive operations on data.

  - These operations can be distributed across a micro-service architecture.
  - Opportunity to capture more telemetry on usage patterns and behavior.

- Data access & permission boundaries are not extended - the user gains no new access.

##### Cons

- More difficult to develop and maintain.
- Requires your service to handle and potentially store user data.

  - Introduces potential for regulatory oversight or required features.
  - Some users may prefer for their data to not leave their device.

- May require additional security considerations due to higher risk profile.

  - User data and refresh tokens are in a centralized location.
  - Can be partially mitigated by diligently protecting and deleting data.

#### Best Practices

If you've chosen to use MSAL to integrate and build your Mobile app + Service, there are very few best practices your app will be missing. MSAL automatically renews refresh tokens, handles most unique Microsoft Entra scenarios \(like Multi-factor Auth, SSO, and Conditional Access\), and caching/managing accounts + tokens.

In addition to what MSAL does automatically, an app may also consider the following practices:

- MSAL + Identity \(Native app\)

  - Use MSAL to get an Access Token right before you make an API call.
  - Do not look inside the Access token in your client app, these can change at any time.

    - If you need information about the user, you can perform a request to [Microsoft Graph /me](https://developer.microsoft.com/en-us/graph/docs/api-reference/v1.0/resources/users).

  - Always attempt `acquireTokenSilent(...)` requests before `acquireToken(...)`.

- MSAL + Identity \(Service\)

  - Use MSAL to perform On-behalf-of requests.
  - Do not look inside the Access token intended for downstream APIs, these can change at any time.
  - Do not store user data where possible, if you do:

    - Use industry standard techniques to protect the data.
    - In key-value databases, use the unique identifier `sub` in the incoming token.
    - Research and implement any regulatory or Microsoft terms of use requirements.

  - Always attempt `acquireTokenSilent(...)` requests before `acquireTokenInteractive(...)`.

- Network requests

  - Research the API you're requesting data from and handle all error conditions.

    - Most Microsoft APIs support and may throw HTTP 400, 401, 403, and 429.
    - In your own service:

      - Implement throttling\(HTTP 429\) to protect from denial-of-service attacks and naive clients.
      - Follow the best practices around protecting your api with proper HTTP codes.

  - Try to use asynchronous requests where possible.
  - If you know you will need to make an API call, do it in advance to minimize waiting time.
  - For blocking requests, convey the current status through a visual cue.

- Security

  - In addition to diligently implementing identity into your service, investigate if your app should [strengthen it's security posture with Azure Security Center](https://azure.microsoft.com/blog/strengthen-your-security-posture-and-protect-against-threats-with-azure-security-center/).

#### Getting started with a Mobile app + Service

The [MSAL.Android getting started sample](https://github.com/Azure-Samples/active-directory-android-native-v2) uses a standalone Mobile app architecture but can be easily modified to call your own service.

To do so, you'll need to:

1. Register your service app and expose a set of scopes / permissions.
2. Change this app's code to request those scopes.
3. Begin sending your access tokens to your new service.

For help building a service, checkout the [Node.js Web API Quickstart](https://github.com/Azure-Samples/active-directory-javascript-nodejs-webapi-v2).

For more help, feel free to create a [Github issue](https://github.com/AzureAD/microsoft-authentication-library-for-android/issues) or post on [StackOverflow with tag `azure-active-directory`](https://stackoverflow.com/questions/ask).

### Architecture 2: Mobile app + Serverless

Coming soon. Need it now? Let us know!
