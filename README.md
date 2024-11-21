# AlpBase Linux

**AlpBase** is an [Alpine Linux](https://www.alpinelinux.org/)-based distribution specifically designed for ARM devices, featured by headless setup. As it is based on Alpine, AlpBase is lightweight, enabling fast boot times. Most importantly, it is built with a security focus.

The installation is trivial as it requires: 
- flashing a memory card with AlpBase image
- powering on system
- waiting a bit as AlpBase grows file system, does initialization and checks

Finally after automatic reboot system is ready for user to login and finish installation by providing keyboard type, time zone, hostname and repository mirror.

See [Installation](#installation) section.

AlpBase is available in the following editions:
**(available soon)**

| Edition                                                                                                                                                   | Devices | Application                                                                             |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------| ------- |-----------------------------------------------------------------------------------------|
| Superˡⁱᵍʰᵗ (32bit)                                                                                                                                        | Raspberry Pi Zero version 1 (32bit processor - one core), old Raspberry Pi 2 boards | Power saving embedded applications, very light for minimum CPU usage, for one-core boards. |
| Justˡⁱᵍʰᵗ [download latest .iso.gz (68 MiB)](https://github.com/tools200ms/alpbase-linux/raw/refs/heads/release/downloads/alpbase-just_light-24r1.iso.gz) | Raspberry Pi 3 and 4 models | For building single board based servers.                                        |
| BeDesktop                                                                                                                                                 | Raspberry Pi 5 | For your desktop! |


Superˡⁱᵍʰᵗ and BeDesktop is to be available soon.

For more details see [More downloads](#more-downloads) section.

## Installation

AlpBase has been developed with SBC computers in mind such as Rasspery PI. Hence, to use it you need a board and a memory card. First flash it (with a caution): 
```commandline
zcat alpbase-just_light-24r1.iso.gz | dd of=/dev/your_sd_card
sync
```
I recommend cards from "endurance", "industrial" or Samsung EVO/PRO series. These should have ['wear-leveling'](https://en.wikipedia.org/wiki/Wear_leveling) mechanism build in, so it should work for years.

Once card is flashed, put it to device and boot. AlpBase at a boot time does partition and filesystem resizing to cover entire space. Also it does some initializationsand checks, after automatic reboot system is ready to boot to root account. There is no password for 'root', hoever it is not allowed to boot to root via SSH.

## More downloads

### Superˡⁱᵍʰᵗ

*Not yet*

### Justˡⁱᵍʰᵗ

- [alpbase-just_light-24r1.iso.gz](https://github.com/tools200ms/alpbase-linux/raw/refs/heads/release/downloads/alpbase-just_light-24r1.iso.gz) (released 20th nov. 2024)

### BeDesktop

*Not yet*

# Development plan

The list of the features to be added with next releases: 
- Add cron to be pre-configures, with: 
  - 'fstrim -a' for periodic trimming (complementary to 'discard' option that is on, but is a bit lazy)
- Change fileststem from default 'ext4' to flash friendly fs: 
  - `jffs2` for SuperLight and JustLight
  - `f2fs` for BeDesktop
- Automatically create swap (but partition, not file). Swap space is multiple of available RAM.
  - for SuperLight: there is noswap
  - for JustLight: 1.1x of available RAM
  - for BeDesktop: 1.5x of available RAM
  Swap partition over swap file is preffered as system will be able to trim in opposition to swap file

# References

- [Alpine Linux](https://www.alpinelinux.org/) website
