# Arch-Install-Speedrun
A guide/guidlines for Arch installation speedrunning

## 1 - Basic Explaination 
Installing arch can be a pain for many people, but many people also tend to enjoy creating a challenge out of this; which is one of the reasons Arch is o popular (you can brag about how hard it is to install, and you did it).
In this guide I will go over the basic guidlines and versions of the speedrun.

### 1.1 - RULES
- NO SCRIPTS ALLOWED (such as archinstall, or any custom-made scripts to auto-input commands)
- NO CHEATING (phony commands, speeding up the video, etc.)

And that's about it, as long as you conform to the %s that follow.

### 1.2 - Versions
note: I don't fully know all of the official terms and most of these are either from mere speculation or a small amount of research; take my definitions with a grain of salt, but I believe these are some good guidlines.

- #### any% - a version which lets you do anything, from preprogramming the ISO to echoing data onto files, and lets you choose when to start and stop the time. Common time: undefined, 30s-5m
- #### boot% - a version which starts the time as soon as you boot the system, and ends as soon as you boot a base version; essentially, if it boots, it's good, which lets you install an extremely basic and minimal version of arch. Common time: 1-2 minutes
- #### desktop% - a version which makes you install a desktop environment (usually of your choice), making you install many more packages in order to do so. Common time: 3-4 minutes
- #### custom% - a version which lets you customize whatever you need to do in order for the run to start and complete (e.g opening google and searching something)
- #### EFI% - a version which requires you to use the EFI boot architecture; which takes considerabely longer to install, due to the added steps.

And there are dozens more variations, which usually can fall under custom%. Here is my personal variation, which I use to measure my runs:

- #### dan-custom-boot% - a version in which the run starts when the first keystroke (after booting) is pressed, to type the first command. The run ends when the system succesfully boots (basically boot% but starts later). Keep in mind - no logging in, just minimal installation required. HOWEVER - you need to input each command manually, you can't use a muli-window editor to pre-program the commands.

## 2 - Examples/Steps
### 2.1 - Example
The video linked here is a boot% speedrun, and as far as I can tell, it is the current World Record for boot%.
https://www.youtube.com/watch?v=8utpbbdj0LQ&t=13s

### 2.2 - Steps (for boot%, the most common %)
Base Arch install steps (for BIOS):

1) Start the VM
2) Open a partition editor, I think `cfdisk` is the easiest to use for this. `cfdisk /dev/your_disk_name`
3) Use 'n' to create a partition, size it 512M (mb) and press enter
4) Scroll to the free space and use 'n' to create a partition, sized the rest of the disk.
5) Scroll up to the first partition, press 't' to change the type and select 'linux swap (82)'
6) Use the arrow keys to navigate to the 'write' option, type 'yes' and hit enter, saving your changes and partitioning the disk.
7) Format the parittions: use `mkfs.ext4 /dev/your_root_partition` for the root partition
8) Format the partitoins: use `mkswap /dev/your_swap_partition`
9) Mount the partitions - use `mount /dev/your_root_partition /mnt`
10) Mount the partitions - use `swapon /dev/your_swap_partition`
11) Install the base packages - use `pacstrap -K /mnt base linux linux-firmware` and also some other packages needed `nano networkmanager grub`
12) Generate the fstab - use `genfstab -U /mnt >> /mnt/etc/fstab`
13) Chroot into the new system - use `arch-chroot /mnt`
14) Configure the locales - use `nano /etc/locale.gen` and uncomment en_US.UTF-8
15) Configure the locales - use `locale-gen`
16) Configure the locales - use `nano /etc/locale.conf` and add LANG=en_US.UTF-8 (or another language if you don't have a US keyboard layout)
17) Configure the hostname - use `nano /etc/hostname` and add a hostname such as `arch`
18) Install GRUB - use `grub-install --target=i386-pc /dev/your_device_name (NOT PARTITION)`
19) Configure GRUB - use `grub-mkconfig -o /boot/grub/grub.cfg`
20) Exit the system - use `exit`
21) Reboot the system - use `reboot`
22) Once rebooting, make sure that the system boots into the disk - on virtualbox, you can use f12 to select the boot device.

And that's it! Make sure to replace `your_device_name` and the `your_partitions` with your _actual_ device name, for example on Virtualbox it is usually /dev/sda.

NOTE: If you don't have a US keyboard layout, you will have to set the keyboard layout at the start (I don't think that would count as starting the run), and also set your locales to said layout.
NOTE2: If you're doing EFI%, make sure to do the extra steps of creating the EFI partition, mounting, etc.

And that's the very interesting world of arch speedrunning. Thank's for reading :D
