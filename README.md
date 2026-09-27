# GKI Kernel for Lenovo Xiaoxin Tab Pro GT 11.1 (TB710FU)

Fork of [zzh20188/GKI_KernelSU_SUSFS](https://github.com/zzh20188/GKI_KernelSU_SUSFS) to build a custom GKI kernel with **Droidspaces** support.
## Comment
This is a repository for building a custom Android kernel. Specifically, in my case, the build is for the Lenovo Xiaoxin Tab Pro GT 11.1 tablet. I built the standard kernel from the AOSP project, adding support for DroidSpaces and ReSukiSU. The build itself is carried out in GitHub Actions, which allows you to completely avoid building on your own computer. GitHub servers are fast and powerful; the entire build took less than an hour.

- **Device**: Lenovo Xiaoxin Tab Pro GT 11.1 (TB710FU), Snapdragon 8 Gen 3
- **Kernel branch**: `android14-6.1` (stock Lenovo ROM, no ColorOS port)
- **Goal**: Enable `PID namespace` and `IPC namespace` for Droidspaces.

## Build
1. Go to **Actions** → **Kernel Build**.
2. Run workflow with:
   - Android: `android14`
   - Kernel: `6.1`
   - Sub-level: e.g. `145`
   - Droidspaces patch slot: `678` (or `123`/`345`)
3. Download artifact when done.

## Install
Use **LTBox** (bootloader locked). **Backup `boot` and `init_boot` first!**
Flash the ZIP via LTBox's kernel flashing option. (I haven’t tried to flash it yet; I’ll add the instructions later.)

## Notes
- No Qualcomm patches needed — this is a GKI kernel.
- Cannot upgrade above 6.1 (GKI is tied to `android14-6.1`).
- 6.1.145 is compatible with 6.1.157 (same branch).
- ACLaniakea's kernel is only for ColorOS 16 — not for stock Lenovo.

## Sources
- [zzh20188/GKI_KernelSU_SUSFS](https://github.com/zzh20188/GKI_KernelSU_SUSFS)
- [ravindu644/Droidspaces-OSS](https://github.com/ravindu644/Droidspaces-OSS)
- [miner7222/LTBox](https://github.com/miner7222/LTBox)

License inherited from upstream.
