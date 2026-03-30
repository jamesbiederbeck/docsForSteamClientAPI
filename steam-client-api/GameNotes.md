# GameNotes

## Overview

The `GameNotes` module provides functionality for managing game notes in the Steam client. This interface allows users to create, read, update, and delete notes associated with games, including support for images and cloud synchronization. Notes are stored in BB code format and can be synchronized between the client and server.

## Methods

### DeleteImage

```typescript
DeleteImage(param0: string): Promise<boolean>
```

Deletes an image associated with game notes.

**Parameters:**
- `param0` (string): The image identifier or filename to delete

**Returns:**
- `Promise<boolean>`: A boolean indicating whether the operation was successful

---

### DeleteNotes

```typescript
DeleteNotes(param0: string): Promise<boolean>
```

Deletes notes for a specific game.

**Parameters:**
- `param0` (string): The filename identifier for the notes to delete

**Returns:**
- `Promise<boolean>`: A boolean indicating whether the operation was successful

---

### GetNotes

```typescript
GetNotes(filenameForNotes: string, directoryForNoteImages: string): Promise<Notes>
```

Retrieves notes for a specific game.

**Parameters:**
- `filenameForNotes` (string): The filename identifier for the notes
- `directoryForNoteImages` (string): The directory path where note images are stored

**Returns:**
- `Promise<Notes>`: A promise that resolves to a `Notes` object containing the result and notes data

---

### GetNotesMetadata

```typescript
GetNotesMetadata(note: string): Promise<NoteMetadata>
```

Retrieves metadata information for a specific note.

**Parameters:**
- `note` (string): The note identifier

**Returns:**
- `Promise<NoteMetadata>`: A promise that resolves to metadata about the note

---

### GetNumNotes

```typescript
GetNumNotes(): Promise<number>
```

Gets the total number of notes stored.

**Returns:**
- `Promise<number>`: The total count of notes

---

### GetQuota

```typescript
GetQuota: Promise<NotesQuota>
```

Retrieves the storage quota information for game notes.

**Returns:**
- `Promise<NotesQuota>`: Information about storage quota including bytes available and file count limits

---

### IterateNotes

```typescript
IterateNotes(appId: number, length: number): Promise<NoteMetadata[]>
```

Iterates through notes for a specific application.

**Parameters:**
- `appId` (number): The Steam application ID
- `length` (number): The number of notes to retrieve

**Returns:**
- `Promise<NoteMetadata[]>`: An array of note metadata objects

---

### ResolveSyncConflicts

```typescript
ResolveSyncConflicts(param0: boolean): Promise<EResult>
```

Resolves synchronization conflicts between local and cloud-stored notes.

**Parameters:**
- `param0` (boolean): Flag indicating how to resolve conflicts

**Returns:**
- `Promise<EResult>`: The result of the conflict resolution operation

---

### SaveNotes

```typescript
SaveNotes(filenameForNotes: string, notes: string): Promise<EResult>
```

Saves notes to storage.

**Parameters:**
- `filenameForNotes` (string): The filename identifier where notes should be saved
- `notes` (string): Escaped JSON array of `Note` objects

**Returns:**
- `Promise<EResult>`: The result of the save operation

---

### SyncToClient

```typescript
SyncToClient(): Promise<EResult>
```

Synchronizes notes from the server to the client.

**Returns:**
- `Promise<EResult>`: The result of the synchronization operation

---

### SyncToServer

```typescript
SyncToServer(): Promise<EResult>
```

Synchronizes notes from the client to the server.

**Returns:**
- `Promise<EResult>`: The result of the synchronization operation

---

### UploadImage

```typescript
UploadImage(imageFileNamePrefix: string, mimeType: string, base64: string): Promise<EResult | OperationResponse>
```

Uploads an image to be used in game notes.

**Parameters:**
- `imageFileNamePrefix` (string): The prefix for the image filename
- `mimeType` (string): Image MIME type (e.g., "image/png", "image/jpeg")
- `base64` (string): Image contents encoded in base64 format

**Returns:**
- `Promise<EResult | OperationResponse>`: An image file name with its extension that's meant to be used as a part of some URL

**Throws:**
- `OperationResponse`: Throws if invalid MIME type or unable to parse base64 (but not if the operation simply failed)

## Types/Interfaces

### Note

```typescript
interface Note {
    appid: number;
    id: string;
    content: string;
    ordinal: number;
    time_created: number;
    time_modified: number;
    title: string;
}
```

Represents a single game note.

**Properties:**
- `appid` (number): The Steam application ID this note belongs to
- `id` (string): Unique identifier for the note
- `content` (string): Note contents in BB code format
- `ordinal` (number): Order/position of the note
- `time_created` (number): Unix timestamp when the note was created
- `time_modified` (number): Unix timestamp when the note was last modified
- `title` (string): The title of the note

---

### Notes

```typescript
interface Notes {
    result: EResult;
    notes?: string;
}
```

Response object containing notes data.

**Properties:**
- `result` (EResult): The result status of the operation
- `notes` (string, optional): Escaped JSON array of `Note` objects. Not present if `result` is `EResult.FileNotFound`

---

### NoteMetadata

```typescript
interface NoteMetadata {
    filename: string;
    filesize: number;
    result: EResult;
    timestamp: number;
}
```

Metadata information about a note.

**Properties:**
- `filename` (string): The filename associated with the note
- `filesize` (number): Size of the note file in bytes
- `result` (EResult): The result status
- `timestamp` (number): Unix timestamp associated with the note

---

### NotesQuota

```typescript
interface NotesQuota {
    bytes: number;
    bytesAvailable: number;
    numFiles: number;
    numFilesAvailable: number;
}
```

Storage quota information for game notes.

**Properties:**
- `bytes` (number): Total bytes allocated for notes storage
- `bytesAvailable` (number): Remaining bytes available for use
- `numFiles` (number): Total number of files allocated
- `numFilesAvailable` (number): Remaining file slots available

## Notes

- All notes are stored in BB code format for the `content` field
- Notes support cloud synchronization between client and server
- Images can be embedded in notes and are managed separately from the note content
- The `SaveNotes` method expects notes to be passed as an escaped JSON array string
- When retrieving notes, check the `result` field to determine if the operation was successful before accessing the `notes` field
