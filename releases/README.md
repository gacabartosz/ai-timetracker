# Windows Releases

This folder contains pre-built Windows executables that are automatically generated on every push to `main`.

## Files

| File | Description |
|------|-------------|
| `TimeTracker-Setup-x64.exe` | Windows installer (recommended) |
| `TimeTracker-latest-portable.zip` | Portable version (no installation required) |
| `TimeTracker-Setup-x64-X.Y.Z.exe` | Versioned installer |
| `TimeTracker-X.Y.Z-portable.zip` | Versioned portable package |

## Installation

### Option 1: Installer (Recommended)
1. Download `TimeTracker-Setup-x64.exe`
2. Run the installer
3. Launch "AI TimeTracker" from Start Menu

### Option 2: Portable
1. Download `TimeTracker-latest-portable.zip`
2. Extract to any folder
3. Run `TimeTracker.bat` or `TimeTracker.ps1`

## Requirements

- **ActivityWatch** - Required for tracking activities
  - Download from: https://activitywatch.net/downloads/
- **Jira/Tempo API tokens** - Configure in Settings after first launch

## Auto-Build

These files are automatically updated by GitHub Actions whenever code is pushed to the `main` branch.

- Build workflow: `.github/workflows/build-windows.yml`
- Build status: Check the Actions tab in the repository

## Manual Download

You can also download releases from:
- [GitHub Releases](../../releases) - Official versioned releases (with changelog)
