# ClientNotifications

## Overview

The `ClientNotifications` interface provides functionality for displaying and managing Steam client notifications. This module enables the creation of native Steam notifications for various events such as chat messages, friend status changes, and other client-level alerts. It handles both the display of notifications and user interactions with them.

## Interface

### ClientNotifications

Main interface for managing Steam client notifications.

## Methods

### DisplayClientNotification

```typescript
DisplayClientNotification(
    notification: EClientUINotificationType,
    options: string,
    callback: (context: BrowserContext) => void,
): void
```

Displays a Steam notification to the user with the specified type and options.

**Parameters:**
- `notification` (EClientUINotificationType): The type of notification to display (e.g., chat message, friend status).
- `options` (string): A stringified JSON object containing `SteamNotificationOptions`. Must be serialized before passing.
- `callback` (function): A callback function that will be executed when the user interacts with the notification.
  - `context` (BrowserContext): The browser context associated with the notification action.

**Returns:** void

**Example:**
```typescript
const options: SteamNotificationOptions = {
    body: "Hello, this is a notification!",
    state: "online",
    steamid: "76561198000000000",
    title: "New Message"
};

DisplayClientNotification(
    EClientUINotificationType.FriendChatMessage,
    JSON.stringify(options),
    (context) => {
        console.log("Notification clicked", context);
    }
);
```

---

### OnRespondToClientNotification

```typescript
OnRespondToClientNotification(notificationId: number, handleAction: boolean): void
```

Responds to a client notification, either executing its associated callback or dismissing it.

**Parameters:**
- `notificationId` (number): The unique identifier of the notification to respond to.
- `handleAction` (boolean): 
  - `true` - Executes the callback function associated with the notification.
  - `false` - Dismisses the notification without executing the callback.

**Returns:** void

---

## Types and Interfaces

### SteamNotificationOptions

Configuration options for creating a Steam notification.

```typescript
interface SteamNotificationOptions {
    body: string;
    chatroomgroupid?: number;
    chatroomid?: number;
    icon?: string;
    state: string;
    steamid: string;
    tag?: string;
    title?: string;
}
```

**Properties:**
- `body` (string, required): The main content/message body of the notification.
- `chatroomgroupid` (number, optional): The ID of the chat room group, used for group chat notifications.
- `chatroomid` (number, optional): The ID of the specific chat room, used for chat notifications.
- `icon` (string, optional): URL or identifier for the icon to display with the notification.
- `state` (string, required): The state associated with the notification (e.g., "online", "offline", "busy").
- `steamid` (string, required): The Steam64 ID of the user associated with the notification.
- `tag` (string, optional): A tag for categorizing or grouping notifications.
- `title` (string, optional): The title/heading of the notification.

---

### EClientUINotificationType

Enumeration of notification types supported by the Steam client.

```typescript
enum EClientUINotificationType {
    GroupChatMessage = 1,
    FriendChatMessage,
    FriendPersonaState,
}
```

**Values:**
- `GroupChatMessage` (1): Notification for a message in a group chat.
- `FriendChatMessage` (2): Notification for a direct message from a friend.
- `FriendPersonaState` (3): Notification for a friend's status/persona state change (e.g., online, offline, away).

---

## Related Types

### BrowserContext

Type imported from `./shared` that represents the browser context associated with notification callbacks. This provides information about the browser environment when a notification action is triggered.

---

## Usage Examples

### Displaying a Friend Chat Message Notification

```typescript
const chatOptions: SteamNotificationOptions = {
    body: "Hey, are you available?",
    state: "online",
    steamid: "76561198012345678",
    title: "John Doe",
    icon: "https://example.com/avatar.jpg"
};

ClientNotifications.DisplayClientNotification(
    EClientUINotificationType.FriendChatMessage,
    JSON.stringify(chatOptions),
    (context) => {
        // Handle notification click - e.g., open chat window
        console.log("User clicked on friend chat notification");
    }
);
```

### Displaying a Group Chat Notification

```typescript
const groupChatOptions: SteamNotificationOptions = {
    body: "New message in Gaming Group",
    state: "active",
    steamid: "76561198087654321",
    chatroomgroupid: 123456,
    chatroomid: 789012,
    title: "Gaming Group",
    tag: "group-123456"
};

ClientNotifications.DisplayClientNotification(
    EClientUINotificationType.GroupChatMessage,
    JSON.stringify(groupChatOptions),
    (context) => {
        // Handle notification click - e.g., open group chat
        console.log("User clicked on group chat notification");
    }
);
```

### Responding to a Notification

```typescript
// Execute the notification's callback
ClientNotifications.OnRespondToClientNotification(notificationId, true);

// Dismiss the notification without executing callback
ClientNotifications.OnRespondToClientNotification(notificationId, false);
```

---

## Notes

- The `options` parameter in `DisplayClientNotification` must be a stringified JSON object, not a direct object reference.
- The `steamid` field in `SteamNotificationOptions` is typed as a string to accommodate Steam64 ID format, which can exceed JavaScript's safe integer range.
- Notification callbacks provide a `BrowserContext` parameter that can be used to determine the appropriate response to user interaction.
- Different notification types may utilize different subsets of the `SteamNotificationOptions` properties (e.g., chat room IDs are only relevant for chat notifications).
- The notification system integrates with Steam's native notification infrastructure, providing a consistent user experience across the Steam client.
- When handling notification responses, the `handleAction` parameter determines whether the associated callback should be executed or if the notification should simply be dismissed.
