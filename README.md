# Patched NVidia macOS Web Driver Installers

* **Why?**
    * Because NVidia installers check the current macOS version and build number before installing

* **What for?**
    * This probably for compatability reasons. However, this isn't always the case.

* **How?**
    * The package is expanded and a file called `DISTRIBUTION` contains the checks. This check mechanism is removed and the package is flattened again.

* **That all?**
    * No. You then need to edit the contents of the real driver and add a patch to your config. To streamline and make things faster, I simply removed checks from all the High Sierra driver versions. See here: https://www.reddit.com/r/hackintosh/comments/7sr4vv/nvidia_web_drivers_and_you_a_patching_guide_for/ on how to modify the installed driver.
