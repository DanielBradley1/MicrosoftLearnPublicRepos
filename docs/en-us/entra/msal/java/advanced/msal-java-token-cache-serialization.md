<!-- Source: https://learn.microsoft.com/en-us/entra/msal/java/advanced/msal-java-token-cache-serialization -->
<!-- Sitemap-Last-Modified: 2024-01-27 -->

# Custom token cache serialization in MSAL for Java

To persist the token cache between instances of your application, you will need to customize the serialization logic. The Java classes and interfaces involved in token cache serialization are the following:

- [ITokenCache](https://learn.microsoft.com/en-us/java/api/com.microsoft.aad.msal4j.itokencache): Interface representing security token cache.
- [ITokenCacheAccessAspect](https://learn.microsoft.com/en-us/java/api/com.microsoft.aad.msal4j.itokencacheaccessaspect) : Interface representing operation of executing code before and after access. You would `@Override` *beforeCacheAccess* and *afterCacheAccess* with the logic responsible for serializing and deserializing the cache.
- [ITokenCacheAccessContext](https://learn.microsoft.com/en-us/java/api/com.microsoft.aad.msal4j.itokencacheaccesscontext) : Interface representing context in which the token cache is accessed.

Below is a naive implementation of custom serialization of the token cache.

Warning

Because the sample code below doesn't showcase the full cache storage lifecycle, we strongly recommend to not copy and paste this into a production environment. Make sure that you're aware of security and access requirements for the token cache.

```java
static class TokenPersistence implements ITokenCacheAccessAspect {
String data;

TokenPersistence(String data) {
        this.data = data;
}

@Override
public void beforeCacheAccess(ITokenCacheAccessContext iTokenCacheAccessContext) {
        iTokenCacheAccessContext.tokenCache().deserialize(data);
}

@Override
public void afterCacheAccess(ITokenCacheAccessContext iTokenCacheAccessContext) {
        data = iTokenCacheAccessContext.tokenCache().serialize();
}
```

```java
// Loads cache from file
String dataToInitCache = readResource(this.getClass(), "/cache_data/serialized_cache.json");

ITokenCacheAccessAspect persistenceAspect = new TokenPersistence(dataToInitCache);

// By setting *TokenPersistence* on the PublicClientApplication, MSAL will call *beforeCacheAccess()* before accessing the cache and *afterCacheAccess()* after accessing the cache. 
PublicClientApplication app = 
PublicClientApplication.builder("my_client_id").setTokenCacheAccessAspect(persistenceAspect).build();
```

## Learn more

Learn about [Get and remove accounts from the token cache using MSAL for Java](https://learn.microsoft.com/en-us/entra/msal/java/advanced/msal-java-get-remove-accounts-token-cache).
