#### Installation:

> The installation process could fail due to the variety of computer hardware. If there is any problem, please contact me as soon as possible to solve it.

After the ISO has been booted up, the terminal will launch automatically. Some features cannot work in a live environment, such as the status bar(waybar), but it will after the OS is installed.

1. Inside the terminal, type in 
	`sudo archinstall --config faisal.config`
	This will launch the installation script. 
2. **Archinstall language**: Choose the language you prefer.
3. **Mirrors** -> Mirror region: Choose your region, this will affect the package download process in pacman.
	-> Back
4. **Locale**: Skip
5. **Disk configuration** -> Use a best-effort default partition layout
	-> Choose your disk: Choose
	-> Select which file system your main partition should be: Ext4
	-> Would you like to create separate partition for home?: No
6. **Bootloader**: Skip (already configured)
7. **Unified kernel images**: Skip (already configured)
8. **Swap**: Skip (already configured)
9. **Host name**: Your computer name (Default is Faisal, you can change it if you want)
10. **Root password**: You have to set the password for your root.
11. **User account** -> Add a user
	-> Username
	-> Password
	-> Re-enter the password
	-> Should you be a superuser?: Yes
	-> Confirm and exit
12. **Profile**: Skip
13. **Audio** -> Pulseaudio
14. **Additional packages**: *Must be skipped, don't touch it*
15. **Network configuration** -> Use Network Manager
16. **Timezone**: Choose your time zone
17. **Automatic time sync**: Skip
18. **Optional Repositories**: Skip

-> **Install**, After the script launches, there will be a prompt that says press enter to proceed. Wait for the installation process completed.

In the end, there will be a prompt that asks if you want to get into the chroot environment, choose no, unplug the USB, and restart the machine into the fresh Archlinux with Hyprland environment.

#### Post-installation:
**Network configuration**: 

If there is any issue with the status bar, the terminal, ... Please contact me as soon as possible to resolve it.

#### Key binding:

*Meta*: The Windows key

**Application launcher**: Meta + d
**Terminal**: Meta + Enter

