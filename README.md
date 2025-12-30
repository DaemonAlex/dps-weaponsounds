# DPS Weapon Sounds

> Professional weapon sound replacement resource for FiveM servers

A lightweight, performance-optimized FiveM resource that enhances the game audio experience by replacing default GTA V sounds with custom alternatives. Features intelligent audio streaming, memory management, and extensive configuration options.

---

## Table of Contents

- [Features](#features)
- [Requirements](#requirements)
- [Installation](#installation)
- [Configuration](#configuration)
- [Usage](#usage)
- [Exports](#exports)
- [Performance Tuning](#performance-tuning)
- [Troubleshooting](#troubleshooting)
- [Contributing](#contributing)
- [License](#license)
- [Credits](#credits)

---

## Features

- 🎵 **Custom Audio Replacement** - Replaces default weapon, environmental, and vehicle sounds
- ⚡ **Smart Memory Management** - Intelligent audio bank loading and unloading
- 🎛️ **Granular Controls** - Per-category volume and enable/disable toggles
- 🔫 **Weapon Filtering** - Apply custom sounds to specific weapons only
- 📊 **Performance Options** - Choose between preload and on-demand streaming
- 🔧 **Extensive Configuration** - Customize every aspect of audio playback
- 🐛 **Debug System** - Built-in logging and diagnostics
- 🔌 **Export API** - Programmatic control for external resources

---

## Requirements

| Component | Version |
|-----------|---------|
| **FiveM Server** | Build 4752+ |
| **Game** | GTA V |
| **Client RAM** | 8GB+ recommended |

---

## Installation

### Step 1: Download

Download the latest release and extract to your server's `resources` directory.

### Step 2: Configure

Add the resource to your `server.cfg`:

```cfg
ensure dps-weaponsounds
```

### Step 3: Restart

Restart your FiveM server or use the command:

```
restart dps-weaponsounds
```

---

## Configuration

All settings are located in `config.lua`. Below are the primary configuration options:

### Audio Settings

| Setting | Type | Default | Description |
|---------|------|---------|-------------|
| `MasterVolume` | float | `1.0` | Global volume multiplier (0.0-1.0) |
| `EnableWeaponSounds` | boolean | `true` | Toggle weapon audio |
| `EnableEnvironmentSounds` | boolean | `true` | Toggle environmental audio |
| `EnableVehicleSounds` | boolean | `true` | Toggle vehicle audio |
| `EnableFootstepSounds` | boolean | `true` | Toggle footstep audio |
| `PreloadAllSounds` | boolean | `false` | Load all audio on startup |
| `BankReleaseDelay` | integer | `300` | Seconds before unloading unused audio |

### Volume Controls

Individual volume multipliers for each category:

```lua
Config.AudioSettings = {
    WeaponVolume = 1.0,        -- Weapon sounds
    EnvironmentVolume = 1.0,   -- Ambient sounds
    VehicleVolume = 1.0,       -- Vehicle sounds
    FootstepVolume = 1.0,      -- Footstep sounds
    ExplosionVolume = 1.0,     -- Explosion sounds
}
```

### Weapon Overrides

Restrict custom sounds to specific weapons:

```lua
Config.WeaponOverrides = {
    [GetHashKey("WEAPON_PISTOL")] = true,
    [GetHashKey("WEAPON_COMBATPISTOL")] = true,
}
```

> **Note:** Leave the table empty to apply sounds to all weapons.

### Debug Options

```lua
Config.Debug = {
    Enabled = false,           -- Enable console logging
    ShowNotifications = false, -- Show in-game notifications
}
```

---

## Usage

### Basic Usage

Once installed and configured, the resource operates automatically. Audio banks load based on your configuration settings.

### Enabling Debug Mode

To troubleshoot or monitor audio loading:

1. Open `config.lua`
2. Set `Config.Debug.Enabled = true`
3. Restart the resource
4. Check console (F8) for detailed logs

### Adjusting Performance

For servers with limited resources:

```lua
Config.AudioSettings.PreloadAllSounds = false  -- Load on-demand
Config.AudioSettings.BankReleaseDelay = 180    -- Unload after 3 minutes
```

For servers prioritizing audio quality:

```lua
Config.AudioSettings.PreloadAllSounds = true   -- Load everything at start
Config.AudioSettings.BankReleaseDelay = 0      -- Never unload
```

---

## Exports

The resource exposes the following exports for programmatic control:

### LoadCustomSounds

Manually load all audio banks.

```lua
exports['dps-weaponsounds']:LoadCustomSounds()
```

### UnloadCustomSounds

Manually unload all audio banks.

```lua
exports['dps-weaponsounds']:UnloadCustomSounds()
```

### IsAudioBankLoaded

Check if a specific audio bank is currently loaded.

```lua
local isLoaded = exports['dps-weaponsounds']:IsAudioBankLoaded('CUSTOM_WEAPON_SOUNDS')

if isLoaded then
    print("Weapon sounds are active")
end
```

**Available Bank Names:**
- `CUSTOM_RESIDENT_SOUNDS` - Environmental/ambient audio
- `CUSTOM_WEAPON_SOUNDS` - Weapon audio

---

## Performance Tuning

### Memory Optimization

The resource implements several optimization strategies:

#### On-Demand Loading

Audio banks load only when needed, reducing initial memory footprint.

```lua
Config.AudioSettings.PreloadAllSounds = false
```

**Pros:** Lower memory usage, faster initial load
**Cons:** Brief delay when first equipping weapons

#### Automatic Unloading

Unused audio banks automatically unload after a configurable delay.

```lua
Config.AudioSettings.BankReleaseDelay = 300  -- 5 minutes
```

**Lower values** = More aggressive memory management
**Higher values** = Less frequent reloading

### Recommended Configurations

#### High-Traffic Server (50+ players)

```lua
PreloadAllSounds = false
BankReleaseDelay = 120
```

#### Standard Server (20-50 players)

```lua
PreloadAllSounds = false
BankReleaseDelay = 300
```

#### Low-Traffic Server (<20 players)

```lua
PreloadAllSounds = true
BankReleaseDelay = 0
```

### Disabling Unused Categories

Reduce resource usage by disabling unneeded sound categories:

```lua
Config.AudioSettings = {
    EnableWeaponSounds = true,
    EnableEnvironmentSounds = false,  -- Disabled
    EnableVehicleSounds = false,      -- Disabled
    EnableFootstepSounds = true,
}
```

---

## Troubleshooting

### Sounds Not Playing

**Symptoms:** No custom sounds are audible in-game

**Solutions:**
1. Verify resource is started: Check `server.cfg` contains `ensure dps-weaponsounds`
2. Check resource name: Ensure folder name matches what's in `server.cfg`
3. Enable debug mode: Set `Config.Debug.Enabled = true` and check console (F8)
4. Verify file paths: Ensure all paths in `fxmanifest.lua` are correct

### Memory Warnings

**Symptoms:** "Oversized asset" or memory-related warnings

**Solutions:**
1. Enable on-demand loading: `PreloadAllSounds = false`
2. Reduce unload delay: `BankReleaseDelay = 120`
3. Disable categories: Turn off unused sound categories
4. Check streaming limits: Increase server-side streaming limits if needed

### Performance Issues

**Symptoms:** Client lag or stuttering

**Solutions:**
1. Use on-demand loading: `PreloadAllSounds = false`
2. Increase release delay: `BankReleaseDelay = 600`
3. Reduce volume: Lower individual category volumes
4. Check conflicts: Disable other sound resources temporarily

### Resource Conflicts

**Symptoms:** Sounds cut out or overlap incorrectly

**Solutions:**
1. Check load order: Place this resource first in `server.cfg`
2. Use weapon overrides: Limit scope to specific weapons
3. Review other resources: Ensure no other resources replace the same audio banks

### Debug Checklist

Run through this checklist when troubleshooting:

- [ ] Resource appears in `server.cfg`
- [ ] Resource shows as "started" in server console
- [ ] No errors in server console on startup
- [ ] No errors in client console (F8)
- [ ] Debug mode enabled and showing logs
- [ ] File paths in `fxmanifest.lua` match actual files
- [ ] `.awc` files exist in `stream/sfx/` directories

---

## Contributing

Contributions are welcome! If you'd like to improve this resource:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/improvement`)
3. Commit your changes (`git commit -am 'Add new feature'`)
4. Push to the branch (`git push origin feature/improvement`)
5. Open a Pull Request

### Guidelines

- Maintain existing code style
- Test thoroughly before submitting
- Update documentation for new features
- Follow semantic versioning

---

## License

This project is licensed under the **GNU General Public License v3.0**.

See [LICENSE](LICENSE) for complete terms.

### Key Points

- ✅ Free to use, modify, and distribute
- ✅ Source code must remain open
- ✅ Derivative works must use GPL-3.0
- ❌ No warranty provided

---

## Credits

**Author:** DPS Development Team
**Organization:** DPS Development
**Version:** 2.0.0
**Repository:** [GitHub](https://github.com/yourusername/dps-weaponsounds)

### Special Thanks

- FiveM Community for documentation and support
- OpenIV team for audio conversion tools
- All contributors and testers

---

## Support

Need help? Check these resources:

- 📖 [Configuration Guide](config.lua)
- 🔧 [Troubleshooting](#troubleshooting)
- 🐛 [Debug Mode](#enabling-debug-mode)

For additional support, enable debug mode and review console output for diagnostic information.

---

<div align="center">

**[⬆ Back to Top](#dps-weapon-sounds)**

Made with ❤️ by DPS Development

</div>
