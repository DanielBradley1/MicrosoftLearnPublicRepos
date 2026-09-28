<!-- Source: https://learn.microsoft.com/en-us/entra/msal/javascript/angular/logging -->
<!-- Sitemap-Last-Modified: 2025-08-14 -->

# Logging in MSAL Angular

The logger definition has the following properties:

1. correlationId
2. logLevel

   - logLevels include: `Error`, `Warning`, `Info`, `Trace`, and `Verbose`

3. piiLoggingEnabled

You can enable logging in your app as shown below:

```js
import { LogLevel, PublicClientApplication } from '@azure/msal-browser';

export function loggerCallback(logLevel, message) {
    console.log(message);
}

@NgModule({
    imports: [ 
        MsalModule.forRoot(new PublicClientApplication({
            auth: {
                clientId: 'Your client ID',
            },
            system: {
                loggerOptions: {
                    loggerCallback,
                    piiLoggingEnabled: true,
                    logLevel: LogLevel.Info
                }
            }
        }))
    ]
})
```

The `logger` can also be set dynamically by using `MsalService.setLogger()`.

```js
this.authService.setLogger(new Logger({
    loggerCallback: (logLevel, message, piiEnabled) => {
        console.log('MSAL Logging: ', message);
    },
    piiLoggingEnabled: false,
    logLevel: LogLevel.Info
}));
```
