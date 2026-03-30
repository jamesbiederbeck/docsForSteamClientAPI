# User

## Overview

The User module manages user authentication, account management, login state, and system power operations. It provides extensive functionality for handling user sessions, credentials, offline mode, shutdown/restart procedures, and hardware surveys.

## Methods

### `AuthorizeMicrotxn()`
```typescript
AuthorizeMicrotxn(txnId: number | string): void
```
Authorizes a microtransaction.

**Parameters:**
- `txnId` (`number | string`) - The transaction ID to authorize.

**Returns:** `void`

---

### `CancelLogin()`
```typescript
CancelLogin(): void
```
Cancels the current login attempt.

**Returns:** `void`

---

### `CancelMicrotxn()`
```typescript
CancelMicrotxn(txnId: number | string): void
```
Cancels a microtransaction.

**Parameters:**
- `txnId` (`number | string`) - The transaction ID to cancel.

**Returns:** `void`

---

### `CancelShutdown()`
```typescript
CancelShutdown(): void
```
Tries to cancel Steam shutdown.

**Returns:** `void`

**Notes:** Used in the "Shutting down" dialog.

---

### `ChangeUser()`
```typescript
ChangeUser(): void
```
Opens the "Change Account" dialog.

**Returns:** `void`

---

### `Connect()`
```typescript
Connect(): Promise<OperationResponse>
```
Connects to the Steam network.

**Returns:** `Promise<OperationResponse>` - Response indicating the connection result.

---

### `FlipToLogin()`
```typescript
FlipToLogin(): void
```
Flips to the login screen.

**Returns:** `void`

---

### `ForceShutdown()`
```typescript
ForceShutdown(): void
```
Forces a shutdown while shutting down.

**Returns:** `void`

**Notes:** Used in the "Shutting down" dialog.

---

### `ForgetPassword()`
```typescript
ForgetPassword(accountName: string): Promise<boolean>
```
Forgets an account's password.

**Parameters:**
- `accountName` (`string`) - Login of the account to forget.

**Returns:** `Promise<boolean>` - A boolean indicating whether the operation succeeded or not.

---

### `GetIPCountry()`
```typescript
GetIPCountry(): Promise<string>
```
Gets your country code.

**Returns:** `Promise<string>` - A string containing your country code.

---

### `GetLoginProgress()`
```typescript
GetLoginProgress(callback: (param0: number, param1: number) => void): Unregisterable
```
Retrieves login progress updates.

**Parameters:**
- `callback` (`(param0: number, param1: number) => void`) - The callback function to receive progress updates.

**Returns:** `Unregisterable` - An object that can unregister the callback.

**Notes:** param0 mirrors param3 of `RegisterForLoginStateChange`.

---

### `GetLoginUsers()`
```typescript
GetLoginUsers(): Promise<LoginUser[]>
```
Retrieves the list of remembered login users.

**Returns:** `Promise<LoginUser[]>` - An array of login user information.

---

### `GoOffline()`
```typescript
GoOffline(): void
```
Switches Steam to offline mode.

**Returns:** `void`

---

### `GoOnline()`
```typescript
GoOnline(): void
```
Switches Steam to online mode.

**Returns:** `void`

---

### `OptOutOfSurvey()`
```typescript
OptOutOfSurvey(): void
```
Opts out of the hardware survey.

**Returns:** `void`

---

### `PrepareForSystemSuspend()`
```typescript
PrepareForSystemSuspend(): Promise<{ result: EResult }>
```
Prepares Steam for system suspend.

**Returns:** `Promise<{ result: EResult }>` - The result of the preparation.

---

### `Reconnect()`
```typescript
Reconnect(): void
```
Reconnects to the Steam network.

**Returns:** `void`

---

### `RegisterForConnectionAttemptsThrottled()`
```typescript
RegisterForConnectionAttemptsThrottled(callback: (data: ConnectionAttempt) => void): Unregisterable
```
Registers a callback for when connection attempts are throttled.

**Parameters:**
- `callback` (`(data: ConnectionAttempt) => void`) - The callback function.

**Returns:** `Unregisterable` - An object that can unregister the callback.

---

### `RegisterForCurrentUserChanges()`
```typescript
RegisterForCurrentUserChanges(callback: (user: CurrentUser) => void): void
```
Registers a callback for when the current user information changes.

**Parameters:**
- `callback` (`(user: CurrentUser) => void`) - The callback function receiving updated user information.

**Returns:** `void`

---

### `RegisterForLoginStateChange()`
```typescript
RegisterForLoginStateChange(
    callback: (
        accountName: string,
        state: ELoginState,
        result: EResult,
        param3: number,
        percentage: number,
        emailDomain: string,
    ) => void
): Unregisterable
```
Registers a callback for login state changes.

**Parameters:**
- `callback` - The callback function with the following parameters:
  - `accountName` (`string`) - Account name (empty if not logged in).
  - `state` (`ELoginState`) - The current login state.
  - `result` (`EResult`) - The result code.
  - `param3` (`number`) - Additional parameter.
  - `percentage` (`number`) - Login progress percentage.
  - `emailDomain` (`string`) - Email domain (from CLoginStore, usually empty/unused).

**Returns:** `Unregisterable` - An object that can unregister the callback.

---

### `RegisterForPrepareForSystemSuspendProgress()`
```typescript
RegisterForPrepareForSystemSuspendProgress(callback: (progress: SuspendProgress) => void): Unregisterable
```
Registers a callback for system suspend preparation progress.

**Parameters:**
- `callback` (`(progress: SuspendProgress) => void`) - The callback function.

**Returns:** `Unregisterable` - An object that can unregister the callback.

---

### `RegisterForResumeSuspendedGamesProgress()`
```typescript
RegisterForResumeSuspendedGamesProgress(callback: (progress: SuspendProgress) => void): Unregisterable
```
Registers a callback for resuming suspended games progress.

**Parameters:**
- `callback` (`(progress: SuspendProgress) => void`) - The callback function.

**Returns:** `Unregisterable` - An object that can unregister the callback.

---

### `RegisterForShowHardwareSurvey()`
```typescript
RegisterForShowHardwareSurvey(callback: () => void): Unregisterable
```
Registers a callback for when the hardware survey should be shown.

**Parameters:**
- `callback` (`() => void`) - The callback function.

**Returns:** `Unregisterable` - An object that can unregister the callback.

---

### `RegisterForShutdownDone()`
```typescript
RegisterForShutdownDone(callback: (state: EShutdownStep, appid: number, param2: boolean) => void): Unregisterable
```
Register a function to be executed when shutdown completes.

**Parameters:**
- `callback` - The function to be executed on completion with the following parameters:
  - `state` (`EShutdownStep`) - The shutdown step.
  - `appid` (`number`) - The application ID.
  - `param2` (`boolean`) - Additional parameter.

**Returns:** `Unregisterable` - An object that can unregister the callback.

---

### `RegisterForShutdownFailed()`
```typescript
RegisterForShutdownFailed(callback: (state: EShutdownStep, appid: number, success: boolean) => void): Unregisterable
```
Registers a callback for when shutdown fails.

**Parameters:**
- `callback` - The callback function with the following parameters:
  - `state` (`EShutdownStep`) - The shutdown step.
  - `appid` (`number`) - The application ID.
  - `success` (`boolean`) - Whether the operation succeeded.

**Returns:** `Unregisterable` - An object that can unregister the callback.

---

### `RegisterForShutdownStart()`
```typescript
RegisterForShutdownStart(callback: (param0: boolean) => void): Unregisterable
```
Register a function to be executed when Steam starts shutting down.

**Parameters:**
- `callback` (`(param0: boolean) => void`) - The function to be executed on shutdown start.

**Returns:** `Unregisterable` - An object that can unregister the callback.

---

### `RegisterForShutdownState()`
```typescript
RegisterForShutdownState(callback: (state: EShutdownStep, appid: number, allowForceQuit: boolean) => void): Unregisterable
```
Register a function to be executed when shutdown state changes.

**Parameters:**
- `callback` - The function to be executed on change with the following parameters:
  - `state` (`EShutdownStep`) - The shutdown step.
  - `appid` (`number`) - The application ID.
  - `allowForceQuit` (`boolean`) - Whether force quit is allowed.

**Returns:** `Unregisterable` - An object that can unregister the callback.

---

### `RemoveUser()`
```typescript
RemoveUser(accountName: string): void
```
Removes an account from remembered users.

**Parameters:**
- `accountName` (`string`) - The account to remove.

**Returns:** `void`

---

### `RequestSupportSystemReport()`
```typescript
RequestSupportSystemReport(reportId: string): Promise<{ bSuccess: boolean }>
```
Requests a support system report.

**Parameters:**
- `reportId` (`string`) - The report ID.

**Returns:** `Promise<{ bSuccess: boolean }>` - Whether the request succeeded.

---

### `ResumeSuspendedGames()`
```typescript
ResumeSuspendedGames(param0: boolean): Promise<ResumeSuspendedGamesResult>
```
Resumes suspended games.

**Parameters:**
- `param0` (`boolean`) - Additional parameter.

**Returns:** `Promise<ResumeSuspendedGamesResult>` - The result of resuming games.

---

### `RunSurvey()`
```typescript
RunSurvey(callback: (surveySections: SurveySection[]) => void): void
```
Runs the hardware survey and retrieves information.

**Parameters:**
- `callback` (`(surveySections: SurveySection[]) => void`) - The callback receiving survey sections.

**Returns:** `void`

---

### `SendSurvey()`
```typescript
SendSurvey(): void
```
Sends the hardware survey results to Steam.

**Returns:** `void`

---

### `SetAsyncNotificationEnabled()`
```typescript
SetAsyncNotificationEnabled(appId: number, enable: boolean): void
```
Enables or disables async notifications for a specific app.

**Parameters:**
- `appId` (`number`) - The application ID.
- `enable` (`boolean`) - Whether to enable notifications.

**Returns:** `void`

---

### `SetLoginCredentials()`
```typescript
SetLoginCredentials(accountName: string, password: string, rememberMe: boolean): void
```
Sets given login credentials, but doesn't log in to that account.

**Parameters:**
- `accountName` (`string`) - Account name.
- `password` (`string`) - Account password.
- `rememberMe` (`boolean`) - Whether to remember that account.

**Returns:** `void`

---

### `SetOOBEComplete()`
```typescript
SetOOBEComplete(): void
```
Marks out-of-box experience (OOBE) as complete.

**Returns:** `void`

---

### `ShouldShowUserChooser()`
```typescript
ShouldShowUserChooser(): Promise<boolean>
```
Determines whether the user chooser should be shown.

**Returns:** `Promise<boolean>` - Whether to show the user chooser.

---

### `SignOutAndRestart()`
```typescript
SignOutAndRestart(): void
```
Signs out and restarts Steam.

**Returns:** `void`

---

### `StartLogin()`
```typescript
StartLogin(): void
```
Relogin after disabling offline mode.

**Returns:** `void`

**Notes:** Not commonly used; there isn't even a single mention of it in Steam's JavaScript.

---

### `StartOffline()`
```typescript
StartOffline(value: boolean): void
```
Toggles offline mode.

**Parameters:**
- `value` (`boolean`) - Whether to enable offline mode.

**Returns:** `void`

**Notes:** After disabling offline mode, you have to relogin with `StartLogin()`.

---

### `StartRestart()`
```typescript
StartRestart(force: boolean): void
```
Restarts the Steam client.

**Parameters:**
- `force` (`boolean`) - Force restart parameter (disables some checks on slow PCs).

**Returns:** `void`

---

### `StartShutdown()`
```typescript
StartShutdown(force: boolean): void
```
Initiates Steam shutdown.

**Parameters:**
- `force` (`boolean`) - Force shutdown parameter (disables some checks on slow PCs).

**Returns:** `void`

---

## Types and Interfaces

### `ConnectionAttempt`
```typescript
interface ConnectionAttempt {
    rtCooldownExpiration: number;
}
```
Information about throttled connection attempts.

**Properties:**
- `rtCooldownExpiration` (`number`) - Timestamp when the cooldown expires.

---

### `CurrentUser`
```typescript
interface CurrentUser {
    NotificationCounts: {
        async_game_updates: number;
        comments: number;
        gifts: number;
        help_request_replies: number;
        inventory_items: number;
        invites: number;
        moderator_messages: number;
        offline_messages: number;
        trade_offers: number;
    };
    bHWSurveyPending: boolean;
    bIsLimited: boolean;
    bIsOfflineMode: boolean;
    bPromptToChangePassword: boolean;
    bSupportAckOnlyMessages: boolean;
    bSupportAlertActive: boolean;
    bSupportPopupMessage: boolean;
    clientinstanceid: string;
    strAccountBalance: string;
    strAccountBalancePending: string;
    strAccountName: string;
    strFamilyGroupID: string;
    strSteamID: string;
}
```
Complete information about the current logged-in user.

**Properties:**
- `NotificationCounts` - Object containing counts for various notification types.
- `bHWSurveyPending` (`boolean`) - Whether a hardware survey is pending.
- `bIsLimited` (`boolean`) - Whether the account is limited.
- `bIsOfflineMode` (`boolean`) - Whether in offline mode.
- `bPromptToChangePassword` (`boolean`) - Whether to prompt for password change.
- `bSupportAckOnlyMessages` (`boolean`) - Support acknowledgment messages flag.
- `bSupportAlertActive` (`boolean`) - Whether a support alert is active.
- `bSupportPopupMessage` (`boolean`) - Whether to show support popup messages.
- `clientinstanceid` (`string`) - Client instance ID.
- `strAccountBalance` (`string`) - Account balance as string.
- `strAccountBalancePending` (`string`) - Pending account balance.
- `strAccountName` (`string`) - Account name.
- `strFamilyGroupID` (`string`) - Family group ID.
- `strSteamID` (`string`) - Steam ID.

---

### `ELoginState`
```typescript
enum ELoginState {
    None,
    WelcomeDialog,
    WaitingForCreateUser,
    WaitingForCredentials,
    WaitingForNetwork,
    WaitingForServerResponse,
    WaitingForLibraryReady,
    Success,
    Quit,
}
```
Enumeration of login states.

**Values:**
- `None` (0)
- `WelcomeDialog` (1)
- `WaitingForCreateUser` (2)
- `WaitingForCredentials` (3)
- `WaitingForNetwork` (4)
- `WaitingForServerResponse` (5)
- `WaitingForLibraryReady` (6)
- `Success` (7)
- `Quit` (8)

---

### `EShutdownStep`
```typescript
enum EShutdownStep {
    None,
    Start,
    WaitForGames,
    WaitForCloud,
    FinishingDownload,
    WaitForDownload,
    WaitForServiceApps,
    WaitForLogOff,
    Done,
}
```
Enumeration of shutdown steps.

**Values:**
- `None` (0)
- `Start` (1)
- `WaitForGames` (2)
- `WaitForCloud` (3)
- `FinishingDownload` (4)
- `WaitForDownload` (5)
- `WaitForServiceApps` (6)
- `WaitForLogOff` (7)
- `Done` (8)

**Notes:** `RegisterForShutdownDone` may output value 9.

---

### `ESuspendResumeProgressState`
```typescript
enum ESuspendResumeProgressState {
    Invalid,
    Complete,
    CloudSync,
    LoggingIn,
    WaitingForApp,
    Working,
}
```
Enumeration of suspend/resume progress states.

**Values:**
- `Invalid` (0)
- `Complete` (1)
- `CloudSync` (2)
- `LoggingIn` (3)
- `WaitingForApp` (4)
- `Working` (5)

---

### `LoginUser`
```typescript
interface LoginUser {
    personaName: string;
    accountName: string;
    hasPin: boolean;
    rememberPassword: boolean;
    avatarUrl: string;
}
```
Information about a remembered login user.

**Properties:**
- `personaName` (`string`) - Display name.
- `accountName` (`string`) - Account login name.
- `hasPin` (`boolean`) - Whether a PIN is set.
- `rememberPassword` (`boolean`) - Whether password is remembered.
- `avatarUrl` (`string`) - URL to the user's avatar.

---

### `ResumeSuspendedGamesResult`
```typescript
interface ResumeSuspendedGamesResult {
    nAppIDPlayingElsewhere: number;
    result: EResult;
}
```
Result of resuming suspended games.

**Properties:**
- `nAppIDPlayingElsewhere` (`number`) - App ID playing elsewhere.
- `result` (`EResult`) - The operation result code.

---

### `SuspendProgress`
```typescript
interface SuspendProgress {
    bGameSuspended: boolean;
    state: ESuspendResumeProgressState;
}
```
Progress information for suspend/resume operations.

**Properties:**
- `bGameSuspended` (`boolean`) - Whether games are suspended.
- `state` (`ESuspendResumeProgressState`) - Current progress state.

---

### `SurveyEntry`
```typescript
interface SurveyEntry {
    strName: string;
    vecArgs: string[];
}
```
A single entry in a hardware survey section.

**Properties:**
- `strName` (`string`) - Name of the survey entry.
- `vecArgs` (`string[]`) - Array of arguments/values.

---

### `SurveySection`
```typescript
interface SurveySection {
    strSectionName: string;
    vecEntries: SurveyEntry[];
}
```
A section of the hardware survey containing multiple entries.

**Properties:**
- `strSectionName` (`string`) - Name of the survey section.
- `vecEntries` (`SurveyEntry[]`) - Array of survey entries.

---

## Notes

- `EResult`, `OperationResponse`, and `Unregisterable` types are imported from the `shared` module.
- Many shutdown and restart operations include a `force` parameter that affects performance checks, primarily noticeable on slower systems.
- Offline mode changes require explicit relogin using `StartLogin()`.
- The hardware survey functionality provides detailed system information to Steam.
