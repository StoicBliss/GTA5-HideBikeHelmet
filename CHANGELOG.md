# HideBikeHelmet - Changelog

## Overview

**HideBikeHelmet** prevents the player character from automatically donning motorcycle and bicycle helmets in Grand Theft Auto V, while preserving the ability to manually equip or remove helmets on demand with customizable hotkeys and variant cycling.

---

## Releases & Changes

## [1.4.1] - 2026-10-10

### 🧢 Cap & Hat Preservation on Bike Mounting

* **Fixed Cap Unequipping on Bike Mount**:
  * Removed over-broad check in `IsWearingHelmet()` that was mistakenly classifying any prop on slot 0 (including baseball caps, hats, beanies, and fedoras) as a helmet while on a bike.
  * Added active hat/cap tracking when on foot and automatic restoration if native GTA V mounting sequences strip the player's headwear.
  * Prevented `InstantRemoveHelmet()` from clearing prop slot 0 when the player is wearing a cap/hat rather than a helmet drawable.
  * Ensured `SET_PED_CONFIG_FLAG(player, 35, false)` is continuously enforced to prevent native auto-donning routines from removing the player's cap.

---

## [1.4.0] - 2026-09-13

### 🏍️ Bike-Only Helmet Enforcement & On-Foot Protection

* **Strict Bike-Only Equipping**:
  * Helmets can now **only** be equipped while actively riding a motorcycle, bicycle, quad bike, or jet ski (`IsRidingBikeOrQuad`).
  * Equipping helmets while on foot or inside cars/automobiles is strictly disabled.
  * Pressing `ToggleHelmetKey` on foot will silently do nothing and will never equip a helmet (or removes any lingering helmet if one was still worn).
* **Prevention of Masks, Headphones, and Arbitrary Head Props**:
  * Completely eliminated all on-foot prop slot variations. The mod will never equip headphones, masks, caps, or non-helmet props on foot.
* **On-Foot Radio Suppression**:
  * Added active deactivation of mobile radio (`SET_MOBILE_RADIO_ENABLED_DURING_GAMEPLAY, false` and `SET_MOBILE_PHONE_RADIO_STATE, false`) on foot to ensure zero unwanted radio audio triggers.

---

## [1.3.1] - 2026-09-13

### 🛡️ On-Foot Helmet Crash Fix

* **Fixed CTD on Foot When Equipping Helmet**:
  * Resolved game crash (Access Violation 0xC0000005) when pressing `ToggleHelmetKey` (`K`) while on foot.
  * In GTA V, calling the native vehicle helmet assignment (`GIVE_PED_HELMET` / `Ped.GiveHelmet`) on a character not mounted on a motorcycle causes the engine to dereference a null vehicle pointer, instantly crashing the game.
  * Re-architected on-foot helmet equipping to use GTA V's native prop variation pipeline (`SET_PED_PROP_INDEX` on Prop Slot 0), directly mapping authentic motorcycle helmet models for Michael, Franklin, Trevor, MP characters, and ambient peds.
  * Removed invalid native hash invocation (`0x6D4065975D4DE76CL`) during on-foot helmet removal.
  * Added clean prop clearing and pre-existing hat restoration when toggling the helmet off on foot.

---

## [1.3.0] - 2026-09-12

### 🎮 Gamepad Controller Support & Control Uniformity

* **Full Gamepad Support**:
  * Added controller hold toggle support (`D-Pad Up` / `GTA.Control.Phone`, 400ms hold threshold) matching `MinimapControl` and `RadioControl`.
  * Quick tap on `D-Pad Up` preserves default phone opening / navigation; holding 400ms cleanly toggles the helmet switch ON / OFF.
  * Added `[Controller]` configuration section to `HideBikeHelmet.ini` with `EnableController`, `ControllerToggleControl`, and `ControllerHoldTimeMs`.
* **Cinematic & Pause Protection**:
  * Added active guards against input handling during the pause menu and cutscenes.

---

## [1.2.0] - 2026-09-10

### 🚗 In-Car & Non-Bike Vehicle Helmet Protection

* **Prevented Helmet Equipping Inside Cars**:
  * Fixed an issue where pressing `ToggleHelmetKey` while sitting inside a car or automobile would equip a motorcycle helmet onto the player's head.
  * Added `IsInNonBikeVehicle` and `IsInOrEnteringNonBikeVehicle` checks that identify any vehicle that is not a motorcycle, bicycle, quad bike, or jet ski (e.g., cars, sports cars, trucks, SUVs, vans, buses, emergency vehicles, aircraft, boats).
  * Pressing `ToggleHelmetKey` while inside or entering a car/non-bike vehicle is now safely ignored and will **never** equip a helmet.
* **In-Car Helmet Removal Support**:
  * If the player entered a car while already wearing a helmet (e.g., hopped off a motorcycle or walked into a car), pressing `ToggleHelmetKey` while inside will cleanly remove the helmet and reset the switch state to OFF.
* **Automatic In-Car Helmet Cleanup**:
  * `Update()` now monitors vehicle state and automatically strips lingering motorcycle helmets when seated in an enclosed car or automobile, restoring any previously saved cap or hat.
* **Core Defense-in-Depth Guard**:
  * Added an immediate vehicle check in `PutOnHelmet()` to guarantee that no code path can spawn or attach a helmet prop while the character is in a non-bike vehicle.

---

## [1.1.0] - 2026-09-08

### 🎛️ Hotkey Modifiers & Prop State Tracking

* **Modifier Key Support**:
  * Added `ToggleHelmetModifier` support (e.g., `None`, `Shift`, `Control`, `Alt`) to avoid conflicting hotkey activations.
* **Variant Cycling**:
  * Added `CycleVariantsOnToggle` to cycle through helmet types (standard, motocross, full-face) and textures upon equipping.
* **Original Hat / Cap Restoration**:
  * Caches existing headwear (caps, beanies, hats) before equipping a helmet, and restores the original prop when removing the helmet.
* **Ground Drop Interception**:
  * Added `PreventGroundDrop` logic to track detached helmet props during take-off animations and clean them up before hitting the asphalt.

---

## [1.0.0] - 2026-09-05

### 🏍️ Initial Release

* Suppresses automatic engine helmet donning on motorcycles and bicycles (`SET_PED_CONFIG_FLAG 35`, `SET_PED_HELMET`).
* Manual helmet toggling via configurable keyboard hotkey (`ToggleHelmetKey`).
* Realistic helmet removal animations when dismounting.
* Custom helmet model hash registry for add-on and DLC helmets.
