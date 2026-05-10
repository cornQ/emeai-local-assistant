# Changelog

Project changes are listed here in release order.

## v1.0.3 Beta

Released: 2026-05-10

This release focuses on Chrome local AI session stability, clear debugging, and recovery guidance when the browser model process crashes.

### Fixed

- Normal text chat no longer depends on image input support.
- The app tries a simpler Chrome model session if strict model options are rejected.
- The app retries once when Chrome returns a destroyed session or unknown model session error.
- Text chat and image input checks are handled separately.

### Added

- `emeAIDebugModel()` Console helper for checking:
  - basic model availability
  - text model availability
  - image model availability
  - current app version
- Toast message when Chrome local AI crashes too many times.
- Copy button for the Windows Chrome close command inside the crash toast.

### Notes

- If Chrome local AI crashes too many times, fully close Chrome and relaunch it.
- Image attachment support still depends on the user's Chrome Prompt API build.
- The visible app version format is `v1.0.3 Beta`.

## v1.0.2 Beta

Released: 2026-05-10

First public beta release.

### Added

- Local Chrome AI chat workspace.
- Chat history saved in browser localStorage.
- Chat search, rename, export, import, and trash.
- Dark mode, light mode, compact mode, and regular mode.
- Voice to text input.
- Stop generation button.
- Reload resume for unfinished text prompts.
- Safe attachment support for TXT, MD, PDF, DOCX, PNG, JPG, JPEG, and WEBP.
- Strict public file guard.
- Dynamic version display from `CHANGELOG.json`.
- Local setup guide.
- MIT License.
