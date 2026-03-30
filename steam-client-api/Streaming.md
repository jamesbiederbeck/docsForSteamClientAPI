# Streaming

## Overview

The Streaming module provides access to Steam's remote play and game streaming functionality. This interface allows applications to control streaming sessions, accept EULA agreements, manage launch options for streamed games, and register callbacks for various streaming events such as client start, progress updates, and completion status. It enables seamless integration with Steam's remote play features for streaming games from one device to another.

## Methods

### AcceptStreamingEULA

```typescript
AcceptStreamingEULA(appId: number, id: string, version: number): void
```

Accepts the End User License Agreement (EULA) for streaming a specific application.

**Parameters:**
- `appId` (number): The application ID for which to accept the EULA.
- `id` (string): The EULA identifier.
- `version` (number): The version number of the EULA being accepted.

**Returns:** void

---

### CancelStreamGame

```typescript
CancelStreamGame(): void
```

Cancels the currently active streaming session.

**Returns:** void

---

### RegisterForStreamingClientFinished

```typescript
RegisterForStreamingClientFinished(callback: (code: EResult, result: string) => void): Unregisterable
```

Registers a callback function to be called when the streaming client finishes.

**Parameters:**
- `callback` ((code: EResult, result: string) => void): The callback function that will be invoked when streaming ends.
  - `code` (EResult): The result code indicating the outcome of the streaming session.
  - `result` (string): A string containing additional result information or error details.

**Returns:** Unregisterable - An object that can be used to unregister the callback.

---

### RegisterForStreamingClientLaunchProgress

```typescript
RegisterForStreamingClientLaunchProgress(
    callback: (actionType: string, taskDetails: string, done: number, total: number) => void
): Unregisterable
```

Registers a callback function to be called when there is progress in the launch of the streaming client.

**Parameters:**
- `callback` ((actionType: string, taskDetails: string, done: number, total: number) => void): The callback function that receives progress updates.
  - `actionType` (string): The type of action currently being performed (e.g., "downloading", "installing", "initializing").
  - `taskDetails` (string): Detailed description of the current task.
  - `done` (number): The amount of work completed.
  - `total` (number): The total amount of work to be done.

**Returns:** Unregisterable - An object that can be used to unregister the callback.

**Example usage:**
```typescript
const unregister = SteamClient.Streaming.RegisterForStreamingClientLaunchProgress(
    (actionType, taskDetails, done, total) => {
        const progress = (done / total) * 100;
        console.log(`${actionType}: ${taskDetails} - ${progress.toFixed(1)}%`);
    }
);

// Later, when no longer needed:
unregister.unregister();
```

---

### RegisterForStreamingClientStarted

```typescript
RegisterForStreamingClientStarted(callback: (appId: number) => void): Unregisterable
```

Registers a callback function to be called when the streaming client is started (e.g., when clicking the stream button).

**Parameters:**
- `callback` ((appId: number) => void): The callback function that will be invoked when streaming starts.
  - `appId` (number): The application ID of the game being streamed.

**Returns:** Unregisterable - An object that can be used to unregister the callback.

---

### RegisterForStreamingLaunchComplete

```typescript
RegisterForStreamingLaunchComplete(callback: (code: EResult, result: string) => void): Unregisterable
```

Registers a callback function to be called when the streaming launch is complete.

**Parameters:**
- `callback` ((code: EResult, result: string) => void): The callback function that will be invoked when launch completes.
  - `code` (EResult): The result code indicating success or failure of the launch.
  - `result` (string): A string containing additional result information or error details.

**Returns:** Unregisterable - An object that can be used to unregister the callback.

---

### RegisterForStreamingShowEula

```typescript
RegisterForStreamingShowEula(callback: (appId: number) => void): Unregisterable
```

Registers a callback function to be called when a streaming EULA needs to be shown to the user.

**Parameters:**
- `callback` ((appId: number) => void): The callback function that will be invoked when a EULA should be displayed.
  - `appId` (number): The application ID for which the EULA should be shown.

**Returns:** Unregisterable - An object that can be used to unregister the callback.

**Note:** When this callback is triggered, you should present the EULA to the user and call `AcceptStreamingEULA()` if they accept.

---

### RegisterForStreamingShowIntro

```typescript
RegisterForStreamingShowIntro(callback: (appId: number, param: string) => void): Unregisterable
```

Registers a callback function to be called when the streaming intro should be shown.

**Parameters:**
- `callback` ((appId: number, param: string) => void): The callback function that will be invoked when the intro should be displayed.
  - `appId` (number): The application ID for the game being streamed.
  - `param` (string): Additional parameters for the intro screen.

**Returns:** Unregisterable - An object that can be used to unregister the callback.

---

### RegisterForStreamingShowLaunchOptions

```typescript
RegisterForStreamingShowLaunchOptions(
    callback: (appId: number, launchOptions: LaunchOption[]) => void
): Unregisterable
```

Registers a callback function to be called when the streaming client receives launch options from the host.

**Parameters:**
- `callback` ((appId: number, launchOptions: LaunchOption[]) => void): The callback function that receives launch options.
  - `appId` (number): The application ID of the game being streamed.
  - `launchOptions` (LaunchOption[]): An array of available launch options for the game.

**Returns:** Unregisterable - An object that can be used to unregister the callback.

**Note:** When this callback is triggered, present the launch options to the user and call `StreamingSetLaunchOption()` with the selected index.

---

### StreamingContinueStreamGame

```typescript
StreamingContinueStreamGame(): void
```

Continues streaming an existing game that is already running on another streaming-capable device.

**Returns:** void

**Use case:** This method is used when you want to resume streaming a game that is already running on another device in your home network, rather than starting a new streaming session.

---

### StreamingSetLaunchOption

```typescript
StreamingSetLaunchOption(index: number): void
```

Chooses the launch option for the streamed app by its index and restarts the stream.

**Parameters:**
- `index` (number): The zero-based index of the launch option to use, corresponding to the array received in `RegisterForStreamingShowLaunchOptions`.

**Returns:** void

**Note:** This should be called in response to the `RegisterForStreamingShowLaunchOptions` callback after the user has selected their preferred launch option.

---

## Related Types

### LaunchOption

The `LaunchOption` type is imported from the App module and represents a launch configuration for an application.

```typescript
interface LaunchOption {
    // Properties defined in the App module
    // Used to represent different ways to launch a game (e.g., with different DLCs, modes, or configurations)
}
```

Refer to the App module documentation for the complete definition of `LaunchOption`.

---

### EResult

The `EResult` enum is imported from the shared module and represents the result codes returned by Steam operations.

```typescript
enum EResult {
    // Common values include:
    // OK = 1: Operation succeeded
    // Fail = 2: Generic failure
    // NoConnection = 3: No network connection
    // InvalidPassword = 5: Invalid password
    // ... and many more
}
```

Refer to the shared module documentation for the complete enumeration of result codes.

---

### Unregisterable

The `Unregisterable` interface is imported from the shared module and provides a way to unregister callbacks.

```typescript
interface Unregisterable {
    unregister(): void;
}
```

All `RegisterFor*` methods return an `Unregisterable` object that should be used to clean up the callback when it's no longer needed.

---

## Usage Examples

### Basic Streaming Flow

```typescript
// Listen for when streaming starts
const streamStartedUnreg = SteamClient.Streaming.RegisterForStreamingClientStarted((appId) => {
    console.log(`Streaming started for app ${appId}`);
});

// Monitor launch progress
const progressUnreg = SteamClient.Streaming.RegisterForStreamingClientLaunchProgress(
    (actionType, taskDetails, done, total) => {
        const percent = ((done / total) * 100).toFixed(1);
        console.log(`${actionType}: ${percent}% - ${taskDetails}`);
    }
);

// Handle launch completion
const launchCompleteUnreg = SteamClient.Streaming.RegisterForStreamingLaunchComplete(
    (code, result) => {
        if (code === EResult.OK) {
            console.log('Streaming launched successfully');
        } else {
            console.error(`Streaming launch failed: ${result}`);
        }
    }
);

// Clean up when done
// streamStartedUnreg.unregister();
// progressUnreg.unregister();
// launchCompleteUnreg.unregister();
```

---

### Handling Launch Options

```typescript
// Register for launch options
const launchOptionsUnreg = SteamClient.Streaming.RegisterForStreamingShowLaunchOptions(
    (appId, launchOptions) => {
        console.log(`Launch options for app ${appId}:`, launchOptions);
        
        // Present options to user and get their selection
        // For this example, we'll just select the first option
        const selectedIndex = 0;
        
        // Apply the selected launch option
        SteamClient.Streaming.StreamingSetLaunchOption(selectedIndex);
    }
);
```

---

### Handling EULA

```typescript
// Register for EULA display
const eulaUnreg = SteamClient.Streaming.RegisterForStreamingShowEula((appId) => {
    console.log(`EULA required for app ${appId}`);
    
    // Show EULA to user
    // If user accepts, call:
    SteamClient.Streaming.AcceptStreamingEULA(appId, 'eula_id', 1);
});
```

---

### Continuing an Existing Stream

```typescript
// Resume streaming a game already running on another device
SteamClient.Streaming.StreamingContinueStreamGame();
```

---

### Canceling a Stream

```typescript
// Cancel the current streaming session
SteamClient.Streaming.CancelStreamGame();
```

---

## Notes

- **Remote Play**: The Streaming interface is primarily used for Steam's Remote Play functionality, which allows you to stream games from one device to another on your local network or over the internet.

- **Callback Management**: All `RegisterFor*` methods return an `Unregisterable` object. It's important to call `unregister()` on these objects when they're no longer needed to prevent memory leaks and unexpected behavior.

- **Launch Options**: Some games have multiple launch options (e.g., different DLCs, 32-bit vs 64-bit versions, or different game modes). The `RegisterForStreamingShowLaunchOptions` callback provides a way to handle these scenarios during streaming.

- **EULA Acceptance**: Some games may require EULA acceptance before streaming can begin. Handle the `RegisterForStreamingShowEula` callback to present the EULA to users and call `AcceptStreamingEULA()` if they accept.

- **Progress Tracking**: The `RegisterForStreamingClientLaunchProgress` callback provides detailed progress information that can be used to show loading screens or progress bars to users during the streaming client launch process.

- **Error Handling**: Always check the `EResult` code in completion callbacks to determine if operations succeeded and handle errors appropriately.

- **Network Requirements**: Remote Play streaming requires a stable network connection. Performance will vary based on network quality, bandwidth, and latency.

- **Device Compatibility**: Not all devices support streaming equally. Ensure that both the host (streaming source) and client (streaming target) meet Steam's Remote Play requirements.
