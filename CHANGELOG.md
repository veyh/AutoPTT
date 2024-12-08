# Changelog

## 1.24.0 - 2024-12-08
### Added
* Support binding PTT and any other hotkey to just CTRL, SHIFT or ALT. (Well, it supports WIN too but you probably don't want to use that.)
* Support arbitrary key combinations for hotkeys. For example, you can now use `A-B`, `A-C` or even `A-B-C` as hotkeys, if you really want to. Think of it as being able to use any key as a "modifier."
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
