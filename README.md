ez430rf2500 - Updated kernel extension
======================================

This is an updated kernel extension that is codeless and just makes sure that
no other kernel extensions load when plugging in an Ti Launchpad programmer
(ez430rf2500) this then allows a tool like [mspdebug][1] to communicate with
the device.


# Installation

1. Open Terminal.app
2. Navigate to this repository
3. Type `xcodebuild`
4. Navigate to `build/Release`
5. Execute 
        sudo chown -R root:wheel ez430rf2500.kext
        sudo chmod -R 755 ez430rf2500.kext
6. cp -R ez430rf2500.kext /System/Library/Extensions/
7. Execute `sudo kextload -b com.colossaldynamics.ez430rf2500`

If the extension is not loaded automatically after rebooting, then simply 
execute the last step before using mspdebug.

---

The work was inspired by [westf][2] on the [Ti e2e][3] community, he wrote the
first and original codeless kernel extension, however due to changes in Lion
the original version did not compile, mostly due to renamed existing kernel
extensions (com.apple.kernel.iokit is not com.apple.kpi.iokit). Instead of
having a project moved from Xcode 3 to Xcode 4 with its own issues, I created
the project from scratch.

[1]: http://mspdebug.sourceforge.net/
[2]: http://e2e.ti.com/support/microcontrollers/msp43016-bit_ultra-low_power_mcus/f/166/p/18554/212659.aspx#212659
[3]: http://e2e.ti.com/
