<!-- Source: https://learn.microsoft.com/en-us/entra/identity-platform/how-to-native-authentication-single-page-app-javascript-sdk-set-up-local-cors -->
<!-- Sitemap-Last-Modified: 2025-08-08 -->

# Set up CORS proxy server to manage CORS headers for native authentication JavaScript SDK

**Applies to**: ![Green circle with a white check mark symbol that indicates the following content applies to external tenants.](https://learn.microsoft.com/en-us/entra/external-id/media/common/applies-to-yes.png) External tenants \([learn more](https://learn.microsoft.com/en-us/entra/external-id/tenant-configurations)\)

In this guide, you learn how to set up a local CORS proxy server to manage CORS headers while interacting with native authentication API from your single-page app \(SPA\). The CORS proxy server is a solution to the native authentication API's inability to support [Cross-Origin Resource Sharing \(CORS\)](https://developer.mozilla.org/docs/Web/HTTP/CORS).

You can use the CORS server you set up in this article for local app development. Alternatively:

- You can [set up a reverse proxy server to manage CORS headers by using Azure Function App](https://learn.microsoft.com/en-us/entra/identity-platform/how-to-native-authentication-cors-solution-test-environment) for a test environment.
- In a production environment, you can [use Azure Front Door as a reverse proxy](https://learn.microsoft.com/en-us/entra/identity-platform/how-to-native-authentication-cors-solution-production-environment).

## Create the CORS proxy server

1. In the root folder of your SPA, create a file called *cors.js*, then add the following code:

   ```javascript
   const http = require("http");
   const https = require("https");
   const url = require("url");
   const proxyConfig = require("./proxy.config");

   const extraHeaders = [
       "x-client-SKU",
       "x-client-VER",
       "x-client-OS",
       "x-client-CPU",
       "x-client-current-telemetry",
       "x-client-last-telemetry",
       "client-request-id",
   ];
   http.createServer((req, res) => {
       const reqUrl = url.parse(req.url);
       const domain = url.parse(proxyConfig.proxy).hostname;

       // Set CORS headers for all responses including OPTIONS
       const corsHeaders = {
           "Access-Control-Allow-Origin": "*",
           "Access-Control-Allow-Methods": "GET, POST, PUT, DELETE, OPTIONS",
           "Access-Control-Allow-Headers": "Content-Type, Authorization, " + extraHeaders.join(", "),
           "Access-Control-Allow-Credentials": "true",
           "Access-Control-Max-Age": "86400", // 24 hours
       };

       // Handle preflight OPTIONS request
       if (req.method === "OPTIONS") {
           res.writeHead(204, corsHeaders);
           res.end();
           return;
       }

       if (reqUrl.pathname.startsWith(proxyConfig.localApiPath)) {
           const targetUrl = proxyConfig.proxy + reqUrl.pathname?.replace(proxyConfig.localApiPath, "") + (reqUrl.search || "");

           console.log("Incoming request -> " + req.url + " ===> " + reqUrl.pathname);

           const newHeaders = {};
           for (let [key, value] of Object.entries(req.headers)) {
               if (key !== 'origin') {
                   newHeaders[key] = value;
               }
           }

           const proxyReq = https.request(
               targetUrl,
               {
                   method: req.method,
                   headers: {
                       ...newHeaders,
                       host: domain,
                   },
               },
               (proxyRes) => {
                   res.writeHead(proxyRes.statusCode, {
                       ...proxyRes.headers,
                       ...corsHeaders,
                   });

                   proxyRes.pipe(res);
               }
           );

           proxyReq.on("error", (err) => {
               console.error("Error with the proxy request:", err);
               res.writeHead(500, { "Content-Type": "text/plain" });
               res.end("Proxy error.");
           });

           req.pipe(proxyReq);
       } else {
           res.writeHead(404, { "Content-Type": "text/plain" });
           res.end("Not Found");
       }
   }).listen(proxyConfig.port, () => {
       console.log("CORS proxy running on http://localhost:3001");
       console.log("Proxying from " + proxyConfig.localApiPath + " ===> " + proxyConfig.proxy);
   });
   ```

2. In the root folder of your SPA, create a file called *proxy.config.js*, then add the following code:

   ```javascript
   const tenantSubdomain = "Enter_the_Tenant_Subdomain_Here";
   const tenantId = "Enter_the_Tenant_Id_Here";

   const config = {
       localApiPath: "/api",
       port: 3001,
       proxy: `https://${tenantSubdomain}.ciamlogin.com/${tenantId}`,
   };
   module.exports = config;
   ```


   - Find the placeholder `Enter_the_Tenant_Subdomain_Here` and replace it with the Directory \(tenant\) subdomain. For example, if your tenant primary domain is `contoso.onmicrosoft.com`, use `contoso`. If you don't have your tenant subdomain, learn how to [read your tenant details](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-create-external-tenant-portal#get-the-external-tenant-details).
   - `tenantId` and replace it with the Directory \(tenant\) ID. If you don't have your tenant ID, learn how to [read your tenant details](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-create-external-tenant-portal#get-the-external-tenant-details).

3. Open *package.json* file of your SPA, then add the following command in the *scripts* object:

   ```json
   "cors": "node cors.js",
   ```

At this point, the CORS proxy server is ready to run.

## Run the CORS server

To start the CORS proxy server, run the following command in your terminal:

```console
npm run cors
```

## Related content

- [Tutorial: Sign in users into a React single-page app app by using native authentication](https://learn.microsoft.com/en-us/entra/identity-platform/tutorial-native-authentication-single-page-app-react-sign-in).
- [Tutorial: Reset password in a React single-page app app by using native authentication](https://learn.microsoft.com/en-us/entra/identity-platform/tutorial-native-authentication-single-page-app-react-reset-password).
