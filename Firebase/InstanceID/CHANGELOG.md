# 2019-06-18 -- 4.2.0
- Added macOS support for InstanceID (#2880)
- Corrected timezone proto key (#3132)

# 2019-06-04 -- 4.1.1
- Fixed a crash in token fetching. Removed debug assertion that is only for develop build. (#3018)

# 2019-05-21 -- 4.1.0
- Fixed a race condition where checkin was deleted before writing during app start, causing notifications to not be delivered correctly. (#2438)
- Fixed a keychain migration crash. (#2731)
- Remove reflection call to get checkin info from Firebase Messaging. (#2825)

# 2019-05-07 -- 4.0.0
- Remove deprecated `token` method. Use `instanceIDWithHandler:` instead. (#2741)
- Send `firebaseUserAgent` with a register request (#2679)

# 2019-04-02 -- v3.8.1
- Fixed handling the multiple calls of instanceIDWithHandler. (#2445)
- Fixed a race condition where token kept getting refreshed at app start. (#2438)

# 2019-03-19 -- v3.8.0
- Adding community support for tvOS. (#2428)
- Adding Firebase info to checkin. (#2509)
- Fixed a crash in FIRInstanceIDCheckinService. (#2548)

# 2019-03-05 -- v3.7.0
- Open source Firebase InstanceID. (#186)

# 2019-02-20 -- v3.5.0
- Always update keychain access control when adding new keychain to ensure it won't be blocked when device is locked. (#1399)

# 2019-01-22 -- v3.4.0
- Move all keychain write operations off the main thread. (#1399)
- Make keychain operations asynchronous where possible (given the current APIs)
- Avoid redundant keychain operations when it's been queried and cached before.

# 2018-10-25 -- v3.3.0
- Fixed a crash caused by keychain operation when accessing default access group. (#1399, #1393)
- Remove internal APIs that are no longer used.

# 2018-09-25 -- v3.2.2
- Fixed a crash caused by NSUserDefaults being called on background thread.

# 2018-08-14 -- v3.2.1
- Fixed an issue that checkin is not cached properly when app first started. (#1561)

# 2018-07-31 -- v3.2.0
- Added support for global Firebase data collection flag. (#1219)
- Improved message tracking sent by server API.
- Fixed an issue that InstanceID doesn't compile in app extensions, allowing its
dependents like remote config to be working inside the app extensions.

# 2018-06-19 -- v3.1.1
- Ensure the checkin and tokens are refreshed if firebase project changed.
- Fixed an issue that checkin should be turned off when FCM's autoInitEnabled flag is off.

# 2018-06-12 -- v3.1.0
- Added a new API to fetch InstanceID and Token with a completion handler. The completion handler returns a FIRInstanceIDResult with a instanceID and a token properties.
- Deprecated the token method.
- Added support to log a new customized label provided by developer.

# 2018-05-08 -- v3.0.0
- Removed deprecated method `setAPNSToken:type` defined in FIRInstanceID, please use `setAPNSToken:type` defined in FIRMessaging instead.
- Removed deprecated enum `FIRInstanceIDAPNSTokenType` defined in FIRInstanceID, please use `FIRMessagingAPNSTokenType` defined in FIRMessaging instead.
- Fixed an issue that FCM scheduled messages were not tracked successfully.

# 2018-03-06 -- v2.0.10
- Improved documentation on InstanceID usage for GDPR.
- Improved the keypair handling during GCM to FCM migration. If you are migrating from GCM to FCM, we encourage you to update to this version and above.

# 2018-02-06 -- v2.0.9
- Improved support for language targeting for FCM service. Server updates happen more efficiently when language changes.
- Improved support for FCM token auto generation enable/disable functions.

# 2017-12-11 -- v2.0.8
- Fixed a crash caused by a reflection call during logging.
- Updating server with the latest parameters and deprecating old ones.

# 2017-11-27 -- v2.0.7
- Improve identity reset process, ensuring all information is reset during Identity deletion.

# 2017-11-06 -- v2.0.6
- Make token refresh weekly.
- Fixed a crash when performing token operation.

# 2017-10-11 -- v2.0.5
- Improved support for working in shared Keychain environments.

# 2017-09-26 -- v2.0.4
- Fixed an issue where the FCM token was not associating correctly with an APNs
  device token, depending on when the APNs device token was made available.
- Fixed an issue where FCM tokens for different Sender IDs were not associating
  correctly with an APNs device token.
- Fixed an issue that was preventing the FCM direct channel from being
  established on the first start after 24 hours of being opened.

# 2017-09-13 -- v2.0.3
- Fixed a race condition where a token was not being generated on first start,
  if Firebase Messaging was included and the app did not register for remote
  notifications.

# 2017-08-25 -- v2.0.2
- Fixed a startup performance regression, removing a call which was blocking the
  main thread.

# 2017-08-07 -- v2.0.1
- Fixed issues with token and app identifier being inaccessible when the device
  is locked.
- Fixed a crash if bundle identifier is nil, which is possible in some testing
  environments.
- Fixed a small memory leak fetching a new token.
- Moved to a new and simplified token storage system.
- Moved to a new queuing system for token fetches and deletes.
- Simplified logic and code around configuration and logging.
- Added clarification about the 'apns_sandbox' parameter, in header comments.

# 2017-05-08 -- v2.0.0
- Introduced an improved interface for Swift 3 developers
- Deprecated some methods and properties after moving their logic to the
  Firebase Cloud Messaging SDK
- Fixed an intermittent stability issue when a debug build of an app was
  replaced with a release build of the same version
- Removed swizzling logic that was sometimes resulting in developers receiving
  a validation notice about enabling push notification capabilities, even though
  they weren't using push notifications
- Fixed a notification that would sometimes fire twice in quick succession
  during the first run of an app

# 2017-03-31 -- v1.0.10

- Improvements to token-fetching logic
- Fixed some warnings in Instance ID
- Improved error messages if Instance ID couldn't be initialized properly
- Improvements to console logging

# 2017-01-31 -- v1.0.9

- Removed an error being mistakenly logged to the console.

# 2016-07-06 -- v1.0.8

- Don't store InstanceID plists in Documents folder.

# 2016-06-19 -- v1.0.7

- Fix remote-notifications warning on app submission.

# 2016-05-16 -- v1.0.6

- Fix CocoaPod linter issues for InstanceID pod.

# 2016-05-13 -- v1.0.5

- Fix Authorization errors for InstanceID tokens.

# 2016-05-11 -- v1.0.4

- Reduce wait for InstanceID token during parallel requests.

# 2016-04-18 -- v1.0.3

- Change flag to disable swizzling to *FirebaseAppDelegateProxyEnabled*.
- Fix incessant Keychain errors while accessing InstanceID.
- Fix max retries for fetching IID token.

# 2016-04-18 -- v1.0.2

- Register for remote notifications on iOS8+ in the SDK itself.
