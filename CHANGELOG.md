# unreleased

**Features**

* Add automatic updating. Now you only need to click `Download update` and the app does the rest.

**UI**

* Add `View changelog` button to new version notification.
* Add new version notification to license view (in case of unexpected problems with license servers that a new version might fix).

**Fixes**

* Use Gumroad License API directly if mine is unresponsive. This ensures that the license verification always works for paying customers. My server only handles manually-generated licenses, like limited time trial keys.
* Save license key in settings file even if it's considered invalid at the moment. Previously, if, for example, the user's internet connection was down and they started the app with a valid license key, the key would be cleared from settings because it could not be validated. Then the user would have to go back to their email or Gumroad page to look up the license key again.
* Fix potential issue with saving and loading config files (`fopen` with `rb` and `wb` instead of `r` and `w`. No such nonsense on Linux :)
* Remove `DEV` from app title. It was only supposed to be shown in the build that I use for development but it snuck into the release as well.

# 1.1.2 (22745cda) -- 2022-06-09

**Fixes**

* Allow setting a virtual key (like F24) as the PTT key. Note that this will not work in `Tap PTT` mode, as it requires a physical key (for now).

# 1.1.1 (cac42e58) -- 2022-03-28

**Fixes**

* Show `Update Available` in UI. It was disabled in `1.1.0` by mistake :)

# 1.1.0 (cbcfd7f7) -- 2022-03-28

**Features**

* Add new `Tap PTT` activation mode, which requires the user to activate the microphone manually by pressing the PTT key. The physical release event of the key is blocked from Windows, and AutoPTT releases it only after the user is done speaking. So the user can just quickly tap the key, and their mic will stay open as long as they're speaking over the activation threshold (or within the release delay).

**UI**

* Use decibel scale for `Activation Threshold` and `Current Value`.
* Add `Buy License` button.
* Add a separate keybind view instead of a popup.

# 1.0.0 (b30acd91) -- 2022-02-25

Initial release.
