# Downloads

## Overview

The Downloads module provides a comprehensive interface for managing Steam downloads, including game installations, updates, and DLC. It offers control over download queues, bandwidth throttling, and real-time monitoring of download progress.

This module allows applications to programmatically manage the Steam download system, including pausing/resuming downloads, reordering the download queue, and receiving notifications when download states change.

## Interface

### Downloads

The main interface for interacting with Steam's download management system.

## Methods

### EnableAllDownloads

```typescript
EnableAllDownloads(enable: boolean): void
```

Enables or disables all downloads in Steam.

This is equivalent to toggling the "Pause All Downloads" option in the Steam client.

**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `enable` | `boolean` | `true` to enable downloads, `false` to disable. |

**Returns:** `void`

---

### MoveAppUpdateDown

```typescript
MoveAppUpdateDown(appId: number): void
```

Moves the update for a specific app down the download queue.

This decreases the priority of the app's download by moving it one position down in the queue.

**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `appId` | `number` | The ID of the application to move. |

**Returns:** `void`

---

### MoveAppUpdateUp

```typescript
MoveAppUpdateUp(appId: number): void
```

Moves the update for a specific app up the download queue.

This increases the priority of the app's download by moving it one position up in the queue.

**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `appId` | `number` | The ID of the application to move. |

**Returns:** `void`

---

### PauseAppUpdate

```typescript
PauseAppUpdate(appId: number): void
```

Pauses the update for a specific app.

**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `appId` | `number` | The ID of the application to pause. |

**Returns:** `void`

**Note:** This method may be broken. It seems to be removing the app from the download list like `RemoveFromDownloadList` instead of actually pausing it.

---

### QueueAppUpdate

```typescript
QueueAppUpdate(appId: number): void
```

Adds the update for a specific app to the download queue.

This schedules an app for download if it's not already in the queue.

**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `appId` | `number` | The ID of the application to queue. |

**Returns:** `void`

---

### RegisterForDownloadItems

```typescript
RegisterForDownloadItems(
    callback: (isDownloading: boolean, downloadItems: DownloadItem[]) => void
): Unregisterable
```

Registers a callback function to be called when download items change.

This provides real-time updates about the state of individual downloads in the queue.

**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `callback` | `(isDownloading: boolean, downloadItems: DownloadItem[]) => void` | The callback function to be called when download items change. The callback receives two parameters: `isDownloading` (whether any download is currently active) and `downloadItems` (array of current download items). |

**Returns:** `Unregisterable` - An object with an `unregister()` method that can be used to remove the callback.

---

### RegisterForDownloadOverview

```typescript
RegisterForDownloadOverview(callback: (overview: DownloadOverview) => void): Unregisterable
```

Registers a callback function to be called when download overview changes.

This provides high-level information about the current download state, including bandwidth usage and overall progress.

**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `callback` | `(overview: DownloadOverview) => void` | The callback function to be called when the download overview changes. |

**Returns:** `Unregisterable` - An object with an `unregister()` method that can be used to remove the callback.

---

### RemoveFromDownloadList

```typescript
RemoveFromDownloadList(appId: number): void
```

Removes the update for a specific app from the download list and places it in the unscheduled list.

This removes the app from the active download queue but doesn't cancel the update entirely. The update can be re-queued later with `QueueAppUpdate`.

**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `appId` | `number` | The ID of the application to remove. |

**Returns:** `void`

---

### ResumeAppUpdate

```typescript
ResumeAppUpdate(appId: number): void
```

Resumes the update for a specific app in the queue.

This resumes a paused download for the specified app.

**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `appId` | `number` | The ID of the application to resume. |

**Returns:** `void`

---

### SetLaunchOnUpdateComplete

```typescript
SetLaunchOnUpdateComplete(appId: number): void
```

Sets an app to launch when its download is complete.

This configures Steam to automatically launch the game once its update or installation finishes.

**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `appId` | `number` | The ID of the application to set. |

**Returns:** `void`

---

### SetQueueIndex

```typescript
SetQueueIndex(appId: number, index: number): void
```

Sets the queue index for an app in the download queue.

This allows direct manipulation of an app's position in the download queue.

**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `appId` | `number` | The ID of the application to set the index for. |
| `index` | `number` | The index to set. Index of 0 is the current download in progress. |

**Returns:** `void`

**Remarks:** Index of 0 is the current download in progress. Lower indices have higher priority.

---

### SuspendDownloadThrottling

```typescript
SuspendDownloadThrottling(suspend: boolean): void
```

Suspends or resumes download throttling.

This temporarily disables bandwidth limits configured in Steam settings, allowing downloads to use maximum available bandwidth.

**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `suspend` | `boolean` | `true` to suspend download throttling (use maximum bandwidth), `false` to resume normal throttling. |

**Returns:** `void`

---

### SuspendLanPeerContent

```typescript
SuspendLanPeerContent(suspend: boolean): void
```

Suspends or resumes local transfers.

This controls whether Steam can download from other Steam clients on the local network (LAN) instead of from Steam servers.

**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `suspend` | `boolean` | `true` to suspend local transfers, `false` to resume. |

**Returns:** `void`

## Types and Interfaces

### DownloadItem

Represents a single item in the download queue.

```typescript
interface DownloadItem {
    /** True if this app is currently downloading */
    active: boolean;
    
    /** Appid of app */
    appid: number;
    
    /** Current build ID for the installed app, zero if the app isn't installed yet */
    buildid: number;
    
    /** True if this update has been completed */
    completed: boolean;
    
    /** For completed downloads, time of completion, 0 if not completed */
    completed_time: number;
    
    deferred_time: number;
    
    /** Bytes already downloaded, sum across all content types */
    downloaded_bytes: number;
    
    /** If true, game will launch when its download completes successfully */
    launch_on_completion: boolean;
    
    /** True if this app has been paused by the user or the system */
    paused: boolean;
    
    /** Queue index, -1 if the item is unqueued */
    queue_index: number;
    
    /** Build ID that this download is moving towards. This can be the same as buildid. */
    target_buildid: number;
    
    /** Total bytes to download, sum across all content types */
    total_bytes: number;
    
    /**
     * Update error description, when paused and there has been an error.
     * Unlocalized and shouldn't be displayed to the user.
     */
    update_error: string;
    
    update_result: EAppUpdateError;
    
    update_type_info: UpdateTypeInfo[];
}
```

---

### DownloadOverview

Provides a high-level overview of the current download state.

```typescript
interface DownloadOverview {
    /** Set if we are downloading from LAN peer content server */
    lan_peer_hostname: string;
    
    /** True if all downloads are paused */
    paused: boolean;
    
    /** True if download throttling has been temporarily suspended for the current download */
    throttling_suspended: boolean;
    
    /** Appid of currently updating app */
    update_appid: number;
    
    /** Bytes already downloaded */
    update_bytes_downloaded: number;
    
    /** Bytes already processed in current phase - resets to zero when update stage changes */
    update_bytes_processed: number;
    
    /** Bytes already staged */
    update_bytes_staged: number;
    
    /** Total bytes to download */
    update_bytes_to_download: number;
    
    /** Total bytes to process in current phase - resets to zero when update stage changes */
    update_bytes_to_process: number;
    
    /** Total bytes to be staged */
    update_bytes_to_stage: number;
    
    /** Current disk throughput estimate */
    update_disc_bytes_per_second: number;
    
    /** True if the current update is an initial install */
    update_is_install: boolean;
    
    /** True if download and staging sizes are prefetch estimates */
    update_is_prefetch_estimate: boolean;
    
    /** True if the current update is for shader update */
    update_is_shader: boolean;
    
    /** True if the client is running in peer content server mode serving other peers */
    update_is_upload: boolean;
    
    /** True if the current update is for workshop content */
    update_is_workshop: boolean;
    
    /** Current bandwidth estimate for download */
    update_network_bytes_per_second: number;
    
    /** Peak bandwidth estimate for download */
    update_peak_network_bytes_per_second: number;
    
    /** Estimate of remaining time (in seconds) until download completes (not including staging) */
    update_seconds_remaining: number;
    
    /** Time current update started */
    update_start_time: number;
    
    update_state: 'None' | 'Starting' | 'Updating' | 'Stopping';
}
```

---

### UpdateTypeInfo

Provides information about different content types in a download (e.g., base game, DLC, workshop content).

```typescript
interface UpdateTypeInfo {
    /** True if this content type had an update and it has completed */
    completed_update: boolean;
    
    /** Bytes already downloaded for this content type */
    downloaded_bytes: number;
    
    /** True if this content type has or had an update */
    has_update: boolean;
    
    /** Total bytes to download for this content type */
    total_bytes: number;
}
```

---

### EAppUpdateError

An enum type imported from the `App` module that represents error codes for app updates.

## Usage Example

```typescript
// Access the Downloads interface through SteamClient
const downloads = SteamClient.Downloads;

// Enable all downloads
downloads.EnableAllDownloads(true);

// Queue an app for download
downloads.QueueAppUpdate(1234567);

// Register for download progress updates
const unregister = downloads.RegisterForDownloadOverview((overview) => {
    console.log(`Downloading: ${overview.update_appid}`);
    console.log(`Progress: ${overview.update_bytes_downloaded} / ${overview.update_bytes_to_download}`);
    console.log(`Speed: ${overview.update_network_bytes_per_second} bytes/sec`);
    console.log(`Time remaining: ${overview.update_seconds_remaining} seconds`);
});

// Register for download items updates
const unregisterItems = downloads.RegisterForDownloadItems((isDownloading, items) => {
    console.log(`Currently downloading: ${isDownloading}`);
    items.forEach(item => {
        console.log(`App ${item.appid}: ${item.downloaded_bytes}/${item.total_bytes} bytes`);
    });
});

// Move an app to the top of the queue
downloads.SetQueueIndex(1234567, 0);

// Set app to launch when complete
downloads.SetLaunchOnUpdateComplete(1234567);

// Later: cleanup
unregister.unregister();
unregisterItems.unregister();
```

## Notes

- Most methods operate synchronously and return `void`
- The download queue is 0-indexed, where 0 is the currently downloading app
- Registering callbacks returns an `Unregisterable` object - always call `unregister()` when done to prevent memory leaks
- Download progress is tracked in bytes - use the overview data to calculate percentages and speeds
- The `PauseAppUpdate` method may have unexpected behavior - consider using `RemoveFromDownloadList` instead
- Build IDs uniquely identify specific versions of games and are used internally by Steam
