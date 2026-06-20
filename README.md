# SavePass - Smart Notepad Credential Vault

SavePass is a local-first, privacy-respecting desktop application designed to bridge the gap between unstructured notepad logs and structured password managers. Write or paste your unstructured credential dumps (e.g., server details, database credentials, API tokens) as raw text, and SavePass will automatically parse them into beautiful, organized, and searchable "Smart Cards" with quick copy, auto-type, security auditing, and offline revision history.

---

## Key Features

- **Smart Notation Parser**: Instantly turns plain-text notepad entries into structured interactive cards.
- **Global Hotkey Pinned HUD (`Alt + Shift + C`)**: Access a compact panel of your pinned credentials system-wide from any external application. Click to copy and automatically hide.
- **Command Palette (`Ctrl + K`)**: Navigate tabs, search credentials, and copy keys instantly without lifting your hands from the keyboard.
- **Auto-Type Desktop Helper**: Automatically minimizes the app, focuses your last active window, types the username, tabs, types the password, and logs you in automatically.
- **Local-First & Offline History**: Zero network requirements. Every modification in the raw editor creates local revision history so you can revert edits at any time.
- **Password Expiry Tracker**: Flags passwords older than 6 months (180 days) for security hygiene.
- **Customizable Premium Themes**: Switch between Sapphire, Emerald, Carbon, and Amber themes.
- **Optional Git Sync**: Setup a private repository to sync and backup your credentials securely with a single click.

---

## Installation & Getting Started

SavePass is distributed as a standard Windows application installer.

1. **Download the Installer**:
   - Download **`SavePassSetup.exe`** from the release files.
2. **Run the Installer**:
   - Double-click `SavePassSetup.exe` and follow the installation wizard.
   - The installer will automatically add a desktop icon and shortcut for easy access.
3. **First Launch**:
   - Start SavePass. It will load a default vault configuration to show you the layout.
   - Go to the **Raw Notepad Editor** tab to paste or write your credentials.

---

## Plain-Text Notation Format

Separate each credential block using a **blank line** (double newlines). Title line goes first, followed by key-value configurations and command actions:

```text
Acme Staging Server:
category: ssh
pinned: true
uname: deploy_user
pass: zX9#wV2!rK8*mQ
host: 10.0.8.25
tags: staging, infrastructure
updated: 2026-06-15
ssh deploy_user@10.0.8.25 -p 22

Customer Portal DB:
category: database
uname: db_reader
pass: kY1@jC6$pL9#vW2!
host: postgres-staging.local
DB Port: 5432
```

### Parser Rules & Fields:
- **Title Line**: The first line of a block (before any keys or commands).
- **category**: Standard categories: `database`, `ssh`, `token`, `web`, or `other`.
- **pinned**: Set to `true` or `yes` to keep this entry pinned to the Security Dashboard.
- **uname / username / email**: Username credentials.
- **pass / password**: Automatically masked secrets with copy shortcuts.
- **host / ip**: Host address or domain name.
- **updated / date**: Date format `YYYY-MM-DD` used for tracking password age.
- **custom fields**: Any `Key: Value` line that is not a standard keyword.
- **commands**: Lines starting with shell protocols (e.g. `ssh `, `docker `) are parsed as runnable command shortcuts.
