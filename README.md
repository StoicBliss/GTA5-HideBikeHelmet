# HideBikeHelmet for Grand Theft Auto V

[![GTA V](https://img.shields.io/badge/Game-Grand%20Theft%20Auto%20V-blue.svg)](https://www.rockstargames.com/gta-v)
[![ScriptHookVDotNet](https://img.shields.io/badge/ScriptHookVDotNet-v3.7.0+-orange.svg)](https://github.com/scripthookvdotnet/scripthookvdotnet)
[![Platform](https://img.shields.io/badge/Platform-PC%20%28x64%29-lightgrey.svg)]()
[![Target](https://img.shields.io/badge/.NET%20Framework-4.8-purple.svg)]()
[![Version](https://img.shields.io/badge/Version-1.4.0-green.svg)](CHANGELOG.md)

**HideBikeHelmet** gives you complete control over motorcycle, bicycle, and quad bike helmet behavior in Grand Theft Auto V.

It eliminates the annoying mechanic where your character automatically puts on a motorcycle helmet every time you hop on a bike, while preserving the ability to manually equip or remove helmets on demand with authentic animations, texture cycling, and controller gamepad support.

---

## Key Features

- **No Automatic Helmet Donning (`DefaultWithoutHelmet = true`)**:
  - Mount any motorcycle, bicycle, quad bike, or jet ski without the game forcing a helmet onto your head.
  - Keep your custom hairstyles, hats, caps, and sunglasses visible while riding.

- **Manual Helmet Toggling on Demand**:
  - **Keyboard**: Press **K** (fully customizable to any key or modifier combination).
  - **Controller / Gamepad**: Hold **D-Pad Up** (400ms hold threshold). A quick tap opens the phone or navigates up normally, while holding for 400ms toggles the helmet.

- **Bike-Only Helmet Enforcement & Protection**:
  - Helmets can **only** be equipped while actively riding a motorcycle, bicycle, quad bike, or jet ski.
  - Equipping helmets while on foot or inside cars/automobiles is strictly disabled to prevent immersion-breaking glitches.

- **Automobile Protection & Automatic Cleanup**:
  - Prevents accidental helmet spawning while inside or entering cars, trucks, SUVs, vans, aircraft, or boats.
  - Automatically strips lingering motorcycle helmets when entering an enclosed automobile and restores your previous hat or cap.

- **Texture & Variant Cycling (`CycleVariantsOnToggle = true`)**:
  - Automatically cycles through authentic helmet styles and color variations each time you turn the helmet switch ON.

- **Ground Drop Interception (`PreventGroundDrop = true`)**:
  - Intercepts and cleans up dropped helmet props the instant they are removed, preventing physics clutter on the ground.

- **Custom DLC / Add-on Helmet Support**:
  - Add your own custom DLC helmet model names or numeric hashes in `HideBikeHelmet.ini`.

---

## Default Controls

| Action | Default Keyboard | Default Controller | Config Key |
| :--- | :--- | :--- | :--- |
| **Toggle Helmet** | `K` | `D-Pad Up` *(Hold 400ms)* | `ToggleHelmetKey` / `ControllerToggleControl` |
| **Toggle Modifier** | `None` | — | `ToggleHelmetModifier` |

*All keybinds, modifiers, and hold thresholds are fully customizable in `HideBikeHelmet.ini`.*

---

## Requirements

* [Script Hook V](http://www.dev-c.com/gtav/scripthookv/) by Alexander Blade
* [ScriptHookVDotNet v3](https://github.com/scripthookvdotnet/scripthookvdotnet/releases) (v3.7.0 nightly or later)
* Microsoft .NET Framework 4.8 runtime

---

## Installation

1. Install **Script Hook V** and **ScriptHookVDotNet v3** into your main GTA V game directory (where `GTA5.exe` is located).
2. Extract **`HideBikeHelmet.dll`** and **`HideBikeHelmet.ini`** into your GTA V **`scripts/`** folder:
   ```
   <Grand Theft Auto V>\scripts\HideBikeHelmet.dll
   <Grand Theft Auto V>\scripts\HideBikeHelmet.ini
   ```
3. *(Optional)* Configure your preferences in `HideBikeHelmet.ini`.
4. Launch GTA V and ride freely!

---

## Download & Releases

Download the latest compiled release from [GitHub Releases](https://github.com/StoicBliss/GTA5-HideBikeHelmet/releases/latest).

Each release includes:
- `HideBikeHelmet.dll` (ScriptHookVDotNet plugin)
- `HideBikeHelmet.ini` (default configuration)
- `HideBikeHelmet_Release.zip` (complete release archive)
## Author & Credits

- Developed by **StoicBliss** ([@StoicBliss](https://github.com/StoicBliss))
- Built on [ScriptHookVDotNet](https://github.com/scripthookvdotnet/scripthookvdotnet) by crosire and contributors
