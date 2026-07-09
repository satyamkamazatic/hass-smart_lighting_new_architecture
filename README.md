# Smart Lighting - Testing Integration

Home Assistant integration for testing the updated preset apply flow with i-array support.

Domain: `smart_lighting`
Version: 1.2.0

## Installation via HACS (Custom Repository)

1. Open HACS in Home Assistant
2. Go to **Integrations**
3. Click the three dots (⋮) in the top right → **Custom repositories**
4. Add repository:
   - URL: `https://github.com/satyamkamazatic/hass-smart_lighting_new_architecture`
   - Category: **Integration**
5. Click **Add**
6. Find "Smart Lighting (Testing)" in the HACS integrations list and click **Download**
7. Restart Home Assistant
8. Go to **Settings → Devices & Services → Add Integration** → search "Smart Lighting"
9. Sign in with your account credentials

## Verifying the new code is loaded

Add this to `configuration.yaml`:
```yaml
logger:
  default: warning
  logs:
    custom_components.smart_lighting: debug
```

After restart, in the logs you should see:
```
Smart Lighting integration v1.2.0 loading
```

When applying a preset, look for `BOSSO_V1.2` markers in the debug logs.

## What's new in v1.2.0

- Fixed i-array detection: `get_device_i_array()` now correctly finds the `i` array nested under `device.i` (previously looked at top-level `i` which doesn't exist in API responses).
- Added support for i-arrays inside `zones[]`.
- Added detailed debug logging to trace preset application flow.
