# UI

## Overview

The UI module provides control over Steam's user interface modes, window management, and UI-related events. It allows switching between Big Picture Mode and Desktop Mode, monitoring UI state changes, and managing Steam windows.

## Methods

### `EnsureMainWindowCreated()`
```typescript
EnsureMainWindowCreated(): void
```
Ensures that the main Steam window is created.

**Returns:** `void`

---

### `ExitBigPictureMode()`
```typescript
ExitBigPictureMode(): void
```
Exits Big Picture Mode and returns to Desktop Mode.

**Returns:** `void`

---

### `GetDesiredSteamUIWindows()`
```typescript
GetDesiredSteamUIWindows(): Promise<SteamWindow[]>
```
Retrieves a list of desired Steam UI windows.

**Returns:** `Promise<SteamWindow[]>` - An array of Steam window objects.

---

### `GetOSEndOfLifeInfo()`
```typescript
GetOSEndOfLifeInfo(): Promise<OSEndOfLifeInfo>
```
Gets information about whether your OS will be unsupported in the future or not.

**Returns:** `Promise<OSEndOfLifeInfo>` - Information about OS end-of-life status.

---

### `GetUIMode()`
```typescript
GetUIMode(): Promise<EUIMode>
```
Retrieves the current UI mode.

**Returns:** `Promise<EUIMode>` - The current UI mode.

---

### `NotifyAppInitialized()`
```typescript
NotifyAppInitialized(): void
```
Notifies that the application has been initialized.

**Returns:** `void`

---

### `RegisterDesiredSteamUIWindowsChanged()`
```typescript
RegisterDesiredSteamUIWindowsChanged(callback: () => void): Unregisterable
```
Registers a callback to be called when the desired Steam UI windows change.

**Parameters:**
- `callback` (`() => void`) - The callback function to be invoked.

**Returns:** `Unregisterable` - An object that can unregister the callback.

---

### `RegisterForClientConVar()`
```typescript
RegisterForClientConVar(convar: string, callback: (value: string) => void): Unregisterable
```
Registers a callback function to be called when a convar's value gets changed.

**⚠️ Warning:** Hard crashes if such a convar does not exist or if you can't set it.

**Parameters:**
- `convar` (`string`) - The ConVar to watch.
- `callback` (`(value: string) => void`) - The callback function to be called with the new value.

**Returns:** `Unregisterable` - An object that can unregister the callback.

---

### `RegisterForErrorCondition()`
```typescript
RegisterForErrorCondition(callback: (param0: number, param1: number) => void): Unregisterable
```
Registers a callback for error conditions.

**Parameters:**
- `callback` (`(param0: number, param1: number) => void`) - The callback function to be called.

**Returns:** `Unregisterable` - An object that can unregister the callback.

**Notes:** Parameters are enums (specific types to be documented).

---

### `RegisterForKioskModeResetSignal()`
```typescript
RegisterForKioskModeResetSignal(callback: () => void): Unregisterable
```
Registers a callback for kiosk mode reset signals.

**Parameters:**
- `callback` (`() => void`) - The callback function to be invoked.

**Returns:** `Unregisterable` - An object that can unregister the callback.

---

### `RegisterForStartupFinished()`
```typescript
RegisterForStartupFinished(callback: () => void): Unregisterable
```
Registers a callback for when startup has finished.

**Parameters:**
- `callback` (`() => void`) - The callback function to be invoked.

**Returns:** `Unregisterable` - An object that can unregister the callback.

**Notes:** This fires multiple times.

---

### `RegisterForUIModeChanged()`
```typescript
RegisterForUIModeChanged(callback: (mode: EUIMode) => void): Unregisterable
```
Registers a callback to be called when the UI mode changes.

**Parameters:**
- `callback` (`(mode: EUIMode) => void`) - The callback function with the new UI mode.

**Returns:** `Unregisterable` - An object that can unregister the callback.

---

### `ResetErrorCondition()`
```typescript
ResetErrorCondition(): void
```
Resets the error condition.

**Returns:** `void`

---

### `SetUIMode()`
```typescript
SetUIMode(mode: EUIMode): void
```
Sets the UI mode to the specified value.

**Parameters:**
- `mode` (`EUIMode`) - The UI mode to set.

**Returns:** `void`

---

## Types and Interfaces

### `EWindowType`
```typescript
enum EWindowType {
    MainGamepadUI,
    OverlayGamepadUI,
    Keyboard,
    ControllerConfigurator,
    VR,
    MainDesktopUI,
    DesktopLogin,
    OverlayDesktopUI,
    SteamChinaReviewLauncher,
}
```
Enumeration of different Steam window types.

---

### `OSEndOfLifeInfo`
```typescript
interface OSEndOfLifeInfo {
    bOSWillBeUnsupported: boolean;
    osType: EOSType;
}
```
Information about OS end-of-life status.

**Properties:**
- `bOSWillBeUnsupported` (`boolean`) - Whether the OS will be unsupported in the future.
- `osType` (`EOSType`) - The type of the operating system.

---

### `SteamWindow`
```typescript
interface SteamWindow {
    appid: number;
    hwndParent: number;
    nBrowserID: number;
    strAppName: string;
    unID: number;
    unPID: number;
    windowType: EWindowType;
    x: number;
    y: number;
}
```
Represents a Steam window with its properties.

**Properties:**
- `appid` (`number`) - Application ID associated with the window.
- `hwndParent` (`number`) - Parent window handle.
- `nBrowserID` (`number`) - Browser ID.
- `strAppName` (`string`) - Application name.
- `unID` (`number`) - Unique ID.
- `unPID` (`number`) - Process ID.
- `windowType` (`EWindowType`) - Type of the window.
- `x` (`number`) - X coordinate of the window.
- `y` (`number`) - Y coordinate of the window.

**Notes:** More correct information may be available at: [SteamTracking Protobufs](https://github.com/SteamDatabase/SteamTracking/blob/master/Protobufs/webuimessages_sharedjscontext.proto)

---

## Notes

- The `EUIMode` type is imported from the `shared` module.
- The `EOSType` type is imported from the `system` module.
- The `Unregisterable` type is imported from the `shared` module and represents an object that can be used to unregister callbacks.
