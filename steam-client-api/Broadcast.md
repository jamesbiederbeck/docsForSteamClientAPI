# Broadcast

The Broadcast interface provides functionality for managing Steam broadcasting features, including viewer management, invitations, and broadcast status monitoring.

## Overview

The `Broadcast` interface handles Steam's game broadcasting capabilities, allowing users to:
- Start and stop broadcasts
- Manage viewer requests and approvals
- Invite users to watch broadcasts
- Monitor broadcast status and metrics
- Register callbacks for broadcast events

## Methods

### ApproveViewerRequest
```typescript
ApproveViewerRequest(steamId64: string, param1: number): void
```
Approves a viewer request for the broadcast.

**Parameters:**
- `steamId64` - The SteamID64 of the user whose request is to be approved
- `param1` - Additional parameter

---

### InviteToWatch
```typescript
InviteToWatch(steamId64: string): Promise<EResult>
```
Invites a user identified by their SteamID64 to watch the broadcast.

**Parameters:**
- `steamId64` - The SteamID64 of the user to invite

**Returns:** EResult indicating the success or failure of the invitation

---

### RegisterForBroadcastStatus
```typescript
RegisterForBroadcastStatus(callback: (status: BroadcastStatus) => void): Unregisterable
```
Registers a callback to be called when the broadcast status changes.

**Parameters:**
- `callback` - The callback function to be called with BroadcastStatus updates

**Returns:** An object that can be used to unregister the callback

---

### RegisterForViewerRequests
```typescript
RegisterForViewerRequests(
  callback: (viewerFriendCode: number, param1: number, param2: number) => void
): Unregisterable
```
Registers a callback to be called when viewer requests are received.

**Parameters:**
- `callback` - The callback function to be called with viewer request information
  - `viewerFriendCode` - The friend code of the viewer requesting access
  - `param1` - Additional parameter
  - `param2` - Additional parameter

**Returns:** An object that can be used to unregister the callback

---

### RejectViewerRequest
```typescript
RejectViewerRequest(steamId64: string, param1: number): void
```
Rejects a viewer request for the broadcast.

**Parameters:**
- `steamId64` - The SteamID64 of the user whose request is to be rejected
- `param1` - Additional parameter

---

### StopBroadcasting
```typescript
StopBroadcasting(): void
```
Stops the current broadcast.

---

## Types and Interfaces

### BroadcastStatus
```typescript
interface BroadcastStatus {
  broadcastid: string;
  nViewers: number;
  nRequests: number;
  bIsBroadcasting: boolean;
  bIsRecordingDesktop: boolean;
  eBroadcastReady: EResult;
  bBroadcastCapable: boolean;
  bMicrophoneEnabled: boolean;
  bMicrophoneActive: boolean;
  nCurrentFPS: number;
  nUploadKbps: number;
}
```
Represents the current status of a broadcast.

**Properties:**
- `broadcastid` - Unique identifier for the broadcast
- `nViewers` - Current number of viewers watching the broadcast
- `nRequests` - Number of pending viewer requests
- `bIsBroadcasting` - Whether a broadcast is currently active
- `bIsRecordingDesktop` - Whether desktop recording is active
- `eBroadcastReady` - EResult status indicating if the broadcast system is ready
- `bBroadcastCapable` - Whether the system is capable of broadcasting
- `bMicrophoneEnabled` - Whether the microphone is enabled for broadcasting
- `bMicrophoneActive` - Whether the microphone is currently active
- `nCurrentFPS` - Current frames per second of the broadcast
- `nUploadKbps` - Current upload speed in kilobits per second

---

## Notes

- Broadcasts can be private (requiring approval) or public
- Viewer requests need to be explicitly approved or rejected
- The broadcast status provides real-time metrics about the broadcast quality and viewership
- Callbacks allow applications to respond to broadcast events in real-time
- SteamID64 is used as the primary identifier for users in the broadcasting system
- The Unregisterable return type allows callbacks to be cleaned up when no longer needed
- Microphone settings are separate from the broadcast itself and can be toggled independently
- Upload speed and FPS metrics can be used to monitor broadcast quality
