# Updates

## Overview

The Updates module manages Steam client and operating system updates. It provides functionality to check for updates, apply updates, manage OS branches, and monitor update state changes.

## Methods

### `ApplyUpdates()`
```typescript
ApplyUpdates(base64: string): Promise<OperationResponse>
```
Applies system updates using serialized parameters.

**Parameters:**
- `base64` (`string`) - Serialized base64 message from `CMsgSystemUpdateApplyParams`.

**Returns:** `Promise<OperationResponse>` - Response indicating the operation result.

---

### `CheckForUpdates()`
```typescript
CheckForUpdates(): Promise<OperationResponse>
```
Checks for software updates.

**Returns:** `Promise<OperationResponse>` - Response indicating whether updates are available.

---

### `GetCurrentOSBranch()`
```typescript
GetCurrentOSBranch(): Promise<OSBranch>
```
Retrieves the current operating system branch.

**Returns:** `Promise<OSBranch>` - Information about the current OS branch.

---

### `GetOSBranchList()`
```typescript
GetOSBranchList(): Promise<any[]>
```
Retrieves the list of available OS branches.

**Returns:** `Promise<any[]>` - An array of available OS branches.

---

### `RegisterForUpdateStateChanges()`
```typescript
RegisterForUpdateStateChanges(callback: (data: ArrayBuffer) => void): Unregisterable
```
Registers a callback to be notified when update state changes.

**Parameters:**
- `callback` (`(data: ArrayBuffer) => void`) - The callback function receiving update state data as ArrayBuffer.

**Returns:** `Unregisterable` - An object that can unregister the callback.

**Notes:** If `data` is deserialized, it returns a `MsgSystemUpdateState` ProtoBuf message.

---

### `SelectOSBranch()`
```typescript
SelectOSBranch(base64: string): Promise<OperationResponse>
```
Selects a specific OS branch.

**Parameters:**
- `base64` (`string`) - Serialized base64 message from `CMsgSelectOSBranchParams`.

**Returns:** `Promise<OperationResponse>` - Response indicating the operation result.

---

## Types and Interfaces

### `OSBranch`
```typescript
interface OSBranch {
    eBranch: EOSBranch;
    sRawName: string;
}
```
Represents an operating system branch.

**Properties:**
- `eBranch` (`EOSBranch`) - The branch type (e.g., 1 for Stable).
- `sRawName` (`string`) - The raw name of the branch.

---

### `EOSBranch`
```typescript
enum EOSBranch {
    Unknown,
    Release,
    ReleaseCandidate,
    Beta,
    BetaCandidate,
    Preview,
    PreviewCandidate,
    Main,
    Staging,
}
```
Enumeration of available OS branch types.

**Values:**
- `Unknown` (0)
- `Release` (1)
- `ReleaseCandidate` (2)
- `Beta` (3)
- `BetaCandidate` (4)
- `Preview` (5)
- `PreviewCandidate` (6)
- `Main` (7)
- `Staging` (8)

---

### `MsgSystemUpdateState`
```typescript
interface MsgSystemUpdateState extends JsPbMessage {
    state(): EUpdaterState | undefined;
    progress(): UpdateProgress | undefined;
    supports_os_updates(): boolean | undefined;
    update_apply_results(): UpdateApplyResult[];
    update_check_results(): UpdateCheckResult[];
}
```
Represents the system update state message (CMsgSystemUpdateState).

**Methods:**
- `state()` - Returns the current updater state.
- `progress()` - Returns the update progress information.
- `supports_os_updates()` - Returns whether OS updates are supported.
- `update_apply_results()` - Returns an array of update apply results.
- `update_check_results()` - Returns an array of update check results.

---

### `UpdateApplyResult`
```typescript
interface UpdateApplyResult {
    type: EUpdaterType;
    eresult: EResult;
    requires_client_restart: boolean;
    requires_system_restart: boolean;
}
```
Result of applying an update.

**Properties:**
- `type` (`EUpdaterType`) - The type of updater.
- `eresult` (`EResult`) - The result code.
- `requires_client_restart` (`boolean`) - Whether a client restart is required.
- `requires_system_restart` (`boolean`) - Whether a system restart is required.

---

### `UpdateCheckResult`
```typescript
interface UpdateCheckResult {
    type: EUpdaterType;
    eresult: EResult;
    rtime_checked: number;
    available: boolean;
}
```
Result of checking for updates.

**Properties:**
- `type` (`EUpdaterType`) - The type of updater.
- `eresult` (`EResult`) - The result code.
- `rtime_checked` (`number`) - Timestamp when the check was performed.
- `available` (`boolean`) - Whether an update is available.

---

### `UpdateProgress`
```typescript
interface UpdateProgress {
    stage_progress: number | undefined;
    stage_size_bytes: number | undefined;
    rtime_estimated_completion: number | undefined;
}
```
Progress information for an ongoing update.

**Properties:**
- `stage_progress` (`number | undefined`) - Progress of the current stage.
- `stage_size_bytes` (`number | undefined`) - Size of the current stage in bytes.
- `rtime_estimated_completion` (`number | undefined`) - Estimated completion timestamp.

---

### `EUpdaterState`
```typescript
enum EUpdaterState {
    Invalid,
    UpToDate = 2,
    Checking,
    Available,
    Applying,
    ClientRestartPending,
    SystemRestartPending,
    RollBack,
}
```
Enumeration of updater states.

**Values:**
- `Invalid` (0)
- `UpToDate` (2) - System is up to date
- `Checking` (3) - Checking for updates
- `Available` (4) - Updates are available
- `Applying` (5) - Applying updates
- `ClientRestartPending` (6) - Client restart required
- `SystemRestartPending` (7) - System restart required
- `RollBack` (8) - Rolling back update

---

### `EUpdaterType`
```typescript
enum EUpdaterType {
    Invalid,
    Client,
    OS,
    BIOS,
    Aggregated,
    Test1,
    Test2,
    Dummy,
}
```
Enumeration of updater types.

**Values:**
- `Invalid` (0)
- `Client` (1) - Steam client updates
- `OS` (2) - Operating system updates
- `BIOS` (3) - BIOS/firmware updates
- `Aggregated` (4) - Aggregated updates
- `Test1` (5) - Test updater 1
- `Test2` (6) - Test updater 2
- `Dummy` (7) - Dummy updater

---

## Notes

- `EResult`, `JsPbMessage`, `OperationResponse`, and `Unregisterable` types are imported from the `shared` module.
- ProtoBuf messages are used for serialization of update parameters and state.
- Update state changes can be monitored in real-time using the `RegisterForUpdateStateChanges` method.
