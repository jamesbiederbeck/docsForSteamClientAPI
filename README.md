# SteamClient API Documentation

Complete API documentation for the Steam Client's JavaScript interface, based on the TypeScript definitions from [decky-frontend-lib](https://github.com/SteamDeckHomebrew/decky-frontend-lib).

## 📚 Documentation

All API documentation is available in the **[steam-client-api/](./steam-client-api/)** directory.

### Quick Links

- **[Main Documentation Index](./steam-client-api/README.md)** - Complete overview with summaries of all 23 API modules
- **[Getting Started Guide](./steam-client-api/README.md#getting-started)** - Learn how to use the SteamClient API
- **[Common Patterns](./steam-client-api/README.md#common-patterns)** - Promises, event handling, and error management

## 📖 API Modules

| Module | Description |
|--------|-------------|
| [App](./steam-client-api/App.md) | Application management, installation, shortcuts, and metadata (100+ methods) |
| [Auth](./steam-client-api/Auth.md) | User authentication, login tokens, and Steam Guard |
| [Broadcast](./steam-client-api/Broadcast.md) | Live streaming and broadcast management |
| [Browser](./steam-client-api/Browser.md) | Browser functionality, dev tools, and clipboard operations |
| [BrowserView](./steam-client-api/BrowserView.md) | Embedded browser windows and popups |
| [ClientNotifications](./steam-client-api/ClientNotifications.md) | System notifications and alerts |
| [Cloud](./steam-client-api/Cloud.md) | Steam Cloud save synchronization |
| [Downloads](./steam-client-api/Downloads.md) | Download queue and bandwidth management |
| [Friends](./steam-client-api/Friends.md) | Friend list, invitations, and social features |
| [GameNotes](./steam-client-api/GameNotes.md) | Cloud-synced in-game notes |
| [GameRecording](./steam-client-api/GameRecording.md) | Audio session management for recording |
| [Input](./steam-client-api/Input.md) | Controller configuration and input devices |
| [Music](./steam-client-api/Music.md) | Steam Music playback controls |
| [OpenVR](./steam-client-api/OpenVR.md) | Virtual reality and VR application management |
| [Screenshots](./steam-client-api/Screenshots.md) | Screenshot capture and cloud management |
| [Settings](./steam-client-api/Settings.md) | Steam client configuration (30+ methods) |
| [Streaming](./steam-client-api/Streaming.md) | Remote Play and game streaming |
| [System](./steam-client-api/System.md) | System operations, hardware, and 8 sub-modules |
| [UI](./steam-client-api/UI.md) | UI mode management and interface controls |
| [Updates](./steam-client-api/Updates.md) | Steam client updates and beta management |
| [User](./steam-client-api/User.md) | User account and profile information |
| [Window](./steam-client-api/Window.md) | Window positioning, resizing, and display |

## 🚀 Example Usage

```typescript
// Check if SteamClient is available
if (typeof SteamClient !== 'undefined') {
    // Get system information
    const systemInfo = await SteamClient.System.GetSystemInfo();
    console.log(`OS: ${systemInfo.sOSName}`);
    
    // Monitor battery status
    const unregister = SteamClient.System.RegisterForBatteryStateChanges((state) => {
        console.log(`Battery: ${(state.flLevel * 100).toFixed(0)}%`);
    });
    
    // Get app details
    const appDetails = await SteamClient.Apps.GetAppDetails(appId);
    console.log(`App: ${appDetails.strDisplayName}`);
}
```

## 📊 Documentation Statistics

- **23 API Modules** fully documented
- **300+ Methods** with complete signatures
- **200+ Interfaces** and type definitions
- **50+ Enumerations** documented
- **10,850 total lines** of documentation

## 🎯 Key Features Documented

### Application & Content
- App installation, launching, and management
- Non-Steam shortcuts and Flatpak integration
- Workshop items and DLC
- Screenshots and achievements
- Download management and scheduling

### User & Social
- Authentication and Steam Guard
- Friend list and multiplayer invitations
- User profiles and account information
- Voice chat status

### Media & Gaming
- Music playback controls
- Screenshot capture and cloud sync
- Game broadcasting
- Game recording audio sessions
- In-game notes system

### System & Hardware
- System information and diagnostics
- Audio device management
- Bluetooth pairing
- Network and WiFi configuration
- Display and color management
- Performance monitoring
- Battery and power management

### Interface & Platform
- UI mode switching (Desktop/Big Picture)
- Window management
- Browser integration
- VR and OpenVR support
- Steam client settings
- Client updates

## 🔗 Resources

- [Decky Loader](https://github.com/SteamDeckHomebrew/decky-loader) - Plugin loader for Steam Deck
- [decky-frontend-lib](https://github.com/SteamDeckHomebrew/decky-frontend-lib) - Source TypeScript definitions
- [Steam Database](https://github.com/SteamDatabase/SteamTracking) - Protocol buffer definitions

## 📝 License

This documentation is provided as-is for the Steam Deck homebrew community.

---

*Documentation based on decky-frontend-lib TypeScript definitions*