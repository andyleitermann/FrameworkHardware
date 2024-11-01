# QubesOS on the Framework Laptop

As a professional IT and security nerd, I've been excited about hardware by Framework since it was announced because of its emphasis on right-to-repair, hackability, and the active community surrounding it. As a long-time Linux enthusiast I've run several distributions on my Framework machines, but I've recently grown quite attached to QubesOS as my operating system of choice. These notes intend to document my Qubes setup on both my Intel Framework 13", and my newer AMD Framework 16" model.
	
# Documented Hardware

## 13" 11th Gen Intel Core i7

* CPU: 11th Gen Intel Core i7-1185G7 @ 3.00GHz
* Chipset: Intel 11th Gen Core Processor
* Graphics: Intel TigerLake-LP GT2 Iris Xe Graphics
* Ram: 64GB
* BIOS Version: 03.02

## 16" AMD Ryzen 7040 Series

* CPU: AMD Ryzen 7 7840HS w/ Radeon 780M Graphics
* Chipset: AMD
* Graphics: AMD/ATI Phoenix
* Ram: 64GB
* BIOS Version: 03.03

# Installation

1. Download the latest Qubes installation ISO from https://www.qubes-os.org/downloads/ (the version I installed was "Qubes-R4.2.3-x86_64.iso")
	* Use the MD5 checksum provided on the Qubes download page to verify the authenticity and integrity of your ISO file.
3. Burn a flash drive using the `dd` command, Balena Etcher or any similar program.
4. Upgrade the BIOS
	* I did this on the 16". I forgot this step on the 13" model, but it hasn't seemed to present any issues so far. 
5. Power on the machine while continuously tapping F2 to enter BIOS Settings
	1. Ensure Intel VT-d (or the AMD equivalent) is enabled
	2. Ensure Secure Boot is disabled
	3. Ensure USB Boot is enabled
	4. Save and Exit BIOS Settings
6. Power off the machine and insert the Qubes flash drive. 
7. Power on the machine while continuously tapping F12 to enter the BIOS boot selection screen
8. Select your USB flash device from the menu and hit Enter
9. Select the default "Test media and install Qubes OS..." option from the GRUB menu
	* This test may take a few minutes, but it's worth it to make sure your installation media isn't corrupted. 
10. Once the graphical installation process begins, select your language and keyboard layout, and click Continue.
11. From the Installation Summary page, navigate to the Installation Destination settings page
12. On the Installation Destination page, make sure the correct drive for installation is selected, and the correct options are selected, and click Done. 
13. If you're reclaiming disk space from an existing installation, make sure the correct partitions are selected for preservation or deletion, and click Reclaim space.
14. Back on the Installation Summary page, select User Creation.
15. Create your user account including Full name, User name, and Password, then click Done. 
	* It is not necessary to create a Root Account - the administrator account has sudo privileges by default, and unprivileged users can be created once the installation is complete. 
16. Ensure that Time & Date settings are correct. 
17. Software Selection and other settings should probably be fine on the defaults, but you can poke around if you want. 
18. Once you're satisfied that all the settings are correct on the Installation Summary page, click Begin Installation (this will take a while).
19. Once the installation is complete, click Reboot System (be sure to remove the flash drive before it boots back up). 
20. The GRUB menu now present on your internal drive should come up. Select the default boot option to boot into Qubes for the first time. 
21. Enter your disk encryption password if prompted.
22. On the Initial Setup page, under System, select Qubes OS.
23. On the Templates Configuration page:
	* Framework laptops use a USB controller rather than a PS/2 controller for the keyboard (at least I know this is true of the 16" model), so it is necessary to check on the "Automatically accept USB keyboard" option. 
	* I've also enabled the "Automatically accept USB mice" option for the same reason. 
	* On my first install, I switched the Default Template to Debian, which didn't present any major issues. But it's important to note that the Qubes developers are mostly testing with a Fedora-based Dom0 and default templates, so most documentation and development is tailored to Fedora. So if you're new to Qubes, you should probably just get to know it using Fedora, then switch to Debian if you prefer once you're already comfortable with Qubes. 
	* If you don't know what you're doing here, it's best not to change any of the other default settings. 
	* Once you're sure your Templates Configuration is ready, click Done.
24. Back on the Initial Setup page, click Finish Configuration.