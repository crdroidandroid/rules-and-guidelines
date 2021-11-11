# crDroidAndroid Official Requirements
---

### General rules
* All maintainers must have knowledge about source control tools such as *git* and *repo*.
* All maintainers must release device sources publicly, i.e. common device tree if present, device tree, vendor, kernel; these should be moved to *crdroidandroid* org for consistency
* Device trees can be co-maintained
* All maintainers must test every build before release
* If some quality requirement can’t be passed, the maintainer must provide the reason for the exception and it **must** be approved by the crDroid core team
* Members of crDroid core team are: **Pranav Vashi**, **Gabriel Lup**, **Simone Esposito**, **Andrzej Perczak**, **Hikari-no-Tenshi**, **firebird11**
* Ignoring any rule may end up with a warning and a temporary loss of builds release permission or with a complete banish from crDroid maintainer group
* Maintainers must respect each other, any act of hate or abuse will be severely punished
* XDA thread must be made using official template and contain all the device documentation such as installation steps, download links, sources

### Communication and chat rules
* crDroid VIP Lounge is a chat dedicated to rom maintainers and developers
* PMs should be avoided as much as possible so all users can participate in a discussion
* Mentions shouldn’t be misused nor notifying too many (possibly unrelated) people, when mentioning try to describe the problem as much as possible, avoid mentions that forces the person to read the whole conversation (e.g. *‘@devnick Can you help???’* in the middle of 20 messages long conversation, instead use *‘@devnick I get an error x when compiling y after adding z, do you have any idea about it?’*) 
* Although, off topics are usually allowed don’t go too far from around crdroid development issues
* Don’t spam about any ETAs and upcoming source updates (like new Android Security Bulletin release or *the-feature-that-los-pushed-to-gerrit-that-you-need-very-much*), each of core team devs have their own life, they try to keep track of important updates whenever possible
* Specific bugs should be reported via Github *Issue* section in the affected repository
* Feature requests should be made using *Pull Requests* with a properly prepared and **tested** commits

### Git:
* Git trees should be maintained in a tidy and organized manner
* Original commit autorhip must be maintained. If you modified it by some degree (forward port, conflict fix) you can leave a signoff or add your note at the end of a commit message, e.g. *'xNombre: fixed for R'*
Commits must preserve proper and informative naming, e.g. *'sm6150-common: Add missing camera prop'* no *'fix cam'* or *'aldksjflkajsd'*. For kernels shortened path or affected source file must be used for name, e.g. *'block: cfq: Fix uninitialized variable'* or *'adsprpcd: Fix memory leak'*
* Commits must describe the change, especially reverts. Commits without proper messages are meaningless, showing that you have no actual idea what you’re doing. Reverts without a message doesn’t let others know what problem it was causing and it is generally bad for community
* Rebasing and force-pushing is allowed as long as it doesn’t affect other users badly, e.g. don’t force-push main branch of a common dt repository until consulted with all maintainers using it
* When force-pushing a branch it is advised to create a copy of it just in case, named *'mybranch-old'* or *'mybranch-today's date'*

---
### Builds quality requirements

#### Hardware:
* **Audio**
    * All audio outputs that are available in stock rom must be operational
* **RIL**
    * Must be operational if it is available in stock rom, it must not crash in any case
    * Devices should support call recording
* **Camera**
    * Default’s system app - Snap must be working, however can be overridden. Prebuilt camera apps extracted from stock (like *AnxCamera*) can be included only if it is fully functional and doesn’t crash randomly
* **USB**
     * All usb features such as MTP, PTP, ADB, tethering must be working
* **Bluetooth**
    * Must be fully operational
    * Maintainers can switch to A2DP stack if their hardware supports it
* **Wifi**
    *  5GHz must be working if it’s available in stock rom
    * Wifi hotspot must be working and should support 5GHz
* **Fingerprint Sensor**
    * Must be operational if included
* **Sensors**
    * All basic sensors must be working
* **GPS**
    * Must be operational and support same range of satellite types as stock
* **Storage**
    * Every storage memory must be working, internal and external (like sd cards)
    * Devices must support encryption. FDE devices should switch to FBE if possible, FBE encryption must be enabled by default
    * Devices should use latest encryption method following Google recommendations, metadata partition should be used when available

#### Kernel:
* Builtin kernel must not modify default hardware configuration, which is altering cpu/gpu/mem/etc frequency/voltage because of stability reasons
* Must be built with stack protector strong
* Must be built with selinux and seccomp enabled, audit can be disabled
* Must not feature any legacy, community-driven services or driver modifications like wakelock blocker, force fast-charging, dynamic fsync
* Kernels can implement blockers for system tweaks like *L Speed*, *LKT* etc, however, must not implement blockers for any of user apps, like *PUBG*
* Kernels should be built using latest clang (which is set as a default kernel toolchain in crDroid)
* You must not use any commit that masks disabled selinux or any other security-related feature; cmdline patches for passing Safetynet are allowed (however deprecated in 12.0)

#### Vendor
Maintainers are free to use stock-extracted blobs, blobs from other devices or leaked BSPs, however, maintainers must test them after any alteration and make sure new blobs are fully operational. They must check logcat and dmesg for any unusual output (like dlsym errors).

#### Software:
* Only production builds can be shipped (user/userdebug)
* Official builds can be released weekly, monthly or as nightlies when needed but at least they must be released on every crDroid minor version update
* Selinux can be permissive during initial bringup days, only in beta builds. It must be enforced in every official release
* Sepolicy must meet security standards, it must cover every system and vendor component (no random denials), however it must not contain any rules for 3rd party apps
* Official builds must not be released with gapps unless it is impossible to flash them without bootloop
* Official builds must not contain any additional apps included by the maintainer, except from apps extracted from stock rom and *GCam*

---
### Version history:
* **1.0** - first release

