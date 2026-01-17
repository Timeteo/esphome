# ESPHome Project - ESP32-S3-Box-3

## Session Startup Checklist
At the start of each session, validate the environment:
1. Check ESPHome version: `esphome version`
2. Verify device connection: `ls /dev/cu.usb*`
3. Confirm current git branch: `git branch --show-current`

## Git Safety Rules (CRITICAL)
- **Always create a new branch before making any changes** - never commit directly to `main`
- Branch naming: `feature/<description>` or `fix/<description>`
- **Never push without explicit user approval** - ask first, push only after confirmation
- After changes are verified working, the user will merge manually

## Backup Policy
- **Always create a backup before modifying any file**
- Backup naming: `<filename>.bak` (e.g., `esp32-s3-box-3-05a670.yaml.bak`)
- Create backup immediately before the first edit to a file
- **Backups should be committed to git** for restore options

## Project Overview
- ESPHome configurations for ESP32 devices integrating with Home Assistant
- Primary device: ESP32-S3-Box-3 touchscreen controller
- Current firmware version tracked in `substitutions.firmware_ver`

## File Structure
- `esp32-s3-box-3-05a670.yaml` - Main device configuration (~2000+ lines)
- `secrets.yaml` - Contains sensitive credentials (DO NOT read, modify, or commit)
- `resources/image/` - Custom icons and images
- Additional device YAML files may be added for other ESPHome devices

## Before Making Changes
1. Create a new branch: `git checkout -b feature/<description>`
2. Create a backup of the file(s) to be modified
3. Read the relevant section of the YAML before editing
4. Increment `firmware_ver` in substitutions when making functional changes

## Testing & Deployment
- Build and deploy command: `esphome run <config-file>.yaml --device <device-path>`
- Example: `esphome run esp32-s3-box-3-05a670.yaml --device /dev/cu.usbmodem101`
- **Automatically troubleshoot any compilation or deployment errors**
- **May install/update dependencies as needed** to resolve issues

### Device Path Validation
- **Validate device path once per session** (not every execution)
- Run `ls /dev/cu.usb*` to check connected USB devices
- Common path: `/dev/cu.usbmodem101`

### Multiple Device Configs
- **Ask user which device to deploy** when multiple configs exist
- Help identify target devices with tips:
  - Check `ls /dev/cu.usb*` for connected devices
  - Unplug/replug to identify which port corresponds to which device
  - Device labels often include serial numbers matching config filenames
  - Use `esphome logs <config>.yaml --device <path>` to see device output and confirm identity

## Rollback Procedure
1. **Primary method: Use git** - restore via `git checkout`, `git revert`, or `git reset`
2. **Fallback: .bak files** - only when git cannot achieve the desired state
   - Restoring from .bak requires **user approval** (never automatic)
   - Ask user which backup to restore and confirm before proceeding

## ESPHome YAML Conventions
- **Follow ESPHome configuration best practices** (search web if uncertain)
- Substitutions are defined at the top for easy customization
- Home Assistant entity IDs are configured in the substitutions section
- Version history is documented in comments at the top of the file
- Use clear, descriptive component IDs
- Group related configurations together
- Prefer substitutions for values that may change or are reused
