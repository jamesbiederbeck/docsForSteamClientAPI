# System

## Overview

The `System` interface provides comprehensive access to system-level operations and hardware management on the Steam Deck and Steam Client. This module includes sub-modules for audio, bluetooth, display, networking, performance monitoring, and various system utilities.

## Sub-Modules

The System module provides access to several specialized sub-modules:

- **Audio**: Audio device and application management
- **AudioDevice**: Individual audio device controls
- **Bluetooth**: Bluetooth device pairing and management
- **Devkit**: Development kit utilities
- **Display**: Display configuration and management
- **DisplayManager**: Multi-display management
- **Dock**: Steam Deck dock detection and management
- **Network**: Network connectivity and configuration (includes Network.Device sub-module)
- **Perf**: Performance monitoring and statistics
- **Report**: System diagnostics and reporting
- **UI**: System UI interactions

## Methods

### CopyFile

```typescript
CopyFile(target: string, destination: string): Promise<boolean>
```

Copies a file from one location to another.

**Parameters:**
- `target` - Source file path
- `destination` - Destination file path

**Returns:** `Promise<boolean>` - True if the operation succeeded

---

### CopyFilesToClipboard

```typescript
CopyFilesToClipboard(paths: string[]): void
```

Copies specified files to the system clipboard. Does not throw if files are not found.

**Parameters:**
- `paths` - Array of file paths to copy to clipboard

---

### CreateTempPath

```typescript
CreateTempPath(path: string): Promise<string>
```

Creates a temporary folder at the specified path.

**Parameters:**
- `path` - The folder path to create

**Returns:** `Promise<string>` - The created path

**Note:** The behavior with relative paths may vary.

---

### ExitFakeCaptivePortal

```typescript
ExitFakeCaptivePortal(): any
```

Exits the fake captive portal mode.

---

### FactoryReset

```typescript
FactoryReset(): any
```

Performs a factory reset of the system.

---

### FormatStorage

```typescript
FormatStorage(force: boolean): any
```

Formats the storage device.

**Parameters:**
- `force` - Whether to force the formatting operation

---

### GetOSType

```typescript
GetOSType(): Promise<EOSType>
```

Retrieves the operating system type.

**Returns:** `Promise<EOSType>` - The OS type enumeration value

---

### GetSystemInfo

```typescript
GetSystemInfo(): Promise<SystemInfo>
```

Retrieves comprehensive system information including hardware and software details.

**Returns:** `Promise<SystemInfo>` - Detailed system information

---

### IsDeckFactoryImage

```typescript
IsDeckFactoryImage(): Promise<boolean>
```

Checks if the system is running a Steam Deck factory image.

**Returns:** `Promise<boolean>` - True if running factory image

---

### IsSteamInTournamentMode

```typescript
IsSteamInTournamentMode(): Promise<boolean>
```

Checks if Steam is currently in tournament mode.

**Returns:** `Promise<boolean>` - True if in tournament mode

---

### MoveFile

```typescript
MoveFile(target: string, destination: string): void
```

Moves a file or folder from one location to another. Does not throw on error.

**Parameters:**
- `target` - Target file or folder path
- `destination` - Destination path

---

### NotifyGameOverlayStateChanged

```typescript
NotifyGameOverlayStateChanged(latestAppOverlayStateActive: boolean, appId: number): any
```

Notifies the system of a game overlay state change.

**Parameters:**
- `latestAppOverlayStateActive` - Whether the overlay is active
- `appId` - The application ID

---

### OpenFileDialog

```typescript
OpenFileDialog(prefs: FileDialog): Promise<string | OperationResponse>
```

Opens a file selection dialog.

**Parameters:**
- `prefs` - Dialog preferences including filters, title, and initial selection

**Returns:** `Promise<string | OperationResponse>` - The selected file name, or throws OperationResponse if cancelled

---

### OpenInSystemBrowser

```typescript
OpenInSystemBrowser(url: string): void
```

Opens a URL in the system's default web browser.

**Parameters:**
- `url` - The URL to open

---

### OpenLocalDirectoryInSystemExplorer

```typescript
OpenLocalDirectoryInSystemExplorer(directory: string): void
```

Opens a local directory in the system file explorer.

**Parameters:**
- `directory` - The directory path to open

---

### RebootToAlternateSystemPartition

```typescript
RebootToAlternateSystemPartition(): any
```

Reboots the system to an alternate system partition.

---

### RebootToFactoryTestImage

```typescript
RebootToFactoryTestImage(param0: any): any
```

Reboots to the factory test image.

---

### RegisterForAirplaneModeChanges

```typescript
RegisterForAirplaneModeChanges(callback: (state: AirplaneModeState) => void): Unregisterable
```

Registers a callback for airplane mode state changes.

**Parameters:**
- `callback` - Function called when airplane mode state changes

**Returns:** `Unregisterable` - Object to unregister the callback

---

### RegisterForBatteryStateChanges

```typescript
RegisterForBatteryStateChanges(callback: (state: BatteryState) => void): Unregisterable
```

Registers a callback for battery state changes.

**Parameters:**
- `callback` - Function called when battery state changes

**Returns:** `Unregisterable` - Object to unregister the callback

---

### RegisterForFormatStorageProgress

```typescript
RegisterForFormatStorageProgress(callback: (progress: FormatStorageProgress) => void): Unregisterable
```

Registers a callback for storage formatting progress updates.

**Parameters:**
- `callback` - Function called with formatting progress

**Returns:** `Unregisterable` - Object to unregister the callback

---

### RegisterForOnResumeFromSuspend

```typescript
RegisterForOnResumeFromSuspend(callback: () => void): Unregisterable
```

Registers a callback for when the system resumes from suspend.

**Parameters:**
- `callback` - Function called on resume from suspend

**Returns:** `Unregisterable` - Object to unregister the callback

---

### RegisterForOnSuspendRequest

```typescript
RegisterForOnSuspendRequest(callback: () => void): Unregisterable
```

Registers a callback for when the system is about to suspend.

**Parameters:**
- `callback` - Function called on suspend request

**Returns:** `Unregisterable` - Object to unregister the callback

---

### RegisterForSettingsChanges

```typescript
RegisterForSettingsChanges(callback: (data: ArrayBuffer) => void): Unregisterable
```

Registers a callback for system settings changes. The data is a ProtoBuf message that deserializes to `CMsgSystemManagerSettings`.

**Parameters:**
- `callback` - Function called with settings data

**Returns:** `Unregisterable` - Object to unregister the callback

---

### RestartPC

```typescript
RestartPC(): any
```

Restarts the system.

---

### SetAirplaneMode

```typescript
SetAirplaneMode(value: boolean): void
```

Enables or disables airplane mode.

**Parameters:**
- `value` - True to enable, false to disable

---

### ShutdownPC

```typescript
ShutdownPC(): any
```

Shuts down the system.

---

### SteamRuntimeSystemInfo

```typescript
SteamRuntimeSystemInfo(): Promise<string>
```

Retrieves Steam Runtime system information.

**Returns:** `Promise<string>` - Steam runtime information

---

### SuspendPC

```typescript
SuspendPC(): any
```

Suspends the system.

---

### SwitchToDesktop

```typescript
SwitchToDesktop(): any
```

Switches to desktop mode.

---

### VideoRecordingDriverCheck

```typescript
VideoRecordingDriverCheck(): any
```

Checks video recording driver compatibility.

---

## Types and Interfaces

### SystemInfo

```typescript
interface SystemInfo {
    sOSName: string;
    sKernelVersion: string;
    sBIOSVersion: string;
    sHostname: string;
    sOSCodename: string;
    sOSVariantId: string;
    sOSVersionId: string;
    sOSBuildId: string;
    nSteamVersion: number;
    sSteamBuildDate: string;
    sSteamAPI: string;
    sCPUVendor: string;
    sCPUName: string;
    nCPUHz: number;
    nCPUPhysicalCores: number;
    nCPULogicalCores: number;
    nSystemRAMSizeMB: number;
    sVideoCardName: string;
    sVideoDriverVersion: string;
    nVideoRAMSizeMB: number;
    bIsUnsupportedPrototypeHardware: boolean;
}
```

Comprehensive system information including OS, hardware, and Steam client details.

---

### BatteryState

```typescript
interface BatteryState {
    bHasBattery: boolean;
    eACState: EACState;
    eBatteryState: EBatteryState;
    flLevel: number; // Battery percentage (0-1)
    nSecondsRemaining: number; // Time remaining in seconds
    bShutdownRequested: boolean;
}
```

Current battery status information.

---

### AirplaneModeState

```typescript
interface AirplaneModeState {
    bEnabled: boolean;
}
```

Current airplane mode status.

---

### FormatStorageProgress

```typescript
interface FormatStorageProgress {
    flProgress: number;
    rtEstimatedCompletionTime: number;
    eStage: EStorageFormatStage;
}
```

Progress information for storage formatting operations.

---

### FileDialog

```typescript
interface FileDialog {
    bChooseDirectory?: boolean;
    rgFilters?: FileDialogFilter[];
    strInitialFile?: string;
    strTitle?: string;
}
```

Configuration for file selection dialogs.

**Properties:**
- `bChooseDirectory` - Whether to choose a directory instead of a file
- `rgFilters` - Array of file filters to apply
- `strInitialFile` - Initially selected file
- `strTitle` - Dialog window title

---

### FileDialogFilter

```typescript
interface FileDialogFilter {
    strFileTypeName: string;
    rFilePatterns: string[];
    bUseAsDefault?: boolean;
}
```

File filter configuration for dialogs.

**Example:**
```typescript
{
    strFileTypeName: "Executable Files",
    rFilePatterns: ["*.application", "*.exe", "*.sh", "*.AppImage"],
    bUseAsDefault: true
}
```

---

### CMsgSystemManagerSettings

Protocol Buffer message interface for system settings with methods for accessing various display, power, and system configuration options including:
- Display brightness, color management, night mode
- Fan control settings
- Idle timeout and suspend settings
- WiFi power save options

---

## Enumerations

### EOSType

Operating system type enumeration with values for:
- Windows variants (Win7, Win8, Win10, Win11, etc.)
- macOS versions (10.4 through 15)
- Linux kernel versions
- Mobile platforms (iOS, Android)
- Other platforms (PS3, Web)

---

### EACState

```typescript
enum EACState {
    Unknown,
    Disconnected,
    Connected,
    ConnectedSlow
}
```

AC power connection state.

---

### EBatteryState

```typescript
enum EBatteryState {
    Unknown,
    Discharging,
    Charging,
    Full
}
```

Battery charging state.

---

### EStorageFormatStage

```typescript
enum EStorageFormatStage {
    Invalid,
    NotRunning,
    Starting,
    Testing,
    Rescuing,
    Formatting,
    Finalizing
}
```

Storage formatting operation stages.

---

## Example Usage

### Get System Information

```typescript
const systemInfo = await SteamClient.System.GetSystemInfo();
console.log(`OS: ${systemInfo.sOSName}`);
console.log(`CPU: ${systemInfo.sCPUName}`);
console.log(`RAM: ${systemInfo.nSystemRAMSizeMB} MB`);
console.log(`GPU: ${systemInfo.sVideoCardName}`);
```

### Monitor Battery State

```typescript
const unregister = SteamClient.System.RegisterForBatteryStateChanges((state) => {
    console.log(`Battery: ${(state.flLevel * 100).toFixed(0)}%`);
    console.log(`AC: ${state.eACState === EACState.Connected}`);
    console.log(`State: ${EBatteryState[state.eBatteryState]}`);
});

// Later: unregister.unregister();
```

### Open File Dialog

```typescript
try {
    const filename = await SteamClient.System.OpenFileDialog({
        strTitle: "Select a file",
        rgFilters: [
            {
                strFileTypeName: "Images",
                rFilePatterns: ["*.png", "*.jpg", "*.jpeg"],
                bUseAsDefault: true
            },
            {
                strFileTypeName: "All Files",
                rFilePatterns: ["*"]
            }
        ]
    });
    console.log(`Selected: ${filename}`);
} catch (error) {
    console.log("File selection cancelled");
}
```

### Copy Files to Clipboard

```typescript
SteamClient.System.CopyFilesToClipboard([
    "/path/to/file1.txt",
    "/path/to/file2.txt"
]);
```

### Audio Device Management

```typescript
const devices = await SteamClient.System.Audio.GetDevices();
console.log("Audio devices:", devices);

// Register for device changes
const unregister = SteamClient.System.Audio.RegisterForDeviceAdded((device) => {
    console.log("New audio device:", device);
});
```

### Network Management

```typescript
// Get network connectivity status
const unregister = SteamClient.System.Network.RegisterForConnectivityTestChanges((test) => {
    console.log("Connection status:", test.eConnectivityTestResult);
});

// Enable/disable WiFi
await SteamClient.System.Network.SetWifiEnabled(true);
```

### Bluetooth Management

```typescript
// Register for Bluetooth state changes
const unregister = SteamClient.System.Bluetooth.RegisterForStateChanges((state) => {
    console.log("Bluetooth devices:", state.vecDevices);
});

// Connect to a device
await SteamClient.System.Bluetooth.Connect(adapterId, deviceId);
```

---

## Related Modules

- [Audio](./Audio.md) - Detailed audio device management
- [Input](./Input.md) - Controller and input device management
- [Settings](./Settings.md) - Steam client configuration
- [Window](./Window.md) - Window management and display
