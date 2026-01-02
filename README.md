# crDroid Android Official Requirements

This repository defines the quality and maintenance requirements for all official crDroid device maintainers.
These rules are set by the crDroid core team to ensure consistent standards across all devices, protect user data and deliver a stable user experience.

---

## General rules

* Maintainers must be proficient with source control tools such as **git** and **repo**.
* All device-related sources must be published publicly under the crDroid Android GitHub organization, including:

  * Common device trees (if applicable)
  * Device trees
  * Kernel sources
* Providing a vendor repository is not mandatory due to potential proprietary or DMCA-related issues, but it is strongly recommended.
* Device trees and device-specific sources must be cloned via `crdroid.dependencies`. Any source alteration or cloning through `vendorsetup.sh` or other scripts is not allowed.
* All sources must be fully synced and pushed to GitHub before every official build release.
* Device trees may be co-maintained, but only in the case when maintainers already part of crDroid.
* Maintainers must test every build before release, preferably with external testers, to minimize user-facing issues.
* If any quality requirement (see below) cannot be met, the maintainer must clearly justify the exception when applying for maintainer status.
* An official forum thread (usually XDA) must be created using the official template and must include:

  * Installation instructions
  * Download links
  * Source links
  * Device documentation
* Installation instructions must be added to the [install_docs](https://github.com/crdroidandroid/install_docs) repository.

---

## Communication & code improvements

* Official communication takes place in the Telegram group, to which maintainers are invited upon acceptance.
* New features should be proposed via Pull Requests with clean commits for proper review.

---

## Git Rules

* Repositories must be kept clean, organized, and readable.
* Release branches must be named after the Android version, for example:

  * Android 16 → `16.0`
  * This naming is mandatory, except in the case below.
* If existing hosted sources are incompatible, maintainers must create device-specific branches, e.g.:

  * `16.0-guacamole`
* Additional branches for testing or backup are allowed.
* Original commit authorship must be preserved.
* Commit messages must be descriptive and meaningful:
* Commits must clearly explain what and why, especially reverts.
* Rebasing and force-pushing are allowed only if they do not disrupt other maintainers.

  * Never force-push shared branches without consulting all users.
* When force-pushing, create a backup branch first, e.g.:

  * `mybranch-old`
  * `mybranch-YYYYMMDD`

---

## Build Quality Requirements

### Hardware

#### Audio

* All audio outputs available in the stock ROM must work.

#### RIL

* Must be fully operational if present in stock ROM.
* Must never crash.

#### Camera

* The default camera app (Aperture) must work.
* Alternative camera apps (e.g. GCam) are allowed only if fully stable.

#### USB

* MTP, PTP, ADB, and USB tethering must work.

#### Bluetooth

* Must be fully functional.
* A2DP stack may be used if hardware supports it.

#### Wi-Fi

* 5 GHz must work if supported by stock ROM.
* Wi-Fi hotspot must work and support 5 GHz where applicable.

#### Fingerprint

* Must work if the device includes a fingerprint sensor.

#### Sensors

* All core sensors must be functional.

#### GPS

* Must be operational and support the same satellite systems as stock.

#### Storage & Encryption

* Internal and external storage (e.g. SD cards) must work.
* Encryption is mandatory.

---

### Kernel

* Kernel must not alter stock hardware parameters (CPU/GPU/memory frequencies or voltages).
* Must be built with:

  * SELinux enabled
  * Audit may be disabled
* Blocking system tweak apps (e.g. *L Speed*, *LKT*) is allowed.
* Blocking user applications (e.g. games like *PUBG*) is not allowed.

---

### Vendor

* Blobs may come from:

  * Stock ROMs
  * Other devices
  * Leaked BSPs

---

### Software

* Only production builds (`user` or `userdebug`) are allowed.
* Official builds may be:

  * Weekly
  * Monthly
  * Nightly
    but must be released for every crDroid minor version update.
* SELinux:

  * Permissive allowed only during early bring-up and beta builds.
  * Must be enforcing for all official releases.
* Official builds must not include GApps, unless booting without them is impossible.
* If GApps are included:

  * Only the minimum required package is allowed.
  * No extra or non-essential apps.
* No additional apps may be bundled by maintainers, except:

  * Stock ROM apps
  * GCam
  * Dolby

---

## Version History

* **1.0** – Initial release
* **1.1** – Rule review and adjustments
* **1.2** – Clarifications
* **1.3** – Security hardening, source maintenance clarification, removed bundled GApps
* **1.4** – Vendor inclusion cleanup and clarification
* **1.5** – Defined `vendorsetup.sh` cloning rules
* **1.6** – Installation instructions requirement
* **1.7** – Rule review and adjustments
