# Auth

The Auth interface provides authentication and security-related functionality for the Steam client, including managing cached sign-in PINs, refresh tokens, and Steam Guard data.

## Overview

The `Auth` interface handles various authentication operations in the Steam client, including:
- Managing cached sign-in PINs for quick authentication
- Handling refresh tokens for maintaining login sessions
- Working with Steam Guard authentication data
- Retrieving machine identification information
- Managing secure computer settings

## Methods

### ClearCachedSignInPin
```typescript
ClearCachedSignInPin(): Promise<boolean>
```
Clears the cached sign-in PIN for the current user.

**Returns:** A boolean indicating if the operation succeeded

---

### CurrentUserHasCachedSignInPin
```typescript
CurrentUserHasCachedSignInPin(): Promise<boolean>
```
Checks if the current user has a cached sign-in PIN.

**Returns:** A boolean indicating if a cached PIN exists

---

### GetLocalHostname
```typescript
GetLocalHostname(): Promise<string>
```
Retrieves the local hostname of the machine.

**Returns:** The local hostname as a string

---

### GetMachineID
```typescript
GetMachineID(): Promise<ArrayBuffer>
```
Retrieves the machine ID.

**Returns:** A ProtoBuf message. If deserialized, returns CAuthentication_DeviceDetails

---

### GetRefreshInfo
```typescript
GetRefreshInfo(): Promise<AuthRefreshInfo>
```
Gets the current authentication refresh information.

**Returns:** AuthRefreshInfo object containing refresh token details

---

### GetSteamGuardData
```typescript
GetSteamGuardData(param0: string): Promise<SteamGuardData>
```
Retrieves Steam Guard data for a specific account.

**Parameters:**
- `param0` - Account identifier

**Returns:** SteamGuardData object containing guard data and result status

---

### IsSecureComputer
```typescript
IsSecureComputer(): Promise<boolean>
```
Checks if the current computer is marked as secure (unshared).

**Returns:** A boolean indicating if the computer is secure

**Remarks:** "Secured" refers to unshared

---

### SetCachedSignInPin
```typescript
SetCachedSignInPin(pin: string): Promise<boolean>
```
Sets a cached sign-in PIN for quick authentication.

**Parameters:**
- `pin` - The PIN to cache

**Returns:** A boolean indicating if the operation succeeded

---

### SetLoginToken
```typescript
SetLoginToken(refreshToken: string, accountName: string): Promise<OperationResponse>
```
Sets the login token (refresh token) for an account.

**Parameters:**
- `refreshToken` - The refresh token to set
- `accountName` - The name of the account

**Returns:** OperationResponse indicating the result of the operation

---

### SetSteamGuardData
```typescript
SetSteamGuardData(accountName: string, newGuardData: string): void
```
Sets new Steam Guard data for a specific account.

**Parameters:**
- `accountName` - The name of the account
- `newGuardData` - The new Steam Guard data to set

---

### StartSignInFromCache
```typescript
StartSignInFromCache(accountName: string, offlineMode: boolean): Promise<OperationResponse | void>
```
Starts the sign-in process using cached credentials.

**Parameters:**
- `accountName` - The name of the account to sign in
- `offlineMode` - Whether to sign in in offline mode

**Returns:** OperationResponse or void

---

### UserHasCachedSignInPin
```typescript
UserHasCachedSignInPin(accountName: string): Promise<boolean>
```
Checks if a specific user has a cached sign-in PIN.

**Parameters:**
- `accountName` - The name of the account to check

**Returns:** A boolean indicating if a cached PIN exists for the user

---

### ValidateCachedSignInPin
```typescript
ValidateCachedSignInPin(accountName: string, pin: string): Promise<boolean>
```
Validates a cached sign-in PIN for a specific account.

**Parameters:**
- `accountName` - The name of the account
- `pin` - The PIN to validate

**Returns:** A boolean indicating if the PIN is valid

---

## Types and Interfaces

### AuthRefreshInfo
```typescript
interface AuthRefreshInfo {
  reason: number;
  account_name: string;
  login_id_token: string;
}
```
Contains authentication refresh information.

**Properties:**
- `reason` - Numeric reason code for the refresh
- `account_name` - The account name
- `login_id_token` - The login ID token

---

### SteamGuardData
```typescript
interface SteamGuardData {
  data: string;
  eresult: EResult;
}
```
Contains Steam Guard authentication data.

**Properties:**
- `data` - The Steam Guard data
- `eresult` - Result code indicating success or failure

---

### CAuthentication_DeviceDetails
```typescript
interface CAuthentication_DeviceDetails extends JsPbMessage {
  client_count(): number | undefined;
  device_friendly_name(): string | undefined;
  gaming_device_type(): EGamingDeviceType | undefined;
  machine_id(): Uint8Array | string;
  os_type(): EOSType | undefined;
  platform_type(): EAuthTokenPlatformType | undefined;
  set_client_count(): any;
  set_device_friendly_name(): any;
  set_gaming_device_type(): any;
  set_machine_id(): any;
  set_os_type(): any;
  set_platform_type(): any;
}
```
Represents device details for authentication. This is a ProtoBuf message interface.

**Usage Note:**
The `deserializeBinary` argument should be:
```typescript
[
  await SteamClient.System.GetOSType(),
  await SteamClient.Auth.GetLocalHostname(),
  await SteamClient.Auth.GetMachineID(),
]
```

---

### EAuthTokenPlatformType
```typescript
enum EAuthTokenPlatformType {
  Unknown,
  SteamClient,
  WebBrowser,
  MobileApp
}
```
Represents the platform type for authentication tokens.

**Values:**
- `Unknown` (0) - Unknown platform
- `SteamClient` (1) - Steam desktop client
- `WebBrowser` (2) - Web browser
- `MobileApp` (3) - Mobile application

---

### EGamingDeviceType
```typescript
enum EGamingDeviceType {
  Unknown,
  StandardPC,
  Console = 256,
  PS3 = 272,
  Steambox = 288,
  Tesla = 320,
  Handheld = 512,
  Phone = 528,
  SteamDeck = 544
}
```
Represents the type of gaming device.

**Values:**
- `Unknown` (0) - Unknown device type
- `StandardPC` (1) - Standard PC
- `Console` (256) - Generic console
- `PS3` (272) - PlayStation 3
- `Steambox` (288) - Steam Box
- `Tesla` (320) - Tesla device
- `Handheld` (512) - Generic handheld device
- `Phone` (528) - Phone
- `SteamDeck` (544) - Steam Deck

---

## Notes

- The Auth interface works closely with Steam's authentication system
- Many methods deal with cached credentials for quick sign-in
- Steam Guard provides two-factor authentication protection
- Machine IDs are used to identify unique devices
- Refresh tokens maintain authentication sessions without requiring password re-entry
- ProtoBuf messages require deserialization to access structured data
- The "secure computer" setting determines whether credentials can be cached
