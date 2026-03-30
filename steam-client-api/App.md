# Apps

## Overview

The `Apps` interface provides comprehensive functionality for managing Steam applications, including:

- Installing, launching, and managing Steam games and applications
- Managing non-Steam application shortcuts
- Handling workshop items and downloadable content (DLC)
- Managing achievements and playtime tracking
- Configuring application settings (language, launch options, compatibility tools, etc.)
- Managing screenshots and cloud synchronization
- Handling game actions and monitoring application state
- Managing backups and verifying application files
- Controlling Steam Overlay, controller configuration, and other features

This module serves as the primary interface for all application-related operations in the Steam client.

---

## Methods

### AddShortcut

```typescript
AddShortcut(appName: string, executablePath: string, directory: string, launchOptions: string): Promise<number>
```

Adds a non-Steam application shortcut to the local Steam library.

**Parameters:**
- `appName` (string): The name of the non-Steam application.
- `executablePath` (string): The path to the executable file of the non-Steam application.
- `directory` (string): The working directory for the non-Steam application.
- `launchOptions` (string): Options to be passed when launching the non-Steam application.

**Returns:** `Promise<number>` - A unique AppID assigned to the added non-Steam application shortcut.

---

### BackupFilesForApp

```typescript
BackupFilesForApp(appId: number, backupPath: string): Promise<number>
```

Backs up an app to the specified path.

**Parameters:**
- `appId` (number): The ID of the application to back up.
- `backupPath` (string): The path to store the backup.

**Returns:** `Promise<number>` - A number. This value may be "20" for backup busy and "0" for success.

---

### BrowseScreenshotForApp

```typescript
BrowseScreenshotForApp(appId: string, handle: number): void
```

Opens the screenshot folder for a specific app.

**Parameters:**
- `appId` (string): The ID of the app to browse screenshots for.
- `handle` (number): The screenshot handle to use.

---

### BrowseScreenshotsForApp

```typescript
BrowseScreenshotsForApp(appId: string): void
```

Opens the screenshot folder for a specific app.

**Parameters:**
- `appId` (string): The ID of the app to browse screenshots for.

---

### CancelBackup

```typescript
CancelBackup(): void
```

Cancels the current backup process.

---

### CancelGameAction

```typescript
CancelGameAction(gameActionId: number): void
```

Cancels a specific game action.

**Parameters:**
- `gameActionId` (number): The ID of the game action to cancel.

---

### CancelLaunch

```typescript
CancelLaunch(appId: string): void
```

Cancels the launch of an application with the specified ID.

**Parameters:**
- `appId` (string): The ID of the application whose launch is to be canceled.

---

### ClearCustomArtworkForApp

```typescript
ClearCustomArtworkForApp(appId: number, assetType: ELibraryAssetType): Promise<void>
```

Clears the custom artwork for a given application.

**Parameters:**
- `appId` (number): The ID of the application to clear custom artwork for.
- `assetType` (ELibraryAssetType): The type of artwork to clear.

---

### ClearCustomLogoPositionForApp

```typescript
ClearCustomLogoPositionForApp(appId: number): Promise<void>
```

Clears the custom logo position for a specific application.

**Parameters:**
- `appId` (number): The ID of the application.

**Returns:** `Promise<void>` - A Promise that resolves once the custom logo position is cleared.

---

### ClearProton

```typescript
ClearProton(appId: number): Promise<void>
```

Clears the Proton compatibility tool configuration for an application.

**Parameters:**
- `appId` (number): The ID of the application.

---

### ContinueGameAction

```typescript
ContinueGameAction(gameActionId: number, actionType: string): void
```

Continues a specific game action.

**Parameters:**
- `gameActionId` (number): The ID of the game action to continue.
- `actionType` (string): The type of action to perform during continuation.

**Remarks:** actionType values include "SkipShaders", "skip", "ShowDurationControl".

---

### CreateDesktopShortcutForApp

```typescript
CreateDesktopShortcutForApp(appId: number): void
```

Creates a Steam application shortcut on the desktop.

**Parameters:**
- `appId` (number): The ID of the application for which to create a desktop shortcut.

---

### DownloadWorkshopItem

```typescript
DownloadWorkshopItem(appId: number, itemId: string, param1: boolean): void
```

Downloads a workshop item.

**Parameters:**
- `appId` (number): The ID of the application.
- `itemId` (string): The ID of the workshop item.
- `param1` (boolean): Additional parameter.

---

### GetAchievementsInTimeRange

```typescript
GetAchievementsInTimeRange(appId: number, start: number, end: number): Promise<AppAchievement[]>
```

Retrieves achievements within a specified time range for a given app.

**Parameters:**
- `appId` (number): The ID of the application.
- `start` (number): The start of the time range as a Unix timestamp.
- `end` (number): The end of the time range as a Unix timestamp.

**Returns:** `Promise<AppAchievement[]>` - An array of AppAchievement objects.

**Throws:** `OperationResponse`

---

### GetActiveGameActions

```typescript
GetActiveGameActions(): Promise<GameAction[]>
```

Retrieves a list of active game actions, such as launching an application.

**Returns:** `Promise<GameAction[]>` - An array of active game actions.

---

### GetAvailableCompatTools

```typescript
GetAvailableCompatTools(appId: number): Promise<CompatibilityTool[]>
```

Retrieves a list of available compatibility tools for a specific application.

**Parameters:**
- `appId` (number): The ID of the application to retrieve compatibility tools for.

**Returns:** `Promise<CompatibilityTool[]>` - An array of CompatibilityToolInfo objects.

---

### GetBackupsInFolder

```typescript
GetBackupsInFolder(appBackupPath: string): Promise<string | undefined>
```

Retrieves the name of the application in a backup folder.

**Parameters:**
- `appBackupPath` (string): The path to the application's backup folder.

**Returns:** `Promise<string | undefined>` - The name of the application in the backup folder, or undefined if the path is invalid.

**Remarks:** This function checks for the "sku.sis" file in that path.

---

### GetCachedAppDetails

```typescript
GetCachedAppDetails(appId: number): Promise<string>
```

Retrieves cached details for a specific application.

**Parameters:**
- `appId` (number): The ID of the application.

**Returns:** `Promise<string>` - A stringified object. Returns `CachedAppDetails` when parsed.

---

### GetCloudPendingRemoteOperations

```typescript
GetCloudPendingRemoteOperations(appId: number): Promise<{ PendingOperations: ArrayBuffer }>
```

Retrieves pending cloud operations for an application.

**Parameters:**
- `appId` (number): The ID of the application.

**Returns:** `Promise<{ PendingOperations: ArrayBuffer }>` - A ProtoBuf message. If deserialized, returns `CMsgCloudPendingRemoteOperations`.

---

### GetCompatExperiment

```typescript
GetCompatExperiment(param0: number): Promise<string>
```

Gets the compatibility experiment for an application.

**Parameters:**
- `param0` (number): Application ID.

**Returns:** `Promise<string>`

---

### GetConflictingFileTimestamps

```typescript
GetConflictingFileTimestamps(appId: number): Promise<ConflictingFileTimestamp>
```

Gets conflicting file timestamps for cloud synchronization.

**Parameters:**
- `appId` (number): The ID of the application.

**Returns:** `Promise<ConflictingFileTimestamp>`

---

### GetDetailsForScreenshotUpload

```typescript
GetDetailsForScreenshotUpload(appId: string, hHandle: number): Promise<ScreenshotUploadDetails>
```

Retrieves details for a specific screenshot upload.

**Parameters:**
- `appId` (string): The ID of the application.
- `hHandle` (number): The handle of the screenshot upload.

**Returns:** `Promise<ScreenshotUploadDetails>` - Details about the screenshot upload.

---

### GetDetailsForScreenshotUploads

```typescript
GetDetailsForScreenshotUploads(appId: string, hHandles: number[]): Promise<ScreenshotUploadsDetails>
```

Retrieves details for multiple screenshot uploads.

**Parameters:**
- `appId` (string): The ID of the application.
- `hHandles` (number[]): An array of handles of the screenshot uploads.

**Returns:** `Promise<ScreenshotUploadsDetails>` - Details about the screenshot uploads.

---

### GetDownloadedWorkshopItems

```typescript
GetDownloadedWorkshopItems(appId: number): Promise<WorkshopItem[]>
```

Retrieves a list of downloaded workshop items for a specific application.

**Parameters:**
- `appId` (number): The ID of the application to retrieve downloaded workshop items for.

**Returns:** `Promise<WorkshopItem[]>` - An array of downloaded workshop items for the specified application.

---

### GetDurationControlInfo

```typescript
GetDurationControlInfo(appId: number): Promise<{ bApplicable: boolean }>
```

Gets duration control information for an application.

**Parameters:**
- `appId` (number): The ID of the application.

**Returns:** `Promise<{ bApplicable: boolean }>`

---

### GetFriendAchievementsForApp

```typescript
GetFriendAchievementsForApp(appId: string, friendSteam64Id: string): Promise<AppAchievementResponse>
```

Retrieves achievement information for a specific application for a given friend.

**Parameters:**
- `appId` (string): The ID of the application to retrieve achievement information for.
- `friendSteam64Id` (string): The Steam64 ID of the friend for whom to retrieve achievement information.

**Returns:** `Promise<AppAchievementResponse>` - An object containing achievement information for the specified friend and application.

---

### GetFriendsWhoPlay

```typescript
GetFriendsWhoPlay(appId: number): Promise<string[]>
```

Retrieves a list of friends who play the specified application.

**Parameters:**
- `appId` (number): The ID of the application.

**Returns:** `Promise<string[]>` - An array of Steam64 IDs representing friends who play the application.

---

### GetGameActionDetails

```typescript
GetGameActionDetails(appId: number, callback: (gameAction: GameAction) => void): void
```

Retrieves details of a game action.

**Parameters:**
- `appId` (number): The ID of the application.
- `callback` (function): The callback function to handle the retrieved game action details.
  - `gameAction` (GameAction): The game action received in the callback.

---

### GetGameActionForApp

```typescript
GetGameActionForApp(
    appId: string,
    callback: (
        gameActionId: number,
        appId: 0 | string,
        taskName: AppAction_t,
    ) => void,
): void
```

Gets the current game action for an application.

**Parameters:**
- `appId` (string): The ID of the application.
- `callback` (function): The callback function to handle the game action information.

---

### GetLaunchOptionsForApp

```typescript
GetLaunchOptionsForApp(appId: number): Promise<LaunchOption[]>
```

Retrieves launch options for a specified application.

**Parameters:**
- `appId` (number): The ID of the application.

**Returns:** `Promise<LaunchOption[]>` - An array of launch options for the specified application.

**Remarks:** These options may include different configurations or settings for launching the application, such as DirectX, Vulkan, OpenGL, 32-bit, 64-bit, etc. This function does not retrieve launch/argument options inputted by the user.

---

### GetLibraryBootstrapData

```typescript
GetLibraryBootstrapData(): Promise<ArrayBuffer>
```

Gets library bootstrap data.

**Returns:** `Promise<ArrayBuffer>` - A ProtoBuf message. If deserialized, returns `CLibraryBootstrapData`.

---

### GetMyAchievementsForApp

```typescript
GetMyAchievementsForApp(appId: string): Promise<AppAchievementResponse>
```

Retrieves achievement information for the authenticated user in a specific Steam application.

**Parameters:**
- `appId` (string): The ID of the application to retrieve achievement information for.

**Returns:** `Promise<AppAchievementResponse>` - An AppAchievementResponse object containing the achievement information for the authenticated user in the specified application.

---

### GetPlaytime

```typescript
GetPlaytime(appId: number): Promise<Playtime | undefined>
```

Retrieves the playtime information for a specific application.

**Parameters:**
- `appId` (number): The ID of the application to get playtime information for.

**Returns:** `Promise<Playtime | undefined>` - Playtime information or undefined if not available.

---

### GetPrePurchasedApps

```typescript
GetPrePurchasedApps(appIds: number[]): Promise<PrePurchaseInfo>
```

Gets pre-purchase information for applications.

**Parameters:**
- `appIds` (number[]): Array of application IDs.

**Returns:** `Promise<PrePurchaseInfo>`

---

### GetResolutionOverrideForApp

```typescript
GetResolutionOverrideForApp(appId: number): Promise<string>
```

Retrieves the resolution override for a specific application.

**Parameters:**
- `appId` (number): The ID of the application to retrieve the resolution override for.

**Returns:** `Promise<string>` - A string of the resolution override.

---

### GetScreenshotInfo

```typescript
GetScreenshotInfo(appId: string, hHandle: number): Promise<Screenshot>
```

Retrieves detailed information about a specific screenshot.

**Parameters:**
- `appId` (string): The ID of the application the screenshot belongs to.
- `hHandle` (number): The handle of the screenshot.

**Returns:** `Promise<Screenshot>` - Detailed information about the specified screenshot.

---

### GetScreenshotsInTimeRange

```typescript
GetScreenshotsInTimeRange(appId: number, start: number, end: number): Promise<Screenshot[]>
```

Retrieves screenshots within a specified time range.

**Parameters:**
- `appId` (number): The ID of the application.
- `start` (number): The start of the time range as a Unix timestamp.
- `end` (number): The end of the time range as a Unix timestamp.

**Returns:** `Promise<Screenshot[]>` - An array of screenshots taken within the specified time range.

---

### GetShortcutDataForPath

```typescript
GetShortcutDataForPath(pathToShortcut: string): Promise<Shortcut>
```

Retrieves shortcut data for a given shortcut file path.

**Parameters:**
- `pathToShortcut` (string): The path to the shortcut file.

**Returns:** `Promise<Shortcut>` - The shortcut data.

---

### GetSoundtrackDetails

```typescript
GetSoundtrackDetails(appId: number): Promise<SoundtrackDetails>
```

Retrieves details about a soundtrack associated with a soundtrack application.

**Parameters:**
- `appId` (number): The ID of the soundtrack application.

**Returns:** `Promise<SoundtrackDetails>` - The details of the soundtrack associated with the specified soundtrack application.

**Remarks:** The soundtrack has to be installed.

---

### GetStoreTagLocalization

```typescript
GetStoreTagLocalization(tags: number[]): Promise<StoreTagLocalization[]>
```

Gets store tag localizations.

**Parameters:**
- `tags` (number[]): Array of tag IDs.

**Returns:** `Promise<StoreTagLocalization[]>`

---

### GetSubscribedWorkshopItemDetails

```typescript
GetSubscribedWorkshopItemDetails(appId: number, itemIds: string[]): Promise<WorkshopItem[] | OperationResponse>
```

Retrieves a list of subscribed workshop item details for a specific application.

**Parameters:**
- `appId` (number): The ID of the application to retrieve subscribed workshop item details for.
- `itemIds` (string[]): Workshop item IDs to retrieve details for.

**Returns:** `Promise<WorkshopItem[] | OperationResponse>` - An array of subscribed workshop item details for the specified application.

**Throws:** Throws if the query failed.

---

### GetSubscribedWorkshopItems

```typescript
GetSubscribedWorkshopItems(appId: number): Promise<WorkshopItem[]>
```

Retrieves a list of subscribed workshop items for a specific application.

**Parameters:**
- `appId` (number): The ID of the application to retrieve subscribed workshop items for.

**Returns:** `Promise<WorkshopItem[]>` - An array of subscribed workshop items for the specified application.

---

### InstallFlatpakAppAndCreateShortcut

```typescript
InstallFlatpakAppAndCreateShortcut(appName: string, appCommandLineOptions: string): Promise<{ appid: number; strInstallOutput: string }>
```

Installs a Flatpak application and creates a shortcut.

**Parameters:**
- `appName` (string): The name of the Flatpak application.
- `appCommandLineOptions` (string): Command-line options for the application.

**Returns:** `Promise<{ appid: number; strInstallOutput: string }>`

---

### JoinAppContentBeta

```typescript
JoinAppContentBeta(appId: number, name: string): Promise<EResult>
```

Joins an app beta.

**Parameters:**
- `appId` (number): App ID of the beta to join.
- `name` (string): Beta name. Empty string to opt out of betas.

**Returns:** `Promise<EResult>`

**Throws:** EResult if no beta found.

---

### JoinAppContentBetaByPassword

```typescript
JoinAppContentBetaByPassword(appId: number, accessCode: string): Promise<any>
```

Joins an app beta by password.

**Parameters:**
- `appId` (number): The ID of the application.
- `accessCode` (string): The access code for the beta.

**Returns:** `Promise<any>` - Contains `strName` property.

**Throws:** EResult if no beta found.

---

### ListFlatpakApps

```typescript
ListFlatpakApps(): Promise<any>
```

Lists available Flatpak applications.

**Returns:** `Promise<any>`

---

### LoadEula

```typescript
LoadEula(appId: number): Promise<EndUserLicenseAgreement[]>
```

Loads the End User License Agreement for an application.

**Parameters:**
- `appId` (number): The ID of the application.

**Returns:** `Promise<EndUserLicenseAgreement[]>` - Array of EULA data.

**Remarks:** Doesn't bring up the EULA dialog, just returns the EULA data.

**Throws:** If the user does not own the app or no EULA exists.

---

### MarkEulaAccepted

```typescript
MarkEulaAccepted(appId: number, id: string, version: number): void
```

Marks a EULA as accepted.

**Parameters:**
- `appId` (number): The ID of the application.
- `id` (string): The EULA ID.
- `version` (number): The EULA version.

---

### MarkEulaRejected

```typescript
MarkEulaRejected(appId: number, id: string, version: number): void
```

Marks a EULA as rejected.

**Parameters:**
- `appId` (number): The ID of the application.
- `id` (string): The EULA ID.
- `version` (number): The EULA version.

---

### MoveWorkshopItemLoadOrder

```typescript
MoveWorkshopItemLoadOrder(appId: number, oldOrder: number, newOrder: number): void
```

Moves a specified workshop item's load order.

**Parameters:**
- `appId` (number): The ID of the application.
- `oldOrder` (number): The item to move, referenced by its position number.
- `newOrder` (number): The position number to move the item to.

**Remarks:** Orders are zero-indexed.

---

### OpenAppSettingsDialog

```typescript
OpenAppSettingsDialog(appId: number, section: string): void
```

Opens the settings dialog for a specific application.

**Parameters:**
- `appId` (number): The ID of the application for which to open the settings dialog.
- `section` (string): The section (tab) to switch to.

---

### RaiseWindowForGame

```typescript
RaiseWindowForGame(appId: number): Promise<ERaiseGameWindowResult>
```

Raises the window for a given application.

**Parameters:**
- `appId` (number): The ID of the application to raise the window of.

**Returns:** `Promise<ERaiseGameWindowResult>`

---

### RegisterForAchievementChanges

```typescript
RegisterForAchievementChanges(callback: (data: ArrayBuffer) => void): Unregisterable
```

Registers a callback function to be called when achievement changes occur.

**Parameters:**
- `callback` (function): The callback function to be called.
  - `data` (ArrayBuffer): Achievement change data.

**Returns:** `Unregisterable` - An object that can be used to unregister the callback.

---

### RegisterForAppBackupStatus

```typescript
RegisterForAppBackupStatus(callback: (status: AppBackupStatus) => void): Unregisterable
```

Registers a callback for app backup status updates.

**Parameters:**
- `callback` (function): The callback function to be called.
  - `status` (AppBackupStatus): Backup status information.

**Returns:** `Unregisterable`

---

### RegisterForAppDetails

```typescript
RegisterForAppDetails(appId: number, callback: (data: AppDetails) => void): Unregisterable
```

Registers a callback function to be called when app details change.

**Parameters:**
- `appId` (number): The ID of the application to monitor.
- `callback` (function): The callback function to be called.
  - `data` (AppDetails): Updated app details.

**Returns:** `Unregisterable` - An object that can be used to unregister the callback.

---

### RegisterForAppOverviewChanges

```typescript
RegisterForAppOverviewChanges(callback: (data: ArrayBuffer) => void): void
```

Registers a callback for app overview changes.

**Parameters:**
- `callback` (function): The callback function to be called.
  - `data` (ArrayBuffer): If deserialized, returns `CAppOverview_Change`.

**Remarks:** This is not a mistake, it doesn't return anything.

---

### RegisterForDRMFailureResponse

```typescript
RegisterForDRMFailureResponse(
    callback: (appid: number, eResult: EResult, errorCode: number) => void,
): Unregisterable
```

Registers a callback for DRM failure responses.

**Parameters:**
- `callback` (function): The callback function to be called.

**Returns:** `Unregisterable`

---

### RegisterForGameActionEnd

```typescript
RegisterForGameActionEnd(callback: (gameActionId: number) => void): Unregisterable
```

Registers a callback function to be called when a game action ends.

**Parameters:**
- `callback` (function): The callback function to be called.
  - `gameActionId` (number): The ID of the game action that ended.

**Returns:** `Unregisterable` - An object that can be used to unregister the callback.

---

### RegisterForGameActionShowError

```typescript
RegisterForGameActionShowError(
    callback: (
        gameActionId: number,
        appId: string,
        actionName: string,
        error: string,
        param4: string,
    ) => void
): Unregisterable
```

Registers a callback for game action errors.

**Parameters:**
- `callback` (function): The callback function to be called.
  - `error` (string): Localization token.

**Returns:** `Unregisterable`

---

### RegisterForGameActionShowUI

```typescript
RegisterForGameActionShowUI(callback: () => void): Unregisterable
```

Registers a callback function to be called when a game action UI is shown.

**Parameters:**
- `callback` (function): The callback function to be called.

**Returns:** `Unregisterable` - An object that can be used to unregister the callback.

---

### RegisterForGameActionStart

```typescript
RegisterForGameActionStart(
    callback: (gameActionId: number, appId: string, action: string, param3: ELaunchSource) => void,
): Unregisterable
```

Registers a callback function to be called when a game action starts.

**Parameters:**
- `callback` (function): The callback function to be called.

**Returns:** `Unregisterable` - An object that can be used to unregister the callback.

---

### RegisterForGameActionTaskChange

```typescript
RegisterForGameActionTaskChange(
    callback: (
        gameActionId: number,
        appId: string,
        action: string,
        requestedAction: string,
        param4: string,
    ) => void,
): Unregisterable
```

Registers a callback function to be called when a game action task changes.

**Parameters:**
- `callback` (function): The callback function to be called.

**Returns:** `Unregisterable` - An object that can be used to unregister the callback.

---

### RegisterForGameActionUserRequest

```typescript
RegisterForGameActionUserRequest(
    callback: (
        gameActionId: number,
        appId: string,
        action: string,
        requestedAction: string,
        appId2: string,
    ) => void,
): Unregisterable
```

Registers a callback function to be called when a user requests a game action.

**Parameters:**
- `callback` (function): The callback function to be called.

**Returns:** `Unregisterable` - An object that can be used to unregister the callback.

---

### RegisterForPrePurchasedAppChanges

```typescript
RegisterForPrePurchasedAppChanges(callback: () => void): Unregisterable
```

Registers a callback for pre-purchased app changes.

**Parameters:**
- `callback` (function): The callback function to be called.

**Returns:** `Unregisterable`

---

### RegisterForShowMarketingMessageDialog

```typescript
RegisterForShowMarketingMessageDialog: Unregisterable
```

Registers for marketing message dialog notifications.

---

### RegisterForWorkshopChanges

```typescript
RegisterForWorkshopChanges(callback: (appId: number) => void): Unregisterable
```

Registers a callback function to be notified when workshop items are added or removed from a Steam application.

**Parameters:**
- `callback` (function): The callback function to be called.
  - `appId` (number): The ID of the application with workshop changes.

**Returns:** `Unregisterable` - An object that can be used to unregister the callback.

---

### RegisterForWorkshopItemDownloads

```typescript
RegisterForWorkshopItemDownloads(
    appId: number,
    callback: (appId: number, publishedFileId: string, param2: number) => void,
): Unregisterable
```

Registers a callback for workshop item download updates.

**Parameters:**
- `appId` (number): The ID of the application.
- `callback` (function): The callback function to be called.

**Returns:** `Unregisterable`

---

### RegisterForWorkshopItemInstalled

```typescript
RegisterForWorkshopItemInstalled(callback: (item: InstalledWorkshopItem) => void): Unregisterable
```

Registers a callback for when workshop items are installed.

**Parameters:**
- `callback` (function): The callback function to be called.
  - `item` (InstalledWorkshopItem): The installed workshop item information.

**Returns:** `Unregisterable`

---

### RemoveShortcut

```typescript
RemoveShortcut(appId: number): void
```

Removes a non-Steam application shortcut from the Steam library.

**Parameters:**
- `appId` (number): The ID of the application for which to remove the shortcut.

---

### ReportLibraryAssetCacheMiss

```typescript
ReportLibraryAssetCacheMiss(appId: number, assetType: ELibraryAssetType): void
```

Reports a library asset cache miss.

**Parameters:**
- `appId` (number): The ID of the application.
- `assetType` (ELibraryAssetType): The type of asset.

---

### ReportMarketingMessageDialogShown

```typescript
ReportMarketingMessageDialogShown(): void
```

Reports that a marketing message dialog was shown.

---

### RequestIconDataForApp

```typescript
RequestIconDataForApp(appId: number): void
```

Requests icon data for an application.

**Parameters:**
- `appId` (number): The ID of the application.

---

### RequestLegacyCDKeysForApp

```typescript
RequestLegacyCDKeysForApp(appId: number): void
```

Requests legacy CD keys for an application.

**Parameters:**
- `appId` (number): The ID of the application.

---

### RunGame

```typescript
RunGame(appId: string, launchOptions: string, param2: number, launchSource: ELaunchSource): void
```

Runs a game with specified parameters. Focuses the game if already launched.

**Parameters:**
- `appId` (string): The ID of the application to run.
- `launchOptions` (string): Additional launch options for the application.
- `param2` (number): Additional parameter (exact usage may vary).
- `launchSource` (ELaunchSource): Launch source.

**Remarks:** `launchOptions` is appended before the ones specified in the application's settings.

---

### SaveAchievementProgressCache

```typescript
SaveAchievementProgressCache(progress: string): Promise<void>
```

Saves achievement progress cache.

**Parameters:**
- `progress` (string): Stringified JSON of achievement progress.

**Returns:** `Promise<void>`

---

### ScanForInstalledNonSteamApps

```typescript
ScanForInstalledNonSteamApps(): Promise<NonSteamApp[]>
```

Scans the system for installed non-Steam applications.

**Returns:** `Promise<NonSteamApp[]>` - An array of NonSteamApp objects representing installed non-Steam applications.

**Remarks:** This function scans the user's system for installed applications that are not part of the Steam library. It does not scan for shortcuts added to the Steam library. On Linux, it scans inside /usr/share/applications and $XDG_DATA_HOME/applications.

---

### SetAppAutoUpdateBehavior

```typescript
SetAppAutoUpdateBehavior(appId: number, mode: EAppAutoUpdateBehavior): void
```

Sets the automatic update behavior for a Steam application.

**Parameters:**
- `appId` (number): The ID of the application to set the update behavior for.
- `mode` (EAppAutoUpdateBehavior): The update behavior mode to set.

**Remarks:** This function only works with installed Steam applications.

---

### SetAppBackgroundDownloadsBehavior

```typescript
SetAppBackgroundDownloadsBehavior(appId: number, mode: EAppAllowDownloadsWhileRunningBehavior): void
```

Sets the background downloads behavior for a specific Steam application.

**Parameters:**
- `appId` (number): The ID of the application to set the background downloads behavior for.
- `mode` (EAppAllowDownloadsWhileRunningBehavior): The background downloads mode to set.

**Remarks:** This function only works with installed Steam applications.

---

### SetAppCurrentLanguage

```typescript
SetAppCurrentLanguage(appId: number, language: string): void
```

Sets the current language for a specific Steam application.

**Parameters:**
- `appId` (number): The ID of the application to set the current language for.
- `language` (string): The language to set, represented as a language code (e.g., "english", "spanish", "tchinese", "schinese").

---

### SetAppFamilyBlockedState

```typescript
SetAppFamilyBlockedState(appIds: number[], state: boolean): void
```

Sets the blocked state for apps.

**Parameters:**
- `appIds` (number[]): An array of app IDs to set the blocked state for.
- `state` (boolean): The state to set (true for blocked, false for unblocked).

---

### SetAppLaunchOptions

```typescript
SetAppLaunchOptions(appId: number, launchOptions: string): void
```

Sets launch options for a Steam application.

**Parameters:**
- `appId` (number): The ID of the application to set launch options for.
- `launchOptions` (string): The launch options to be set for the application.

---

### SetAppResolutionOverride

```typescript
SetAppResolutionOverride(appId: number, resolution: string): void
```

Sets a resolution override for a Steam application.

**Parameters:**
- `appId` (number): The ID of the application to set the resolution override for.
- `resolution` (string): The resolution to be set for the application. It can be "Default", "Native", or other compatible resolutions for the user's monitor.

---

### SetCachedAppDetails

```typescript
SetCachedAppDetails(appId: number, details: string): Promise<void>
```

Sets cached details for a specific application.

**Parameters:**
- `appId` (number): The ID of the application.
- `details` (string): The details to be cached, a stringified object.

**Returns:** `Promise<void>` - A Promise that resolves when the details are successfully cached.

---

### SetControllerRumblePreference

```typescript
SetControllerRumblePreference(appId: number, value: EControllerRumbleSetting): void
```

Sets the controller rumble preference for an application.

**Parameters:**
- `appId` (number): The ID of the application.
- `value` (EControllerRumbleSetting): The rumble preference.

---

### SetCustomArtworkForApp

```typescript
SetCustomArtworkForApp(appId: number, base64: string, imageType: 'jpg' | 'png', assetType: ELibraryAssetType): Promise<void>
```

Sets the custom artwork for a given application.

**Parameters:**
- `appId` (number): The ID of the application to set custom artwork for.
- `base64` (string): Base64 encoded image.
- `imageType` ('jpg' | 'png'): The image format.
- `assetType` (ELibraryAssetType): The type of artwork to set.

**Returns:** `Promise<void>` - A Promise that resolves after the custom artwork is set.

---

### SetCustomLogoPositionForApp

```typescript
SetCustomLogoPositionForApp(appId: number, details: string): Promise<void>
```

Sets a custom logo position for a specific app.

**Parameters:**
- `appId` (number): The ID of the application.
- `details` (string): The details of the custom logo position, expected to be a stringified `LogoPositionForApp` object.

**Returns:** `Promise<void>` - A Promise that resolves when the custom logo position is successfully set.

---

### SetDLCEnabled

```typescript
SetDLCEnabled(appId: number, appDLCId: number, value: boolean): void
```

Sets the enabled state for downloadable content (DLC) of a specific app.

**Parameters:**
- `appId` (number): The ID of the parent application.
- `appDLCId` (number): The ID of the DLC to set the state for.
- `value` (boolean): The value to set (true for enabled, false for disabled).

---

### SetLocalScreenshotCaption

```typescript
SetLocalScreenshotCaption(appId: string, hHandle: number, caption: string): void
```

Sets a local screenshot's caption.

**Parameters:**
- `appId` (string): The application ID the screenshot belongs to.
- `hHandle` (number): The handle of the screenshot.
- `caption` (string): The caption text.

---

### SetLocalScreenshotPrivacy

```typescript
SetLocalScreenshotPrivacy(appId: string, hHandle: number, privacy: EUCMFilePrivacyState): void
```

Sets a local screenshot's privacy state.

**Parameters:**
- `appId` (string): The application ID the screenshot belongs to.
- `hHandle` (number): The handle of the screenshot.
- `privacy` (EUCMFilePrivacyState): Screenshot privacy state.

---

### SetLocalScreenshotSpoiler

```typescript
SetLocalScreenshotSpoiler(appId: string, hHandle: number, spoilered: boolean): void
```

Sets a local screenshot's spoiler state.

**Parameters:**
- `appId` (string): The application ID the screenshot belongs to.
- `hHandle` (number): The handle of the screenshot.
- `spoilered` (boolean): Is the screenshot spoilered?

---

### SetShortcutExe

```typescript
SetShortcutExe(appId: number, path: string): void
```

Sets the executable path for a non-Steam application shortcut.

**Parameters:**
- `appId` (number): The ID of the application to set the shortcut executable for.
- `path` (string): The path to the executable.

---

### SetShortcutIcon

```typescript
SetShortcutIcon(appId: number, path: string): void
```

Sets the icon for a non-Steam application shortcut.

**Parameters:**
- `appId` (number): The ID of the application to set the shortcut icon for.
- `path` (string): The path to the icon image (can be png or tga format).

---

### SetShortcutIsVR

```typescript
SetShortcutIsVR(appId: number, value: boolean): void
```

Sets whether a non-Steam application shortcut should be included in the VR library.

**Parameters:**
- `appId` (number): The ID of the application to set the VR status for.
- `value` (boolean): A boolean indicating whether the application should be included in the VR library.

---

### SetShortcutLaunchOptions

```typescript
SetShortcutLaunchOptions(appId: number, options: string): void
```

Sets launch options for a non-Steam application shortcut.

**Parameters:**
- `appId` (number): The ID of the application to set the launch options for.
- `options` (string): The launch options to be used when starting the application.

---

### SetShortcutName

```typescript
SetShortcutName(appId: number, name: string): void
```

Sets the name for a non-Steam application shortcut.

**Parameters:**
- `appId` (number): The ID of the application to set the shortcut name for.
- `name` (string): The name to be displayed for the application shortcut.

---

### SetShortcutStartDir

```typescript
SetShortcutStartDir(appId: number, directory: string): void
```

Sets the starting directory for a non-Steam application shortcut.

**Parameters:**
- `appId` (number): The ID of the application to set the starting directory for.
- `directory` (string): The directory from which the application should be launched.

---

### SetStreamingClientForApp

```typescript
SetStreamingClientForApp(appId: number, clientId: string): void
```

Sets the client ID for streaming for a specific application.

**Parameters:**
- `appId` (number): The ID of the application.
- `clientId` (string): The client ID for streaming.

---

### SetThirdPartyControllerConfiguration

```typescript
SetThirdPartyControllerConfiguration(appId: number, value: EThirdPartyControllerConfiguration): void
```

Sets third-party controller configuration for an application.

**Parameters:**
- `appId` (number): The ID of the application.
- `value` (EThirdPartyControllerConfiguration): The configuration value.

---

### SetWorkshopItemsDisabledLocally

```typescript
SetWorkshopItemsDisabledLocally(appId: number, itemIds: string[], value: boolean): void
```

Sets the workshop items disabled state.

**Parameters:**
- `appId` (number): The ID of the application.
- `itemIds` (string[]): Workshop item IDs to change the state for.
- `value` (boolean): `true` to disable, `false` otherwise.

---

### SetWorkshopItemsLoadOrder

```typescript
SetWorkshopItemsLoadOrder(appId: number, itemIds: string[]): void
```

Sets the workshop items load order for a specified application.

**Parameters:**
- `appId` (number): The ID of the application.
- `itemIds` (string[]): Workshop item IDs. Has to be the full list of subscribed items, otherwise the specified items get moved to the last position.

---

### ShowControllerConfigurator

```typescript
ShowControllerConfigurator(appId: number): void
```

Opens the controller configurator for a specific application.

**Parameters:**
- `appId` (number): The ID of the application for which to open the controller configurator.

---

### ShowStore

```typescript
ShowStore(appId: number): void
```

Opens the Steam store page for a specific application.

**Parameters:**
- `appId` (number): The ID of the application.

---

### SpecifyCompatExperiment

```typescript
SpecifyCompatExperiment(appId: number, param1: string): void
```

Specifies a compatibility experiment for an application.

**Parameters:**
- `appId` (number): The ID of the application.
- `param1` (string): Experiment identifier.

---

### SpecifyCompatTool

```typescript
SpecifyCompatTool(appId: number, strToolName: string): void
```

Specifies a compatibility tool by its name for a given application.

**Parameters:**
- `appId` (number): The ID of the application to specify compatibility tool for.
- `strToolName` (string): The name of the compatibility tool to specify. If strToolName is an empty string, the specified application will no longer use a compatibility tool.

---

### StreamGame

```typescript
StreamGame(appId: number, clientId: string, param2: number): void
```

Streams a game to another client.

**Parameters:**
- `appId` (number): The ID of the application.
- `clientId` (string): The client ID to stream to.
- `param2` (number): Additional parameter.

---

### SubscribeWorkshopItem

```typescript
SubscribeWorkshopItem(appId: number, workshopId: string, subscribed: boolean): void
```

Subscribes or unsubscribes from a workshop item for a specific app.

**Parameters:**
- `appId` (number): The ID of the application.
- `workshopId` (string): The ID of the workshop item.
- `subscribed` (boolean): True to subscribe, false to unsubscribe.

---

### TerminateApp

```typescript
TerminateApp(appId: string, param1: boolean): void
```

Terminates a running application.

**Parameters:**
- `appId` (string): The ID of the application to terminate.
- `param1` (boolean): Additional parameter. Exact usage may vary.

---

### ToggleAllowDesktopConfiguration

```typescript
ToggleAllowDesktopConfiguration(appId: number): void
```

Toggles the allow desktop configuration setting.

**Parameters:**
- `appId` (number): The ID of the application.

**Remarks:** Related to "#AppProperties_SteamInputDesktopConfigInLauncher".

---

### ToggleAppSteamCloudEnabled

```typescript
ToggleAppSteamCloudEnabled(appId: number): void
```

Toggles the Steam Cloud synchronization for game saves for a specific application.

**Parameters:**
- `appId` (number): The ID of the application.

**Remarks:** This function modifies the "<STEAMPATH>/userdata/<STEAMID3>/7/remote/sharedconfig.vdf" file.

---

### ToggleAppSteamCloudSyncOnSuspendEnabled

```typescript
ToggleAppSteamCloudSyncOnSuspendEnabled(appId: number): void
```

Toggles Steam Cloud sync on suspend for an application.

**Parameters:**
- `appId` (number): The ID of the application.

**Remarks:** Related to "#AppProperties_EnableSteamCloudSyncOnSuspend".

---

### ToggleEnableSteamOverlayForApp

```typescript
ToggleEnableSteamOverlayForApp(appId: number): void
```

Toggles the Steam Overlay setting for a specific application.

**Parameters:**
- `appId` (number): The ID of the application.

---

### ToggleOverrideResolutionForInternalDisplay

```typescript
ToggleOverrideResolutionForInternalDisplay(appId: number): void
```

Toggles resolution override for internal display.

**Parameters:**
- `appId` (number): The ID of the application.

**Remarks:** Related to "#AppProperties_ResolutionOverride_Internal".

---

### UninstallFlatpakApp

```typescript
UninstallFlatpakApp(app: string): Promise<boolean>
```

Uninstalls a Flatpak application.

**Parameters:**
- `app` (string): The Flatpak application identifier.

**Returns:** `Promise<boolean>` - Success status.

---

### VerifyApp

```typescript
VerifyApp(appId: number): Promise<{ nGameActionID: number }>
```

Verifies the integrity of an app's files.

**Parameters:**
- `appId` (number): The ID of the app to verify.

**Returns:** `Promise<{ nGameActionID: number }>` - The game action ID for the verification process.

---

## Types and Interfaces

### ELibraryAssetType

```typescript
enum ELibraryAssetType {
    Capsule,
    Hero,
    Logo,
    Header,
    Icon,
    HeroBlur,
}
```

Enum representing different types of library assets.

---

### AppAchievements

```typescript
interface AppAchievements {
    nAchieved: number;
    nTotal: number;
    vecAchievedHidden: AppAchievement[];
    vecHighlight: AppAchievement[];
    vecUnachieved: AppAchievement[];
}
```

Represents the achievement status for an application.

---

### AppAchievement

```typescript
interface AppAchievement {
    bAchieved: boolean;
    bHidden: boolean;
    flMinProgress: number;
    flCurrentProgress: number;
    flMaxProgress: number;
    flAchieved: number;
    rtUnlocked: number;
    strDescription: string;
    strID: string;
    strImage: string;
    strName: string;
}
```

Represents a single achievement.

**Properties:**
- `bAchieved` (boolean): Whether the achievement has been unlocked.
- `bHidden` (boolean): Is it a hidden achievement before unlocking it?
- `flMinProgress` (number): Minimum progress value.
- `flCurrentProgress` (number): Current progress value.
- `flMaxProgress` (number): Maximum progress value.
- `flAchieved` (number): How many players have this achievement, in 0-100 range.
- `rtUnlocked` (number): When this achievement was unlocked.
- `strDescription` (string): Localized achievement description.
- `strID` (string): Achievement ID.
- `strImage` (string): Achievement icon URL.
- `strName` (string): Localized achievement name.

---

### AppAction_t

```typescript
type AppAction_t = "LaunchApp" | "VerifyApp"
```

Type representing different app actions.

---

### LaunchAppTask_t

```typescript
type LaunchAppTask_t =
    | "None"
    | "Completed"
    | "Cancelled"
    | "Failed"
    | "Starting"
    | "ConnectingToSteam"
    | "RequestingLicense"
    | "UpdatingAppInfo"
    | "UpdatingAppTicket"
    | "UnlockingH264"
    | "WaitingOnWideVineUpdate"
    | "ShowCheckSystem"
    | "CheckTimedTrial"
    | "GetDurationControl"
    | "ShowDurationControl"
    | "ShowLaunchOption"
    | "ShowEula"
    | "ShowVR2DWarning"
    | "ShowVROculusOnly"
    | "ShowVRStreamingLaunch"
    | "ShowGameArgs"
    | "ShowCDKey"
    | "WaitingPrevProcess"
    | "DownloadingDepots"
    | "DownloadingWorkshop"
    | "UpdatingDRM"
    | "GettingLegacyKey"
    | "ProcessingInstallScript"
    | "RunningInstallScript"
    | "SynchronizingCloud"
    | "SynchronizingControllerConfig"
    | "ShowNoControllerConfig"
    | "ProcessingShaderCache"
    | "VerifyingFiles"
    | "KickingOtherSession"
    | "WaitingOpenVRAppQuit"
    | "SiteLicenseSeatCheckout"
    | "DelayLaunch"
    | "CreatingProcess"
    | "WaitingGameWindow"
```

Type representing different tasks during app launch.

---

### GameAction

```typescript
interface GameAction {
    nGameActionID: number;
    gameid: string;
    strActionName: AppAction_t;
    strTaskName: LaunchAppTask_t;
    strTaskDetails: string;
    nLaunchOption: number;
    nSecondsRemaing: number;
    strNumDone: string;
    strNumTotal: string;
    bWaitingForUI: boolean;
}
```

Represents a game action (like launching or verifying).

**Note:** `nSecondsRemaing` is not a typo - it's actually spelled this way by Valve.

---

### ConflictingFileTimestamp

```typescript
interface ConflictingFileTimestamp {
    rtLocalTime: number;
    rtRemoteTime: number;
}
```

Represents conflicting file timestamps for cloud sync.

---

### CompatibilityTool

```typescript
interface CompatibilityTool {
    strToolName: string;
    strDisplayName: string;
}
```

Represents information about a compatibility tool.

**Properties:**
- `strToolName` (string): Name of the compatibility tool.
- `strDisplayName` (string): Display name of the compatibility tool.

---

### ScreenshotUploadDetails

```typescript
interface ScreenshotUploadDetails {
    strSizeOnDisk: string;
    strCloudAvailable: string;
    strCloudTotal: string;
}
```

Represents details about a single screenshot upload.

**Properties:**
- `strSizeOnDisk` (string): The size of the screenshot upload on disk (including thumbnail).
- `strCloudAvailable` (string): The amount of cloud storage available.
- `strCloudTotal` (string): The total cloud storage.

---

### ScreenshotUploadsDetails

```typescript
interface ScreenshotUploadsDetails {
    unSizeOnDisk: number;
    strCloudAvailable: string;
    strCloudTotal: string;
}
```

Represents details about multiple screenshot uploads.

**Properties:**
- `unSizeOnDisk` (number): The total size of all screenshot uploads on disk (sum of sizes including thumbnails).
- `strCloudAvailable` (string): The amount of cloud storage available.
- `strCloudTotal` (string): The total cloud storage.

---

### InstalledWorkshopItem

```typescript
interface InstalledWorkshopItem {
    appid: number;
    legacy_content: string;
    manifestid: string;
    publishedfileid: string;
}
```

Represents an installed workshop item.

---

### WorkshopItem

```typescript
interface WorkshopItem {
    children: string[];
    eresult: EResult;
    file_size: string;
    file_type: EWorkshopFileType;
    preview_url: string;
    publishedfileid: string;
    short_description: string;
    tags: string[];
    title: string;
}
```

Represents a workshop item.

**Properties:**
- `children` (string[]): Required items' IDs.
- `eresult` (EResult): Result code.
- `file_size` (string): Item size, in bytes.
- `file_type` (EWorkshopFileType): Workshop file type.
- `preview_url` (string): Item preview image URL.
- `publishedfileid` (string): Item ID.
- `short_description` (string): Item description.
- `tags` (string[]): Item tags.
- `title` (string): Item title.

---

### AppAchievementData

```typescript
interface AppAchievementData {
    rgAchievements: AppAchievement[];
}
```

Container for achievement data.

---

### AppAchievementResponse

```typescript
interface AppAchievementResponse {
    result: EResult;
    data: AppAchievementData;
}
```

Response object for achievement queries.

---

### LaunchOption

```typescript
interface LaunchOption {
    bIsLaunchOptionTypeExemptFromGameTheater: VDFBoolean_t;
    bIsVRLaunchOption: VDFBoolean_t;
    eType: EAppLaunchOptionType;
    nIndex: number;
    strDescription: string;
    strGameName: string;
}
```

Represents a launch option for an application.

**Properties:**
- `strDescription` (string): Description of the launch option (may be a localization string).

---

### Playtime

```typescript
interface Playtime {
    nPlaytimeLastTwoWeeks: number;
    nPlaytimeForever: number;
    rtLastTimePlayed: number;
}
```

Represents playtime information for an application.

**Properties:**
- `nPlaytimeLastTwoWeeks` (number): Total playtime in minutes for the last 2 weeks.
- `nPlaytimeForever` (number): Total playtime in minutes.
- `rtLastTimePlayed` (number): Last played time in Unix Epoch time format.

---

### PrePurchaseApp

```typescript
interface PrePurchaseApp {
    nAppID: number;
    eState: EAppReleaseState;
}
```

Represents a pre-purchased application.

---

### PrePurchaseInfo

```typescript
interface PrePurchaseInfo {
    apps: PrePurchaseApp[];
    lastChangeNumber: number;
}
```

Contains information about pre-purchased applications.

---

### EAppReleaseState

```typescript
enum EAppReleaseState {
    Unknown,
    Unavailable,
    Prerelease,
    PreloadOnly,
    Released,
    Disabled,
}
```

Enum representing application release states.

---

### EAppLaunchOptionType

```typescript
enum EAppLaunchOptionType {
    None,
    Default,
    SafeMode,
    Multiplayer,
    Config,
    OpenVR,
    Server,
    Editor,
    Manual,
    Benchmark,
    Option1,
    Option2,
    Option3,
    OculusVR,
    OpenVROverlay,
    OSVR,
    OpenXR,
    Dialog = 1000,
}
```

Enum representing different types of launch options.

---

### SoundtrackDetails

```typescript
interface SoundtrackDetails {
    tracks: SoundtrackTrack[];
    metadata: SoundtrackMetadata;
    vecAdditionalImageAssetURLs: string[];
    strCoverImageAssetURL: string;
}
```

Details about a soundtrack.

---

### SoundtrackTrack

```typescript
interface SoundtrackTrack {
    discNumber: number;
    trackNumber: number;
    durationSeconds: number;
    trackDisplayName: string;
}
```

Represents a single soundtrack track.

---

### SoundtrackMetadata

```typescript
interface SoundtrackMetadata {
    artist: string;
}
```

Metadata for a soundtrack.

---

### StoreTagLocalization

```typescript
interface StoreTagLocalization {
    tag: number;
    string: string;
}
```

Represents a localized store tag.

---

### EWorkshopFileType

```typescript
enum EWorkshopFileType {
    Invalid = -1,
    Community,
    Microtransaction,
    Collection,
    Art,
    Video,
    Screenshot,
    Game,
    Software,
    Concept,
    WebGuide,
    IntegratedGuide,
    Merch,
    ControllerBinding,
    SteamworksAccessInvite,
    SteamVideo,
    GameManagedItem,
    Max,
}
```

Enum representing workshop file types.

---

### EndUserLicenseAgreement

```typescript
interface EndUserLicenseAgreement {
    id: string;
    url: string;
    version: number;
}
```

Represents an End User License Agreement.

---

### AppBackupStatus

```typescript
interface AppBackupStatus {
    appid: number;
    eError: EAppUpdateError;
    strBytesToProcess: string;
    strBytesProcessed: string;
    strTotalBytesWritten: string;
}
```

Status information for app backup operations.

---

### EAppUpdateError

```typescript
enum EAppUpdateError {
    None,
    Unspecified,
    Paused,
    Canceled,
    Suspended,
    NoSubscription,
    NoConnection,
    Timeout,
    MissingKey,
    MissingConfig,
    DiskReadFailure,
    DiskWriteFailure,
    NotEnoughDiskSpace,
    CorruptGameFiles,
    WaitingForNextDisk,
    InvalidInstallPath,
    AppRunning,
    DependencyFailure,
    NotInstalled,
    UpdateRequired,
    Busy,
    NoDownloadSources,
    InvalidAppConfig,
    InvalidDepotConfig,
    MissingManifest,
    NotReleased,
    RegionRestricted,
    CorruptDepotCache,
    MissingExecutable,
    InvalidPlatform,
    InvalidFileSystem,
    CorruptUpdateFiles,
    DownloadDisabled,
    SharedLibraryLocked,
    PendingLicense,
    OtherSessionPlaying,
    CorruptDownload,
    CorruptDisk,
    FilePermissions,
    FileLocked,
    MissingContent,
    Requires64BitOS,
    MissingUpdateFiles,
    NotEnoughDiskQuota,
    LockedSiteLicense,
    ParentalControlBlocked,
    CreateProcessFailure,
    SteamClientOutdated,
    PlaytimeExceeded,
    CorruptFileSignature,
    MissingInstalledFiles,
    CompatibilityToolFailure,
    UnmountedUninstallPath,
    InvalidBackupPath,
    InvalidPasscode,
    ThirdPartyUpdater,
    ParentalPlaytimeExceeded,
    Max,
}
```

Enum representing various app update errors.

---

### ESteamInputController

```typescript
enum ESteamInputController {
    PlayStation = 1 << 0,
    Xbox = 1 << 1,
    Generic = 1 << 2,
    NintendoSwitch = 1 << 3,
}
```

Enum representing Steam Input controller types.

---

### AppPlatform_t

```typescript
type AppPlatform_t = 'windows' | 'osx' | 'linux'
```

Type representing application platforms.

---

### AppDetails

```typescript
interface AppDetails {
    achievements: AppAchievements;
    bAvailableContentOnStore: boolean;
    bCanMoveInstallFolder: boolean;
    bCloudAvailable: boolean;
    bCloudEnabledForAccount: boolean;
    bCloudEnabledForApp: boolean;
    bCloudSyncOnSuspendAvailable: boolean;
    bCloudSyncOnSuspendEnabled: boolean;
    bCommunityMarketPresence: boolean;
    bEnableAllowDesktopConfiguration: boolean;
    bFreeRemovableLicense: boolean;
    bHasAllLegacyCDKeys: boolean;
    bHasAnyLocalContent: boolean;
    bHasLockedPrivateBetas: boolean;
    bIsExcludedFromSharing: boolean;
    bIsSubscribedTo: boolean;
    bIsThirdPartyUpdater: boolean;
    bOverlayEnabled: boolean;
    bOverrideInternalResolution: boolean;
    bRequiresLegacyCDKey: boolean;
    bShortcutIsVR: boolean;
    bShowCDKeyInMenus: boolean;
    bShowControllerConfig: boolean;
    bSupportsCDKeyCopyToClipboard: boolean;
    bVRGameTheatreEnabled: boolean;
    bWorkshopVisible: boolean;
    deckDerivedProperties?: AppDeckDerivedProperties;
    eAppOwnershipFlags: number;
    eAutoUpdateValue: EAppAutoUpdateBehavior;
    eBackgroundDownloads: EAppAllowDownloadsWhileRunningBehavior;
    eCloudStatus: EAppCloudStatus;
    eCloudSync: number;
    eControllerRumblePreference: EControllerRumbleSetting;
    eDisplayStatus: EDisplayStatus;
    eEnableThirdPartyControllerConfiguration: EThirdPartyControllerConfiguration;
    eSteamInputControllerMask: number;
    iInstallFolder: number;
    lDiskSpaceRequiredBytes: number;
    lDiskUsageBytes: number;
    lDlcUsageBytes: number;
    nBuildID: number;
    nCompatToolPriority: number;
    nPlaytimeForever: number;
    nScreenshots: number;
    rtLastTimePlayed: number;
    rtLastUpdated: number;
    rtPurchased: number;
    selectedLanguage: AppLanguage;
    strCloudBytesAvailable: string;
    strCloudBytesUsed: string;
    strCompatToolDisplayName: string;
    strCompatToolName: string;
    strDeveloperName: string;
    strDeveloperURL: string;
    strDisplayName: string;
    strExternalSubscriptionURL: string;
    strFlatpakAppID: string;
    strHomepageURL: string;
    strLaunchOptions: string;
    strManualURL: string;
    strOwnerSteamID: string;
    strResolutionOverride: string;
    strSelectedBeta: string;
    strShortcutExe: string;
    strShortcutLaunchOptions: string;
    strShortcutStartDir: string;
    strSteamDeckBlogURL: string;
    unAppID: number;
    unEntitledContentApp: number;
    unTimedTrialSecondsAllowed: number;
    unTimedTrialSecondsPlayed: number;
    vecBetas: AppBeta[];
    vecChildConfigApps: number[];
    vecDLC: AppDLC[];
    vecDeckCompatTestResults: DeckCompatTestResult[];
    vecLanguages: AppLanguage[];
    vecLegacyCDKeys: LegacyCDKey[];
    vecMusicAlbums: AppSoundtrack[];
    vecPlatforms: AppPlatform_t[];
    vecScreenShots: Screenshot[];
    libraryAssets?: AppLibraryAsset;
}
```

Comprehensive details about an application.

**Properties:**
- `bAvailableContentOnStore` (boolean): Indicates whether the application is available on the store.
- `bCommunityMarketPresence` (boolean): Indicates whether the application has community market available.
- `eAppOwnershipFlags` (number): See `EAppOwnershipFlags`.
- `eSteamInputControllerMask` (number): See `ESteamInputController`.
- `iInstallFolder` (number): Index of the install folder. -1 if not installed.
- `lDiskSpaceRequiredBytes` (number): Disk space required for installation, in bytes.
- `lDiskUsageBytes` (number): Application disk space usage, in bytes.
- `lDlcUsageBytes` (number): DLC disk space usage, in bytes.
- `nPlaytimeForever` (number): Total play time, in minutes.
- `nScreenshots` (number): Screenshot count.
- `strOwnerSteamID` (string): Steam64 ID.

---

### AppAssociation

```typescript
interface AppAssociation {
    strName: string;
    strURL: string;
}
```

Represents an app association (developer, publisher, franchise).

---

### AppAssociations

```typescript
interface AppAssociations {
    rgDevelopers: AppAssociation[];
    rgFranchises: AppAssociation[];
    rgPublishers: AppAssociation[];
}
```

Contains app associations.

---

### BadgeCard

```typescript
interface BadgeCard {
    nOwned: number;
    strArtworkURL: string;
    strImgURL: string;
    strMarketHash: string;
    strName: string;
    strTitle: string;
}
```

Represents a badge card.

---

### Badge

```typescript
interface Badge {
    bMaxed: VDFBoolean_t;
    dtNextRetry: number | null;
    nLevel: number;
    nMaxLevel: number;
    nNextLevelXP: number;
    nXP: number;
    rgCards: BadgeCard[];
    strIconURL: string;
    strName: string;
    strNextLevelName: string;
}
```

Represents a Steam badge.

---

### AppDescription

```typescript
interface AppDescription {
    strFullDescription: string;
    strSnippet: string;
}
```

Application description.

**Properties:**
- `strFullDescription` (string): Full app description. Note that it uses BB code and so must be rendered.
- `strSnippet` (string): Short game description.

---

### CachedAppDetailMap

```typescript
interface CachedAppDetailMap {
    achievementmap: string;
    achievements: AppAchievements;
    associations: AppAssociations;
    badge: Badge;
    descriptions: AppDescription;
    gameactivity: any[];
    usernews: string[];
    workshop_trendy_items: any;
}
```

Map of cached app detail types.

**Properties:**
- `achievementmap` (string): Stringified JSON data of achievements.
- `usernews` (string[]): Each string is a base64 encoded binary data.

---

### CachedAppDetails

```typescript
type CachedAppDetails = {
    [K in keyof CachedAppDetailMap]: {
        version: number;
        data: CachedAppDetailMap[K];
    };
}
```

Type representing cached app details with versioning.

---

### AppDeckDerivedProperties

```typescript
interface AppDeckDerivedProperties {
    gamescope_frame_limiter_not_supported?: boolean;
    non_deck_display_glyphs: boolean;
    primary_player_is_controller_slot_0: boolean;
    requires_h264: boolean;
    requires_internet_for_setup: boolean;
    requires_internet_for_singleplayer: boolean;
    requires_manual_keyboard_invoke: false;
    requires_non_controller_launcher_nav: false;
    small_text: boolean;
    supported_input: number;
}
```

Steam Deck-specific derived properties for an application.

---

### EAppOwnershipFlags

```typescript
enum EAppOwnershipFlags {
    None,
    Subscribed = 1 << 0,
    Free = 1 << 1,
    RegionRestricted = 1 << 2,
    LowViolence = 1 << 3,
    InvalidPlatform = 1 << 4,
    Borrowed = 1 << 5,
    FreeWeekend = 1 << 6,
    Retail = 1 << 7,
    Locked = 1 << 8,
    Pending = 1 << 9,
    Expired = 1 << 10,
    Permanent = 1 << 11,
    Recurring = 1 << 12,
    Canceled = 1 << 13,
    AutoGrant = 1 << 14,
    PendingGift = 1 << 15,
    RentalNotActivated = 1 << 16,
    Rental = 1 << 17,
    SiteLicense = 1 << 18,
    LegacyFreeSub = 1 << 19,
    InvalidOSType = 1 << 20,
    TimedTrial = 1 << 21,
}
```

Enum representing app ownership flags.

---

### EAppAutoUpdateBehavior

```typescript
enum EAppAutoUpdateBehavior {
    Always,
    Launch,
    HighPriority,
}
```

Enum representing automatic update behaviors.

---

### EAppAllowDownloadsWhileRunningBehavior

```typescript
enum EAppAllowDownloadsWhileRunningBehavior {
    UseGlobal,
    AlwaysAllow,
    NeverAllow,
}
```

Enum representing background download behaviors.

---

### EDisplayStatus

```typescript
enum EDisplayStatus {
    Invalid,
    Launching,
    Uninstalling,
    Installing,
    Running,
    Validating,
    Updating,
    Downloading,
    Synchronizing,
    ReadyToInstall,
    ReadyToPreload,
    ReadyToLaunch,
    RegionRestricted,
    PresaleOnly,
    InvalidPlatform,
    PreloadComplete = 16,
    BorrowerLocked,
    UpdatePaused,
    UpdateQueued,
    UpdateRequired,
    UpdateDisabled,
    DownloadPaused,
    DownloadQueued,
    DownloadRequired,
    DownloadDisabled,
    LicensePending,
    LicenseExpired,
    AvailForFree,
    AvailToBorrow,
    AvailGuestPass,
    Purchase,
    Unavailable,
    NotLaunchable,
    CloudError,
    CloudOutOfDate,
    Terminating,
    OwnerLocked,
    DownloadFailed,
    UpdateFailed,
}
```

Enum representing application display status.

---

### ESteamDeckCompatibilityTestResult

```typescript
enum ESteamDeckCompatibilityTestResult {
    Invalid,
    NotApplicable,
    Pass,
    Fail,
    FailMinor,
}
```

Enum representing Steam Deck compatibility test results.

---

### AppLanguage

```typescript
interface AppLanguage {
    strDisplayName: string;
    strShortName: string;
}
```

Represents a language option for an application.

**Properties:**
- `strShortName` (string): A localization string for the language.

---

### LegacyCDKey

```typescript
interface LegacyCDKey {
    eResult: EResult;
    strKey: string;
    strName: string;
}
```

Represents a legacy CD key.

---

### AppBeta

```typescript
interface AppBeta {
    strName: string;
    strDescription: string;
}
```

Represents a beta branch for an application.

**Properties:**
- `strName` (string): Beta name.
- `strDescription` (string): Beta description.

---

### AppDLC

```typescript
interface AppDLC {
    bAvailableOnStore: boolean;
    bEnabled: boolean;
    lDiskUsageBytes: number;
    rtPurchaseDate: number;
    rtStoreAssetModifyType: number;
    strHeaderFilename: string;
    strName: string;
    strState: string;
    unAppID: number;
}
```

Represents downloadable content for an application.

**Properties:**
- `bAvailableOnStore` (boolean): Is the DLC available on the store?
- `lDiskUsageBytes` (number): Disk usage, in bytes.
- `rtPurchaseDate` (number): Purchase date.
- `strHeaderFilename` (string): Store header image filename.
- `strName` (string): Display name.
- `strState` (string): State (installed/notinstalled).
- `unAppID` (number): App ID.

---

### DeckCompatTestResult

```typescript
interface DeckCompatTestResult {
    test_result: ESteamDeckCompatibilityTestResult;
    test_loc_token: string;
}
```

Represents a Steam Deck compatibility test result.

**Properties:**
- `test_loc_token` (string): A localization string.

---

### AppSoundtrack

```typescript
interface AppSoundtrack {
    rtPurchaseDate: number;
    rtStoreAssetModifyType: number;
    strName: string;
    strState: string;
    unAppID: number;
}
```

Represents a soundtrack associated with an application.

**Properties:**
- `rtPurchaseDate` (number): Purchase date.
- `strName` (string): Display name.
- `strState` (string): State (installed/notinstalled).
- `unAppID` (number): App ID.

---

### AppLibraryAsset

```typescript
interface AppLibraryAsset {
    logoPosition?: LogoPosition;
    strCapsuleImage: string;
    strHeroBlurImage: string;
    strHeroImage: string;
    strLogoImage: string;
}
```

Represents library assets for an application.

---

### LogoPosition

```typescript
interface LogoPosition {
    pinnedPosition: LogoPinPosition_t;
    nWidthPct: number;
    nHeightPct: number;
}
```

Represents the position of a logo in library assets.

---

### LogoPinPosition_t

```typescript
type LogoPinPosition_t = 'BottomLeft' | 'UpperLeft' | 'CenterCenter' | 'UpperCenter' | 'BottomCenter'
```

Type representing logo pin positions.

---

### ELaunchSource

```typescript
enum ELaunchSource {
    None,
    _2ftLibraryDetails = 100,
    _2ftLibraryListView,
    _2ftLibraryGrid,
    InstallSubComplete,
    DownloadsPage,
    RemoteClientStartStreaming,
    _2ftMiniModeList,
    _10ft = 200,
    DashAppLaunchCmdLine = 300,
    DashGameIdLaunchCmdLine,
    RunByGameDir,
    SubCmdRunDashGame,
    SteamURL_Launch = 400,
    SteamURL_Run,
    SteamURL_JoinLobby,
    SteamURL_RunGame,
    SteamURL_RunGameIdOrJumplist,
    SteamURL_RunSafe,
    TrayIcon = 500,
    LibraryLeftColumnContextMenu = 600,
    LibraryLeftColumnDoubleClick,
    Dota2Launcher = 700,
    IRunGameEngine = 800,
    DRMFailureResponse,
    DRMDataRequest,
    CloudFilePanel,
    DiscoveredAlreadyRunning,
    GameActionJoinParty = 900,
    AppPortraitContextMenu = 1000,
}
```

Enum representing different launch sources.

---

### NonSteamApp

```typescript
interface NonSteamApp {
    bIsApplication: boolean;
    strAppName: string;
    strExePath: string;
    strArguments: string;
    strCmdline: string;
    strIconDataBase64: string | undefined;
}
```

Represents a non-Steam application found on the system.

---

### Shortcut

```typescript
interface Shortcut extends NonSteamApp {
    strShortcutPath: string | undefined;
    strSortAs: string | undefined;
}
```

Represents a shortcut (extends NonSteamApp).

---

### LogoPositionForApp

```typescript
interface LogoPositionForApp {
    nVersion: number;
    logoPosition: LogoPosition;
}
```

Represents custom logo position data for an application.

**Properties:**
- `nVersion` (number): Usually 1.

---

### CLibraryBootstrapData

```typescript
interface CLibraryBootstrapData extends JsPbMessage {
    app_data(): AppBootstrapData[];
    add_app_data(param0: any, param1: any): any;
    set_app_data(param0: any): any;
}
```

ProtoBuf message for library bootstrap data.

---

### AppBootstrapData

```typescript
interface AppBootstrapData {
    appid: number;
    hidden: boolean;
    user_tag: string[];
}
```

Bootstrap data for an application.

---

### CAppOverview_Change

```typescript
interface CAppOverview_Change extends JsPbMessage {
    app_overview(): SteamAppOverview[];
    full_update(): boolean;
    removed_appid(): number[];
    update_complete(): boolean;
    add_app_overview(param0: any, param1: any): any;
    add_removed_appid(param0: any, param1: any): any;
    set_app_overview(param0: any): any;
    set_full_update(param0: any): any;
    set_removed_appid(param0: any): any;
    set_update_complete(param0: any): any;
}
```

ProtoBuf message for app overview changes.

---

### ECloudPendingRemoteOperation

```typescript
enum ECloudPendingRemoteOperation {
    None,
    AppSessionActive,
    UploadInProgress,
    UploadPending,
    AppSessionSuspended,
}
```

Enum representing pending cloud remote operations.

---

### CCloud_PendingRemoteOperation

```typescript
interface CCloud_PendingRemoteOperation {
    operation(): ECloudPendingRemoteOperation;
    machine_name(): string;
    client_id(): number;
    time_last_updated(): number;
    os_type(): number;
    device_type(): number;
}
```

Represents a pending cloud remote operation.

---

### CMsgCloudPendingRemoteOperations

```typescript
interface CMsgCloudPendingRemoteOperations extends JsPbMessage {
    operations: CCloud_PendingRemoteOperation[];
}
```

ProtoBuf message containing cloud pending remote operations.

---

### SteamAppOverview

```typescript
interface SteamAppOverview {
    appid: number;
    display_name: string;
    visible_in_game_list: boolean;
    sort_as: string;
    app_type: EAppType;
    mru_index: number | undefined;
    rt_recent_activity_time: number;
    minutes_playtime_forever: number;
    minutes_playtime_last_two_weeks: number;
    rt_last_time_played_or_installed: number;
    rt_last_time_played: number;
    store_tag?: number[];
    association: SteamAppOverviewAssociation[];
    store_category?: number[];
    rt_original_release_date: number;
    rt_steam_release_date: number;
    icon_hash: string;
    controller_support?: EAppControllerSupportLevel;
    vr_supported?: boolean;
    metacritic_score: number;
    size_on_disk?: number;
    third_party_mod?: boolean;
    icon_data?: string;
    icon_data_format?: string;
    gameid: string;
    library_capsule_filename?: string;
    per_client_data: SteamAppOverviewRemoteClientData[];
    most_available_clientid: string;
    selected_clientid?: string;
    rt_store_asset_mtime: number;
    rt_custom_image_mtime?: number;
    optional_parent_app_id?: number;
    owner_account_id?: number;
    review_score_with_bombs: number;
    review_percentage_with_bombs: number;
    review_score_without_bombs: number;
    review_percentage_without_bombs: number;
    library_id?: string;
    vr_only?: boolean;
    mastersub_appid?: number;
    mastersub_includedwith_logo?: string;
    site_license_site_name?: string;
    shortcut_override_appid?: number;
    steam_deck_compat_category: ESteamDeckCompatibilityCategory;
    rt_last_time_locally_played?: number;
    rt_purchased_time: number;
    header_filename?: string;
    local_cache_version?: number;
    ps4_controller_support?: EAppControllerSupportLevel;
    ps5_controller_support?: EAppControllerSupportLevel;
    gamepad_preferred?: boolean;
    canonicalAppType: number;
    local_per_client_data: SteamAppOverviewRemoteClientData;
    most_available_per_client_data: SteamAppOverviewRemoteClientData;
    selected_per_client_data: SteamAppOverviewRemoteClientData;
}
```

Comprehensive overview of a Steam application.

**Remarks:** Appears to be all optional fields.

---

### EAppType

```typescript
enum EAppType {
    DepotOnly = -2147483648,
    Invalid = 0,
    Game = 1 << 0,
    Application = 1 << 1,
    Tool = 1 << 2,
    Demo = 1 << 3,
    Deprecated = 1 << 4,
    DLC = 1 << 5,
    Guide = 1 << 6,
    Driver = 1 << 7,
    Config = 1 << 8,
    Hardware = 1 << 9,
    Franchise = 1 << 10,
    Video = 1 << 11,
    Plugin = 1 << 12,
    MusicAlbum = 1 << 13,
    Series = 1 << 14,
    Comic = 1 << 15,
    Beta = 1 << 16,
    Shortcut = 1073741824,
}
```

Enum representing application types. Possible bitmask values, but typically used as an enum.

---

### SteamAppOverviewAssociation

```typescript
interface SteamAppOverviewAssociation {
    type: EAppAssociationType;
    name: string;
}
```

Represents an association in app overview.

---

### EAppAssociationType

```typescript
enum EAppAssociationType {
    Invalid,
    Publisher,
    Developer,
    Franchise,
}
```

Enum representing app association types.

---

### EAppControllerSupportLevel

```typescript
enum EAppControllerSupportLevel {
    None,
    Partial,
    Full,
}
```

Enum representing controller support levels.

---

### SteamAppOverviewRemoteClientData

```typescript
interface SteamAppOverviewRemoteClientData {
    clientid: string;
    client_name: string;
    display_status: EDisplayStatus;
    status_percentage: number;
    active_beta?: string;
    installed?: boolean;
    bytes_downloaded: string;
    bytes_total: string;
    streaming_to_local_client?: boolean;
    is_available_on_current_platform: boolean;
    is_invalid_os_type?: boolean;
    playtime_left?: number;
    cloud_status: EAppCloudStatus;
}
```

Represents remote client data in app overview.

---

### ESteamDeckCompatibilityCategory

```typescript
enum ESteamDeckCompatibilityCategory {
    Unknown,
    Unsupported,
    Playable,
    Verified,
}
```

Enum representing Steam Deck compatibility categories.

---

### EAppCloudStatus

```typescript
enum EAppCloudStatus {
    Invalid,
    Disabled,
    Unknown,
    Synchronized,
    Checking,
    OutOfSync,
    Uploading,
    Downloading,
    SyncFailed,
    Conflict,
    PendingElsewhere,
}
```

Enum representing app cloud synchronization status.

---

### ERaiseGameWindowResult

```typescript
enum ERaiseGameWindowResult {
    NotRunning = 1,
    Success,
    Failure,
}
```

Enum representing results from raising a game window.

---

## Notes

1. **Type Safety**: Many methods use string types for app IDs. Some methods accept `number` while others accept `string`. Be sure to use the correct type as specified in each method signature.

2. **Promises**: Most data retrieval methods return Promises. Always handle potential rejections appropriately.

3. **Callbacks**: Several `RegisterFor*` methods return `Unregisterable` objects. Be sure to call the unregister method when you no longer need the callback to prevent memory leaks.

4. **ProtoBuf Messages**: Some methods return `ArrayBuffer` data that needs to be deserialized using appropriate ProtoBuf message definitions (e.g., `CLibraryBootstrapData`, `CMsgCloudPendingRemoteOperations`, `CAppOverview_Change`).

5. **Steam IDs**: Steam64 IDs are represented as strings in this API to prevent precision loss with JavaScript numbers.

6. **VDF Files**: Some methods modify VDF (Valve Data Format) configuration files directly. These operations typically don't require admin privileges but do modify Steam's configuration.

7. **Platform-Specific**: Some functionality (like `ScanForInstalledNonSteamApps`, `InstallFlatpakAppAndCreateShortcut`) is platform-specific and may behave differently or not be available on all operating systems.

8. **Non-Steam Apps**: Non-Steam application shortcuts are assigned special app IDs in the range that distinguishes them from regular Steam applications.

9. **Workshop Items**: Workshop item IDs are represented as strings (published file IDs) rather than numbers.

10. **Enums**: Many enums use bitwise flags. Check the specific enum to determine if values can be combined or if they're mutually exclusive.

11. **Typos**: Some property names contain typos from the original Valve implementation (e.g., `nSecondsRemaing` in `GameAction`). These are preserved to match the actual API.

12. **Compatibility Tools**: On Linux, compatibility tools like Proton can be configured per-application using the `SpecifyCompatTool` and related methods.
