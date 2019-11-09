# Patched NVidia macOS Web Driver Installers

* **Why?**
    * Because NVidia installers check the current macOS version and build number before installing

* **What for?**
    * This probably for compatability reasons. However, this isn't always the case.

* **How?**
    * The package is expanded and a file called `DISTRIBUTION` contains the checks. This check mechanism is removed and the package is flattened again.

* **That all?**
    * No. You then need to edit the contents of the real driver and add a patch to your config. To streamline and make things faster, I simply removed checks from all the High Sierra driver installers.
    
# Config Kext Patch

To bypass checks on boot, you need to add a kext patch to your config. See file *DisableDriverCheck.plist*. Add the contents to your config and save it.
    
# Patching The Driver

Once you've ran the installer you preffered, *don't* reboot the computer. Just ignore the request to do so. You can't close it, so leave it be.

1. Navigate to /Library/Extensions/
2. Right click on *NVDAStartupWeb.kext* and choose *Show package contents*
3. Go to *Contents* and copy the file *Info.plist* to your dekstop.
4. Open *Info.plist* with Xcode or your preffered plist editor.
5. Expand *IOKitPersonalities* > *NVDAStartup*
6. Edit the value of *NVDARequiredOS* and change it to your current build number.
    * Tip: If you don't know your Build Number, you can obtain it with Terminal by typing in `sw_vers`
7. Save the file and place it back in the kext *Contents* folder.
8. Repair permissions with Terminal
    * `sudo chmod -Rf 755 /L*/E*`
    * `sudo chown -Rf 0:0 /L*/E*`
9. Rebuild kext cache with Terminal
    * `sudo kextcache -i /`
10. Click the restart button on the installer.

[*Sourced from reddit*](https://www.reddit.com/r/hackintosh/comments/7sr4vv/nvidia_web_drivers_and_you_a_patching_guide_for/)


---


I realise this is a bit behind. I will add the missing updates on Nov 09 2019

Nvidia Web Driver - 387.10.10.10.40.132
Nvidia Web Driver - 387.10.10.10.40.131
Nvidia Web Driver - 387.10.10.10.40.130
Nvidia Web Driver - 387.10.10.10.40.129

These versions will be added soon.
