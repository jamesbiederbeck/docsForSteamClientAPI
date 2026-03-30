# Steam Client API Documentation

This directory contains comprehensive markdown documentation for the Steam Client API TypeScript interfaces.

## Documentation Files

### 1. App.md
**Size:** 73KB  
**Source:** `/tmp/decky-frontend-lib/src/globals/steam-client/App.ts` (1,749 lines)

Comprehensive documentation for the Apps interface, which provides functionality for managing Steam applications including:
- Application installation, launching, and termination
- Non-Steam shortcuts management
- Workshop items and DLC handling
- Achievement and playtime tracking
- Screenshot management
- Compatibility tools and Proton configuration
- Game backups and verification
- 100+ methods, 80+ types/interfaces/enums

### 2. Auth.md
**Size:** 6.7KB  
**Source:** `/tmp/decky-frontend-lib/src/globals/steam-client/Auth.ts` (106 lines)

Documentation for the Auth interface, covering authentication and security features:
- Cached sign-in PIN management
- Refresh token handling
- Steam Guard data management
- Machine identification
- Secure computer settings
- 13 methods, 5 types/interfaces/enums

### 3. Broadcast.md
**Size:** 4.1KB  
**Source:** `/tmp/decky-frontend-lib/src/globals/steam-client/Broadcast.ts` (57 lines)

Documentation for the Broadcast interface for game broadcasting features:
- Broadcast start/stop operations
- Viewer request management
- User invitations
- Broadcast status monitoring
- Event callbacks
- 6 methods, 1 primary interface

## Documentation Structure

Each documentation file follows a consistent structure:

1. **Title** - Module name
2. **Overview** - High-level description of the module's purpose
3. **Methods** - Detailed documentation of all methods including:
   - Method signatures with TypeScript types
   - Parameter descriptions
   - Return type descriptions
   - JSDoc comments and remarks
4. **Types and Interfaces** - Complete documentation of all:
   - Interfaces
   - Type aliases
   - Enums
5. **Notes** - Important usage information and caveats

## Format

All code blocks are formatted with proper TypeScript syntax highlighting using triple backticks with the `typescript` language identifier.

## Source

These documentation files were generated from the Decky Frontend Library TypeScript definitions, which provide type-safe access to the Steam Client's internal APIs.

---

*Generated: March 30, 2024*
