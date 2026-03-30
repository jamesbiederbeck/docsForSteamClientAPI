# Cloud

## Overview

The Cloud module provides an interface for managing Steam Cloud synchronization functionality. It allows applications to handle cloud save conflicts and retry failed synchronization operations for games and applications.

Steam Cloud is Steam's cloud storage service that automatically stores game saves and configuration files, enabling users to access their data across multiple devices.

## Interface

### Cloud

The main interface for interacting with Steam Cloud functionality.

## Methods

### ResolveAppSyncConflict

```typescript
ResolveAppSyncConflict(appId: number, keepLocal: boolean): void
```

Resolves a synchronization conflict for an app in the cloud.

When a game has both local and cloud save data that conflicts (typically when the game has been played on multiple devices without syncing), this method allows you to choose which version to keep.

**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `appId` | `number` | The ID of the app with the sync conflict. |
| `keepLocal` | `boolean` | Whether to keep the local version during conflict resolution. If `true`, the local version will be kept and uploaded to the cloud. If `false`, the cloud version will be downloaded and replace the local version. |

**Returns:** `void`

---

### RetryAppSync

```typescript
RetryAppSync(appId: number): void
```

Retries syncing an app with the cloud.

This method is useful when a previous sync operation has failed and you want to attempt synchronization again.

**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `appId` | `number` | The ID of the app to retry syncing. |

**Returns:** `void`

## Usage Example

```typescript
// Access the Cloud interface through SteamClient
const cloud = SteamClient.Cloud;

// Resolve a sync conflict by keeping the local version
cloud.ResolveAppSyncConflict(1234567, true);

// Retry syncing an app that failed to sync
cloud.RetryAppSync(1234567);
```

## Notes

- The Cloud interface operates synchronously (methods return `void`)
- Conflict resolution is permanent - the chosen version will overwrite the other
- App IDs can be found in the Steam store URL or through other Steam Client API methods
- These methods do not provide feedback on success or failure through return values
