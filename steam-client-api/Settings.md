# Settings

## Overview

The Settings module provides comprehensive access to Steam client configuration and preferences. This interface allows applications to manage Steam settings including language preferences, time zones, compatibility tools, display settings, Steam Deck registration, beta participation, and various other client options. It also provides real-time monitoring through callback registration for settings changes.

## Methods

### AddClientBeta

```typescript
AddClientBeta(name: string, password: string): void
```

Adds a client beta with the specified name and password.

**Parameters:**
- `name` (string): The name of the beta.
- `password` (string): The password for the beta.

**Returns:** void

---

### ClearAllHTTPCaches

```typescript
ClearAllHTTPCaches(): void
```

Clears HTTP cache located in `<STEAMPATH>/appcache/httpcache`.

**Returns:** void

---

### ClearDownloadCache

```typescript
ClearDownloadCache(): void
```

Clears download cache and logs you out.

**Returns:** void

---

### GetAccountSettings

```typescript
GetAccountSettings(): Promise<AccountSettings>
```

Retrieves the current account settings.

**Returns:** Promise<[AccountSettings](#accountsettings)> - A promise that resolves with the account settings.

---

### GetAppUsesP2PVoice

```typescript
GetAppUsesP2PVoice(appId: number): Promise<boolean>
```

Checks if an application uses P2P voice communication.

**Parameters:**
- `appId` (number): The application ID to check.

**Returns:** Promise<boolean> - A promise that resolves with a boolean indicating if the app uses P2P voice.

---

### GetAvailableLanguages

```typescript
GetAvailableLanguages(): Promise<Language[]>
```

Retrieves all available languages for the Steam client.

**Returns:** Promise<[Language](#language)[]> - A promise that resolves with an array of available languages.

---

### GetAvailableTimeZones

```typescript
GetAvailableTimeZones(): Promise<TimeZone[]>
```

Retrieves all available time zones.

**Returns:** Promise<[TimeZone](#timezone)[]> - A promise that resolves with an array of available time zones.

---

### GetCurrentLanguage

```typescript
GetCurrentLanguage(): Promise<string>
```

Returns the current language (e.g., "english").

**Returns:** Promise<string> - A promise that resolves with the current language identifier.

---

### GetGlobalCompatTools

```typescript
GetGlobalCompatTools(): Promise<CompatibilityTool[]>
```

Retrieves the global compatibility tools (e.g., Proton versions).

**Returns:** Promise<CompatibilityTool[]> - A promise that resolves with an array of compatibility tools.

---

### GetMonitorInfo

```typescript
GetMonitorInfo(): Promise<ArrayBuffer>
```

Gets information about connected monitors as a ProtoBuf message. If deserialized, returns [MsgMonitorInfo](#msgmonitorinfo).

**Returns:** Promise<ArrayBuffer> - A promise that resolves with a serialized ProtoBuf message containing monitor information.

---

### GetOOBETestMode

```typescript
GetOOBETestMode(): Promise<boolean>
```

Gets the OOBE (Out Of Box Experience) test mode status.

**Returns:** Promise<boolean> - A promise that resolves with the OOBE test mode status.

---

### GetRegisteredSteamDeck

```typescript
GetRegisteredSteamDeck(): Promise<RegisteredSteamDeck>
```

Gets information about the registered Steam Deck.

**Returns:** Promise<[RegisteredSteamDeck](#registeredsteamdeck)> - A promise that resolves with Steam Deck registration information.

---

### GetTimeZone

```typescript
GetTimeZone(): Promise<string>
```

Returns the current timezone.

**Returns:** Promise<string> - A promise that resolves with the current timezone ID.

---

### GetWindowed

```typescript
GetWindowed(): Promise<boolean>
```

Gets whether the Steam client is running in windowed mode.

**Returns:** Promise<boolean> - A promise that resolves with the windowed mode status.

---

### IgnoreSteamDeckRewards

```typescript
IgnoreSteamDeckRewards(): void
```

Ignores Steam Deck rewards prompts.

**Returns:** void

---

### OpenWindowsMicSettings

```typescript
OpenWindowsMicSettings(): void
```

Opens the Windows microphones dialog.

**Returns:** void

---

### RegisterForMicVolumeUpdates

```typescript
RegisterForMicVolumeUpdates: Unregisterable
```

Registers for microphone volume updates. The property itself is an Unregisterable object.

**Type:** Unregisterable

---

### RegisterForSettingsArrayChanges

```typescript
RegisterForSettingsArrayChanges(callback: (data: ArrayBuffer) => void): Unregisterable
```

Registers a callback for settings array changes. If `data` is deserialized, returns [MsgClientSettings](#msgclientsettings).

**Parameters:**
- `callback` ((data: ArrayBuffer) => void): The callback function that receives serialized settings data.

**Returns:** Unregisterable - An object that can be used to unregister the callback.

---

### RegisterForSettingsChanges

```typescript
RegisterForSettingsChanges(callback: (settings: SteamSettings) => void): Unregisterable
```

Registers a callback for general settings changes.

**Parameters:**
- `callback` ((settings: SteamSettings) => void): The callback function that receives settings updates.

**Returns:** Unregisterable - An object that can be used to unregister the callback.

---

### RegisterForTimeZoneChange

```typescript
RegisterForTimeZoneChange(callback: (timezoneId: string) => void): Unregisterable
```

Registers a callback for timezone changes. When timezone is changed from settings, callback will return new timezoneId.

**Parameters:**
- `callback` ((timezoneId: string) => void): The callback function that receives the new timezone ID.

**Returns:** Unregisterable - An object that can be used to unregister the callback.

---

### ReinitMicSettings

```typescript
ReinitMicSettings(): void
```

Reinitializes microphone settings.

**Returns:** void

---

### RenderHotkey

```typescript
RenderHotkey(event: KeyCaptureEvent): Promise<string>
```

Renders a hotkey event to a string representation.

**Parameters:**
- `event` ([KeyCaptureEvent](#keycaptureevent)): The key capture event to render.

**Returns:** Promise<string> - A promise that resolves with the string representation of the hotkey.

---

### RequestDeviceAuthInfo

```typescript
RequestDeviceAuthInfo(): void
```

Requests device authentication information.

**Returns:** void

---

### SelectClientBeta

```typescript
SelectClientBeta(nBetaID: number): void
```

Selects a client beta by its ID.

**Parameters:**
- `nBetaID` (number): The beta ID to select.

**Returns:** void

---

### SetCurrentLanguage

```typescript
SetCurrentLanguage(strShortName: string): void
```

Sets the current language. Get valid language short names from [GetAvailableLanguages](#getavailablelanguages).

**Parameters:**
- `strShortName` (string): The short name of the language to set.

**Returns:** void

---

### SetEnableSoftProcessKill

```typescript
SetEnableSoftProcessKill(value: boolean): void
```

Enables or disables soft process kill. Default value is false. This is a Valve internal menu option.

**Parameters:**
- `value` (boolean): Whether to enable soft process kill.

**Returns:** void

---

### SetHostname

```typescript
SetHostname(hostname: string): void
```

Sets the hostname for the Steam client.

**Parameters:**
- `hostname` (string): The hostname to set.

**Returns:** void

---

### SetMicTestMode

```typescript
SetMicTestMode(value: boolean): void
```

Enables or disables microphone test mode.

**Parameters:**
- `value` (boolean): Whether to enable microphone test mode.

**Returns:** void

---

### SetOOBETestMode

```typescript
SetOOBETestMode(value: boolean): void
```

Enables or disables OOBE (Out Of Box Experience) test mode.

**Parameters:**
- `value` (boolean): Whether to enable OOBE test mode.

**Returns:** void

---

### SetPreferredMonitor

```typescript
SetPreferredMonitor(monitor: string): void
```

Sets the preferred monitor for the Steam client.

**Parameters:**
- `monitor` (string): The monitor identifier.

**Returns:** void

---

### SetRegisteredSteamDeck

```typescript
SetRegisteredSteamDeck(steam64Id: string, serialNumber: string): void
```

Registers a Steam Deck with the specified Steam64 ID and serial number.

**Parameters:**
- `steam64Id` (string): The Steam64 ID.
- `serialNumber` (string): The serial number of the Steam Deck.

**Returns:** void

---

### SetSaveAccountCredentials

```typescript
SetSaveAccountCredentials(value: boolean): void
```

Sets the "Don't save account credentials on this computer" option.

**Parameters:**
- `value` (boolean): Whether to save account credentials.

**Returns:** void

---

### SetSetting

```typescript
SetSetting(base64: string): Promise<boolean>
```

Sets a setting using a serialized base64 message from `CMsgClientSettings`.

**Parameters:**
- `base64` (string): Serialized base64 message from `CMsgClientSettings`.

**Returns:** Promise<boolean> - A promise that resolves with a boolean indicating whether the operation was successful.

---

### SetTimeZone

```typescript
SetTimeZone(timezoneId: string): void
```

Sets the timezone. You can get valid timezoneIds from [GetAvailableTimeZones](#getavailabletimezones).

**Parameters:**
- `timezoneId` (string): The timezone ID to set.

**Returns:** void

---

### SetUseNintendoButtonLayout

```typescript
SetUseNintendoButtonLayout(controllerIndex: number, value: boolean): void
```

Sets whether to use Nintendo button layout for a specific controller.

**Parameters:**
- `controllerIndex` (number): The controller index.
- `value` (boolean): Whether to use Nintendo button layout.

**Returns:** void

---

### SetUseUniversalFaceButtonGlyphs

```typescript
SetUseUniversalFaceButtonGlyphs(nControllerIndex: number, value: boolean): void
```

Sets whether to use universal face button glyphs for a specific controller.

**Parameters:**
- `nControllerIndex` (number): The controller index.
- `value` (boolean): Whether to use universal face button glyphs.

**Returns:** void

---

### SetWindowed

```typescript
SetWindowed(value: boolean): void
```

Sets whether the Steam client should run in windowed mode.

**Parameters:**
- `value` (boolean): Whether to enable windowed mode.

**Returns:** void

---

### SpecifyGlobalCompatTool

```typescript
SpecifyGlobalCompatTool(strToolName: string): void
```

Specifies the global compatibility tool to use.

**Parameters:**
- `strToolName` (string): The name of the compatibility tool.

**Returns:** void

---

### ToggleSteamInstall

```typescript
ToggleSteamInstall(): Promise<OperationResponse>
```

Toggles the Steam installation state.

**Returns:** Promise<OperationResponse> - A promise that resolves with the operation response.

---

## Types & Interfaces

### AccountSettings

```typescript
interface AccountSettings {
    strEmail: string;
    bEmailValidated: boolean;
    bHasAnyVACBans: boolean;
    bHasTwoFactor: boolean;
    eSteamGuardState: ESteamGuardState;
    rtSteamGuardEnableTime: number;
    bSaveAccountCredentials: boolean;
}
```

Contains account-related settings and security information.

**Properties:**
- `strEmail` (string): The account email address.
- `bEmailValidated` (boolean): Whether the email has been validated.
- `bHasAnyVACBans` (boolean): Whether the account has any VAC bans.
- `bHasTwoFactor` (boolean): Whether two-factor authentication is enabled.
- `eSteamGuardState` ([ESteamGuardState](#esteamguardstate)): The Steam Guard state.
- `rtSteamGuardEnableTime` (number): The time when Steam Guard was enabled.
- `bSaveAccountCredentials` (boolean): Whether account credentials are saved.

---

### KeyCaptureEvent

```typescript
interface KeyCaptureEvent {
    alt_key: boolean;
    ctrl_key: boolean;
    display_name: string;
    meta_key: boolean;
    shift_key: boolean;
}
```

Represents a keyboard key capture event for hotkey configuration.

**Properties:**
- `alt_key` (boolean): Whether the Alt key is pressed.
- `ctrl_key` (boolean): Whether the Ctrl key is pressed.
- `display_name` (string): The display name of the key.
- `meta_key` (boolean): Whether the Meta (Windows/Command) key is pressed.
- `shift_key` (boolean): Whether the Shift key is pressed.

---

### Language

```typescript
interface Language {
    language: ELanguage;
    strShortName: string;
}
```

Represents a language available in Steam.

**Properties:**
- `language` ([ELanguage](#elanguage)): The language enumeration value.
- `strShortName` (string): The short name identifier for the language (e.g., "english").

---

### RegisteredSteamDeck

```typescript
interface RegisteredSteamDeck {
    bRegistered: boolean;
    bIgnoreRegistrationPrompt: boolean;
    strSteamID: string;
    strSerialNumber: string;
}
```

Contains Steam Deck registration information.

**Properties:**
- `bRegistered` (boolean): Whether a Steam Deck is registered.
- `bIgnoreRegistrationPrompt` (boolean): Whether to ignore the registration prompt.
- `strSteamID` (string): The Steam ID associated with the Steam Deck.
- `strSerialNumber` (string): The serial number of the Steam Deck.

---

### TimeZone

```typescript
interface TimeZone {
    utcOffset: number;
    timezoneID: string;
    timezoneLocalizationToken: string;
    regionsLocalizationToken: string;
}
```

Represents a timezone with localization information.

**Properties:**
- `utcOffset` (number): The UTC offset for the timezone.
- `timezoneID` (string): The timezone identifier.
- `timezoneLocalizationToken` (string): The localization token for the timezone name.
- `regionsLocalizationToken` (string): The localization token for regions using this timezone.

---

### Monitor

```typescript
interface Monitor {
    monitor_device_name: string;
    monitor_display_name: string;
}
```

Represents a display monitor.

**Properties:**
- `monitor_device_name` (string): The device name of the monitor.
- `monitor_display_name` (string): The display name of the monitor.

**Note:** Doesn't work on Linux.

---

### MsgMonitorInfo

```typescript
interface MsgMonitorInfo extends JsPbMessage {
    monitors(): Monitor[];
    selected_display_name(): string;
    add_monitors(param0: any, param1: any): any;
    set_monitors(param0: any): any;
    set_selected_display_name(param0: any): any;
}
```

ProtoBuf message (CMsgMonitorInfo) containing monitor information.

**Methods:**
- `monitors()`: Returns an array of monitors.
- `selected_display_name()`: Returns the selected display name.
- `add_monitors(param0, param1)`: Adds monitors to the message.
- `set_monitors(param0)`: Sets the monitors.
- `set_selected_display_name(param0)`: Sets the selected display name.

---

### MsgClientSettings

```typescript
interface MsgClientSettings extends JsPbMessage {
    // Controller settings
    controller_combine_nintendo_joycons(): boolean;
    controller_enable_chord(): boolean;
    controller_generic_support(): boolean;
    controller_guide_button_focus_steam(): boolean;
    controller_poll_rate(): boolean;
    controller_power_off_timeout(): number;
    controller_ps_support(): number;
    controller_switch_support(): boolean;
    controller_xbox_driver(): boolean;
    controller_xbox_support(): boolean;
    
    // Display and UI settings
    always_show_user_chooser(): boolean;
    always_use_gamepadui_overlay(): boolean;
    auto_scale_factor(): number;
    bigpicture_windowed(): boolean;
    display_name(): string;
    enable_dpi_scaling(): boolean;
    enable_ui_sounds(): boolean;
    is_external_display(): boolean;
    max_scale_factor(): number;
    min_scale_factor(): number;
    preferred_monitor(): string;
    small_mode(): boolean;
    smooth_scroll_webviews(): boolean;
    start_in_big_picture_mode(): boolean;
    
    // Broadcasting settings
    broadcast_bitrate(): number;
    broadcast_chat_corner(): number;
    broadcast_encoding_option(): EBroadcastEncoderSetting;
    broadcast_output_height(): number;
    broadcast_output_width(): number;
    broadcast_permissions(): EBroadcastPermission;
    broadcast_record_all_audio(): boolean;
    broadcast_record_all_video(): boolean;
    broadcast_record_microphone(): boolean;
    broadcast_show_live_reminder(): boolean;
    broadcast_show_upload_stats(): boolean;
    
    // Download settings
    download_peer_content(): number;
    download_rate_bits_per_s(): boolean;
    download_region(): number;
    download_throttle_rate(): number;
    download_throttle_while_streaming(): boolean;
    download_while_app_running(): boolean;
    restrict_auto_updates(): boolean;
    restrict_auto_updates_end(): number;
    restrict_auto_updates_start(): number;
    
    // Game recording settings
    g_background_audio(): EGRAudio;
    g_background_a_m(): number;
    g_background_a_s(): boolean;
    g_background_path(): string;
    g_background_max_keep(): string;
    g_background_mode(): EGRMode;
    g_background_time_resolution(): number;
    g_background_mk(): CMsgHotkey;
    g_background_tg(): CMsgHotkey;
    g_max_fps(): number;
    gamerecording_automatic_gain_control(): boolean;
    gamerecording_export_codec(): EExportCodec;
    gamerecording_export_directory(): number;
    gamerecording_export_limit_bitrate(): number;
    gamerecording_export_limit_frame_rate(): number;
    gamerecording_export_limit_height(): number;
    gamerecording_export_limit_size_mb(): number;
    gamerecording_export_limit_width(): number;
    gamerecording_export_limit_type(): EGRExportLimitType;
    gamerecording_force_mic_mono(): boolean;
    gamerecording_hotkey_ic(): CMsgHotkey;
    gamerecording_ic_seconds(): number;
    gamerecording_video_bitrate(): string;
    gamerecording_video_maxheight(): number;
    
    // Gamescope settings (Steam Deck)
    gamescope_allow_tearing(): boolean;
    gamescope_app_target_framerate(): number;
    gamescope_composite_debug(): boolean;
    gamescope_disable_framelimit(): boolean;
    gamescope_disable_mura_correction(): boolean;
    gamescope_display_refresh_rate(): number;
    gamescope_enable_app_target_framerate(): boolean;
    gamescope_force_composite(): boolean;
    gamescope_hdr_visualization(): EHDRVisualization;
    gamescope_include_steamui_in_screenshots(): boolean;
    gamescope_use_game_refresh_rate_in_steam(): boolean;
    
    // Library settings
    library_disable_community_content(): boolean;
    library_display_icon_in_game_list(): boolean;
    library_display_size(): number;
    library_low_bandwidth_mode(): boolean;
    library_low_perf_mode(): boolean;
    library_whats_new_show_only_product_updates(): boolean;
    
    // Music settings
    music_download_high_quality(): boolean;
    music_pause_on_app_start(): boolean;
    music_pause_on_voice_chat(): boolean;
    music_playlist_notification(): boolean;
    music_volume(): number;
    
    // Overlay settings
    enable_overlay(): boolean;
    overlay_fps_counter_corner(): number;
    overlay_fps_counter_high_contrast(): boolean;
    overlay_key(): CMsgHotkey;
    overlay_restore_browser_tabs(): boolean;
    overlay_scale_interface(): boolean;
    overlay_tabs(): string;
    overlay_toolbar_list_view(): boolean;
    
    // Screenshot settings
    enable_avif_screenshots(): boolean;
    enable_screenshot_notification(): boolean;
    enable_screenshot_sound(): boolean;
    save_uncompressed_screenshots(): boolean;
    screenshot_items_per_row(): number;
    screenshot_key(): CMsgHotkey;
    screenshots_path(): string;
    show_screenshot_manager(): boolean;
    
    // Shader and performance settings
    enable_shader_background_processing(): boolean;
    enable_shader_precache(): boolean;
    shader_precached_size(): string;
    
    // Streaming settings
    gamestream_enable_video_h265(): boolean;
    gamestream_hardware_video_encode(): boolean;
    
    // SteamOS specific settings
    steamos_cec_enabled(): boolean;
    steamos_cec_wake_on_resume(): boolean;
    steamos_magnifier_scale(): number;
    steamos_status_led_brightness(): number;
    steamos_tdp_limit(): number;
    steamos_tdp_limit_enabled(): boolean;
    steamos_wifi_debug(): boolean;
    steamos_wifi_force_wpa_supplicant(): boolean;
    steam_os_underscan_enabled(): boolean;
    steam_os_underscan_level(): number;
    
    // Voice settings
    voice_mic_device_name(): string;
    voice_mic_input_gain(): number;
    voice_push_to_talk_key(): CMsgHotkey;
    voice_push_to_talk_setting(): number;
    voice_speaker_output_gain(): number;
    
    // Notification settings
    disable_all_toasts(): boolean;
    disable_toasts_in_game(): boolean;
    enable_marketing_messages(): boolean;
    play_sound_on_toast(): boolean;
    show_family_sharing_notifications(): boolean;
    
    // Beta and system settings
    in_client_beta(): boolean;
    is_steam_sideloaded(): boolean;
    needs_steam_service_repair(): boolean;
    no_save_personal_info(): boolean;
    oobe_test_mode_enabled(): boolean;
    os_version_unsupported(): boolean;
    
    // Miscellaneous settings
    cef_remote_debugging_enabled(): boolean;
    cloud_enabled(): boolean;
    default_ping_rate(): number;
    enable_gpu_accelerated_webviews(): boolean;
    enable_hardware_video_decoding(): boolean;
    force_deck_perf_tab(): boolean;
    force_fake_mandatory_update(): boolean;
    force_oobe(): boolean;
    game_notes_enable_spellcheck(): boolean;
    hdr_compat_testing(): boolean;
    jumplist_flags(): number;
    override_browser_composer_mode(): number;
    ready_to_play_includes_streaming(): boolean;
    run_at_startup(): boolean;
    server_ping_rate(): number;
    show_copy_count_in_library(): boolean;
    show_steam_deck_info(): boolean;
    show_store_content_on_home(): boolean;
    show_timestamps_in_console(): boolean;
    skip_steamvr_install_dialog(): boolean;
    start_page(): string;
    startup_movie_id(): string;
    startup_movie_local_path(): string;
    startup_movie_shuffle(): boolean;
    startup_movie_used_for_resume(): boolean;
    steam_cef_gpu_blocklist_disabled(): boolean;
    steam_input_configurator_error_msg_enable(): boolean;
    steam_networking_share_ip(): number;
    system_bluetooth_enabled(): boolean;
    turn_off_controller_on_exit(): boolean;
    web_browser_home(): string;
    
    // Validation settings (for testing)
    setting_validation_bool(): boolean;
    setting_validation_enum(): EHDRVisualization;
    setting_validation_int32(): number;
    setting_validation_uint32(): number;
    setting_validation_uint64(): number;
    setting_validation_float(): number;
    setting_validation_string(): string;
}
```

ProtoBuf message (CMsgClientSettings) containing comprehensive Steam client settings. This extensive interface provides access to nearly all configurable aspects of the Steam client.

---

### CMsgHotkey

```typescript
interface CMsgHotkey extends JsPbMessage {
    key_code(): number;
    alt_key(): boolean;
    shift_key(): boolean;
    ctrl_key(): boolean;
    meta_key(): boolean;
    display_name(): string;
}
```

ProtoBuf message representing a hotkey configuration.

**Methods:**
- `key_code()`: Returns the key code.
- `alt_key()`: Returns whether Alt key is part of the hotkey.
- `shift_key()`: Returns whether Shift key is part of the hotkey.
- `ctrl_key()`: Returns whether Ctrl key is part of the hotkey.
- `meta_key()`: Returns whether Meta key is part of the hotkey.
- `display_name()`: Returns the display name of the hotkey.

---

## Enums

### ESteamGuardState

```typescript
enum ESteamGuardState {
    EmailUnverified = 0,
    Protected = 1,
    Disabled = 2,
    Offline = 3,
    NotEnabled = 4,
}
```

Represents the state of Steam Guard protection. Values are unconfirmed and taken from localization strings.

**Values:**
- `EmailUnverified` (0): Email is not verified.
- `Protected` (1): Steam Guard is active and protecting the account.
- `Disabled` (2): Steam Guard is disabled.
- `Offline` (3): Steam Guard is in offline mode.
- `NotEnabled` (4): Steam Guard is not enabled.

---

### ELanguage

```typescript
enum ELanguage {
    None = -1,
    English = 0,
    German = 1,
    French = 2,
    Italian = 3,
    Korean = 4,
    Spanish = 5,
    SimplifiedChinese = 6,
    TraditionalChinese = 7,
    Russian = 8,
    Thai = 9,
    Japanese = 10,
    Portuguese = 11,
    Polish = 12,
    Danish = 13,
    Dutch = 14,
    Finnish = 15,
    Norwegian = 16,
    Swedish = 17,
    Hungarian = 18,
    Czech = 19,
    Romanian = 20,
    Turkish = 21,
    Brazilian = 22,
    Bulgarian = 23,
    Greek = 24,
    Arabic = 25,
    Ukrainian = 26,
    LatamSpanish = 27,
    Vietnamese = 28,
    SteamChina_SChinese = 29,
    Max = 30,
}
```

Enumeration of all supported languages in Steam.

---

### EClientBetaState

```typescript
enum EClientBetaState {
    None = 0,
    NoneChosen = 1,
    NoneChosenNonAdmin = 2,
    InBeta = 3,
    InBetaNonAdmin = 4,
}
```

Represents the client beta participation state.

**Values:**
- `None` (0): Not in any beta state.
- `NoneChosen` (1): No beta chosen, admin access available.
- `NoneChosenNonAdmin` (2): No beta chosen, non-admin user.
- `InBeta` (3): Currently in a beta, admin access available.
- `InBetaNonAdmin` (4): Currently in a beta, non-admin user.

---

### EBroadcastEncoderSetting

```typescript
enum EBroadcastEncoderSetting {
    BestQuality = 0,
    BestPerformance = 1,
}
```

Encoder settings for broadcasting.

**Values:**
- `BestQuality` (0): Prioritize broadcast quality.
- `BestPerformance` (1): Prioritize system performance.

---

### EBroadcastPermission

```typescript
enum EBroadcastPermission {
    Disabled = 0,
    FriendsApprove = 1,
    FriendsAllowed = 2,
    Public = 3,
    Subscribers = 4,
}
```

Permission levels for broadcasting.

**Values:**
- `Disabled` (0): Broadcasting is disabled.
- `FriendsApprove` (1): Friends need approval to watch.
- `FriendsAllowed` (2): Friends can watch without approval.
- `Public` (3): Anyone can watch.
- `Subscribers` (4): Only subscribers can watch.

---

### EExportCodec

```typescript
enum EExportCodec {
    Default = 0,
    H264 = 1,
    H265 = 2,
}
```

Video codecs for game recording export.

**Values:**
- `Default` (0): Use default codec.
- `H264` (1): Use H.264 codec.
- `H265` (2): Use H.265 codec.

---

### EGRAudio

```typescript
enum EGRAudio {
    Game = 0,
    System = 1,
    Select = 2,
}
```

Audio source options for game recording.

**Values:**
- `Game` (0): Record only game audio.
- `System` (1): Record all system audio.
- `Select` (2): Select specific audio sources.

---

### EGRExportLimitType

```typescript
enum EGRExportLimitType {
    Native = 0,
    FileSize = 1,
    Advanced = 2,
}
```

Export limitation types for game recordings.

**Values:**
- `Native` (0): Use native resolution and settings.
- `FileSize` (1): Limit by file size.
- `Advanced` (2): Use advanced custom limits.

---

### EGRMode

```typescript
enum EGRMode {
    Never = 0,
    Always = 1,
    Manual = 2,
}
```

Game recording mode options.

**Values:**
- `Never` (0): Never record.
- `Always` (1): Always record gameplay.
- `Manual` (2): Record only when manually triggered.

---

### EHDRVisualization

```typescript
enum EHDRVisualization {
    None = 0,
    Heatmap = 1,
    Analysis = 2,
    HeatmapExtended = 3,
    HeatmapClassic = 4,
}
```

HDR visualization modes for development and testing.

**Values:**
- `None` (0): No HDR visualization.
- `Heatmap` (1): Display HDR heatmap.
- `Analysis` (2): Display HDR analysis.
- `HeatmapExtended` (3): Display extended HDR heatmap.
- `HeatmapClassic` (4): Display classic HDR heatmap.

---

## Notes

- The Settings interface provides both getter and setter methods for most configuration options.
- Many settings changes require a Steam client restart to take full effect.
- ProtoBuf messages (ArrayBuffer) can be deserialized using appropriate ProtoBuf libraries to access structured data.
- Some methods are platform-specific (e.g., `OpenWindowsMicSettings` only works on Windows, Monitor detection doesn't work on Linux).
- The `RegisterFor*` methods return an `Unregisterable` object that should be used to clean up listeners when they are no longer needed.
- Time zone IDs should be obtained from `GetAvailableTimeZones()` before using `SetTimeZone()`.
- Language short names should be obtained from `GetAvailableLanguages()` before using `SetCurrentLanguage()`.
- Beta participation requires appropriate credentials and admin access depending on the beta state.
- Steam Deck specific settings (gamescope, steamos) are primarily relevant when running on Steam Deck hardware.
