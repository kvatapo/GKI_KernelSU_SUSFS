# GKI Kernel for Lenovo Xiaoxin Tab Pro GT 11.1 (TB710FU)

Fork of [zzh20188/GKI_KernelSU_SUSFS](https://github.com/zzh20188/GKI_KernelSU_SUSFS) to build a custom GKI kernel with **Droidspaces** support.
## Comment
This is a repository for building a custom Android kernel. Specifically, in my case, the build is for the Lenovo Xiaoxin Tab Pro GT 11.1 tablet. I built the standard kernel from the AOSP project, adding support for DroidSpaces and ReSukiSU. The build itself is carried out in GitHub Actions, which allows you to completely avoid building on your own computer. GitHub servers are fast and powerful; the entire build took less than an hour.

- **Device**: Lenovo Xiaoxin Tab Pro GT 11.1 (TB710FU), Snapdragon 8 Gen 3
- **Kernel branch**: `android14-6.1` (stock Lenovo ROM, no ColorOS port)
- **Goal**: Enable `PID namespace` and `IPC namespace` for Droidspaces.

## Build
0. Fork this repository, and you'll get access to "GitHub Actions".
1. Go to **Actions** → **Kernel Build**.
2. Run workflow with:
   - Android: `android14`
   - Kernel: `6.1`
     Pls, remember:
     Please do not change the main kernel version. I haven't tried looking for patches for vendor modules, and besides, Lenovo doesn't provide us with the source code at all. As far as I understand, you can change the secondary version to whatever you like—for example, 6.1.165 or 6.1.420. Not all of these versions are stable, but I haven't noticed any issues with 6.1.165. If you're up for it, you could write something online about how Lenovo "lawfully complies" with the GPL license 😉
   - Sub-level: e.g. `145` (or 165, or 420, maybe 80085 or 228)
   - Droidspaces patch slot: `678` (or `123`/`345`) 
3. Download artifact when done.

## Install
Use **LTBox** (for devices with a locked bootloader). **First, back up the `boot` and `init_boot` partitions!**
Flash the ZIP file: 
1. Use the Root flashing function in the LTBox menu.
2. Select the KernelSU option.
3. You don't need to rename the kernel file (ZIP); simply feed the file to LTBox.
4. Wait...
5. Profit! The bootloader remains locked, but our custom GKI kernel is working.

## Notes
- No Qualcomm patches needed — this is a GKI kernel.
- Cannot upgrade above 6.1 (GKI is tied to `android14-6.1`).
- 6.1.145 is compatible with 6.1.157 (same branch).
- ACLaniakea's kernel is only for ColorOS 16 — not for stock Lenovo.

## Sources+respect
- [zzh20188/GKI_KernelSU_SUSFS](https://github.com/zzh20188/GKI_KernelSU_SUSFS)
- [ravindu644/Droidspaces-OSS](https://github.com/ravindu644/Droidspaces-OSS)
- [miner7222/LTBox](https://github.com/miner7222/LTBox)
- [coloros-pad-fixes](https://github.com/ACLaniakea/coloros-pad-fixes)

License inherited from upstream.
