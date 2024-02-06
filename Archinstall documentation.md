#### Installation:

> The installation process could fail due to the variety of computer hardware. If there is any problem, please contact me as soon as possible to solve it.

After the ISO has been booted up, the terminal will launch automatically. Some features cannot work in a live environment, such as the status bar(waybar), but it will after the OS is installed.

1. Inside the terminal, type in 
	`sudo archinstall --config faisal.config`
	This will launch the installation script. 
2. **Archinstall language**: Choose the language you prefer.
3. **Mirrors** -> Mirror region: Choose your region, this will affect the package download process in pacman.
	-> Back
4. **Disk configuration** -> Use a best-effort default partition layout
	-> Choose your disk: Choose
	-> Select which file system your main partition should be: Ext4
	-> Would you like to create separate partition for home?: No
5. **Bootloader**: Skip (already configured)
6. **Unified kernel images**: Skip (already configured)
7. **Swap**: Skip (already configured)
8. **Host name**: Your computer name (Default is Faisal, you can change it if you want)
9. **Root password**: You have to set the password for your root.
10. **User account** -> Add a user
	-> Username
	-> Password
	-> Re-enter the password
	-> Should you be a superuser?: Yes
	-> Confirm and exit
11. **Profile**: Skip
12. **Audio** -> Pulseaudio
13. **Additional packages**: *Must be skipped, don't touch it*
14. **Network configuration** -> Use Network Manager
15. **Timezone**: Skip
16. **Automatic time sync**: Skip
17. 