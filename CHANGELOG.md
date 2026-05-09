# Changelog

All notable project changes are written here in plain language.

## v1.0.2 Beta

Released: 2026-05-10

### Changed

```text
Added a clear PowerShell command note in README.md.
Highlighted that cd /d works in CMD, not PowerShell.
Added a fix note for the Directory listing page.
Updated the app version shown from CHANGELOG.json.
```

## v1.0.1 Beta (Initial release)

Released: 2026-05-10

This is the first public beta release of emeAI.

### Added

```text
Local Chrome AI chat workspace
Chat history saved in browser localStorage
Search chats
Rename chats
Export and import single chat JSON
Move chats to trash
Restore chats from trash
Delete chats forever
Dark and light mode
Compact and regular layout
Voice to text
Stop generation
Reload resume for unfinished text prompts
TXT and MD text attachment reading
PDF text extraction
DOCX text extraction
Image attachment support for supported Chrome Prompt API builds
Strict public file guard
Dynamic version display from CHANGELOG.json
Branding guide for changing app name, logo, and favicon
MIT License information
Full local setup guide in README.md
```

### Security notes

```text
The app does not run uploaded files.
Approved files are read as plain text or browser decoded image data.
Risky file types are blocked before reading.
Public mode allows TXT, MD, PDF, DOCX, PNG, JPG, JPEG, and WEBP only.
```

### Known notes

```text
Chrome built in AI must be available in the user's Chrome setup.
Image input depends on the Chrome Prompt API build.
PDF and DOCX reading use browser loaded helper libraries.
Open the app through localhost, not file://.
```
