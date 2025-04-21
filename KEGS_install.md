# Installation of old emulators in Android 14.

So, Android 14 has happened to be a piece of restrictions and installing old applications is a kind of unnecessary challenges. The change as disappointing as this for me was the disable of USB Mass Storage option. 
The issue is present not only with one emulator, as I thought before, but several. The list of emulators I know to have the issue:
* KEGS (Apple IIGS)
* Colleen (Atari 8-bit)

Nonetheless, there is still an option to install applications with lower mininal SDK than required (lowest SDK version of Android 14 is SDK 27, but KEGS has minimal requirement of SDK 16).
For the example, I'll take the Apple ][ emulator KEGS.

After you have downloaded the APK of KEGS, steps are the following:

1. Download Termux __and__ Termux API. Install versions from F-Droid, they are told to be newer than ones in Google Play.
2. Search for ADB tools for Termux. I used tools from here <https://github.com/MasterDevX/Termux-ADB>, but you may want to use this link <https://github.com/nohajc/termux-adb>.
   I am not sure if the difference is critical between these links, so I used one from MasterDevX, like, I don't need USB debugging tools.
3. You may want to run command `pkg install android-tools`, since for some reason after the scripts from the links above there the version of ADB didn't know the `pair` command yet.

For the better experience, you may want to run `termux-setup-storage`, so you wouldn't need to deal with copying your APK somewhere to the `/data/.../termux/` directory.  
After that make sure you have Developer Mode on your device enabled. If you still have't enabled it yet, tap several times on the Build number in Software information of your Device settings.

4. Pair your Termux and your device via Wireless debugging. In Termux, run `adb pair ip:pairing_port pairing_number`, where IP, pairing_port and pairing_number are provided by the Wireless debugging menu in the Pairing dialog.
5. Check `adb devices`. You may want to run `adb kill-server` if you have performed some unsuccessful commands and you have more than one device in the list. 
6. Run `adb connect ip:port`, where IP and port are provided by the Wireless debugging menu.
7. After you have copied KEGS.apk into the location where Termux can access it, run `adb install --bypass-low-target-sdk-block kegs.apk`.

Actions above have worked for the Android 14 as for 2025-04-21.
