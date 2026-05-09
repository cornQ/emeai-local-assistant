# emeAI

emeAI is a small local AI chat app that runs inside Google Chrome. It is made for people who want a private writing, learning, coding, and document review space without setting up a cloud API.

The app uses Chrome built in local AI through the `LanguageModel` API. Your chats stay in your browser storage. Files are read inside the browser as safe text or image data. There is no backend in this release.

This project is useful when you want:

```text
A simple local AI chat workspace
A clean UI that is easy to edit
Private browser based chat history
Safe document and image attachment testing
A starter project for Chrome built in AI experiments
```

## Screenshot

![emeAI Dashboard](./screenshots/dashboad.png)

## Version

Current version:

```text
v1.0.2 Beta
```

The app dashboard reads the version from:

```text
CHANGELOG.json
```

The left sidebar shows the version automatically when the app runs on `localhost`.

For GitHub readers, a normal changelog is also available here:

```text
CHANGELOG.md
```

## Feature list

```text
Local Chrome AI chat
Chat history saved in browser localStorage
Search chats
Rename chats
Export single chat JSON
Import single chat JSON
Move chats to trash
Restore chats from trash
Delete chats forever
Dark mode
Light mode
Compact mode
Regular mode
Voice to text
Stop generation
Reload resume for unfinished text prompts
Safe file attachments
TXT and MD reading
PDF text extraction
DOCX text extraction
Image attachment support for supported Chrome builds
Strict public file guard
Dynamic version display from CHANGELOG.json
```

## Recommended project location

Do not keep the project inside `Downloads`, `Desktop`, or Chrome's user data folder.

Recommended Windows location:

```text
C:\Projects\emeAI
```

Another simple Windows path is also fine:

```text
C:\project\emeAI
```

Recommended CORNQ workspace location:

```text
C:\Projects\CORNQ\emeAI
```

Recommended macOS or Linux location:

```text
~/Projects/emeAI
```

Good project location helps with:

```text
Cleaner terminal commands
Fewer permission problems
Easier Git setup
Less chance of deleting files by mistake
```

## Required software

Install or prepare:

```text
Google Chrome with built in AI support
Python 3
VS Code or any code editor
Git, only if you want to publish on GitHub
```

Python is only used to run a local web server. The app itself is plain HTML, CSS, and JavaScript.

## Chrome setup for local AI

Open Chrome and go to:

```text
chrome://flags
```

Enable these flags:

```text
Prompt API for Gemini Nano with Multimodal Input
Enables optimization guide on device
```

Relaunch Chrome after enabling the flags.

If the exact names change in your Chrome build, search in `chrome://flags` using:

```text
Prompt API
Gemini Nano
Optimization Guide
On Device Model
```

## Activate and test from Console

Open any normal Chrome tab, then open DevTools:

```text
Right click
Inspect
Console
```

Check availability:

```js
await LanguageModel.availability()
```

Possible results:

```text
available
downloadable
downloading
unavailable
```

Meaning:

```text
available      The local model is ready.
downloadable   Chrome can download the local model.
downloading    Chrome is downloading the local model.
unavailable    Your current Chrome setup or device cannot use it right now.
```

If it returns `downloadable` or `available`, test with:

```js
const session = await LanguageModel.create()
await session.prompt("Say hello in one short sentence.")
```

The first run may trigger a model download. Wait for Chrome to finish.

## Install on local PC

### Step 1: Create a project folder

Windows PowerShell:

```powershell
mkdir C:\Projects
mkdir C:\Projects\emeAI
```

macOS or Linux:

```bash
mkdir -p ~/Projects/emeAI
```

### Step 2: Copy files into the folder

After extracting the zip, your folder should look like this:

```text
emeAI
├── CHANGELOG.json
├── CHANGELOG.md
├── LICENSE
├── README.md
├── index.html
├── assets
│   ├── emeai-icon.svg
│   └── emeai-logo.svg
├── css
│   └── style.css
└── js
    └── app.js
```

### Step 3: Open terminal in the project folder

Windows PowerShell:

```powershell
cd C:\Projects\emeAI
```

Important for PowerShell:

```text
Do not use cd /d in PowerShell.
cd /d is for CMD, not PowerShell.
```

Wrong in PowerShell:

```powershell
cd /d C:\Projects\emeAI
```

Correct in PowerShell:

```powershell
cd C:\Projects\emeAI
```

CMD users can use:

```cmd
cd /d C:\Projects\emeAI
```

macOS or Linux:

```bash
cd ~/Projects/emeAI
```

### Step 4: Start local server

Run:

```bash
python -m http.server 8000
```

If your system uses `python3`, run:

```bash
python3 -m http.server 8000
```

### Step 5: Open the app

Open Chrome:

```text
http://localhost:8000/
```

Do not open the app with `file://`.

Use `localhost` because:

```text
Chrome local AI works better there
CHANGELOG.json can be loaded
Browser file reading behaves properly
The version can show in the sidebar
```

## How to use the app

### New chat

Click:

```text
New chat
```

### Send message

Type a message and press:

```text
Enter
```

For a new line, press:

```text
Shift + Enter
```

### Stop generation

When the model is generating, the send button changes to a stop button.

Click stop to cancel the current generation.

### Voice to text

Click the microphone button.

Chrome may ask for microphone permission. Allow it only if you want voice input.

### Attach files

Click the attach button beside the message box.

Allowed files in public mode:

```text
TXT
MD
PDF
DOCX
PNG
JPG
JPEG
WEBP
```

Blocked files include:

```text
Executable files
Installers
Scripts
Archives
Macro enabled Office files
SVG files
Code files
Unknown extensionless files
```

The app reads approved documents as text. It reads approved images as browser decoded image data. It does not run uploaded files.

## Attachment limits

```text
Max files per message: 5
Max file size: 10 MB
Max total attachment size: 25 MB
Max image resolution: about 12 megapixels
Max extracted document text: 12000 characters per file
```

These values are in:

```text
js/app.js
```

Look for:

```js
MAX_FILES_PER_MESSAGE
MAX_FILE_SIZE_BYTES
MAX_TOTAL_FILE_SIZE_BYTES
MAX_IMAGE_PIXELS
MAX_ATTACHMENT_TEXT_CHARS
```

## Public safety notes

The upload guard checks files before reading them.

It checks:

```text
File extension
Risky file type
Double extension tricks
File size
Total file size
Image MIME type
Image resolution
```

It also strips some unsafe text patterns after document extraction.

Important:

```text
The app never executes uploaded files.
```

For future backend work:

```text
Repeat all file checks on the server.
Do not trust browser checks as the only security layer.
```

## Change app name, logo, and favicon

You are allowed to modify the app name, logo, and favicon.

### Change app name in HTML

Open:

```text
index.html
```

Find:

```html
<title>emeAI - Your Private Assistant</title>
```

Change it to your app name.

Find:

```html
<h1 class="brandWordmark"><span class="emePart">eme</span><span class="aiPart">AI</span></h1>
```

Change the text inside the spans.

Also update the empty state text if needed:

```html
<div class="heroBadge">emeAI</div>
<h2>Start a private local AI chat</h2>
```

### Change app name in JavaScript text

Open:

```text
js/app.js
```

Search for:

```text
emeAI
```

Update user facing text only. Do not change storage keys unless you want a fresh browser storage namespace.

Current storage keys include:

```js
emeAI.core.chats.v2
emeAI.core.activeChat.v2
emeAI.core.theme.v1
emeAI.core.density.v1
```

Changing these keys will make old local chats not appear under the new key.

### Change favicon

Replace this file:

```text
assets/emeai-icon.svg
```

Or edit this line in `index.html`:

```html
<link rel="icon" href="./assets/emeai-icon.svg" type="image/svg+xml" />
```

Use your own file path.

### Change logo

Replace these files:

```text
assets/emeai-icon.svg
assets/emeai-logo.svg
```

The current sidebar uses:

```html
<img class="brandIcon" src="./assets/emeai-icon.svg" alt="emeAI icon" />
```

If you want to use a full logo image instead of text, edit the brand area in `index.html`.

### Change colors

Open:

```text
css/style.css
```

At the top, update the CSS variables inside:

```css
:root {
}
```

Common variables to change:

```text
--accent
--accent2
--bg
--panel
--text
--muted
```

## Project files

### index.html

Contains:

```text
Sidebar
Topbar
Chat area
Composer
File attach input
Voice button
Stop button
Version display
Script links
```

### css/style.css

Contains:

```text
Theme styles
Layout
Sidebar
Chat bubbles
Composer
Attachment chips
Stop button
Version panel
Responsive layout
```

### js/app.js

Contains:

```text
Chat storage
Message rendering
Chrome LanguageModel session
Prompt sending
Stop generation
Reload resume
Attachment guard
File reading
Voice to text
Theme toggle
Compact mode
Trash
Import and export
Version loader
```

### CHANGELOG.json

Used by the app to show the version.

### CHANGELOG.md

Used by GitHub readers to understand release history.

### LICENSE

MIT License for public use.

## Update version number

Open:

```text
CHANGELOG.json
```

Update:

```json
{
  "version": "1.0.2",
  "channel": "Beta",
  "label": "Next update",
  "displayVersion": "v1.0.2 Beta (Next update)"
}
```

Then update:

```text
CHANGELOG.md
README.md
```

Reload the app on:

```text
http://localhost:8000/
```

The sidebar should show the new version.

## GitHub setup

Open terminal inside the project folder:

```bash
git init
git add .
git commit -m "Initial beta release"
```

Add your GitHub remote:

```bash
git remote add origin https://github.com/your-username/emeAI.git
git branch -M main
git push -u origin main
```

Replace:

```text
your-username
```

with your GitHub username.

## Suggested .gitignore

Create:

```text
.gitignore
```

Suggested content:

```gitignore
.DS_Store
Thumbs.db
.vscode/
.idea/
*.log
node_modules/
dist/
build/
.env
```

## Common issues

### Browser shows Directory listing for /

This means the local server is running from the wrong folder.

Stop the server first:

```text
Ctrl + C
```

Then go to the folder that contains `index.html`.

PowerShell example:

```powershell
cd C:\Projects\emeAI
dir
python -m http.server 8000
```

Before starting the server, `dir` should show:

```text
index.html
CHANGELOG.json
css
js
assets
```

If you see only user folders like `Desktop`, `Documents`, or `Downloads`, you are in the wrong folder.

PowerShell reminder:

```text
Use cd C:\Projects\emeAI
Do not use cd /d C:\Projects\emeAI
```

### Model does not work

Run:

```js
await LanguageModel.availability()
```

Check:

```text
Chrome version
Chrome flags
Device support
Available storage
Model download status
```

### Version shows v0.0.0-local

You probably opened the app with `file://`.

Run:

```bash
python -m http.server 8000
```

Then open:

```text
http://localhost:8000/
```

### PDF or DOCX does not read

This build uses browser loaded helper libraries for PDF and DOCX reading.

Check:

```text
Internet connection
CDN script loading
Browser Console errors
```

For full offline use, download the helper libraries and update script paths in `index.html`.

### Image upload gives a model error

Image support depends on your Chrome Prompt API build.

Text prompts and document text reading can still work even if image input is not available.

### Microphone does not work

Check:

```text
Chrome microphone permission
SpeechRecognition support
localhost URL
```

### Old UI appears after replacing files

Hard refresh Chrome:

```text
Ctrl + Shift + R
```

Or use:

```text
DevTools
Right click reload
Empty Cache and Hard Reload
```

## Before publishing a new release

Check:

```text
Open the app on localhost
Send a text prompt
Stop a running generation
Switch theme
Switch compact mode
Rename a chat
Move a chat to trash
Restore a chat
Attach a TXT or MD file
Attach a PDF file
Attach a DOCX file
Attach one image if your Chrome build supports it
Update CHANGELOG.json
Update CHANGELOG.md
Update README.md current version
Run node syntax check
```

Syntax check:

```bash
node --check js/app.js
```


## Privacy note

emeAI is local first in this beta release.

```text
Chats are saved in browser localStorage
Files are read in the browser
There is no backend
There is no login system
There is no cloud sync
```

## License

This project is released under the **MIT License**.

That means people are allowed to:

```text
Use it
Copy it
Modify it
Publish it
Distribute it
Use it in private or commercial projects
```

Please keep the original license notice when copying or publishing this project.

See the full license text in the [LICENSE](./LICENSE) file.

