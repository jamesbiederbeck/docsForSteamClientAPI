# OpenVR

## Overview

The OpenVR module provides interfaces for interacting with VR (Virtual Reality) functionality in the Steam client. It includes support for VR device management, keyboard input, overlay management, notifications, and various VR-related events. This module allows applications to integrate with SteamVR and access VR hardware capabilities.

## Interface: OpenVR

The main interface for interacting with Steam's OpenVR functionality.

### Properties

#### Device

```typescript
Device: VRDevice
```

Access to VR device-related functionality.

---

#### DeviceProperties

```typescript
DeviceProperties: DeviceProperties
```

Interface for getting and setting VR device properties.

---

#### Keyboard

```typescript
Keyboard: Keyboard
```

Interface for controlling the VR keyboard.

---

#### PathProperties

```typescript
PathProperties: PathProperties
```

Interface for managing VR path properties.

---

#### VRNotifications

```typescript
VRNotifications: VRNotifications
```

Interface for managing VR notifications.

---

#### VROverlay

```typescript
VROverlay: VROverlay
```

Interface for managing VR overlays and dashboard.

---

#### RegisterForButtonPress

```typescript
RegisterForButtonPress: Unregisterable
```

Property for registering button press events.

---

#### RegisterForInstallDialog

```typescript
RegisterForInstallDialog: Unregisterable
```

Property for registering VR installation dialog events.

---

#### SetOverlayInteractionAffordance

```typescript
SetOverlayInteractionAffordance: any
```

Property for setting overlay interaction affordance.

---

#### StartVR

```typescript
StartVR: any
```

Property for starting VR.

---

#### TriggerOverlayHapticEffect

```typescript
TriggerOverlayHapticEffect: any
```

Property for triggering haptic effects in VR overlays.

---

### Methods

#### GetMutualCapabilities

```typescript
GetMutualCapabilities(): Promise<any>
```

Retrieves mutual VR capabilities.

**Parameters:**
- None

**Returns:**
- `Promise<any>`: A promise that resolves with the mutual capabilities.

**Throws:**
- `OperationResponse` if mutual capabilities haven't been loaded.

---

#### GetWebSecret

```typescript
GetWebSecret(): Promise<string>
```

Retrieves the VR web secret.

**Parameters:**
- None

**Returns:**
- `Promise<string>`: A promise that resolves with the web secret string.

---

#### InstallVR

```typescript
InstallVR(): any
```

Initiates VR installation.

**Parameters:**
- None

**Returns:**
- `any`

---

#### QuitAllVR

```typescript
QuitAllVR(): any
```

Quits all VR applications and sessions.

**Parameters:**
- None

**Returns:**
- `any`

---

#### RegisterForHMDActivityLevelChanged

```typescript
RegisterForHMDActivityLevelChanged(callback: (m_eHMDActivityLevel: EHMDActivityLevel) => void): Unregisterable
```

Registers a callback for HMD (Head-Mounted Display) activity level changes.

**Parameters:**
- `callback` (`(m_eHMDActivityLevel: EHMDActivityLevel) => void`): The callback function called when HMD activity level changes.

**Returns:**
- `Unregisterable`: An object that can be used to unregister the callback.

---

#### RegisterForStartupErrors

```typescript
RegisterForStartupErrors(callback: (clientError: any, initError: any, initErrorString: string) => void): Unregisterable
```

Registers a callback for VR startup errors.

**Parameters:**
- `callback` (`(clientError: any, initError: any, initErrorString: string) => void`): The callback function called when startup errors occur. Receives client error, init error, and error string.

**Returns:**
- `Unregisterable`: An object that can be used to unregister the callback.

---

#### RegisterForVRHardwareDetected

```typescript
RegisterForVRHardwareDetected(callback: (m_bHMDPresent: any, m_bHMDHardwareDetected: any, m_strHMDName: any) => void): Unregisterable
```

Registers a callback for VR hardware detection events.

**Parameters:**
- `callback` (`(m_bHMDPresent: any, m_bHMDHardwareDetected: any, m_strHMDName: any) => void`): The callback function called when VR hardware is detected. Receives HMD presence status, hardware detected status, and HMD name.

**Returns:**
- `Unregisterable`: An object that can be used to unregister the callback.

---

#### RegisterForVRModeChange

```typescript
RegisterForVRModeChange(callback: (m_bIsVRRunning: boolean) => void): Unregisterable
```

Registers a callback for VR mode changes.

**Parameters:**
- `callback` (`(m_bIsVRRunning: boolean) => void`): The callback function called when VR mode changes. Receives a boolean indicating whether VR is running.

**Returns:**
- `Unregisterable`: An object that can be used to unregister the callback.

---

#### RegisterForVRSceneAppChange

```typescript
RegisterForVRSceneAppChange(callback: (param0: number) => void): Unregisterable
```

Registers a callback for VR scene application changes.

**Parameters:**
- `callback` (`(param0: number) => void`): The callback function called when the VR scene app changes.

**Returns:**
- `Unregisterable`: An object that can be used to unregister the callback.

---

## Sub-Interfaces

### VRDevice

Interface for VR device connectivity and status.

```typescript
interface VRDevice {
    BIsConnected: any;
    RegisterForDeviceConnectivityChange: Unregisterable;
    RegisterForVRDeviceSeenRecently(callback: (m_bVRDeviceSeenRecently: any) => void): Unregisterable;
}
```

**Properties:**
- `BIsConnected`: Property to check if a VR device is connected.
- `RegisterForDeviceConnectivityChange`: Property for registering device connectivity changes.

**Methods:**
- `RegisterForVRDeviceSeenRecently`: Registers a callback for when a VR device is seen recently.

---

### DeviceProperties

Interface for managing VR device properties.

```typescript
interface DeviceProperties {
    GetBoolDeviceProperty: any;
    GetDoubleDeviceProperty: any;
    GetFloatDeviceProperty: any;
    GetInt32DeviceProperty: any;
    GetStringDeviceProperty: any;
    RegisterForDevicePropertyChange: Unregisterable;
}
```

**Properties:**
- `GetBoolDeviceProperty`: Method to get boolean device properties.
- `GetDoubleDeviceProperty`: Method to get double device properties.
- `GetFloatDeviceProperty`: Method to get float device properties.
- `GetInt32DeviceProperty`: Method to get 32-bit integer device properties.
- `GetStringDeviceProperty`: Method to get string device properties.
- `RegisterForDevicePropertyChange`: Property for registering device property changes.

---

### Keyboard

Interface for controlling the VR keyboard.

```typescript
interface Keyboard {
    Hide(): any;
    RegisterForStatus(callback: (m_bIsKeyboardOpen: boolean, m_eKeyboardFlags: number, m_sInitialKeyboardText: string) => void): Unregisterable;
    SendDone(): any;
    SendText(key: string): any;
    Show(): any;
}
```

**Methods:**

#### Hide

Hides the VR keyboard.

---

#### RegisterForStatus

```typescript
RegisterForStatus(callback: (m_bIsKeyboardOpen: boolean, m_eKeyboardFlags: number, m_sInitialKeyboardText: string) => void): Unregisterable
```

Registers a callback for keyboard status changes.

**Parameters:**
- `callback`: Callback function that receives keyboard open status, keyboard flags (see `EKeyboardFlags`), and initial keyboard text.

**Returns:**
- `Unregisterable`: An object to unregister the callback.

**Note:**
- `EKeyboardFlags` enum can be useful for the `m_eKeyboardFlags` parameter.

---

#### SendDone

Sends a "done" signal to the VR keyboard.

---

#### SendText

```typescript
SendText(key: string): any
```

Sends text input to the VR keyboard.

**Parameters:**
- `key` (`string`): The text to send.

---

#### Show

Shows the VR keyboard.

---

### PathProperties

Interface for managing VR path properties.

```typescript
interface PathProperties {
    GetBoolPathProperty: any;
    GetDoublePathProperty: any;
    GetFloatPathProperty: any;
    GetInt32PathProperty: any;
    GetStringPathProperty: any;
    RegisterForPathPropertyChange: any;
    SetBoolPathProperty: any;
    SetDoublePathProperty: any;
    SetFloatPathProperty: any;
    SetInt32PathProperty: any;
    SetStringPathProperty: any;
}
```

**Properties:**
- `GetBoolPathProperty`: Method to get boolean path properties.
- `GetDoublePathProperty`: Method to get double path properties.
- `GetFloatPathProperty`: Method to get float path properties.
- `GetInt32PathProperty`: Method to get 32-bit integer path properties.
- `GetStringPathProperty`: Method to get string path properties.
- `RegisterForPathPropertyChange`: Method to register for path property changes.
- `SetBoolPathProperty`: Method to set boolean path properties.
- `SetDoublePathProperty`: Method to set double path properties.
- `SetFloatPathProperty`: Method to set float path properties.
- `SetInt32PathProperty`: Method to set 32-bit integer path properties.
- `SetStringPathProperty`: Method to set string path properties.

---

### VRNotifications

Interface for managing VR notifications.

```typescript
interface VRNotifications {
    HideCustomNotification: any;
    RegisterForNotificationEvent: Unregisterable;
    ShowCustomNotification: any;
}
```

**Properties:**
- `HideCustomNotification`: Method to hide custom VR notifications.
- `RegisterForNotificationEvent`: Property for registering notification events.
- `ShowCustomNotification`: Method to show custom VR notifications.

---

### VROverlay

Interface for managing VR overlays and the SteamVR dashboard.

```typescript
interface VROverlay {
    HideDashboard: any;
    IsDashboardVisible(): Promise<boolean>;
    RegisterForButtonPress: Unregisterable;
    RegisterForCursorMovement: Unregisterable;
    RegisterForThumbnailChanged: Unregisterable;
    RegisterForVisibilityChanged: Unregisterable;
    ShowDashboard: any;
    SwitchToDashboardOverlay(param0: string): void;
}
```

**Properties:**
- `HideDashboard`: Method to hide the VR dashboard.
- `RegisterForButtonPress`: Property for registering button press events on overlays.
- `RegisterForCursorMovement`: Property for registering cursor movement events.
- `RegisterForThumbnailChanged`: Property for registering thumbnail change events.
- `RegisterForVisibilityChanged`: Property for registering visibility change events.
- `ShowDashboard`: Method to show the VR dashboard.

**Methods:**

#### IsDashboardVisible

```typescript
IsDashboardVisible(): Promise<boolean>
```

Checks if the VR dashboard is currently visible.

**Returns:**
- `Promise<boolean>`: A promise that resolves with `true` if the dashboard is visible, `false` otherwise.

---

#### SwitchToDashboardOverlay

```typescript
SwitchToDashboardOverlay(param0: string): void
```

Switches to a specific dashboard overlay.

**Parameters:**
- `param0` (`string`): The identifier of the overlay to switch to.

**Returns:**
- `void`

---

## Enums

### EHMDActivityLevel

Represents the activity level of the Head-Mounted Display (HMD).

```typescript
enum EHMDActivityLevel {
    Unknown = -1,
    Idle,
    UserInteraction,
    UserInteraction_Timeout,
    Standby,
    Idle_Timeout,
}
```

**Values:**
- `Unknown` (-1): Activity level is unknown.
- `Idle` (0): HMD is idle.
- `UserInteraction` (1): User is actively interacting with the HMD.
- `UserInteraction_Timeout` (2): User interaction has timed out.
- `Standby` (3): HMD is in standby mode.
- `Idle_Timeout` (4): HMD idle state has timed out.

---

### EKeyboardFlags

Flags for configuring the VR keyboard behavior.

```typescript
enum EKeyboardFlags {
    Minimal = 1 << 0,
    Modal = 1 << 1,
    ShowArrowKeys = 1 << 2,
    HideDoneKey = 1 << 3,
}
```

**Values:**
- `Minimal` (1): Minimal keyboard layout.
- `Modal` (2): Keyboard is displayed as a modal.
- `ShowArrowKeys` (4): Show arrow keys on the keyboard.
- `HideDoneKey` (8): Hide the "done" key on the keyboard.

---

## Notes

- The `Unregisterable` type is imported from the shared module and provides a mechanism to unregister callbacks.
- Many properties in this module are typed as `any`, indicating that their specific types may not be fully documented or may vary.
- The OpenVR module provides comprehensive access to VR hardware and software features through the Steam client.
- Always unregister callbacks when they are no longer needed to prevent memory leaks.
- Error handling is important when working with VR operations, as hardware may not always be available or properly configured.
