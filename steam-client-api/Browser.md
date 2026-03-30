# Browser

## Overview

The `Browser` interface provides access to Steam's browser functionality, allowing control over browser behavior, developer tools, input handling, and various browsing operations. This module is essential for managing the Steam client's web browsing capabilities, including clipboard operations, spell checking, gesture handling, and download management.

## Interface

### Browser

Main interface for interacting with the Steam browser client.

## Methods

### AddWordToDictionary

```typescript
AddWordToDictionary(word: string): void
```

Adds a word to the browser's spell-check dictionary.

**Parameters:**
- `word` (string): The word to add to the dictionary.

**Returns:** void

---

### ClearAllBrowsingData

```typescript
ClearAllBrowsingData(): void
```

Clears all browsing data from the browser, including cookies, cache, and local storage.

**Returns:** void

---

### ClearHistory

```typescript
ClearHistory(): void
```

Clears the browser's navigation history.

**Returns:** void

---

### CloseDevTools

```typescript
CloseDevTools(): void
```

Closes the browser's developer tools window if it's currently open.

**Returns:** void

---

### GetBrowserID

```typescript
GetBrowserID(): Promise<number>
```

Retrieves the unique identifier for the current browser instance.

**Returns:** Promise&lt;number&gt; - A promise that resolves to the browser's unique ID.

---

### GetSpellingSuggestions

```typescript
GetSpellingSuggestions(word: string): string[]
```

Gets spelling suggestions for a potentially misspelled word.

**Parameters:**
- `word` (string): The word to get spelling suggestions for.

**Returns:** string[] - An array of suggested correct spellings.

---

### GetSteamBrowserID

```typescript
GetSteamBrowserID(): Promise<number>
```

Retrieves the Steam-specific browser identifier (likely a 16-bit unsigned integer).

**Returns:** Promise&lt;number&gt; - A promise that resolves to the Steam browser ID.

---

### HideCursorUntilMouseEvent

```typescript
HideCursorUntilMouseEvent(): void
```

Hides the mouse cursor until the next mouse input event occurs.

**Returns:** void

---

### InspectElement

```typescript
InspectElement(clientY: number, clientX: number): void
```

Opens the developer tools and inspects the element at the specified coordinates.

**Parameters:**
- `clientY` (number): The Y coordinate of the element to inspect.
- `clientX` (number): The X coordinate of the element to inspect.

**Note:** The parameter order is reversed - clientY comes before clientX.

**Returns:** void

---

### NotifyUserActivation

```typescript
NotifyUserActivation(): void
```

Notifies the browser of user activation, which can be used to enable certain browser features that require user interaction.

**Returns:** void

---

### OpenDevTools

```typescript
OpenDevTools(): void
```

Opens the browser's developer tools window.

**Returns:** void

---

### Paste

```typescript
Paste(): void
```

Pastes the contents of the clipboard into the currently focused element.

**Returns:** void

---

### RegisterForGestureEvents

```typescript
RegisterForGestureEvents(callback: (gesture: TouchGesture) => void): Unregisterable
```

Registers a callback function to handle touch gesture events.

**Parameters:**
- `callback` (function): A callback function that receives a `TouchGesture` object when a gesture is detected.

**Returns:** Unregisterable - An object that can be used to unregister the callback.

**Notes:**
- Not available on a created BrowserView.
- Status: unconfirmed

---

### RegisterForOpenNewTab

```typescript
RegisterForOpenNewTab: Unregisterable
```

Registers for new tab opening events.

**Notes:**
- Not available on a created BrowserView.

**Type:** Unregisterable

---

### ReplaceMisspelling

```typescript
ReplaceMisspelling(param0: string): void
```

Replaces a misspelled word with the provided correction.

**Parameters:**
- `param0` (string): The replacement text for the misspelled word.

**Returns:** void

---

### RestartJSContext

```typescript
RestartJSContext(): void
```

Restarts the Steam JavaScript context, effectively reloading the browser's JavaScript environment.

**Returns:** void

---

### SetBackgroundThrottlingDisabled

```typescript
SetBackgroundThrottlingDisabled(value: boolean): void
```

Controls whether background throttling is disabled for the browser.

**Parameters:**
- `value` (boolean): `true` to disable background throttling, `false` to enable it.

**Returns:** void

---

### SetPendingFilePath

```typescript
SetPendingFilePath(path: string): Promise<boolean>
```

Sets a pending file path, likely for file upload operations.

**Parameters:**
- `path` (string): The file path to set as pending.

**Returns:** Promise&lt;boolean&gt; - A promise that resolves to `true` if successful, `false` otherwise.

---

### SetShouldExitSteamOnBrowserClosed

```typescript
SetShouldExitSteamOnBrowserClosed(value: boolean): Promise<void>
```

Controls whether Steam should exit when the browser is closed.

**Parameters:**
- `value` (boolean): `true` to exit Steam when browser closes, `false` to keep Steam running.

**Returns:** Promise&lt;void&gt; - A promise that resolves when the setting is applied.

---

### SetTouchGesturesToCancel

```typescript
SetTouchGesturesToCancel(gestures: ETouchGesture[]): void
```

Specifies which touch gestures should be cancelled.

**Parameters:**
- `gestures` (ETouchGesture[]): An array of touch gesture types to cancel.

**Returns:** void

---

### StartDownload

```typescript
StartDownload(url: string): void
```

Prompts the user and initiates a file download from the specified URL.

**Parameters:**
- `url` (string): The URL of the file to download.

**Returns:** void

---

## Types and Interfaces

### TouchGesture

Represents a touch gesture event with position information.

```typescript
interface TouchGesture {
    eTouchGesture: ETouchGesture;
    x: number;
    y: number;
}
```

**Properties:**
- `eTouchGesture` (ETouchGesture): The type of touch gesture that was detected.
- `x` (number): The X coordinate where the gesture occurred.
- `y` (number): The Y coordinate where the gesture occurred.

---

### ETouchGesture

Enumeration of available touch gesture types.

```typescript
enum ETouchGesture {
    None,
    Touch,
    Tap,
    DoubleTap,
    ShortPress,
    LongPress,
    LongTap,
    TwoFingerTap,
    TapCancelled,
    PinchBegin,
    PinchUpdate,
    PinchEnd,
    FlingStart,
    FlingCancelled,
}
```

**Values:**
- `None` (0): No gesture.
- `Touch` (1): A basic touch interaction.
- `Tap` (2): A quick tap gesture.
- `DoubleTap` (3): A double-tap gesture.
- `ShortPress` (4): A short press gesture.
- `LongPress` (5): A long press gesture.
- `LongTap` (6): A long tap gesture.
- `TwoFingerTap` (7): A two-finger tap gesture.
- `TapCancelled` (8): A tap gesture that was cancelled.
- `PinchBegin` (9): The beginning of a pinch gesture.
- `PinchUpdate` (10): An update during a pinch gesture.
- `PinchEnd` (11): The end of a pinch gesture.
- `FlingStart` (12): The start of a fling gesture.
- `FlingCancelled` (13): A fling gesture that was cancelled.

---

## Notes

- The `InspectElement` method has reversed parameter order - `clientY` comes before `clientX`.
- Several methods are marked as not available on created BrowserView instances, including `RegisterForGestureEvents` and `RegisterForOpenNewTab`.
- The browser interface integrates with the Steam client's gesture system, allowing for touch-based interactions.
- Developer tools can be controlled programmatically through `OpenDevTools()` and `CloseDevTools()` methods.
- The interface provides comprehensive spell-checking capabilities with dictionary management and suggestion features.
