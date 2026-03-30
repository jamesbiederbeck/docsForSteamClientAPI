# Input

## Overview

The `Input` module provides comprehensive functionality for managing input devices and controllers in the Steam client. This interface offers extensive control over Steam Input, including controller configuration, keyboard emulation, haptic feedback, gyroscope calibration, and input state monitoring. It supports a wide range of controller types including Steam Controllers, Xbox controllers, PlayStation controllers, Nintendo Switch controllers, and more.

## Methods

This module contains over 100 methods for controller management. Key categories include:

- **Calibration**: IMU, joystick, and trackpad calibration methods
- **Configuration Management**: Loading, saving, and editing controller configurations
- **Keyboard Emulation**: Send keyboard input from controllers
- **Haptic Feedback**: Trigger haptic events with various parameters
- **Event Registration**: Register callbacks for controller state changes, input messages, and more
- **Personalization**: Customize controller settings (deadzones, haptics, LED colors, etc.)
- **Cloud Sync**: Synchronize controller configurations with Steam Cloud

For detailed method signatures and parameters, please refer to the TypeScript source file.

## Key Features

### Controller Types Supported

The Input module supports a wide variety of controllers:
- Steam Controller (Gordon and Headcrab)
- Steam Deck (Neptune)
- Xbox 360, Xbox One, Xbox Elite
- PlayStation 3, 4, 5 (including DualSense and Edge)
- Nintendo Switch Pro Controller, Joy-Cons
- Generic controllers
- Keyboard and Mouse

### Keyboard Emulation

Controllers can emulate keyboard input using `EHIDKeyboardKey` enum values:

```typescript
// Example: Send Ctrl+V (paste)
SteamClient.Input.ControllerKeyboardSetKeyState(EHIDKeyboardKey.LControl, true);
SteamClient.Input.ControllerKeyboardSetKeyState(EHIDKeyboardKey.V, true);
SteamClient.Input.ControllerKeyboardSetKeyState(EHIDKeyboardKey.V, false);
SteamClient.Input.ControllerKeyboardSetKeyState(EHIDKeyboardKey.LControl, false);
```

### State Monitoring

Register for real-time controller state updates:

```typescript
SteamClient.Input.RegisterForControllerStateChanges((changes) => {
    changes.forEach(change => {
        console.log('Controller:', change.unControllerIndex);
        console.log('Buttons:', change.ulButtons);
        console.log('Left Stick:', change.sLeftStickX, change.sLeftStickY);
        console.log('Gyro:', change.flSoftwareGyroDegreesPerSecondPitch);
    });
});
```

## Enums

### EHIDKeyboardKey

Complete keyboard key enumeration for emulation (0-115 values including A-Z, 0-9, F1-F12, modifiers, and special keys).

### EControllerType

Enumeration of all supported controller types (-1 to 800):
- Steam Controllers: 0-4
- Gaming Controllers: 30-48
- Input Devices: 400 (Keyboard), 800 (Mouse)

### ControllerInputGamepadButton

Gamepad button enumeration (0-50) covering all standard and Steam-specific buttons.

### EControllerRumbleSetting

- `ControllerPreference` (0): Use controller's default
- `Off` (1): Disable rumble
- `On` (2): Enable rumble

### EControllerConfigExportType

Configuration source types (0-6): Unknown, PersonalLocal, PersonalCloud, Community, Template, Official, OfficialDefault

### EThirdPartyControllerConfiguration

Third-party controller support settings (0-2): Off, DefaultSetting, On

## Key Interfaces

### ControllerStateChange

Comprehensive state structure containing:
- Button states (bitmasks for `ulButtons` and `ulUpperButtons`)
- Analog inputs (sticks, pads, triggers)
- Motion data (gyroscope, accelerometer, quaternions)
- Battery level and pressure sensors
- Hardware timing information

### ControllerInfo

Complete controller information:
- Hardware details (vendor ID, product ID, serial number)
- Configuration (deadzones, haptic strength, LED settings)
- Account associations
- Capabilities and features

### GameKeyboardMessage

In-game keyboard request information for text input prompts.

### TouchMenuMessage

Touch menu state and configuration.

## Important Notes

- Many configuration methods use protobuf serialization (base64 encoded binary data)
- Controller indices start at 0
- Button states use bitmasks - check specific bit positions for individual buttons
- Gyroscope data is available on Steam Controllers, Steam Deck, and modern PlayStation/Nintendo controllers
- Personal configurations can be stored locally or synced to Steam Cloud
- Always unregister callbacks when no longer needed to prevent memory leaks

## Related Documentation

For complete method signatures, parameters, and return types, please refer to:
- Source TypeScript file: `Input.ts`
- Steam Input API documentation
- Controller configuration examples in the Steam client source
