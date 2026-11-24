# ClipSlots

A lightweight, native macOS menu bar clipboard manager that gives you **two additional dedicated clipboard slots** and a **30-item plain-text history**—all stored strictly in memory.

## Features

- **2 Extra Clipboard Slots:** Copy and paste independent snippets via global shortcuts without overwriting your system clipboard.
- **Plain-Text History:** Automatically tracks your 30 most recent standard copies. Search, copy, or delete individual entries directly from the menu bar, or wipe everything with **Clear All**.
- **Privacy-First & Ephemeral:** Slots and history live exclusively in RAM and clear automatically when you quit the app. Items marked as concealed, transient, or auto-generated (such as password manager copies) are ignored.

## Requirements

- macOS 14 (Sonoma) or later
- Xcode Command Line Tools with Swift 6 or later

## Build & Run

Run the test suite and build the app bundle:

```sh
swift test
./scripts/build_and_run.sh
```

Pass `--debug` to build and launch a debug configuration:

```sh
./scripts/build_and_run.sh --debug
```

The script assembles `build/ClipSlots.app`, signs it with your **ClipSlots Dev** Keychain signing identity when available, and launches it.

> [!NOTE]
> If macOS prompts you during the build, allow `codesign` to access the signing key. If you build with ad-hoc signing instead, you may need to re-grant Accessibility permission after rebuilding.

## First Launch

ClipSlots needs Accessibility access to listen for global shortcuts and paste into active apps.

1. Click the **clipboard icon** in the menu bar and select **Open Accessibility Settings**.
2. In **System Settings → Privacy & Security → Accessibility**, enable **ClipSlots**. If it is not listed, click **+** and select `build/ClipSlots.app` from this repository.
3. Return to the ClipSlots menu and click **Refresh**. If macOS prompts you to reopen the app, quit and relaunch the same app bundle.

## Shortcuts & Usage

| Slot | Copy selection | Paste into active app |
| :--- | :--- | :--- |
| **Slot 1** | <kbd>⌥</kbd><kbd>⌘</kbd><kbd>C</kbd> | <kbd>⌥</kbd><kbd>⌘</kbd><kbd>V</kbd> |
| **Slot 2** | <kbd>⌃</kbd><kbd>⌘</kbd><kbd>C</kbd> | <kbd>⌃</kbd><kbd>⌘</kbd><kbd>V</kbd> |

- **Modifier release:** Release <kbd>⌥</kbd> (Option) or <kbd>⌃</kbd> (Control) promptly after pressing a shortcut—ClipSlots waits up to 300 ms for modifier keys to release.
- **System clipboard behavior:** Slot shortcuts leave your standard system clipboard untouched. Clicking a menu copy button or a history row intentionally replaces the system clipboard so you can paste normally with <kbd>⌘</kbd><kbd>V</kbd>.
