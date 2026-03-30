# Friends

## Overview

The Friends module provides an interface for managing Steam friends and social features. It enables applications to add/remove friends, retrieve information about recent players, manage game invitations, and monitor voice chat status.

This module facilitates social interactions within Steam, including multiplayer invitations, Remote Play Together functionality, and voice chat management.

## Interface

### Friends

The main interface for interacting with Steam's friends and social features.

## Methods

### AddFriend

```typescript
AddFriend(steamId: string): Promise<boolean>
```

Adds a user to the friend list.

This method sends a friend request to the specified user. The request must be accepted by the recipient before they become friends.

**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `steamId` | `string` | The Steam ID of the user to add as a friend. |

**Returns:** `Promise<boolean>` - Resolves to `true` if the friend was added successfully, `false` otherwise.

---

### GetCoplayData

```typescript
GetCoplayData(): Promise<CoplayData>
```

Retrieves a list of players you recently played with.

This method returns information about users you've played multiplayer games with recently, including both current and historical co-play sessions.

**Parameters:** None

**Returns:** `Promise<CoplayData>` - Resolves to a `CoplayData` object containing current and recent co-players.

---

### InviteUserToCurrentGame

```typescript
InviteUserToCurrentGame(steam64Id: string, steamIdTarget: string): Promise<boolean>
```

Invites a user to the currently running game.

**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `steam64Id` | `string` | The Steam ID (64-bit format) of the inviting user. |
| `steamIdTarget` | `string` | The Steam ID of the user to invite. |

**Returns:** `Promise<boolean>` - Resolves to `true` if the invitation was sent successfully.

---

### InviteUserToGame

```typescript
InviteUserToGame(steamId: string, appId: number, connectString: string): Promise<boolean>
```

Invites a user to a specific game.

This method allows you to invite a friend to join a specific game, with optional connection parameters.

**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `steamId` | `string` | The Steam ID of the user to invite. |
| `appId` | `number` | The ID of the game to invite the user to. |
| `connectString` | `string` | Additional parameters for the invitation (e.g., server address, lobby ID). |

**Returns:** `Promise<boolean>` - Resolves to `true` if the user was invited successfully.

---

### InviteUserToLobby

```typescript
InviteUserToLobby(steam64Id: string, steamIdTarget: string): Promise<boolean>
```

Invites a user to a specific lobby.

This method sends a lobby invitation to the specified user for the current game lobby.

**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `steam64Id` | `string` | The Steam ID (64-bit format) of the lobby owner or inviting user. |
| `steamIdTarget` | `string` | The Steam ID of the user to invite to the lobby. |

**Returns:** `Promise<boolean>` - Resolves to `true` if the user was invited successfully.

---

### InviteUserToRemotePlayTogetherCurrentGame

```typescript
InviteUserToRemotePlayTogetherCurrentGame(steam64Id: string): Promise<boolean>
```

Invites a user to play the current game via Steam Remote Play Together.

Remote Play Together allows users to play local multiplayer games online by streaming the game to friends.

**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `steam64Id` | `string` | The Steam ID (64-bit format) of the user to invite. |

**Returns:** `Promise<boolean>` - Resolves to `true` if the invitation was sent successfully.

---

### RegisterForMultiplayerSessionShareURLChanged

```typescript
RegisterForMultiplayerSessionShareURLChanged(
    appId: number,
    callback: (param0: string, param1: string) => void
): Unregisterable
```

Registers a callback function to be called when the multiplayer session share URL changes.

This is useful for monitoring when a sharable multiplayer session link is created or updated.

**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `appId` | `number` | The ID of the application to monitor. |
| `callback` | `(param0: string, param1: string) => void` | The callback function to be called when the share URL changes. The parameters contain URL-related information. |

**Returns:** `Unregisterable` - An object with an `unregister()` method that can be used to remove the callback.

---

### RegisterForVoiceChatStatus

```typescript
RegisterForVoiceChatStatus(callback: (status: VoiceChatStatus) => void): Unregisterable
```

Registers a callback function to be called when voice chat status changes.

This allows monitoring of voice chat state, including whether voice chat is active and the mute status of microphone and output.

**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `callback` | `(status: VoiceChatStatus) => void` | The callback function to be called when voice chat status changes. |

**Returns:** `Unregisterable` - An object with an `unregister()` method that can be used to remove the callback.

---

### RemoveFriend

```typescript
RemoveFriend(steamId: string): Promise<boolean>
```

Removes a user from the friend list.

This permanently removes the friendship relationship. To become friends again, a new friend request must be sent and accepted.

**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `steamId` | `string` | The Steam ID of the user to remove from the friend list. |

**Returns:** `Promise<boolean>` - Resolves to `true` if the friend was removed successfully.

---

### ShowRemotePlayTogetherUI

```typescript
ShowRemotePlayTogetherUI(): void
```

Displays the Remote Play Together UI.

This opens the Steam interface for managing Remote Play Together sessions.

**Parameters:** None

**Returns:** `void`

## Types and Interfaces

### CoplayData

Contains information about players you've recently played with.

```typescript
interface CoplayData {
    /** Users currently in a co-play session */
    currentUsers: CoplayUser[];
    
    /** Users from recent co-play sessions */
    recentUsers: CoplayUser[];
}
```

---

### CoplayUser

Represents a user from a co-play session.

```typescript
interface CoplayUser {
    /** Steam account ID (32-bit) */
    accountid: number;
    
    /** Timestamp of when you last played together */
    rtTimePlayed: number;
    
    /** ID of the app you played together */
    appid: number;
}
```

---

### VoiceChatStatus

Represents the current state of voice chat.

```typescript
interface VoiceChatStatus {
    /** True if voice chat is currently active */
    bVoiceChatActive: boolean;
    
    /** True if the microphone is muted */
    bMicMuted: boolean;
    
    /** True if the output (speakers/headphones) is muted */
    bOutputMuted: boolean;
}
```

## Usage Example

```typescript
// Access the Friends interface through SteamClient
const friends = SteamClient.Friends;

// Add a friend
async function addNewFriend(steamId: string) {
    const success = await friends.AddFriend(steamId);
    if (success) {
        console.log('Friend request sent successfully!');
    }
}

// Get recent co-play data
async function getRecentPlayers() {
    const coplayData = await friends.GetCoplayData();
    
    console.log('Current co-players:');
    coplayData.currentUsers.forEach(user => {
        console.log(`Account ${user.accountid} in app ${user.appid}`);
    });
    
    console.log('Recent co-players:');
    coplayData.recentUsers.forEach(user => {
        console.log(`Account ${user.accountid} in app ${user.appid} at ${user.rtTimePlayed}`);
    });
}

// Monitor voice chat status
const unregisterVoiceChat = friends.RegisterForVoiceChatStatus((status) => {
    console.log(`Voice chat active: ${status.bVoiceChatActive}`);
    console.log(`Mic muted: ${status.bMicMuted}`);
    console.log(`Output muted: ${status.bOutputMuted}`);
});

// Invite a friend to the current game
async function inviteToGame(friendSteamId: string) {
    const success = await friends.InviteUserToCurrentGame(
        'YOUR_STEAM_ID',
        friendSteamId
    );
    if (success) {
        console.log('Invitation sent!');
    }
}

// Invite a friend to Remote Play Together
async function inviteToRemotePlay(friendSteamId: string) {
    const success = await friends.InviteUserToRemotePlayTogetherCurrentGame(friendSteamId);
    if (success) {
        console.log('Remote Play invitation sent!');
    }
}

// Show Remote Play Together UI
friends.ShowRemotePlayTogetherUI();

// Remove a friend
async function removeFriend(steamId: string) {
    const success = await friends.RemoveFriend(steamId);
    if (success) {
        console.log('Friend removed successfully.');
    }
}

// Later: cleanup
unregisterVoiceChat.unregister();
```

## Notes

- Most methods in this interface are asynchronous and return Promises
- Steam IDs can be in either 32-bit (accountid) or 64-bit (steam64Id) format depending on the method
- Friend requests must be accepted by the recipient before the friendship is established
- Voice chat status callbacks provide real-time updates about voice chat state
- Remote Play Together requires both users to have the feature enabled
- Always call `unregister()` on registered callbacks to prevent memory leaks
- Co-play data includes timestamp information that can be used to sort by recency
- The `connectString` parameter in `InviteUserToGame` can contain server IPs, lobby IDs, or other game-specific connection data
