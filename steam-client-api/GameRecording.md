# GameRecording

## Overview

The `GameRecording` module provides functionality for managing game recording features in the Steam client, specifically related to audio session management. This interface allows applications to monitor and control which audio sources are captured during game recordings, providing fine-grained control over audio mixing.

## Methods

### RegisterForAudioSessionsChanged

```typescript
RegisterForAudioSessionsChanged(callback: (data: ArrayBuffer) => void): Unregisterable
```

Registers a callback function to be notified when audio sessions change during game recording.

**Parameters:**
- `callback` ((data: ArrayBuffer) => void): Function to be called when audio sessions change. The data parameter is an ArrayBuffer that, when deserialized, returns a `CGameRecording_AudioSessionsChanged_Notification` object

**Returns:**
- `Unregisterable`: An object that can be used to unregister the callback

**Notes:**
- The `data` parameter in the callback can be deserialized to obtain a `CGameRecording_AudioSessionsChanged_Notification` object

---

### SetAudioSessionCaptureState

```typescript
SetAudioSessionCaptureState(id: string, name: string, state: boolean): void
```

Sets the capture state for a specific audio session.

**Parameters:**
- `id` (string): The unique identifier of the audio session
- `name` (string): The name of the audio session
- `state` (boolean): `true` to enable capture, `false` to disable capture

**Returns:**
- `void`

## Types/Interfaces

### AudioSession

```typescript
interface AudioSession {
    id(): string | undefined;
    name(): string | undefined;
    is_system(): boolean | undefined;
    is_muted(): boolean | undefined;
    is_active(): boolean | undefined;
    is_captured(): boolean | undefined;
    recent_peak(): number | undefined;
    is_game(): boolean | undefined;
    is_steam(): boolean | undefined;
    is_saved(): boolean | undefined;
}
```

Represents an audio session that can be captured during game recording.

**Methods:**
- `id()`: Returns the unique identifier for the audio session
- `name()`: Returns the display name of the audio session
- `is_system()`: Returns `true` if this is a system audio session
- `is_muted()`: Returns `true` if the audio session is currently muted
- `is_active()`: Returns `true` if the audio session is currently active
- `is_captured()`: Returns `true` if the audio session is being captured
- `recent_peak()`: Returns the recent audio peak level as a number
- `is_game()`: Returns `true` if this is the game's audio session
- `is_steam()`: Returns `true` if this is a Steam audio session
- `is_saved()`: Returns `true` if the audio session settings are saved

---

### CGameRecording_AudioSessionsChanged_Notification

```typescript
interface CGameRecording_AudioSessionsChanged_Notification extends JsPbMessage {
    sessions(): AudioSession[];
}
```

Notification message containing information about audio session changes.

**Methods:**
- `sessions()`: Returns an array of `AudioSession` objects representing all current audio sessions

**Notes:**
- This interface is based on the protobuf definition from SteamTracking: `steammessages_gamerecording_objects.proto`
- Extends `JsPbMessage` which is the base interface for protobuf messages in JavaScript

## Notes

- The GameRecording module is primarily focused on audio session management during game recording
- Audio sessions represent individual audio sources (applications, system sounds, etc.) that can be included or excluded from the recording
- The module uses protobuf messages for communication, requiring deserialization of ArrayBuffer data
- Audio sessions can be identified as system, game, or Steam-related, allowing for precise control over what gets recorded
- The notification system allows real-time monitoring of audio session changes during recording
