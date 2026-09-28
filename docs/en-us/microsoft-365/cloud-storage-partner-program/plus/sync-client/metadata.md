<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/sync-client/metadata -->
<!-- Sitemap-Last-Modified: 2022-07-06 -->

# How Office gets metadata from third-party sync engines

This article describes how Microsoft Office gets metadata from third-party sync engines.

## Windows metadata

In Windows, Office uses `IStorageProviderHandler` over COM to retrieve properties from the third-party sync engine. For more information, see [storageprovider.h header - Win32 apps](https://learn.microsoft.com/en-us/windows/win32/api/storageprovider/) in the Windows documentation. As we learned from first-party integration, using `StorageFile` directly can be slow in edge cases. To minimize performance impact and avoid the need to hard-code third-party CLSID GUIDs in Office code, the third-party provider needs to write COM information we can retrieve in a shared registry location. Third-party sync engine providers should write their unique CLSID and hash algorithm in this registry location:

```
Computer\HKEY_CURRENT_USER\SOFTWARE\SyncEngines\Providers\<Third-party sync engine>
       Handler -> REG_SZ
       HashAlgorithm -> REG_SZ
```

They should write their local path root folder, Web Application Open Platform Interface \(WOPI\) Service ID \(assigned by Microsoft\), and WOPI User ID in this location:

```
Computer\HKEY_CURRENT_USER\SOFTWARE\SyncEngines\Providers\<Third-party sync engine>\<Sub engine>
       MountPoint -> REG_SZ
       WOPIServiceId -> REG_SZ
       WOPIUserId -> REG_SZ
```

The `<Sub engine>` path allows third-party providers to register more than one provider, if applicable. Third-party sync engines that have several service locations that sync data can list them all here. Office will parse the registry folder structure to find the right provider to CoCreate based on `MountPoint`, just as we do for OneDrive integration in the same registry location. For example, OneDrive registers several business folders uniquely identified by a GUID and one labeled "Personal."

When resolving a local file as connected with a cloud file URL, early in the Office open stack, Office checks if the path of the local file passed in subsumes the path under the third-party mountpoint, after it iterates through all registered mountpoints. If it does, Office will CoCreate an `IStorageProviderHandler` instance, using the CLSID listed under `Handler`, by using `CoCreateInstance(<Handler CLSID>, NULL, CLSCTX_ALL)`. After the instance is CoCreated, Office calls `GetPropertyHandlerFromPath` with the local file path to retrieve an `IStorageProviderPropertyHandler` object. By using this object, Office calls `RetrieveProperties`, looking for two properties:

```
// Name: System.StorageProviderFileRemoteUri -- PKEY_StorageProviderFileRemoteUri
// Type: String -- VT_LPWSTR (For variants: VT_BSTR)
// FormatID: {FCEFF153-E839-4CF3-A9E7-EA22832094B8}, 112
//
// The storage provider's remote URI for this file.
DEFINE_PROPERTYKEY(PKEY_StorageProviderFileRemoteUri, 0xFCEFF153, 0xE839, 0x4CF3, 0xA9, 0xE7, 0xEA, 0x22, 0x83, 0x20, 0x94, 0xB8, 112);
#define INIT_PKEY_StorageProviderFileRemoteUri { { 0xFCEFF153, 0xE839, 0x4CF3, 0xA9, 0xE7, 0xEA, 0x22, 0x83, 0x20, 0x94, 0xB8 }, 112 }

// Name: System.StorageProviderFileChecksum -- PKEY_StorageProviderFileChecksum
// Type: Buffer -- VT_VECTOR | VT_UI1 (For variants: VT_ARRAY | VT_UI1)
// FormatID: {B2F9B9D6-FEC4-4DD5-94D7-8957488C807B}, 5
//
// The checksum computed by the storage provider for the file. Files with the same checksum value will have the same contents.
DEFINE_PROPERTYKEY(PKEY_StorageProviderFileChecksum, 0xB2F9B9D6, 0xFEC4, 0x4DD5, 0x94, 0xD7, 0x89, 0x57, 0x48, 0x8C, 0x80, 0x7B, 5);
#define INIT_PKEY_StorageProviderFileChecksum { { 0xB2F9B9D6, 0xFEC4, 0x4DD5, 0x94, 0xD7, 0x89, 0x57, 0x48, 0x8C, 0x80, 0x7B }, 5 }

// Name: System.StorageProviderFileFlags -- PKEY_StorageProviderFileFlags
// Type: UInt32 -- VT_UI4
// FormatID: {B2F9B9D6-FEC4-4DD5-94D7-8957488C807B}, 8
//
// Information specified by the storage provider about a file or a folder.
DEFINE_PROPERTYKEY(PKEY_StorageProviderFileFlags, 0xB2F9B9D6, 0xFEC4, 0x4DD5, 0x94, 0xD7, 0x89, 0x57, 0x48, 0x8C, 0x80, 0x7B, 8);
#define INIT_PKEY_StorageProviderFileFlags { { 0xB2F9B9D6, 0xFEC4, 0x4DD5, 0x94, 0xD7, 0x89, 0x57, 0x48, 0x8C, 0x80, 0x7B }, 8 }

// Name: System.StorageProviderSyncClientId -- PKEY_StorageProviderSyncClientId
// Type: String -- VT_LPWSTR (For variants: VT_BSTR)
// FormatID:  {0142C8EA-B555-4562-BC82-4466E3D415FF}, 1
//
// The storage provider's SyncClientId, an optional property, uniquely identifies  an installed sync client per user per machine.
DEFINE_PROPERTYKEY(PKEY_StorageProviderSyncClientId, 0x142c8ea, 0xb555, 0x4562, 0xbc, 0x82, 0x44, 0x66, 0xe3, 0xd4, 0x15, 0xff, 1);
#define INIT_PKEY_StorageProviderSyncClientId { { 0x142c8ea, 0xb555, 0x4562, 0xbc, 0x82, 0x44, 0x66, 0xe3, 0xd4, 0x15, 0xff }, 1 }

// Name: System.StorageProviderSessionId -- PKEY_StorageProviderSessionId
// Type: String -- VT_LPWSTR (For variants: VT_BSTR)
// FormatID:   {57C1C5FF-C98B-436D-A284-E48FE6628276}, 1
//
// The storage provider's SessionId, an optional property, uniquely identifies a communication session with Office client.
DEFINE_PROPERTYKEY(PKEY_StorageProviderSessionId , 0x57c1c5ff, 0xc98b, 0x436d, 0xa2, 0x84, 0xe4, 0x8f, 0xe6, 0x62, 0x82, 0x76, 1);
#define INIT_PKEY_StorageProviderSessionId  { { 0x57c1c5ff, 0xc98b, 0x436d, 0xa2, 0x84, 0xe4, 0x8f, 0xe6, 0x62, 0x82, 0x76 }, 1 }
```

In the `PROPVARIANT` from `StorageProviderFileRemoteUri`, we expect a string with the unique `WopiUrl` for a file. This `PROPVARIANT` is defined by Windows, but the third-party provider holds that information and will respond to the COM call.

In the `PROPVARIANT` from `StorageProviderFileChecksum`, we expect a string value for the last known hash of the file on the service. In other words, the hash of the file when it was last in sync with the service. `HashAlgorithm` in the sync engine provider's registry allows the third-party provider to specify the hash algorithm to use from one of the algorithms defined in [CNG algorithm identifiers \(Bcrypt.h\) - Win32 apps](https://learn.microsoft.com/en-us/windows/win32/seccng/cng-algorithm-identifiers) in the Windows documentation. For example, SHA1 or SHA512 for convenience, if the provider already hashes the files a certain way for its own sync needs. If the value isn't valid, Office defaults to SHA512. This `PROPVARIANT` is defined by Windows, but the third-party provider holds that information and will respond to the COM call.

The Office client uses the `StorageProviderFileChecksum` property to determine if the file is dirty. If the file is dirty, Office doesn't open the file from the service because doing so would create conflicts that the sync engine wouldn't be able to resolve without forking the file. Instead, Office opens the file local-only like any other file that's not in a sync engine location. To determine if the file is dirty, Office will hash the contents of the file on disk and compare it against the hash retrieved from the sync engine. This process creates a perceivable performance impact, depending on file size and the hash algorithm used.

The Office client uses the `StorageProviderWOPIServiceId` and `StorageProviderWOPIUserId` properties internally to retrieve any previously stored authentication info for the file to authenticate with the WOPI service.

`StorageProviderFileFlags` is a bit-flag field used by the sync client to inform the Office client whether the file supports coauthoring. If `0x1` is set, coauthoring is supported. Otherwise, it isn't. If the file supports coauthoring, it will be opened with coauthoring extensions. If not, the Office client will open the file locally without coauthoring.

`StorageProviderSyncClientId` and `StorageProviderSessionId` are custom properties. They are not defined by Windows. Therefore, third-party sync client providers must hard-code these properties using the same GUID and property identifier listed in the FormatID for these properties. The Office client uses the `StorageProviderSyncClientId` and `StorageProviderSessionId` properties to associate with the integration debugging information. No customer or service Personal Identifiable Information should be present in these properties. When troubleshooting integration issues, third-party sync client providers can use the `StorageProviderSyncClientId` and `StorageProviderSessionId` to correlate with the providers' side of debugging data.

To support this flow, the third-party sync engine must implement the *StorageHandler* APIs.

Resolving a local file as connected with a cloud file URL starting from the URL isn't supported for this scenario. This will result in a server-only open regardless of the dirty-file status.

## Mac metadata

macOS has security features that prohibit inter-process communication calls between apps that aren't located in the same publisher's AppGroup. But Apple has FileProvider APIs designed for sync-provider scenarios like this one. By using these APIs, we can communicate cross process with third-party apps.

The APIs let us connect to custom-defined "services" for a given a local file path that belongs to a third-party sync engine. This means third-party partners can implement protocols defined by Office to retrieve the additional information needed to support real-time coauthoring. This technology is similar to COM on Windows. The Apple APIs are available in macOS 10.13 \(High Sierra\) or later.

As on Windows, using XPC can have performance implications. We must first determine that we really need to use XPC before invoking a performance-intensive API. As with the MountPoint registry shortcut we use in Windows, Office must first determine, early in the file-open flow, if the given file path is backed by a sync engine. Third-party sync engines must register their domains with the OS as part of using Apple's FileManager APIs for sync. After successful registration, a call made to `NSURLIsUbiquitousItemKey` returns true if the third party's registered domain is a subpath of the local file path.

For more information, see [NSURLIsUbiquitousItemKey](https://developer.apple.com/documentation/foundation/nsurlisubiquitousitemkey). Although Apple's documentation implies that this API is applicable only to iCloud files, that's no longer the case. The same property now supports third-party synced files.

Here's the declaration for `NSURLIsUbiquitousItemKey`:

`const NSURLResourceKey NSURLIsUbiquitousItemKey;`

After Office determines that a file is "ubiquitous," we look for available services that are supported by the file. If our required service name is in the list of services returned by `getFileProviderServicesForItemAtURL`, we can start the XPC connection with the third-party sync engine.

Office defines a new service named `com.microsoft.office.CoauthoringService.v1`. It will be published in a header file and shared with third-party partners to consume:

```
- (void)getFileProviderServicesForItemAtURL:(NSURL *)url
                          completionHandler:(void 
(^)(NSDictionary<NSFileProviderServiceName,NSFileProviderService *> *services, NSError *error))completionHandler;
```

For more information, see [getFileProviderServicesForItemAtURL:completionHandler:](https://developer.apple.com/documentation/foundation/nsfilemanager/2915262-getfileproviderservicesforitemat) in the Apple developer documentation.

On the Office call to `getFileProviderServicesForItemAtURL`, the OS determines that the item belongs to a File Provider. It internally calls `supportedServiceSourcesForItemIdentifier`. The third-party partner must implement `supportedServiceSourcesForItemIdentifier` to return the preceding service in the list of available services:

```
- (NSArray<id<NSFileProviderServiceSource>> 
*)supportedServiceSourcesForItemIdentifier:(NSFileProviderItemIdentifier)itemIdentifier
```

For more information, see [supportedServiceSourcesForItemIdentifier:error:](https://developer.apple.com/documentation/fileprovider/nsfileproviderextension/2915878-supportedservicesourcesforitemid) in the Apple developer documentation.

After Office iterates through available services and finds the new service, Office initializes a `NSFileProviderService` with the name, and then calls `getFileProviderConnectionWithCompletionHandler` to initialize a `NSXPCConnection`. When those initializations succeed, Office sets the `remoteObjectInterface` to the Office-defined protocol \(`OfficeCoauthoringService`\) shared with third-party partners in the header file mentioned previously.

```
+ (NSXPCInterface *)interfaceWithProtocol:(Protocol *)protocol
```

For more information, see [interfaceWithProtocol:](https://developer.apple.com/documentation/foundation/nsxpcinterface/1410202-interfacewithprotocol) in the Apple developer documentation.

The Office-defined XPC protocol allows us to retrieve the five properties we need for a given file in one call. All XPC protocol calls are asynchronous, so all functions must be void. To receive a response, we need a reply/completion block that we can wait for. Although these calls are asynchronous by nature, Office must synchronously wait for their completion in the critical file-open flow of third-party synced files.

To allow flexibility in the third party's implementation of the XPC service, we again pass in the local path with which we initialized the XPC connection as part of `retrievePropertiesAtItem`. Doing so lets the implementation of the protocol be a single instance for all files instead of one per file, if the third-party provider prefers it for simplicity and performance.

Here's the Office header file to be shared with and implemented by third-party partners:

```
/*
OfficeCoauthoringService.h
Header for XPC between Microsoft Office and third-party sync engines
*/

#import <Foundation/Foundation.h>

#define OfficeCoauthoringServiceName "com.microsoft.office.CoauthoringService.v1"

#define wopiSrcProperty "wopiSrc" // expects NSString
#define wopiUserIdProperty "wopiUserId" // expects NSString
#define wopiServiceIdProperty "wopiServiceId" // expects NSString
#define hashProperty "hash" // expects NSData
#define hashAlgorithmProperty "hashAlgorithm" // expects NSString
#define supportsCoauthAlgorithmProperty "supportsCoauth" // expects NSData
#define synClientIdProperty "syncClientId" // expects NSString
#define sessionIdProperty "sessionId" // expects NSString

@protocol OfficeCoauthoringService

- (void)retrievePropertiesAtItem: (NSURL*)localPath

reply : (void(^)(NSDictionary * result)) reply;

@end
```

Third-party partners that want to support coauthoring must import and implement the `OfficeCoauthoringService` protocol. They must return an `NSDictionary` that contains all five of the required properties in the reply after Office requests those properties during the file-open flow. After Office receives the response, there's no further interaction between Office and third-party sync engines for the rest of the file session.

If any of the required properties aren't present in the response, Office will open the file local-only by using just the local path. If all required properties are present, Office will compute the hash of the file content on disk and compare it to the `FileChecksum` property.

The sync engine is expected to update the `FileChecksum` after every change from the service is written to the local disk. An update is also expected after changes from disk are successfully uploaded to the service. This means Office will treat `Hash of the local file != FileChecksum` as dirty and `Hash of the local file == FileChecksum` as not dirty. It will continue with a shared implementation with Windows. Dirty files will open local-only by using just the local path, and non-dirty files will open without requiring a network round trip with the URL and coauthoring support.

The Office apps internally use `WOPIServiceId` and `WOPIUserId` properties to find authentication info for the WOPI service.

The sync client uses `SupportsCoauth` to notify the Office client whether the file supports coauthoring. If it supports coauthoring, the Office client will open the file and coauthoring will take place. If not, the Office client will open the file locally with no coauthoring.

The Office client uses the `SyncClientId` and `SessionId` properties to associate with the integration debugging information. No customer or service Personal Identifiable Information should be present in these properties. When troubleshooting integration issues, third-party sync client providers can use the `SyncClientId` and `SessionId` to correlate with the providers' side of debugging data.

## Next steps

- Learn how Office gets [data](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/sync-client/data) from third-party sync engines.
- Learn how sync client integration works in key [scenarios and edge cases](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/sync-client/scenarios-edge-cases).
