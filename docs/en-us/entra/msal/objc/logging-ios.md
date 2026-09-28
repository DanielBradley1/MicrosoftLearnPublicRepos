<!-- Source: https://learn.microsoft.com/en-us/entra/msal/objc/logging-ios -->
<!-- Sitemap-Last-Modified: 2024-03-19 -->

# Logging in MSAL for iOS/macOS

The Microsoft Authentication Library \(MSAL\) apps generate log messages that can help diagnose issues. An app can configure logging with a few lines of code, and have custom control over the level of detail and whether or not personal and organizational data is logged. We recommend you create an MSAL logging implementation and provide a way for users to submit logs when they have authentication issues.

## Logging levels

MSAL provides several levels of logging detail:

- LogAlways: No level filtering is done on this log level. Log messages of all levels will be logged.
- Critical: Logs that describe an unrecoverable application or system crash, or a catastrophic failure that requires immediate attention.
- Error: Indicates something has gone wrong and an error was generated. Used for debugging and identifying problems.
- Warning: There hasn't necessarily been an error or failure, but are intended for diagnostics and pinpointing problems.
- Informational: MSAL will log events intended for informational purposes not necessarily intended for debugging.
- Verbose \(Default\): MSAL logs the full details of library behavior.

Note

Not all log levels are available for all MSAL SDK's

## Personal and organizational data

By default, the MSAL logger doesn't capture any highly sensitive personal or organizational data. The library provides the option to enable logging personal and organizational data if you decide to do so.

The following sections provide more details about MSAL error logging for your application.

- [Objective-C](#tabpanel_1_objc)
- [Swift](#tabpanel_1_swift)

## MSAL for iOS and macOS logging-ObjC

Set a callback to capture MSAL logging and incorporate it in your own application's logging. The signature for the callback looks like this:

```objc
/*!
    The LogCallback block for the MSAL logger

    @param  level           The level of the log message
    @param  message         The message being logged
    @param  containsPII     If the message might contain Personally Identifiable Information (PII)
                            this will be true. Log messages possibly containing PII will not be
                            sent to the callback unless PIllLoggingEnabled is set to YES on the
                            logger.

 */
typedef void (^MSALLogCallback)(MSALLogLevel level, NSString *message, BOOL containsPII);
```

For example:

```objc
[MSALGlobalConfig.loggerConfig setLogCallback:^(MSALLogLevel level, NSString *message, BOOL containsPII)
    {
        if (!containsPII)
        {
#if DEBUG
            // IMPORTANT: MSAL logs may contain sensitive information. Never output MSAL logs with NSLog, or print, directly unless you're running your application in debug mode. If you're writing MSAL logs to file, you must store the file securely.
            NSLog(@"MSAL log: %@", message);
#endif
        }
    }];
```

### Personal data

By default, MSAL doesn't capture or log any personal data. The library allows app developers to turn this on through a property in the MSALLogger class. By turning on `pii.Enabled`, the app takes responsibility for safely handling highly sensitive data and following regulatory requirements.

```objc
// By default, the `MSALLogger` doesn't capture any PII

// PII will be logged
MSALGlobalConfig.loggerConfig.piiEnabled = YES;

// PII will NOT be logged
MSALGlobalConfig.loggerConfig.piiEnabled = NO;
```

### Logging levels

To set the logging level when you log using MSAL for iOS and macOS, use one of the following values:

| Level | Description |
| --- | --- |
| `MSALLogLevelNothing` | Disable all logging |
| `MSALLogLevelError` | Default level, prints out information only when errors occur |
| `MSALLogLevelWarning` | Warnings |
| `MSALLogLevelInfo` | Library entry points, with parameters and various keychain operations |
| `MSALLogLevelVerbose` | API tracing |

For example:

```objc
MSALGlobalConfig.loggerConfig.logLevel = MSALLogLevelVerbose;
```

### Log message format

The message portion of MSAL log messages is in the format of `TID = <thread_id> MSAL <sdk_ver> <OS> <OS_ver> [timestamp - correlation_id] message`

For example:

`TID = 551563 MSAL 0.2.0 iOS Sim 12.0 [2018-09-24 00:36:38 - 36764181-EF53-4E4E-B3E5-16FE362CFC44] acquireToken returning with error: (MSALErrorDomain, -42400) User cancelled the authorization session.`

Providing correlation IDs and timestamps are helpful for tracking down issues. Timestamp and correlation ID information is available in the log message. The only reliable place to retrieve them is from MSAL logging messages.

## MSAL for iOS and macOS logging-Swift

Set a callback to capture MSAL logging and incorporate it in your own application's logging. The signature \(represented in Objective-C\) for the callback looks like this:

```objc
/*!
    The LogCallback block for the MSAL logger

    @param  level           The level of the log message
    @param  message         The message being logged
    @param  containsPII     If the message might contain Personally Identifiable Information (PII)
                            this will be true. Log messages possibly containing PII will not be
                            sent to the callback unless PIllLoggingEnabled is set to YES on the
                            logger.

 */
typedef void (^MSALLogCallback)(MSALLogLevel level, NSString *message, BOOL containsPII);
```

For example:

```swift
MSALGlobalConfig.loggerConfig.setLogCallback { (level, message, containsPII) in
    if let message = message, !containsPII
    {
#if DEBUG
    // IMPORTANT: MSAL logs may contain sensitive information. Never output MSAL logs with NSLog, or print, directly unless you're running your application in debug mode. If you're writing MSAL logs to file, you must store the file securely.
    print("MSAL log: \(message)")
#endif
    }
}
```

### Personal data

By default, MSAL doesn't capture or log any personal data. The library allows app developers to turn this on through a property in the MSALLogger class. By turning on `pii.Enabled`, the app takes responsibility for safely handling highly sensitive data and following regulatory requirements.

```swift
// By default, the `MSALLogger` doesn't capture any PII

// PII will be logged
MSALGlobalConfig.loggerConfig.piiEnabled = true

// PII will NOT be logged
MSALGlobalConfig.loggerConfig.piiEnabled = false
```

### Logging levels

To set the logging level when you log using MSAL for iOS and macOS, use one of the following values:

| Level | Description |
| --- | --- |
| `MSALLogLevelNothing` | Disable all logging |
| `MSALLogLevelError` | Default level, prints out information only when errors occur |
| `MSALLogLevelWarning` | Warnings |
| `MSALLogLevelInfo` | Library entry points, with parameters and various keychain operations |
| `MSALLogLevelVerbose` | API tracing |

For example:

```swift
MSALGlobalConfig.loggerConfig.logLevel = .verbose
```

### Log message format

The message portion of MSAL log messages is in the format of `TID = <thread_id> MSAL <sdk_ver> <OS> <OS_ver> [timestamp - correlation_id] message`

For example:

`TID = 551563 MSAL 0.2.0 iOS Sim 12.0 [2018-09-24 00:36:38 - 36764181-EF53-4E4E-B3E5-16FE362CFC44] acquireToken returning with error: (MSALErrorDomain, -42400) User cancelled the authorization session.`

Providing correlation IDs and timestamps are helpful for tracking down issues. Timestamp and correlation ID information is available in the log message. The only reliable place to retrieve them is from MSAL logging messages.

## Next steps

For more code samples, refer to [Microsoft identity platform code samples](https://learn.microsoft.com/en-us/entra/identity-platform/sample-v2-code).
