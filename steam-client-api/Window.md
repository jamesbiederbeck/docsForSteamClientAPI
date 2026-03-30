# Window

## Overview

The Window module provides functionality for managing Steam's windows. This includes operations for positioning, resizing, showing/hiding, and controlling window states like fullscreen, maximized, and minimized.

"Restore details" refers to a string similar to `1&x=604&y=257&w=1010&h=600`, which is usable with certain `window.open()` parameters and methods from this module.

**Important:** Methods in this module must be called from the window you want to use (not from SharedJSContext).

## Methods

### BringToFront
```typescript
BringToFront(forceOS?: EWindowBringToFront): void
```
Brings the window to the front.

### Close
```typescript
Close(): void
```
Closes the window.

### DefaultMonitorHasFullscreenWindow
```typescript
DefaultMonitorHasFullscreenWindow(): Promise<boolean>
```
Gets the window's fullscreen state.

### FlashWindow
```typescript
FlashWindow(): void
```
Flashes the window in the taskbar.

### GetDefaultMonitorDimensions
```typescript
GetDefaultMonitorDimensions(): Promise<MonitorDimensions>
```
Gets the default monitor's dimensions.

### GetMousePositionDetails
```typescript
GetMousePositionDetails(): Promise<string>
```
Gets the mouse position's restore details.

### GetWindowDetails
```typescript
GetWindowDetails(): Promise<WindowDetails>
```
Gets the window's details.

### GetWindowDimensions
```typescript
GetWindowDimensions(): Promise<WindowDimensions>
```
Gets the window's dimensions.

### GetWindowRestoreDetails
```typescript
GetWindowRestoreDetails(): Promise<string>
```
Gets the window's restore details.

### HideWindow
```typescript
HideWindow(): void
```
Hides the window.

### IsWindowMaximized
```typescript
IsWindowMaximized(): Promise<boolean>
```
Gets the window's maximized state.

### IsWindowMinimized
```typescript
IsWindowMinimized(): Promise<boolean>
```
Gets the window's minimized state.

### MoveTo
```typescript
MoveTo(x: number, y: number, dpi?: number): void
```
Moves the window to given coordinates.

### ResizeTo
```typescript
ResizeTo(width: number, height: number, applyBrowserScaleOrDPIValue: boolean | number): void
```
Resizes the window. The window must be created with the resizable flag.

### ShowWindow
```typescript
ShowWindow(): void
```
Shows the window.

## Types

### EWindowBringToFront
```typescript
enum EWindowBringToFront {
    Invalid,
    AndForceOS,
    WithoutForcingOS,
}
```

### WindowDimensions
```typescript
interface WindowDimensions {
    x: number;
    y: number;
    width: number;
    height: number;
}
```
