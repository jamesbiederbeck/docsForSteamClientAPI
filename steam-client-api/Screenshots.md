# Screenshots

## Overview

The Screenshots module provides comprehensive functionality for managing local screenshots in the Steam client. It allows you to retrieve, delete, upload, and view screenshots, as well as query screenshot metadata and storage usage. This module is essential for applications that need to interact with Steam's screenshot management system.

## Interface: Screenshots

The main interface for managing screenshots in the Steam client.

### Methods

#### DeleteLocalScreenshot

```typescript
DeleteLocalScreenshot(appId: string, screenshotIndex: number): Promise<boolean>
```

Deletes a single local screenshot.

**Parameters:**
- `appId` (`string`): The ID of the application.
- `screenshotIndex` (`number`): The index of the local screenshot.

**Returns:**
- `Promise<boolean>`: A promise that resolves with `true` if the deletion was successful, `false` otherwise.

---

#### DeleteLocalScreenshots

```typescript
DeleteLocalScreenshots(screenshots: ScreenshotToDelete[]): Promise<ScreenshotDeletionResponse>
```

Deletes multiple local screenshots in a batch operation.

**Parameters:**
- `screenshots` (`ScreenshotToDelete[]`): An array of screenshots to delete, grouped by game.

**Returns:**
- `Promise<ScreenshotDeletionResponse>`: A promise that resolves with the deletion response containing success status and failed indices.

---

#### GetAllAppsLocalScreenshots

```typescript
GetAllAppsLocalScreenshots(): Promise<Screenshot[]>
```

Retrieves all local screenshots for all applications.

**Parameters:**
- None

**Returns:**
- `Promise<Screenshot[]>`: A promise that resolves with an array of all Screenshot objects across all applications.

---

#### GetAllAppsLocalScreenshotsCount

```typescript
GetAllAppsLocalScreenshotsCount(): Promise<number>
```

Retrieves the total count of all local screenshots across all applications.

**Parameters:**
- None

**Returns:**
- `Promise<number>`: A promise that resolves with the total count of local screenshots.

---

#### GetAllAppsLocalScreenshotsRange

```typescript
GetAllAppsLocalScreenshotsRange(start: number, end: number): Promise<Screenshot[]>
```

Retrieves a range of local screenshots for all applications.

**Parameters:**
- `start` (`number`): The starting index of the screenshot range (inclusive).
- `end` (`number`): The ending index of the screenshot range (inclusive).

**Returns:**
- `Promise<Screenshot[]>`: A promise that resolves with an array of Screenshot objects within the specified range.

---

#### GetAllLocalScreenshots

```typescript
GetAllLocalScreenshots(): Promise<Screenshot[]>
```

Retrieves all local screenshots.

**Parameters:**
- None

**Returns:**
- `Promise<Screenshot[]>`: A promise that resolves with an array of all Screenshot objects.

---

#### GetGameWithLocalScreenshots

```typescript
GetGameWithLocalScreenshots(screenshotIndex: number): Promise<number>
```

Retrieves the game associated with a specific local screenshot index.

**Parameters:**
- `screenshotIndex` (`number`): The index of the local screenshot.

**Returns:**
- `Promise<number>`: A promise that resolves with the App ID of the game associated with the screenshot.

---

#### GetLastScreenshotTaken

```typescript
GetLastScreenshotTaken(): Promise<Screenshot>
```

Retrieves the most recently taken local screenshot.

**Parameters:**
- None

**Returns:**
- `Promise<Screenshot>`: A promise that resolves with the last taken Screenshot object.

---

#### GetLocalScreenshotByHandle

```typescript
GetLocalScreenshotByHandle(appId: string, screenshotIndex: number): Promise<Screenshot>
```

Retrieves a specific local screenshot for an application by its handle.

**Parameters:**
- `appId` (`string`): The ID of the application.
- `screenshotIndex` (`number`): The index/handle of the local screenshot.

**Returns:**
- `Promise<Screenshot>`: A promise that resolves with the requested Screenshot object.

---

#### GetLocalScreenshotCount

```typescript
GetLocalScreenshotCount(appId: number): Promise<number>
```

Retrieves the count of local screenshots for a specific application.

**Parameters:**
- `appId` (`number`): The ID of the application.

**Returns:**
- `Promise<number>`: A promise that resolves with the count of local screenshots for the specified application.

---

#### GetLocalScreenshotPath

```typescript
GetLocalScreenshotPath(appId: number, hHandle: number): Promise<string>
```

Retrieves the file system path of a screenshot.

**Parameters:**
- `appId` (`number`): The ID of the application.
- `hHandle` (`number`): The handle of the screenshot.

**Returns:**
- `Promise<string>`: A promise that resolves with the screenshot path, or the screenshot directory if no such handle exists.

---

#### GetNumGamesWithLocalScreenshots

```typescript
GetNumGamesWithLocalScreenshots(): Promise<number>
```

Retrieves the number of games that have local screenshots.

**Parameters:**
- None

**Returns:**
- `Promise<number>`: A promise that resolves with the number of games with local screenshots.

---

#### GetTotalDiskSpaceUsage

```typescript
GetTotalDiskSpaceUsage(path: string): Promise<number>
```

Gets the total disk space used by screenshots in the specified library folder.

**Parameters:**
- `path` (`string`): The library folder path to check.

**Returns:**
- `Promise<number>`: A promise that resolves with the total disk space usage in bytes.

---

#### ShowScreenshotInSystemViewer

```typescript
ShowScreenshotInSystemViewer(appId: string, screenshotIndex: number): void
```

Opens a local screenshot in the system's default image viewer.

**Parameters:**
- `appId` (`string`): The ID of the application.
- `screenshotIndex` (`number`): The index of the local screenshot.

**Returns:**
- `void`

**Remarks:**
- If the screenshot index is invalid, this function opens the screenshots directory for the specified application ID instead.

---

#### ShowScreenshotsOnDisk

```typescript
ShowScreenshotsOnDisk(appId: string): void
```

Opens the file system folder containing local screenshots for a specific application.

**Parameters:**
- `appId` (`string`): The ID of the application.

**Returns:**
- `void`

---

#### UploadLocalScreenshot

```typescript
UploadLocalScreenshot(
    appId: string,
    localScreenshot_hHandle: number,
    filePrivacyState: EUCMFilePrivacyState,
): Promise<boolean>
```

Uploads a local screenshot to Steam Cloud.

**Parameters:**
- `appId` (`string`): The ID of the application.
- `localScreenshot_hHandle` (`number`): The handle of the local screenshot to upload.
- `filePrivacyState` (`EUCMFilePrivacyState`): The privacy state for the uploaded screenshot.

**Returns:**
- `Promise<boolean>`: A promise that resolves with `true` if the upload was successful, `false` otherwise.

---

## Types and Interfaces

### Screenshot

Represents a screenshot with its metadata.

```typescript
interface Screenshot {
    nAppID: number;
    strGameID: string;
    hHandle: number;
    nWidth: number;
    nHeight: number;
    nCreated: number;
    ePrivacy: EUCMFilePrivacyState;
    strCaption: string;
    bSpoilers: boolean;
    strUrl: string;
    bUploaded: boolean;
    ugcHandle: string;
}
```

**Properties:**
- `nAppID` (`number`): The Steam App ID of the game.
- `strGameID` (`string`): The game ID as a string.
- `hHandle` (`number`): The unique handle/identifier for the screenshot.
- `nWidth` (`number`): The width of the screenshot in pixels.
- `nHeight` (`number`): The height of the screenshot in pixels.
- `nCreated` (`number`): The timestamp when the screenshot was created.
- `ePrivacy` (`EUCMFilePrivacyState`): The privacy state of the screenshot.
- `strCaption` (`string`): The caption/description of the screenshot.
- `bSpoilers` (`boolean`): Whether the screenshot contains spoilers.
- `strUrl` (`string`): The URL of the screenshot (if uploaded).
- `bUploaded` (`boolean`): Whether the screenshot has been uploaded to Steam.
- `ugcHandle` (`string`): The User Generated Content handle (if uploaded).

---

### ScreenshotToDelete

Represents a request to delete screenshots for a specific game.

```typescript
interface ScreenshotToDelete {
    gameID: string;
    rgHandles: number[];
}
```

**Properties:**
- `gameID` (`string`): The ID of the game.
- `rgHandles` (`number[]`): An array of screenshot handles to delete.

---

### ScreenshotDeletionResponse

Represents the response from a batch screenshot deletion operation.

```typescript
interface ScreenshotDeletionResponse {
    bSuccess: boolean;
    rgFailedRequestIndices: number[];
}
```

**Properties:**
- `bSuccess` (`boolean`): Whether the overall deletion operation was successful.
- `rgFailedRequestIndices` (`number[]`): An array of indices indicating which deletion requests failed.

---

## Enums

### EUCMFilePrivacyState

Represents the privacy state for User Generated Content files, including screenshots.

```typescript
enum EUCMFilePrivacyState {
    Invalid = -1,
    Private = 1 << 1,
    FriendsOnly = 1 << 2,
    Public = 1 << 3,
    Unlisted = 1 << 4,
}
```

**Values:**
- `Invalid` (-1): Invalid privacy state.
- `Private` (2): The file is private and only visible to the owner.
- `FriendsOnly` (4): The file is visible to friends only.
- `Public` (8): The file is publicly visible to everyone.
- `Unlisted` (16): The file is unlisted (accessible via direct link but not listed publicly).

---

## Notes

- Screenshot indices and handles are used interchangeably in some methods. The handle is typically a unique identifier for a screenshot.
- The `appId` parameter may be either a `string` or `number` depending on the method. Pay attention to the type specified in each method signature.
- When deleting screenshots in batch using `DeleteLocalScreenshots()`, the operation will attempt to delete all specified screenshots and report which ones failed through the `rgFailedRequestIndices` array.
- Privacy states use bitwise flags, allowing for potential combination of states (though typically only one state is used at a time).
- Timestamps in the `Screenshot` interface (such as `nCreated`) are typically Unix timestamps representing seconds since epoch.
- All asynchronous methods return Promises, so proper error handling with `.catch()` or try-catch blocks is recommended.
- The `GetLocalScreenshotPath()` method will return the screenshots directory if an invalid handle is provided, which can be useful for debugging or directory access.
