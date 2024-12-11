# Sound not working!

## ASUS ROG Strix G16 G614JVR
### Linux Mint 22 Cinnamon
### 6.8.0-50-generic

## Fixing it:

1. Run:
    - $ ```sudo apt install acpica-tools```
2. Run:
    - $ ```iasl -tc cirrus_ssdt_patch.dsl```
    - $ ```mkdir -p kernel/firmware/acpi```
    - $ ```cp cirrus_ssdt_patch.aml kernel/firmware/acpi```
    - $ ```find kernel | cpio -H newc --create > patched_cirrus_acpi.cpio```
    - $ ```sudo cp patched_cirrus_acpi.cpio /boot/patched_cirrus_acpi.cpio```
3. Run/Do:
    - $ ```sudo open /etc/default/grub```
    - Assign ```GRUB_TIMEOUT_STYLE=menu```
    - Assign ```GRUB_TIMEOUT=5```
    - Insert ```GRUB_EARLY_INITRD_LINUX_CUSTOM="patched_cirrus_acpi.cpio"```
4. Run:
    - $ ```sudo grub-mkconfig```
5. Reboot

# Sound Now Working! :)

# Windows 11 ISO contains a file larger than 4GB, problem with FAT32 Bootable USB drive preparation

1. Install:
    - sudo apt install wimtools
2. Convert big file into small ones
    - wimlib-imagex split ./install.wim ./install.swm 3500

# Done
