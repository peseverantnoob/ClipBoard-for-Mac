# ClipSlots is a ClipBoard-for-Mac

It's a native macOS menu bar clipboard manager with two keyboard-accessible slots and 30 recent plain-text copies. It keeps slots and history in memory, so both clear when the app quits. It requires macOS 14 or later and Xcode Command Line Tools with Swift 6 or later.

## Build and launch

```sh
swift test
./scripts/build_and_run.sh
```

Pass `--debug` to build and launch a debug version. The script assembles `build/ClipSlots.app`, signs it with your **ClipSlots Dev** Keychain signing identity when available, and opens the app. If macOS prompts, allow `codesign` to use the signing key. Ad-hoc signing may require you to grant Accessibility again after rebuilding.

## First launch

1. Click the clipboard icon in the menu bar, then click **Open Accessibility Settings**.
2. In **System Settings → Privacy & Security → Accessibility**, enable **ClipSlots**. If it is missing, use **+** and select `build/ClipSlots.app` from this directory.
3. Return to the ClipSlots menu and click **Refresh**. If macOS asks you to reopen the app, quit it and reopen the same app bundle.

## Shortcuts

| Slot | Copy selection | Paste into the active app |
| --- | --- | --- |
| 1 | ⌥⌘C | ⌥⌘V |
| 2 | ⌃⌘C | ⌃⌘V |

Release Option or Control promptly after pressing the shortcut. ClipSlots waits up to 300 ms for those modifiers to be released. Slot shortcuts preserve the system clipboard. The copy buttons in the menu and clicks on history rows intentionally replace the system clipboard so you can use ordinary ⌘V.

Regular copies appear in History. You can search, copy, or delete items from the menu. **Clear All** empties the slots and history. Clipboard items marked concealed, transient, or auto-generated are ignored.
