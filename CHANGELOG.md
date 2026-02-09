# Changelog

## 4.3.9 - 2026-02-09
### Fixed
* Fix a possible crash related to game controllers
* Update library used for game controllers. Fixes a number of issues.

## 4.3.8 - 2026-02-06
### Fixed
* Fix crash when an audio device is added or removed during startup.

## 4.3.7 - 2026-02-05
### Fixed
* Fallback to opening audio device by name in case its hardware identifier has changed (this fixes an issue with virtual devices like NVIDIA Broadcaster).

## 4.3.6 - 2026-02-04
### Fixed
* Fix incorrect text for "Download Update" button

## 4.3.5 - 2026-02-04
### Fixed
* Fix crash after an IPC client disconnect

## 4.3.4 - 2026-02-03
This release contains quite a few internal changes related to how text is
displayed in the GUI, so if you see anything weird, let me know.
### Fixed
* Push-to-Mute now takes priority over Secondary PTT.
* Fix an issue related to copying and pasting in text fields. 

## 4.3.3 - 2026-02-01
### Fixed
* Fix crash when submitting feedback with empty email

## 4.3.2 - 2026-01-30
### Fixed
* Fix error monitoring raw input when program path contains spaces.
* Fix another crash related to multiple PTT keys.

## 4.3.1 - 2026-01-28
### Fixed
* Fix "Device not found" error being displayed on the GUI when the device was actually found.

## 4.3.0 - 2026-01-28
### Added
* Add automatic crash reporting which will help in discovering and fixing issues quicker.
### Fixed
* Fix crash related to profiles with multiple PTT keys.

## 4.2.1 - 2026-01-26
### Fixed
* Fix crash when using **Run at Startup**

## 4.2.0 - 2026-01-26
### Added
* IPC: Add `IpcProfileChanged` event
### Fixed
* Fix possible logging-related crash
* Fix the **Device** field showing the wrong device after manually switching profiles.

## 4.1.1 - 2026-01-26
### Fixed
* Fix a crash caused by changing settings.

## 4.1.0 - 2026-01-24
### Added
* Support automatically starting and stopping programs alongside AutoPTT. To use this feature, create a folder called `autostart` in AutoPTT's installation folder, and place any `.exe` or `.bat` file in there. They will be called with one argument, which will be the IPC Address (default: `tcp://127.1.2.3:4000`). 
    * Can be disabled with the command line argument `--no-autostart` .
    * The directory can be changed with `--autostart-dir`.
### Changed
* Change the duration of the **Trial** (when you run the app without a license) from 5 minutes to 15 minutes.
### Fixed
* Fix a small memory leak (<500 KB/day).
* Fix a crash caused by game controllers without human-readable names.
* Fix a crash caused by an IPC client registering with an empty `ipc_tag`.
* Fix a crash on app exit (caused by attempting to write logs after logging was terminated).
* Fix an issue that sometimes caused keys to get stuck with **Consume PTT Key** enabled.
* Fix an issue with the AutoPTT Sidekick not being treated as virtual input (which also caused PTT keys to get stuck).

## 4.0.0 - 2026-01-05
### Added
* Add support for [FakerInput](https://github.com/Ryochan7/FakerInput), which
works like the [AutoPTT Sidekick](https://github.com/veyh/AutoPTT-Sidekick),
except it's just a software driver instead of physical hardware.
* Support sending feedback directly from the app (no longer opens a browser window).
* Add a Discord link to the feedback view.
### Changed
* Remove UPX packing from **AutoPTT.exe**. It was mostly unnecessary since releases (setup & zip) are already compressed. It just means that the unpacked size is a bit larger now.
* Replace **Use AutoPTT Sidekick** global setting with a profile-specific setting for **Input Method**, which has three choices: Virtual (Default), FakerInput and Sidekick.
### Fixed
* Fix crash on app exit.
* Fix an issue where the app may have become unresponsive when exiting, and the only way to close it would be through the Task Manager.
* Remove startup entry on uninstall.
* Fix SFX not playing when changing activation mode through IPC.

## 3.0.5 - 2025-12-09
### Fixed
* Fix Push-to-Talk and Push-to-Mute not working through IPC (eg. the Stream Deck plugin)

## 3.0.4 - 2025-10-31
### Fixed
* Fix bug in 3.0.3 that caused all sound effects to always be enabled.

## 3.0.3 - 2025-10-31
### Fixed
* Fix a memory leak that happened when using custom sound effects. (This bug affected basically all versions since 1.10.0.)

## 3.0.2 - 2025-10-30
### Fixed
* Fix a memory leak introduced in 3.0.0

## 3.0.1 - 2025-10-26
### Fixed
* Fix a crash that happened when starting AutoPTT with a game controller connected. (Only version 3.0.0 was affected by this.)

## 3.0.0 - 2025-10-16
This release comes with considerable internal changes, so if you run into any bugs, please let me know!
### Added
* Add support for multiple profiles, which can be set to automatically activate based on what programs are currently running on your computer.
### Changed
* Don't store the selected GUI tab in settings. Always start the app in the new Overview tab. Which doesn't currently have a lot of information, so I'm open to suggestions if you find a view like this useful. It was added because the automatic profile switching functionality can't be enabled while in the **Settings / Profile** tab. (You wouldn't want the profile to change while you're busy adjusting its settings, would you?)
### Fixed
* Fix a small memory leak.
* Fix crash when removing a PTT Key that wasn't the last one in the list.

## 2.11.0 - 2025-10-04
### Added
* Support **Toggle Mute** for individual PTT keys, meaning you can now keep AutoPTT from pressing some PTT keys while still pressing others. (In other words, this feature is mostly for the **Voice Activity**, **Tap** and **Push-to-Talk** modes.)
### Fixed
* Fix a crash that sometimes happened when closing the app, and it had been started as admin.

## 2.10.0 - 2025-06-20
### Added
* Make `Current Value` red when global mute is active.
* Match color of `Current Value` text to the value.
* Highlight all active hotkeys, not just Push-to-Talk.
### Changed
* Display game controller buttons starting from 1 instead of 0 (ie. you will no longer see "Button 0" or "POV 0").
### Fixed
* Fix an issue that sometimes prevented the app from shutting down properly.
* When switching to another device, ensure the previous device is unmuted before switching.
* When the app is closed, unmute the current device.

## 2.9.0 - 2025-05-10
### Added
* Allow binding hotkeys to specific gamepads (and gamepads that are not Xbox
compatible).
    * Previously, for example, binding to A on one Xbox controller would
      actually bind to A on any Xbox controller.
    * Just in case, you can go back to the old behavior with the command
      line argument `--bind-xinput`.

## 2.8.0 - 2025-04-14
### Added
* Add support for all types of game controllers like steering wheels and joysticks. (Previously, only XBox-compatible gamepads were supported.)
    * In case of problems, you can add `--no-joystick` to AutoPTT's start command to disable this feature.

## 2.7.1 - 2025-03-19
### Fixed
* Fix an issue that caused the UI to sometimes become unresponsive. (This was caused by recent changes to the tray icon code, and affects versions 2.6.1 and 2.7.0.)

## 2.7.0 - 2025-03-18
### Added
* Add `Toggle Mute (Global)` hotkey. While this functionality has already kind of existed by swapping to different modes, this just makes things simpler.
* Support mp3 sound files.
* Add default sound effects for `Toggle Mute (Global)` and all activation modes.
* When configuring a sound effect, show its name in the dialog title.
* Show a `Play` button for sound effects so they can be previewed without opening the configuration dialog.
### Changed
* Rename some activation modes:
    * `Manual` --> `Push-to-Talk (PTT)`
    * `Open Mic to PTT (Tap)` --> `Open Mic to Tap`
    * `Open Mic to PTT (Manual)` --> `Open Mic to PTT`
* Rename capture modes:
    * `Default` --> `Peak Meter`
    * `Advanced` --> `Audio Stream`
* Make `Audio Stream` the default Capture Mode.
* Overlay: Change defaults to always show the overlay when inactive and to also show the current activation mode name.
### Fixed
* Fix an issue that may have prevented sound settings from being saved.
* Prevent "Configure Sound" dialog from closing immediately.

## 2.6.1 - 2025-03-10
### Fixed
* Fix tray icon sometimes disappearing when the app is minimized to tray.
* Fix error message spam when GPU driver crashes or is reset. Now, the app will simply exit after clicking OK (which was the original intention).

## 2.6.0 - 2025-03-04
### Added
* Support Push-to-Talk, Push-to-Mute and Push-to-Mute (Global) via IPC (eg. Stream Deck plugin).
* Show license error details. Hide the error when the license text is edited or when the "Save" button is clicked. (Previously, the error was hidden on a timer.)
### Changed
* Only automatically activate the trial on startup if the license is empty.
### Fixed
* Stay in the license view when a new license is entered while trial is active. Only exit the view if the new license is valid.
* Fix memory leak in IPC (eg. Overlay, Stream Deck plugin).

## 2.5.0 - 2025-02-09
### Changed
* Increase maximum number of Primary PTT keys from 5 to 20.

## 2.4.0 - 2025-02-08
### Added
* Show license error in Overlay.
### Fixed
* Fix a bug with the [Elgato Stream Deck plugin](https://marketplace.elgato.com/product/autoptt-d8d752ff-b294-4ca3-a432-14f287755ab1)
that caused the currently selected device to reset back to NONE when
changing the activation mode through the plugin.

## 2.3.1 - 2025-02-07
### Fixed
* When the currently selected device is disconnected, the setting no longer
resets back to `NONE`. Instead, all functionality is disabled until the
device is connected, or another device is selected.

## 2.3.0 - 2025-02-06
### Added
* Animate PTT key when `Tap Activation Window` or `Release Delay` is active.
### Fixed
* Fix an issue that may have prevented settings from being saved.

## 2.2.1 - 2025-01-28
### Fixed
* Support secondary PTT keys that are not physical in `Open Mic to PTT`
modes when `Consume PTT Key` is enabled.

## 2.2.0 - 2025-01-26
### Added
* Support using (physical) key combinations as primary PTT keys
### Fixed
* Support `Consume PTT Key` for Secondary PTT keys in `Open Mic to PTT`
modes
* Fix an issue that may have prevented mouse side buttons from being used as PTT.

## 2.1.0 - 2025-01-19
### Added
* Change window icon based on activity.
* Add an overlay icon to the taskbar, indicating activity. Note that the taskbar overlay icon only works when the Windows setting `Use small taskbar buttons` is turned `Off`.
* Make it possible to move the Overlay by enabling the `Unlock for moving` option.

## 2.0.0 - 2025-01-18
### Added
* Add support for multiple Push-to-Talk and Push-to-Mute keys.
    * The activity state displayed in the `Current Value` field, the app
      icon, the tray icon and the icon in the Overlay now represent the
      "aggregate" state of all PTT keys; that is, if one of the PTT keys is
      active (green), then `Current Value` and the icons will be green as
      well.
    * The activity state for an individual PTT key is now indicated by the
      color of the border of the keybind button instead.
    * Furthermore, the system-wide mute in `Open Mic to PTT` modes is also
      determined from the aggregate state.
* Make it possible to use F13-F24 as PTT by selecting them from a menu while binding the key. (This is useful for Voice Activity mode, when you don't need to press the key yourself.)
* Add `Send Feedback` button.
* Add an `Activation Window` setting for `Tap` and `Open Mic to PTT (Tap)`
modes. It starts when the PTT key is released, and lasts until the given
time has passed or the sound level goes over the activation threshold.
    * The mic is kept active during the Activation Window. Basically, it's
    like Release Delay for BEFORE you start talking.
* Backup settings file when it's migrated to a new version or when it fails to load due to an unknown error.
### Changed
* Split GUI into tabs. Currently there are two: `General` and `Device 1`. This is in preparation for multiple device support, which is probably coming at some point in the future.
* Remove `Update Interval` setting. It's now hardcoded to 5 ms (200 Hz).
### Fixed
* Fix files not being deleted when uninstalling.
* Fix an issue with using modifier keys as PTT. The different "sides" are also now differentiated, so instead of "CTRL" the app uses "LCTRL" and "RCTRL".
* When a conflicting keybind is set, the other key(s) are now unbound and a warning is shown.
* Fix an issue that sometimes caused duplicate key down events to be generated in Voice Activity, Tap and Manual modes (which could result in extra characters while typing).
* Prevent setting a hotkey from immediately triggering that hotkey.

## 1.27.1 - 2025-01-01
### Fixed
* Fix a very small memory leak in the Overlay.
* Make hotkey detection more reliable when GPU is under heavy load.

## 1.27.0 - 2024-12-30
### Added
* Add an Overlay that shows the current `Activation Mode` and activity state (green = active; yellow = release delay; gray = inactive; red = system-wide mute).

## 1.26.1 - 2024-12-27
### Fixed
* Fix binding hotkeys that weren't already bound to something before updating to version 1.26.0.

## 1.26.0 - 2024-12-27
In addition to the "visible" changes, this release also changes how settings are stored. There is an automatic migration that should handle things for you but just in case I missed something and your settings got messed up, I'm sorry!

### Added
* Add option to hide the "Update Available" notification.
### Changed
* Use a nicer font in the UI.
### Fixed
* Update list of devices when devices get added or removed.

## 1.25.0 - 2024-12-18
### Added
* Add `Push-to-Mute (Global)` hotkey that mutes the microphone system-wide.

## 1.24.1 - 2024-12-11
### Fixed
* Fix possibly inconsistent PTT key state after switching activation modes while the mic is active.

## 1.24.0 - 2024-12-08
### Added
* Support binding PTT and any other hotkey to just CTRL, SHIFT or ALT. (Well, it supports WIN too but you probably don't want to use that.)
* Support arbitrary key combinations for hotkeys. For example, you can now use `A-B`, `A-C` or even `A-B-C` as hotkeys, if you really want to. Think of it as being able to use any key as a "modifier."
* Support starting multiple instances of AutoPTT with different settings files, using a command line argument: `--settings-file "C:\path\to\settings.bin"`
### Changed
* Remove `VK_` prefix from some of the most common keys.

## 1.23.1 - 2024-12-06
### Fixed
* Fix hotkeys not being saved correctly (this bug was introduced in 1.23.0)

## 1.23.0 - 2024-12-05
### Added
* Add `Mode: Manual/Open Mic to PTT (Manual)` hotkey. You can use it as an "Open Mic with Toggle Mute", since `Manual` mode always unmutes your mic, while `Open Mic to PTT (Manual)` mutes it (unless you press the PTT key, of course).
### Fixed
* Allow selecting a device with a name that contains weird characters. (It still might not be displayed correctly but at least it can be selected, which wasn't the case previously.)

## 1.22.0 - 2024-12-04
### Added
* Add `Consume PTT Key` option for `Open Mic to PTT` modes. Enabling it will block Windows and any app/game from registering the key press. This used to be enabled by default in earlier versions.
### Changed
* Make `Update Available` notification visible even if the main window already has a scrollbar on it.
### Fixed
* Fix PTT key detection after changing it when using `Tap` or either `Open Mic to PTT` activation modes.

## 1.21.1 - 2024-12-02
### Fixed
* Remove some inconsistency in the UI when using `Manual` or either `Open Mic to PTT` activation mode.

## 1.21.0 - 2024-11-30
### Added
* Add `Deactivation Threshold`. When enabled, PTT is released only after the sound level falls below both `Activation Threshold` and `Deactivation Threshold`. Going over either resets `Release Delay`.

## 1.20.0 - 2024-11-27
### Changed
* If no valid license is found on startup, automatically activate the trial.

## 1.19.0 - 2024-11-17
### Changed
* Hide "Activation Threshold" and "Release Delay" settings when using manual activation mode.

## 1.18.1 - 2024-11-16
### Fixed
* Fix crash when setting activation mode to "Open Mic to PTT" without a device selected.
* Fix crash on startupt when using "Open Mic to PTT" activation mode.

## 1.18.0 - 2024-11-07
### Added
* Add activation modes `Open Mic to PTT: Tap` and `Open Mic to PTT: Manual`. They can be used when you want to use Push-to-Talk but your game/app only supports open mic (voice activation).
* Add hotkey for `Mode: Open Mic to PTT: Tap`.
* Add hotkey for `Mode: Open Mic to PTT: Manual`.
* Add sound effect setting for `Mode: Open Mic to PTT: Tap`.
* Add sound effect setting for `Mode: Open Mic to PTT: Manual`.

## 1.17.0 - 2024-10-19
### Added
* Add support for mouse buttons (middle/back/forward).

## 1.16.1 - 2024-10-18
### Fixed
* Prevent multiple instances of AutoPTT from running. Now, trying to start another instance should just bring the already running one into the foreground.
* Support games and apps (eg. Mumble) that use [raw input](https://learn.microsoft.com/en-us/windows/win32/inputdev/about-raw-input) to detect key presses.

## 1.16.0 - 2024-08-31
### Added
* Add option to start AutoPTT on boot.

## 1.15.0 - 2024-05-16
### Added
* Add tray icon. Its color changes based on PTT state, just like the current value meter (green = active, yellow = release delay, grey = inactive).
* Support minimizing to system tray.
### Fixed
* Support starting from command prompt. (It used to throw an "out of memory" error).

## 1.14.1 - 2024-03-26
### Fixed
* Trim leading and trailing whitespace from license key.
* Check license every time the save button is clicked, even if the license text hasn't changed. This should make things a lot less confusing when there is a problem with the license server and not the license key.

## 1.14.0 - 2024-03-23
### Added
* Support using Xbox-like controller buttons as hotkeys.

## 1.13.0 - 2023-09-09
### Added
* Support extra hotkeys to activate PTT in `Tap` and `Manual` activation modes.

## 1.12.0 - 2023-09-09
### Added
* Add `Capture Mode` option. The `Default` mode works as in previous versions of the app. The experimental `Advanced` mode is new and should be more compatible with apps that play sounds through your mic (eg. [Soundpad](https://www.leppsoft.com/soundpad/)).

## 1.11.1 - 2023-05-20
### Fixed
* Play sound effects from the beginning if an event triggering the sound effect happens while already playing. Previously, the current playback would simply finish, which could have led to some confusion as to whether the new event actually happened.

## 1.11.0 - 2023-03-28
### Added
* Add hotkeys and sound effects for changing activation mode.

## 1.10.0 - 2023-03-19
### Added
* Add a button for testing sound effects (in the configuration popup).
* Support changing individual sound effect volume.

## 1.9.0 - 2023-02-13
### Added
* Add `Push-to-Mute` hotkey.
* Add option to play a sound when `Push-to-Mute` key is pressed/released.

## 1.8.0 - 2023-01-15
### Added
* Add help text for `Activation Mode`.
* Add `Activation Mode: Manual`.
### Fixed
* In `Tap` mode, don't release PTT key if it's physically still held down. (This could happen with a short `Release Delay` if you pressed and held the key without speaking.)


## 1.7.0 - 2023-01-09
### Added
* Make PTT down/up sounds customizable.

## 1.6.0 - 2023-01-07
### Added
* Add option to play a sound when PTT key is pressed.
* Add option to play a sound when PTT key is released.

## 1.5.0 - 2023-01-06
### Added
* Add icon.
* Add help text for `Release Delay`.
* Add help text for `Update Interval`.

## 1.4.1 - 2022-11-02
### Changed
* Only show input devices in the device list.
### Fixed
* Fix an issue with the app not being able to listen to a sound device. It should now show up as "listening" to the microphone in Windows Sound Settings.

## 1.4.0 - 2022-08-16
### Added
* Support sending physical key events with [AutoPTT Sidekick](https://github.com/veyh/AutoPTT-sidekick/). It's possible not all keys work with this setup (yet) -- the UI should indicate whether this is the case, and you can try a different key. I would also appreciate it if you let me know which key it was that did not work so that I can fix it.
### Changed
* Hide help text by default. Mouseover `[?]` to show.

## 1.3.1 - 2022-07-16
### Fixed
* Fix crash on auto update. I didn't realize that I'd put the wrong `zip.dll` in the release build. This crash happens with both `1.2.0` and `1.3.0`.

## 1.3.0 - 2022-07-16
### Added
* Add an option to try out the app without a license. Just click the `Trial` button. You'll have 5 minutes. After that, you can restart the app and click the `Trial` button again for another 5 minutes, and so on.

## 1.2.0 - 2022-07-08
### Added
* Add automatic updating. Now you only need to click `Download update` and the app does the rest.
* Add `View changelog` button to new version notification.
* Add new version notification to license view (in case of unexpected problems with license servers that a new version might fix).

### Fixed
* Use Gumroad License API directly if mine is unresponsive. This ensures that the license verification always works for paying customers. My server only handles manually-generated licenses, like limited time keys.
* Save license key in settings file even if it's considered invalid at the moment. Previously, if, for example, the user's internet connection was down and they started the app with a valid license key, the key would be cleared from settings because it could not be validated. Then the user would have to go back to their email or Gumroad page to look up the license key again.
* Fix potential issue with saving and loading config files.
* Remove `DEV` from app title. It was only supposed to be shown in the build that I use for development but it snuck into the release as well.

## 1.1.2 - 2022-06-09
### Fixed
* Allow setting a virtual key (like F24) as the PTT key. Note that this will not work in `Tap PTT` mode, as it requires a physical key (for now).

## 1.1.1 - 2022-03-28
### Fixed
* Show `Update Available` in UI. It was disabled in `1.1.0` by mistake :)

## 1.1.0 - 2022-03-28
### Added
* Add new `Tap PTT` activation mode, which requires the user to activate the microphone manually by pressing the PTT key. The physical release event of the key is blocked from Windows, and AutoPTT releases it only after the user is done speaking. So the user can just quickly tap the key, and their mic will stay open as long as they're speaking over the activation threshold (or within the release delay).
* Add `Buy License` button.

### Changed
* Use decibel scale for `Activation Threshold` and `Current Value`.
* Add a separate keybind view instead of a popup.

## 1.0.0 - 2022-02-25
Initial release.
