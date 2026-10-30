# blocker-ihardlyknower

This repository is a documentation of hardware and software application environments, focusing on the mechanisms, limitations, and configurations of restricted systems.

## WARNING!
This repository was created strictly for educational purposes and proof-of-concept analysis. The author does not condone or encourage violating institutional acceptable use policies or bypassing administrative controls. You assume all responsibility and liability for how you utilize this information.

## Table of Contents
- [Chromebooks](#chromebooks)
  - [Shimboot](#shimboot)
  - [Extension / Enrollment Bypass Tools](#extension--enrollment-bypass-tools)
- [Calculators](#calculators)
  - [TI-84 / TI-Nspire Family](#ti-84--ti-nspire-family)
  - [Casio Family](#casio-family)
- [Windows-Managed Environments](#windows-managed-environments)
- [Resources & Further Reading](#resources--further-reading)
- [Contributing](#contributing)

---

## Chromebooks

### Shimboot
Shimboot is a method of booting a Linux operating system or un-enrolled version of Chrome OS on a Chromebook. This works by basically tricking the Chromebook's RMA (recovery/shim) system into thinking that a bootable image is an official recovery image. It doesn't unenroll the device from device management directly — it boots an entirely separate OS environment off external storage, sidestepping the managed ChromeOS install rather than modifying it.

**Relevant mechanisms:** RMA shim exploitation, verified boot, external boot media.

### Extension / Enrollment Bypass Tools
A number of community projects catalog tools specifically for disabling forced extensions (filtering/monitoring agents like GoGuardian, Securly, Lightspeed) or unenrolling devices from management. These are generally built around one of a few mechanism classes:

- **Enrollment/recovery exploits** — abusing the device's recovery or verified-boot flow to unenroll it from management (conceptually similar in spirit to Shimboot, but targeting the enrollment flag rather than booting an alternate OS).
- **Extension-disabling tricks** — exploiting bugs or resource limits in how Chrome's extension/policy engine handles certain inputs, causing managed extensions to crash, hang, or fail to reload.
- **Policy/sync abuse** — leveraging sync or local-state tooling to modify what the browser believes its managed policy is.

This repo doesn't reproduce specific payloads for these — they're narrow, frequently patched, and functionally indistinguishable from exploit code targeting security software, which is out of scope here. If you want to go deeper, the ChromeOS-exploit community (various GitHub orgs, r/chromeos) tracks current status, since most of these have a shelf life measured in Chrome point releases.

---

## Calculators

### TI-84 / TI-Nspire Family
Graphing calculators in the TI ecosystem have historically supported third-party OS modifications and game loading via:
- **ArTICL / TI-Connect-based transfer exploits** — leveraging the calculator's link protocol to push unsigned programs.
- **Ndless** (TI-Nspire) — a jailbreak framework that allows native C/ASM programs to run outside the sandboxed TI-BASIC/Lua environment.
- **MirageOS / Doors CS** (TI-83/84) — shell environments that allow assembly games and programs to run alongside the stock OS without modifying it.

**Relevant mechanisms:** signed OS validation bypass, unsigned program execution via calculator link protocols.

### Casio Family
Casio's fx-9860/fx-CG series have similar community jailbreaks (e.g. Add-In Gate exploits) that allow unsigned add-ins to execute, generally relying on parsing vulnerabilities in the OS's add-in loader rather than full OS replacement.

---

## Windows-Managed Environments
Documentation here would cover the general *class* of restriction (Group Policy, AppLocker, WDAC) and the general *class* of bypass technique (e.g. LOLBins, alternate execution contexts) at a conceptual level — this repo intentionally avoids live exploit scripts for actively-maintained enterprise tooling.

---

## Resources & Further Reading
- [Shimboot (GitHub)](https://github.com/ading2210/shimboot)
- [Ndless](https://ndless.me/)
- r/calculators, r/chromeos communities for current status of individual exploits (these get patched — check dates before relying on anything here)

---

## Contributing
PRs documenting *mechanisms* (how something works) are welcome. PRs that are just raw exploit payloads with no explanation won't be merged — the goal of this repo is understanding, not a point-and-click toolkit.
