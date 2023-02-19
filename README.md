# Arch-Install-Speedrun
A guide/guidlines for Arch installation speedrunning

## 1 - Basic Explaination 
Installing arch can be a pain for many people, but many people also tend to enjoy creating a challenge out of this; which is one of the reasons Arch is o popular (you can brag about how hard it is to install, and you did it.)
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

- #### dan-custom-boot% - a version in which the run starts when the first keystroke (after booting) is pressed, to type the first command. The run ends when the system succesfully boots (basically boot% but starts later). Keep in mind - no logging in, just minimal installation required.

## 2 - Examples/Steps
### 2.1 - Example
The video linked here is a boot% speedrun, and as far as I can tell, it is the current World Record for boot%.
https://www.youtube.com/watch?v=8utpbbdj0LQ&t=13s

### 2.2 - Steps (for boot%, the most common %)
Base Arch install steps (for BIOS):

    1) Start VM
    2) cfdisk /dev/sda
    3) ‘n’ to create swap (512 mb)
    4) ‘n’ to create root (rest)
    5) mkfs.ext4 /dev/sda2
    6) mkswap /dev/sda1
    7) mount /dev/sda2 /mnt
    8) swapon /dev/sda1
    9) pacstrap -K /mnt base linux linux-firmware nano networkmanager grub
    10) genfstab -U /mnt >> /mnt/etc/fstab
    11) arch-chroot /mnt
    12) nano /etc/locale.gen
    13) uncomment en_US.UTF-8 and the other UTF-8
    14) locale-gen
    15) nano /etc/locale.conf
    16) LANG=en_us.UTF-8
    17) nano /etc/hostname
    18) place hostname (e.g “dan”)
    19) grub-install –target=i386-pc /dev/sda
    20) grub-mkconfig -o /boot/grub/grub.cfg
    21) reboot
       Done
