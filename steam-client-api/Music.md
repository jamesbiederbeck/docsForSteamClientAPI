# Music

## Overview

The Music module provides functions for controlling music playback in the Steam client. It allows you to manage playback controls (play, pause, next, previous), adjust volume settings, configure shuffle and repeat modes, and register callbacks to monitor playback changes and position updates.

## Interface: Music

The main interface for interacting with Steam's music playback functionality.

### Methods

#### DecreaseVolume

```typescript
DecreaseVolume(): void
```

Decreases the music volume by 10%.

**Parameters:**
- None

**Returns:**
- `void`

---

#### IncreaseVolume

```typescript
IncreaseVolume(): void
```

Increases the music volume by 10%.

**Parameters:**
- None

**Returns:**
- `void`

---

#### PlayNext

```typescript
PlayNext(): void
```

Plays the next track in the music playlist.

**Parameters:**
- None

**Returns:**
- `void`

---

#### PlayPrevious

```typescript
PlayPrevious(): void
```

Plays the previous track in the music playlist.

**Parameters:**
- None

**Returns:**
- `void`

---

#### RegisterForMusicPlaybackChanges

```typescript
RegisterForMusicPlaybackChanges(callback: (param0: boolean | MusicTrack) => void): Unregisterable
```

Registers a callback function to be called when music playback changes.

**Parameters:**
- `callback` (`(param0: boolean | MusicTrack) => void`): The callback function to be called when playback changes. The callback receives either a boolean or a MusicTrack object.

**Returns:**
- `Unregisterable`: An object that can be used to unregister the callback.

---

#### RegisterForMusicPlaybackPosition

```typescript
RegisterForMusicPlaybackPosition(callback: (position: number) => void): Unregisterable
```

Registers a callback function to be called when the music playback position changes.

**Parameters:**
- `callback` (`(position: number) => void`): The callback function to be called when the position changes. The callback receives the current position.

**Returns:**
- `Unregisterable`: An object that can be used to unregister the callback.

---

#### SetPlaybackPosition

```typescript
SetPlaybackPosition(position: number): void
```

Sets the playback position of the music track.

**Parameters:**
- `position` (`number`): The position to set in seconds.

**Returns:**
- `void`

---

#### SetPlayingRepeatStatus

```typescript
SetPlayingRepeatStatus(status: EMusicPlayingRepeatStatus): void
```

Sets the repeat status for music playback.

**Parameters:**
- `status` (`EMusicPlayingRepeatStatus`): The repeat status to set.

**Returns:**
- `void`

---

#### SetPlayingShuffled

```typescript
SetPlayingShuffled(value: boolean): void
```

Sets the shuffle status for music playback.

**Parameters:**
- `value` (`boolean`): `true` to enable shuffle, `false` to disable shuffle.

**Returns:**
- `void`

---

#### SetVolume

```typescript
SetVolume(volume: number): void
```

Sets the volume for music playback.

**Parameters:**
- `volume` (`number`): The volume level to set. Ranges from 0 to 100.

**Returns:**
- `void`

**Remarks:**
- Volume ranges from 0 to 100.

---

#### ToggleMuteVolume

```typescript
ToggleMuteVolume(): void
```

Toggles the mute state of the music volume.

**Parameters:**
- None

**Returns:**
- `void`

---

#### TogglePlayPause

```typescript
TogglePlayPause(): void
```

Toggles between play and pause for music playback.

**Parameters:**
- None

**Returns:**
- `void`

---

## Types and Interfaces

### MusicTrack

Represents information about the currently playing music track.

```typescript
interface MusicTrack {
    uSoundtrackAppId: number;
    ePlaybackStatus: EAudioPlayback;
    eRepeatStatus: EMusicPlayingRepeatStatus;
    bShuffle: boolean;
    nVolume: number;
    nActiveTrack: number;
    nLengthInMsec: number;
}
```

**Properties:**
- `uSoundtrackAppId` (`number`): The Steam App ID of the soundtrack.
- `ePlaybackStatus` (`EAudioPlayback`): The current playback status.
- `eRepeatStatus` (`EMusicPlayingRepeatStatus`): The current repeat status.
- `bShuffle` (`boolean`): Whether shuffle is enabled.
- `nVolume` (`number`): The current volume level.
- `nActiveTrack` (`number`): The index of the currently active track.
- `nLengthInMsec` (`number`): The length of the track in milliseconds.

---

## Enums

### EAudioPlayback

Represents the playback status of audio.

```typescript
enum EAudioPlayback {
    Undefined,
    Playing,
    Paused,
    Idle,
}
```

**Values:**
- `Undefined` (0): Playback status is undefined.
- `Playing` (1): Audio is currently playing.
- `Paused` (2): Audio is paused.
- `Idle` (3): Audio player is idle.

---

### EMusicPlayingRepeatStatus

Represents the repeat mode for music playback.

```typescript
enum EMusicPlayingRepeatStatus {
    None,
    All,
    Once,
    Max,
}
```

**Values:**
- `None` (0): No repeat.
- `All` (1): Repeat all tracks.
- `Once` (2): Repeat current track once.
- `Max` (3): Maximum value for the enum.

---

## Notes

- The `Unregisterable` type is imported from the shared module and provides a mechanism to unregister callbacks.
- Volume adjustments can be made incrementally using `IncreaseVolume()` and `DecreaseVolume()` (10% steps) or absolutely using `SetVolume()`.
- Callbacks registered with `RegisterForMusicPlaybackChanges()` and `RegisterForMusicPlaybackPosition()` must be unregistered when no longer needed to prevent memory leaks.
