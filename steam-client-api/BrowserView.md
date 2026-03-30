# BrowserView

## Overview

The `BrowserView` interface provides functionality for creating and managing browser view windows within the Steam client. It enables the creation of popup browser instances, inter-window communication through message passing, and lifecycle management of browser views. This is particularly useful for creating embedded web content or popup windows with controlled behavior.

## Interface

### BrowserView

Main interface for creating and managing browser view instances in the Steam client.

## Methods

### Create

```typescript
Create(options?: BrowserViewCreateOptions): BrowserViewPopup
```

Creates a new browser view instance with the specified options.

**Parameters:**
- `options` (BrowserViewCreateOptions, optional): Configuration options for the browser view.

**Returns:** BrowserViewPopup - The created browser view instance.

**Notes:**
- Not available on a created BrowserView (only available on the parent context).

---

### CreatePopup

```typescript
CreatePopup(options?: BrowserViewCreateOptions): {
    strCreateURL: string;
    browserView: BrowserViewPopup;
}
```

Creates a browser view popup that can be opened with `window.open()` while maintaining control over the BrowserView.

This method is similar to `Create`, but provides a URL that can be used with the standard `window.open()` function, allowing for more flexible popup creation while still maintaining programmatic control.

**Parameters:**
- `options` (BrowserViewCreateOptions, optional): Configuration options for the browser view.

**Returns:** Object containing:
- `strCreateURL` (string): The URL to use with `window.open()` to create the popup.
- `browserView` (BrowserViewPopup): The browser view instance for controlling the popup.

**Notes:**
- Not available on a created BrowserView (only available on the parent context).

---

### Destroy

```typescript
Destroy(browserView: BrowserViewPopup): void
```

Destroys an existing browser view instance, cleaning up its resources.

**Parameters:**
- `browserView` (BrowserViewPopup): The browser view instance to destroy.

**Returns:** void

**Notes:**
- Not available on a created BrowserView (only available on the parent context).

---

### PostMessageToParent

```typescript
PostMessageToParent(message: string, args: string): void
```

Sends a message from a child browser view to its parent window.

**Parameters:**
- `message` (string): The message to send to the parent.
- `args` (string): Additional arguments to send with the message.

**Returns:** void

**Notes:**
- Only works on a created BrowserView (not available in the parent context).

---

### RegisterForMessageFromParent

```typescript
RegisterForMessageFromParent(callback: (message: string, args: string) => void): Unregisterable
```

Registers a callback function to receive messages sent from the parent window using `BrowserViewPopup.PostMessage`.

**Parameters:**
- `callback` (function): A callback function that will be invoked when a message is received.
  - `message` (string): The message content received from the parent.
  - `args` (string): Additional arguments received with the message.

**Returns:** Unregisterable - An object that can be used to unregister the callback.

**Notes:**
- Only available on a created BrowserView (not available in the parent context).

---

## Types and Interfaces

### BrowserViewCreateOptions

Configuration options for creating a new browser view.

```typescript
interface BrowserViewCreateOptions {
    bOnlyAllowTrustedPopups?: boolean;
    parentPopupBrowserID?: number;
    strInitialURL?: string;
    strUserAgentIdentifier?: string;
    strUserAgentOverride?: string;
    strVROverlayKey?: string;
}
```

**Properties:**
- `bOnlyAllowTrustedPopups` (boolean, optional): When `true`, only allows popups from trusted sources.
- `parentPopupBrowserID` (number, optional): The browser ID of the parent popup window, used for establishing parent-child relationships.
- `strInitialURL` (string, optional): The initial URL to load in the browser view.
- `strUserAgentIdentifier` (string, optional): An identifier for the user agent string.
- `strUserAgentOverride` (string, optional): A custom user agent string to override the default.
- `strVROverlayKey` (string, optional): Key for VR overlay integration, used when the browser view is displayed in VR mode.

---

## Related Types

### BrowserViewPopup

Represents a created browser view popup instance. This type is imported from `./BrowserViewPopup` and provides methods for controlling and interacting with the popup window.

### Unregisterable

A type imported from `../shared` that represents an object that can be used to unregister event listeners or callbacks.

---

## Usage Patterns

### Parent Context Operations

The following operations are **only available in the parent context** (not on a created BrowserView):
- `Create()` - Creating new browser views
- `CreatePopup()` - Creating popup browser views
- `Destroy()` - Destroying browser views

### Child BrowserView Operations

The following operations are **only available in a created BrowserView** (not in the parent):
- `PostMessageToParent()` - Sending messages to the parent
- `RegisterForMessageFromParent()` - Receiving messages from the parent

This separation ensures proper communication channels and lifecycle management between parent and child browser views.

---

## Notes

- The BrowserView API has distinct methods for parent and child contexts, which cannot be used interchangeably.
- Message passing between parent and child views uses string-based messages and arguments, requiring serialization of complex data.
- The `CreatePopup` method provides flexibility by allowing the use of standard `window.open()` while maintaining control through the returned `BrowserViewPopup` object.
- User agent customization can be achieved through both identifier-based and override-based approaches.
- VR integration is supported through the `strVROverlayKey` option.
- All creation options are optional, providing sensible defaults for quick setup while allowing fine-grained control when needed.
