# SteamClient API Documentation

Complete API documentation for the Steam Client's JavaScript interface, as documented from the [decky-frontend-lib](https://github.com/SteamDeckHomebrew/decky-frontend-lib) project.

## Overview

The SteamClient API provides JavaScript/TypeScript access to Steam's native functionality. This API is available globally through the `SteamClient` object and enables interaction with various Steam features including application management, user authentication, social features, system controls, and more.

---

## Documentation Files

### [App.md](./App.md)
**3,319 lines** | **Comprehensive**

The most extensive module, providing complete application lifecycle management:
- **Installation & Launching**: Install, uninstall, launch, and terminate applications
- **Non-Steam Shortcuts**: Add and manage non-Steam games and applications
- **Workshop & DLC**: Subscribe to and download workshop items, manage DLC
- **Achievements**: Track and retrieve player achievements
- **Screenshots**: Capture, upload, and manage game screenshots
- **Compatibility Tools**: Configure Proton and compatibility tools
- **Game Actions**: Monitor game launch actions and shader processing
- **Cloud Sync**: Manage Steam Cloud conflicts and operations
- **Metadata**: Access app details, launch options, languages, and more
- 100+ methods with comprehensive type definitions

---

### [Auth.md](./Auth.md)
**292 lines** | **Security & Authentication**

Authentication and user security management:
- **Cached Sign-In**: PIN-based cached login management
- **Refresh Tokens**: Handle login tokens and refresh info
- **Steam Guard**: Manage Steam Guard authentication data
- **Machine ID**: Retrieve machine identification
- **Security Settings**: Configure secure computer settings
- 11 methods with authentication interfaces

---

### [Broadcast.md](./Broadcast.md)
**136 lines** | **Live Streaming**

Steam Broadcasting functionality for live gameplay streaming:
- **Broadcast Control**: Start and stop broadcasts
- **Viewer Management**: Approve/reject viewer requests
- **Invitations**: Invite users to watch broadcasts
- **Status Monitoring**: Track viewers, FPS, bitrate, and more
- **Event Callbacks**: Register for broadcast status changes
- 6 methods with BroadcastStatus interface

---

### [Browser.md](./Browser.md)
**375 lines** | **Browser Integration**

Browser-related functionality within the Steam client:
- **Developer Tools**: Open/close dev tools and inspect elements
- **Browsing Data**: Clear history and browsing data
- **Clipboard**: Paste functionality
- **Dictionary**: Add words to spell checker
- **Downloads**: Initiate file downloads
- **Gesture Events**: Handle touch gestures
- **Context Management**: Restart JS context
- 17 methods with touch gesture support

---

### [BrowserView.md](./BrowserView.md)
**180 lines** | **Embedded Browsers**

Create and manage embedded browser windows within Steam:
- **Create Views**: Create standalone browser views or popups
- **Popup Integration**: Use window.open() with controlled BrowserView
- **Message Passing**: PostMessage communication between parent and child
- **Configuration**: User agent, URL loading, and VR overlay support
- 4 methods with BrowserViewPopup interface

---

### [ClientNotifications.md](./ClientNotifications.md)
**196 lines** | **Notifications**

Display and handle Steam client notifications:
- **Display Notifications**: Show system notifications for chat, friend status
- **Notification Types**: Group chat, friend chat, persona state changes
- **Action Handling**: Respond to notification clicks
- **Context Callbacks**: Execute callbacks with browser context
- 2 methods with notification options interface

---

### [Cloud.md](./Cloud.md)
**74 lines** | **Cloud Saves**

Steam Cloud save synchronization management:
- **Conflict Resolution**: Resolve local vs. cloud save conflicts
- **Retry Sync**: Retry failed synchronization operations
- Simple, focused interface for cloud save management
- 2 methods for sync operations

---

### [Downloads.md](./Downloads.md)
**481 lines** | **Download Management**

Comprehensive download queue and bandwidth management:
- **Queue Control**: Pause, resume, prioritize downloads
- **Bandwidth**: Configure download speeds and throttling
- **Scheduling**: Set download schedules and auto-update windows
- **Monitoring**: Track download progress and statistics
- **Regional Settings**: Configure download regions
- 20+ methods with download state tracking

---

### [Friends.md](./Friends.md)
**346 lines** | **Social Features**

Friend list management and social interactions:
- **Friend Management**: Add and remove friends
- **Game Invitations**: Invite to games, lobbies, Remote Play Together
- **Coplay Data**: Recently played with information
- **Voice Chat**: Monitor voice chat status
- **Multiplayer**: Share session URLs
- 9 methods with coplay and voice chat interfaces

---

### [GameNotes.md](./GameNotes.md)
**287 lines** | **In-Game Notes**

Cloud-synced note-taking system for games:
- **Note Management**: Save, load, delete notes
- **Image Support**: Upload and manage note images
- **Cloud Sync**: Sync notes to/from Steam Cloud
- **Conflict Resolution**: Handle sync conflicts
- **Quota Management**: Track storage usage
- 10 methods with BB code support

---

### [GameRecording.md](./GameRecording.md)
**102 lines** | **Audio Recording**

Audio session management for game recording:
- **Session Monitoring**: Track audio sessions and state changes
- **Capture Control**: Set audio session capture state
- **Session Details**: Monitor volume, muting, system/game audio
- 2 methods with Protocol Buffer support

---

### [Input.md](./Input.md)
**133 lines** | **Controller Management**

Controller and input device configuration:
- **Controller Config**: Show controller configurator
- **Third-Party Controllers**: Configure non-Steam controllers
- **Rumble Settings**: Set controller vibration preferences
- **Desktop Configuration**: Allow/disallow desktop config
- 4 methods with controller enumeration

---

### [Music.md](./Music.md)
**285 lines** | **Music Playback**

Steam Music player controls:
- **Playback Control**: Play, pause, next, previous track
- **Volume**: Adjust, mute, increase/decrease volume
- **Shuffle & Repeat**: Configure playback modes
- **Position**: Seek to specific playback position
- **Event Monitoring**: Track playback changes
- 10 methods with music track interface

---

### [OpenVR.md](./OpenVR.md)
**550 lines** | **Virtual Reality**

VR headset and application management:
- **VR Overlay**: Manage VR overlays and positioning
- **Dashboard**: Show/hide VR dashboard
- **Theater Mode**: Configure VR theater settings
- **Device Management**: Handle VR device connections
- **Performance**: Set supersampling and performance settings
- **SteamVR Control**: Start/restart SteamVR
- 28 methods with extensive VR configuration

---

### [Screenshots.md](./Screenshots.md)
**389 lines** | **Screenshot System**

Screenshot capture and management:
- **Capture**: Take screenshots of games
- **Upload**: Upload to Steam Cloud
- **Management**: Delete, set captions, mark spoilers
- **Retrieval**: Get screenshots by time range
- **Privacy**: Set upload privacy settings
- 8 methods with screenshot metadata

---

### [Settings.md](./Settings.md)
**1,183 lines** | **Client Settings**

Comprehensive Steam client configuration:
- **In-Home Streaming**: Configure streaming quality and settings
- **Controller**: Set controller configurations
- **Voice**: Manage voice chat settings
- **Cloud**: Configure Steam Cloud settings
- **Broadcast**: Set broadcasting preferences
- **Download Throttle**: Configure bandwidth limits
- **Screenshots**: Screenshot folder and format settings
- 30+ methods covering all client settings

---

### [Streaming.md](./Streaming.md)
**365 lines** | **Remote Play**

Steam Remote Play streaming functionality:
- **Stream Control**: Start, continue, cancel game streaming
- **EULA Management**: Accept streaming agreements
- **Launch Options**: Choose streaming launch configurations
- **Progress Monitoring**: Track streaming client launch progress
- **Event Callbacks**: Monitor streaming lifecycle events
- 9 methods with streaming status tracking

---

### [System.md](./System.md)
**698 lines** | **System Integration**

System-level operations and hardware management with multiple sub-modules:
- **Audio**: Audio device and application management
- **Bluetooth**: Bluetooth device pairing and connectivity
- **Display**: Display configuration and color management
- **Network**: WiFi, connectivity testing, proxy configuration
- **Performance**: Performance monitoring and statistics
- **Power**: Battery status, airplane mode, suspend/shutdown
- **File Operations**: File dialogs, clipboard, file system operations
- **System Info**: Hardware details, OS type, system specifications
- 40+ methods with 8 specialized sub-modules

---

### [UI.md](./UI.md)
**247 lines** | **UI Management**

Steam UI mode and interface controls:
- **UI Modes**: Switch between Desktop, Big Picture, Gamepad UI
- **Window Management**: Ensure main window creation
- **ConVar Monitoring**: Track console variable changes
- **Error Handling**: Manage error conditions
- **Startup Events**: Monitor startup completion
- **OS Support**: Check OS end-of-life information
- 10 methods with UI mode enumeration

---

### [Updates.md](./Updates.md)
**260 lines** | **Client Updates**

Steam client update management:
- **Update Control**: Check for and apply client updates
- **Beta Participation**: Opt in/out of beta programs
- **Update State**: Monitor update progress and status
- **Event Callbacks**: Register for update state changes
- 6 methods with update state tracking

---

### [User.md](./User.md)
**758 lines** | **User Account**

User account information and profile data:
- **Account Details**: Steam ID, account name, persona name
- **Profile Information**: Avatar, level, profile data
- **Wallet**: Steam Wallet balance information
- **Ownership**: Check game and DLC ownership
- **Login State**: Monitor login/logout events
- **Licenses**: Retrieve user licenses
- 20+ methods with comprehensive user data

---

### [Window.md](./Window.md)
**122 lines** | **Window Controls**

Window management and display operations:
- **Window Operations**: Minimize, maximize, close, flash
- **Positioning**: Move and resize windows
- **Display**: Monitor dimensions and fullscreen state
- **Focus**: Bring to front and set keyboard focus
- **Mouse**: Get mouse position details
- 15 methods for window control

---

## Common Patterns

### Promises and Async Operations

Most SteamClient methods return Promises for asynchronous operations:

```typescript
const appDetails = await SteamClient.Apps.GetAppDetails(appId);
```

### Event Registration

Many modules provide event registration methods that return an `Unregisterable` object:

```typescript
const unregister = SteamClient.Friends.RegisterForVoiceChatStatus((status) => {
    console.log('Voice chat status:', status);
});

// Later: unregister.unregister();
```

### Error Handling

Operations typically return `EResult` codes or throw `OperationResponse` errors:

```typescript
try {
    const result = await SteamClient.Apps.InstallApp(appId);
    if (result === EResult.OK) {
        console.log('Installation started');
    }
} catch (error) {
    console.error('Installation failed:', error);
}
```

---

## Documentation Structure

Each documentation file follows a consistent structure:

1. **Title** - Module name
2. **Overview** - High-level description of the module's purpose
3. **Methods** - Detailed documentation including:
   - Method signatures with TypeScript types
   - Parameter descriptions with types
   - Return type descriptions
   - JSDoc comments and usage notes
4. **Types and Interfaces** - Complete documentation of:
   - Interfaces and their properties
   - Type aliases
   - Enumerations with values
5. **Example Usage** - Practical code examples

---

## Getting Started

The SteamClient API is globally available in Steam's JavaScript context:

```typescript
if (typeof SteamClient !== 'undefined') {
    SteamClient.System.GetSystemInfo().then(info => {
        console.log('System:', info);
    });
}
```

---

## Resources

- [Decky Loader](https://github.com/SteamDeckHomebrew/decky-loader) - Plugin loader for Steam Deck
- [decky-frontend-lib](https://github.com/SteamDeckHomebrew/decky-frontend-lib) - TypeScript definitions source
- [Steam Database](https://github.com/SteamDatabase/SteamTracking) - Protocol buffer definitions

---

## License

This documentation is provided as-is for the Steam Deck homebrew community.

*Documentation generated from decky-frontend-lib TypeScript definitions*
