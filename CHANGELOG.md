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
