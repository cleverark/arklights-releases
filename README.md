# ArkLights Firmware Releases

Official firmware releases and OTA update manifests for ArkLights LED controllers.

## What is ArkLights?

ArkLights is a smart LED lighting system designed for Onewheels, electric unicycles, and other personal electric vehicles (PEVs). It features synchronized group lighting via ESP-NOW, motion-reactive effects, and over-the-air firmware updates.

## OTA Updates

ArkLights devices check this repository for firmware updates automatically. The update flow:

1. The app fetches [`firmware/manifest.json`](firmware/manifest.json) to check for new versions
2. If an update is available, the firmware binary is downloaded from the [Releases](https://github.com/cleverark/arklights-releases/releases) page
3. The user connects to the device's WiFi AP and the app uploads the binary over a local connection

### Manifest Format

```json
{
  "latest_version": "0.2.3",
  "download_url": "https://github.com/cleverark/arklights-releases/releases/download/v0.2.3/arklights-v0.2.3.bin",
  "file_size": 1623392,
  "release_notes": "Bug fixes and improvements",
  "min_app_version": "1.0.0",
  "build_date": "2026-03-18T05:00:56Z"
}
```

| Field | Description |
|-------|-------------|
| `latest_version` | Semantic version of the latest firmware |
| `download_url` | Direct download link to the `.bin` file |
| `file_size` | Expected file size in bytes (used for download validation) |
| `release_notes` | Human-readable changelog |
| `min_app_version` | Minimum app version required to install this firmware |
| `build_date` | ISO 8601 build timestamp |

## Manual Installation

If you prefer to update manually instead of using the app:

1. Download the latest `.bin` file from [Releases](https://github.com/cleverark/arklights-releases/releases)
2. Power on your ArkLights controller
3. Connect to the device's WiFi network (`ARKLIGHTS-AP`)
4. Open `http://192.168.4.1` in your browser
5. Navigate to Settings > OTA Updates
6. Upload the `.bin` file

The device will restart automatically after a successful update.

## Important

- **Do not modify `firmware/manifest.json` manually** - it is updated automatically by CI when a new release is published
- This repository only contains release artifacts. Source code is maintained separately.
- Firmware binaries are compiled for the ESP32-S3 platform

## Links

- [ArkLights App](https://github.com/cleverark) - Mobile companion app
- [Releases](https://github.com/cleverark/arklights-releases/releases) - All firmware versions
