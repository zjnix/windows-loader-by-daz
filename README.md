# windows-loader-by-daz
Windows Loader by Daz v2.2.2

© All Rights Reserved

Since we don't know the original license

Used for Activate Windows Vista/7 Retail

-------

1. Recovery
2. Genuine status
3. Questions and answers
4. UEFI motherboards
5. Server 2012 (R2) compatibility
6. Checksums
7. Changes
8. Arguments
9. Extra



##########################################################################
#   1   -   Recovery
##########################################################################
Is Windows failing to boot after you installed the loader? Just do the following.

* Boot up the PC from your Windows installation disk
* Press and hold SHIFT and then press F10
* Input "bootsect.exe /nt60 SYS /force" (without quotes)
* Restart the PC

Note: If the above doesn't fix your boot issue then use the command "bootsect.exe /nt60 ALL /force" instead. Just make sure you remove all USB flash drives before you use the command.

Alternatively try holding the 'R' key after your BIOS screen. If you time it right then you'll see a boot menu. From the menu select to boot without a SLIC.



##########################################################################
#   2   -   Genuine status
##########################################################################
Have you installed the loader but you're not genuine? Just check the following.

* Check the details line contains "v2.1", "v2.2" or "v2.3"
* Try to validate online with Internet Explorer at http://www.microsoft.com/genuine/validate/

Note: If the details line doesn't read v2.1, v2.2 or v2.3 then go to the advanced tab, select to disable type 4 memory and reinstall the loader. If that doesn't work then use the legacy setting instead.



##########################################################################
#   3   -   Questions and answers
##########################################################################
Q. The loaders status says "Modified - Uninstall other cracks", what do I do?
A. You can either find a way to uninstall the other cracks, download WAT Fix or format. http://forums.mydigitallife.info/threads/26994

Q. Why did I lose activation after I allowed Windows to run startup repair?
A. Startup repair will write a new boot sector. To prevent this use the following command from command prompt as an administrator "bcdedit /set {default} bootstatuspolicy ignoreshutdownfailures"

Q. I dual boot with Windows 8 and the loaders not working for me, so how do I fix it?
A. Boot to Windows 8 and enter the following command from command prompt as an administrator "bcdedit /set {default} bootmenupolicy legacy"

Q. I installed the loader and I'm still not activated, so what do I do now?
A. Go to the loaders advanced options tab and select to either either disable type 4 memory or use the legacy setting, then press install and reboot when prompted. You may also need to select the option to ignore the systems existing SLIC and/or revalidate online.

Q. The loaders status says "Unsupported partition table", why is this?
A. You're either using GPT on a UEFI motherboard or you've got a locked OEM partition. Both problems can be fixed by fully formatting your entire hard drive.

Q. I received the error message "Error finding your systems active partition", what do I have to do?
A. You need to format the whole hard drive with a program like Active@ Kill Disk. This issue is caused by your locked OEM partition. http://software.lsoft.net/boot-cd-iso.zip

Q. I received the error message "Failed to add loader to the boot code", what do I have to do?
A. Disable any system protection. Some types of software block the loader application from installing to the boot code.

Q. I've used a version of the loader before and it failed to work, what do I have to do?
A. If you previously used bootsect to get back into Windows then you first need to press uninstall, reboot and then install the newest version of the loader.

Q. I've previously used another activation solution and I think it's modified my systems files, can I fix it?
A. You can first try to uninstall what you originally installed and then try running "sfc.exe /scannow" from command prompt as an administrator.

Q. I lose activation status after my systems been to sleep or has been in hibernation, can I fix it?
A. Go to the advanced options and select to disable type 4 memory, install the loader again and see if that cures it. If you're not cured try to disable type 3 memory instead. If it still fails try selecting the legacy setting.

Q. I installed the loader and my system hangs during the boot process, can I fix it?
A. Go to the advanced options and select to disable type 4 memory, install the loader again and see if that cures it. If you're not cured try to disable type 3 memory instead. If it still fails try selecting the legacy setting.

Q. I installed the loader and rebooted but I'm not activated. The loader application displays the message "BAD SLIC SIZE" or "BAD SLIC DATA", can I fix it?
A. Uninstall the loader, power down and then boot up the system again. Go to the applications advanced options and select to ignore the existing SLIC and then press install and reboot when prompted.

Q. My systems UEFI, but I've formatted the drive to use MBR and I'm still not activated. What do I do?
A. Check your UEFI menu for secure boot and make sure it's disabled.



##########################################################################
#   4   -   UEFI motherboards
##########################################################################
The loader doesn't work when the systems using GPT. The workaround is to pre-format your hard drive so that it uses MBR instead.

From your BIOS select to boot the Windows DVD without UEFI, press and hold SHIFT and then press F10 and then enter this:

diskpart
list disk
select disk 0
clean
convert mbr
create partition primary
select partition 1
format fs=ntfs quick

Boot the Windows DVD the same way you did the first time and then continue with the installation of Windows. Once complete you can then install the loader.

To forcefully boot Windows 7 without UEFI you can use the Windows 7 USB/DVD Download Tool. Once the USB is created just delete bootmgr.efi from the USB and then try to boot from it.



##########################################################################
#   5   -   Server 2012 (R2) compatibility
##########################################################################
Starting with the Server 2012 range Microsoft requires the RSDP to be in read only memory. Because of this there are limitations.


* Systems with an existing SLIC in their BIOS should have success
* Systems with an Intel CPU may have success due to chipset lock picking
* Systems with an AMD CPU may struggle to gain activation status if they don't have an existing SLIC in their BIOS
* If the loaders details line contains "v2.3" or "v2.2" but your systems not activated then your systems probably not compatible

======
To convert Windows Server 2012 from an evaluation edition you must use the following command:

DISM /online /Set-Edition:<edition ID> /ProductKey:XXXXX-XXXXX-XXXXX-XXXXX-XXXXX /AcceptEula

Here's two examples:

DISM /online /Set-Edition:ServerDatacenter /ProductKey:B7RRX-RVN4P-PCPBM-89D8Y-X4PQH /AcceptEula
DISM /online /Set-Edition:ServerStandard /ProductKey:VDNYM-JBKJ7-DC4X9-BT3QR-JHRGY /AcceptEula

Your system may then need to reboot 2 times before the loader will work.
======



##########################################################################
#   6   -   Checksums
##########################################################################
File   : Windows Loader.exe
CRC-32 : b4417bb9
MD4    : 10cc300f6c7b1b0fe8fcf5d9cfd07e15
MD5    : 323c0fd51071400b51eedb1be90a8188
SHA-1  : 0efc35935957c25193bbe9a83ab6caa25a487ada



##########################################################################
#   7   -   Changes
##########################################################################
Version 2.2.2
* Added support for Windows Server 2012 R2 operating systems
* Added a valid OEM SLP key for Windows Server 2012 R2 Standard (it was taken from a Dell server)
* Added a warning for virtual machines created in VirtualBox that are using Windows Server 2012 or 2012 R2 (use ICH9 for the loader to work)
* Allowed the loader to be installed onto Xen again (if it doesn't work for you then it can't be fixed)
* Added lots of new keys, SLIC's and certificates
* Cleaned up the UI
* Other minor tweaks and fixes

Version 2.2.1
* Added a new GRLDR
* Redesigned the advanced options tab and added an option to relocate the RSDP to the EBDA
* Added Seneca and Twinhead Windows 7 Professional keys
* Added BenQ Windows 7 Home Premium key
* Added Seneca SLIC and certificate
* Other minor tweaks and fixes

Version 2.2
* Fixed Xen detection
* Fixed a small issue with some decoded keys
* Pressing the delete key will now remove the OEM picture
* Other minor tweaks and fixes

Version 2.1.9
* Added a new GRLDR
* Blocked the loader from installing onto Xen as it's not supported
* Added notes about Windows Server 2012 and Windows 8 to the read me file

Version 2.1.8
* Added a new GRLDR (required to support Server 2012 operating systems)
* Added support for Windows Server 2012 Standard, Essentials, Foundation & Datacenter
* Added support for Windows Storage Server 2012 Standard & Workgroup
* Added support for Windows MultiPoint Server 2012 Standard & Premium
* Added HEDY Windows 7 Ultimate key
* Added ByteSpeed, DakTech, Genuine C&C, INSYS, WIPRO & Zoostorm Windows 7 Professional keys
* Added ByteSpeed & INSYS Windows 7 Home Premium keys
* Added AOC & ByteSpeed Windows 7 Starter keys
* Added AOC, ByteSpeed, EXTRA Computer GmbH, Mustek, Velocity and Western Digital v2.1 SLIC's and certificates
* Added a Dell v2.2 SLIC to activate 2012 server editions (only recommended for Server 2012 unless you're dual booting with Windows 7/Vista)
* Added new launch parameters
* Fixed a Windows key decoding bug
* Fixed the "Licensed" text color for BIOS activated systems
* Other minor tweaks and fixes

Version 2.1.7
* Fixed a bug that was causing the RSDT to get trashed

Version 2.1.6
* Added a new GRLDR version
* Fixed a Hyper-V installation issue
* Added Tangent Professional serial
* Added Dealin Starter serial

Version 2.1.5
* Added a new GRLDR version
* Added Jetway Home Premium, Home Basic and Starter serials
* Added Jetway SLIC and certificate
* Fixed a bug that caused the unsupported status to be set for every type of issue
* Highlighted the status line so that people understand that Windows 7 Enterprise is an unsupported operating system
* Other minor tweaks and fixes

Version 2.1.4
* Fixed a bug that would cause some systems to fail to boot
* Fixed a bug where an unsupported OS would fail to have it's status set to unsupported
* Added Qbex SLIC and certificate
* Other minor tweaks and fixes

Version 2.1.3
* Added a new GRLDR version
* Added support for Windows Home Server 2011
* Added support for Windows Server 2008 R2 Datacenter
* Added a few new serials
* Improved handling for systems with missing ACPI tables

Version 2.1.2
* Added a new GRLDR version that fixes 2 bugs
* Added support for Windows Small Business Server 2011 Essentials
* Added lots of missing Vista serials (Thanks to Tito)

Version 2.1.1
* Fixed a bug that prevented existing SLIC's from being ignored
* Fixed a bug that caused Windows 8 serials to be decoded incorrectly
* Added Equus, Impression Computers and Xplore SLIC's and certificates
* Added Toshiba Windows 7 Ultimate serial
* Added Xplore Windows 7 Professional serial
* Added Impression Computers Windows 7 Home Premium serial
* Added LaCie Windows Server 2008 R2 Standard serial
* Added Western Digital Windows Storage Server 2008 R2 Essentials serial

Version 2.1
* Added a new GRLDR version
* Added CRC32 checksums to SLIC and certificate dumps
* Enhanced serial decoding so that it supports Windows 8
* Added EXO, ONKYO and Quanmax Home Premium serials
* Added EXO and ONKYO SLIC's and certificates
* Removed NEC Ultimate serial as it's not NEC
* Other minor tweaks and fixes

Version 2.0.9
* Added a new GRLDR version
* Added NTFS checks for the active system partition
* Added Paradigit SLIC and certificate
* Added Paradigit Home Premium serial
* Added ZT Systems Home Premium serial
* Added NEC Ultimate serial
* Other minor tweaks and fixes

Version 2.0.8
* Fixed a bug that prevented external SLIC's and certificates from loading
* Fixed a bug that prevented the AT Computers profile from working
* Added BGH e-Nova SLIC and certificate
* Added BGH e-Nova Professional serial

Version 2.0.7
* Added a new GRLDR version
* Added Hyper-V support
* Added Quanmax Professional serial
* Added Stone Ultimate, Professional, Home Basic and Starter serials
* Further enhanced partition identification
* Fixed a bug in the uninstall function
* Fixed access to the recovery menu (Hold 'R' during boot)
* Other minor tweaks and fixes

Version 2.0.6
* Added a new GRLDR version
* Fixed the ignore existing SLIC option
* Added Stone Home Premium serial
* Added Itautec Home Basic serial
* Added Stone and Itautec SLIC's and certificates
* Cleaned up serials for all Windows Server editions
* Other minor tweaks and fixes

Version 2.0.5
* Added a new GRLDR version
* Added a new option to patch all OEM table ID's
* Added CCE, Chuangzhicheng and Crea SLIC's and certificates
* Added CCE Windows 7 Professional serial
* Added KSystems and Crea Windows 7 Starter serials
* Changed the way partitions are identified which should fix boot issues for systems with hidden OS partitions

Version 2.0.4
* Added a new GRLDR version
* Recoded around 30% of the application so that the UI can always remain displayed
* Added progress indicators
* Added LG Starter serial
* Added HP and IBM Windows Small Business Server 2011 Standard serials
* Added Kraftway and Philco Home Premium serials
* Added Philco profile
* Other minor tweaks and fixes

Version 2.0.3
* Added a new GRLDR version
* Removed the prompt to ignore invalid SLIC's and have made the setting apply for Samsung systems only
* Other minor tweaks and fixes

Version 2.0.2
* Added a new GRLDR version
* Added TAROX Ultimate, Professional, Home Premium and Starter serials
* Fixed a bug that caused the wrong certificate to be dumped on some machines
* Added a prompt to ignore the existing SLIC on a system if the SLIC is invalid
* Other minor tweaks and fixes

Version 2.0.1
* Added a new GRLDR version
* Added TAROX and Vestel SLIC's
* Added Positivo and Kraftway Home Basic serials
* Enhanced the installation of GRLDR
* Enhanced the dump option so that it will now dump the certificate and serial as well as the SLIC
* Other minor tweaks and fixes

Version 2.0.0
* Fixed a bug that could cause the application to crash
* Fixed unicode character input for OEM information editing

Version 1.9.9
* Fixed sandbox bug

Version 1.9.8
* Added a new GRLDR version
* Added OEM branding options
* Added AT Computers, Genuine & Zoostorm SLIC's
* Added Genuine Home Premium serial & Zoostorm Starter serial
* Enhanced error handling
* Enhanced environment detection
* Other minor tweaks and fixes

Version 1.9.7
* Added a new GRLDR version (This should fix many problems)
* Added Viewsonic Starter serial

Version 1.9.6
* Added a new GRLDR version
* Added Aquarius, Hannspree, Hyrican, Lanix, Semp Toshiba, Twinhead & Synnex SLIC's
* Added Exper, Fujitsu and Hannspree Starter serials
* Added Dealin, Founder and Fujitsu Home Basic serials
* Added Gigabyte and Shuttle Home Premium serials
* Added Dealin and Mercer Professional serials
* Added Fujitsu Ultimate serial
* Added HP serials for UltimateE, ProfessionalE, HomePremiumE & StarterE
* Other minor tweaks and fixes

Version 1.9.5
* Added a new GRLDR version which fixes a bug that prevented activation on systems with an XSDT

Version 1.9.4
* Added a new GRLDR version (Improves the ignore existing SLIC function)
* Disabled table sorting by default for compatibility reasons
* Added an option to disable type 3 memory as well as an option to reverse the SLIC search direction
* Displays motherboard version to help with debugging
* Added ECS, Dealin, Higrade and KSystems SLIC's
* Added HCL, Ksystems and MSI Home Basic serials
* Added MSI Professional serial
* Added Dealin Home Premium serial
* Other minor tweaks and fixes

Version 1.9.3
* You can now install the loader from safe mode
* Added Panasonic, Viewsonic and Kraftway SLIC's
* Added Viewsonic and Kraftway serials
* Fixed a status refresh bug that caused the OS information to be displayed twice
* Other minor tweaks and fixes

Version 1.9.2
* Added a new GRLDR version
* Added an option to disable ACPI table sort (Use this if your system hangs under the default settings)
* Added an option to disable the usage of type 4 memory (Try this if you lose genuine status after hibernation or sleep)
* Tweaked the UI which now also displays the systems current serial
* Fixed a bug which prevented the application from installing the loader over really old GRLDR versions
* Other minor tweaks and fixes

Version 1.9.1
* Improved corrupt SLIC detection
* Added Medion Starter serial & STEG Professional serial
* Added a new GRLDR version
* Other minor tweaks and fixes

Version 1.9
* Fixed a bug that caused a few systems to hang
* Added an option to ignore a systems existing SLIC

Version 1.8.9
* Added a new GRLDR version
* The default boot menu display time is now set to 30 seconds
* Custom usermenu.lst file scanning is now an option (disabled by default)
* Other minor tweaks and fixes

Version 1.8.8
* Added 8-bit SLIC checksum verification
* Added a new custom application icon (Thanks to Logie)
* Added a new GRLDR version (Fixes custom menu loading, just be sure to call your menu usermenu.lst)
* Improved ASUS system profiling
* Fixed a bug that prevented people upgrading from version 1.7.x to 1.8.4 or newer

Version 1.8.7
* Loads your last used settings (Should work with all 1.8.x builds)
* Added a new GRLDR version

Version 1.8.6
* Added a new GRLDR version
* Added SLIC detection with a dumping feature (Used to check if a SLIC is valid)

Version 1.8.5
* Fixed a bug that caused upgrading to fail when "preserve current boot code" was selected
* Added a new GRLDR version
* Added Alienware serial (Professional)
* Other minor tweaks and fixes

Version 1.8.4
* Added a new GRLDR version (Calculates the EBDA end 256 bytes lower)
* Added the ability to give the SLIC a custom position (Useful if SLIC emulation fails under the default options)
* Added Olidata SLIC, certificate and serial

Version 1.8.3
* Added a new GRLDR version (Fixes EBDA length calculation)

Version 1.8.2
* Reverted the loaders memory scanning back to low memory first and then EBDA
* Fixed x64 partition checks
* Other minor tweaks and fixes

Version 1.8.1
* Added a legacy mode which should activate some systems that don't comply with the normal ACPI specifications
* Improved support for compressed partitions
* Added Toshiba, Exper, Wortmann and Casper SLIC's
* Added a new HCL Windows 7 Professional serial
* Other minor tweaks and fixes

Version 1.8
* Cleaned up and improved a lot of code
* Added a new GRLDR version (Thanks to lash78 for spending a few hours helping to debug)
* Made the UI even more user friendly
* Added some new serials
* Improved certificate OEMID to system OEMID installation
* Made OEM recovery partition ignoring optional

Version 1.7.9
* Fixed a bug that caused an error on non-english systems
* Added an option to disable the loaders random file padding (Use this if you get stuck in a reboot loop and can't access GRUB)

Version 1.7.8
* Fixed loader file padding issue that caused some systems to fail to boot into Windows
* Fixed Windows Server 2008 R2 support
* Fixed loader pointer issues (For when each OS needs it's own active partition exclusive while other primaries are set to hidden)
* Added an option to set the boot menu timeout
* Added an option to install the loader without changing your systems MBR (Good for Linux users & FirstDefense-ISR)
* Added support for Haier, Hasee, HCL, Jooyon, NEC, Tongfang and Viliv
* Added various new OEM SLP serials
* Blocked title version modifications
* Cleaned up some code for better performance (May help fix the rare partition finder error)

Version 1.7.7
* Fixed loader modes to stop system hangs
* Changed the way the loader is wrote to the partition (no more mounting)

Version 1.7.6
* Improved the encryption support
* Added support for Gigabyte
* Added Toshiba Professional serial

Version 1.7.5
* Removed the beta SLIC detection (caused crashes on 1.7.4)
* Added support for LG
* Added various new OEM SLP serials

Version 1.7.4
* Improved SLIC detection (still not tied to anything, it's simply a BETA feature until I get more feedback)
* Fixed file write errors caused by version 1.7.3
* Added support for Server Standard R2
* Added support for FSC, Quanmax and Trigem
* Added various new OEM SLP serials

Version 1.7.3
* Improved free drive letter assignment
* Corrected some grammar
* Added random SLIC encryption support, this means everyones SLIC will have a unique encryption
* Added GRLDR file size randomization
* Added GRLDR v0.97-DAZ+SEC-R2. This is just a minor version to support the random encryption
* Added SLIC table detection (BIOS mod and software, it can tell the difference)
* Added support for Advent, Medion and Nokia
* Added various new OEM SLP serials

Version 1.7.2
* Added encrypted SLIC support
* Added random loader names
* Added byte differences (everyones GRLDR loader won't be byte for byte the same)
* Added a new GRLDR version (0.97) from zsmin (custom edition for my program)
* Added /norestart argument
* Added support for Windows 7 Home Basic (4 new keys)

Version 1.7.1
* Removed window transparency to fix a Windows 7 artifacts bug and improve responsiveness on older systems using onboard graphics
* Improved the "Custom menu.lst" loader option. It will now show all people using this setting the GRUB menu at system startup
* Upgraded some certificates to version 2.1
* Added a new GRLDR version (0.96) from zsmin (custom edition for my program)
* Added external SLIC support (read "How to add support.txt" for more info)
* Added support for BenQ and Sony machines
* Added support for Windows 7 Starter Edition
* Added various new OEM SLP serials

Version 1.7
* Removed the older loader
* Added loader mode options
* Changed the UI so that it's now slightly transparent as well as resized to suit the new options
* Added Samsung support for Windows 7 Ultimate, Professional & Home Premium editions
* Improved internal resources security

Version 1.6.9
* Added amber as a color to the application integrity checking as well as a few tweaks to the existing code (you should still always check the displayed application path even when green)
* Cleaned up some code for better performance
* Added new GRLDR 0.94 from zsmin

Version 1.6.8
* Added application integrity checking. This is a new feature which will display you with information about how the application was launched when the mouse is hovered over the green or red icon. It's goal is to inform you if you are running an untouched version of the application or one that could have been modified in some way by a script kiddie. Of course green is the best result, if it's red then be cautious as someone's likely binded a trojan!

Version 1.6.7
* Fixed Windows Vista activation status
* Added Windows 7 Enterprise editions as a supported OS, although you will need to wait for OEM SLP keys to leak

Version 1.6.6
* Fixed activation checking for non-english systems (This release is just to address confusion as to if a system is activated or not)

Version 1.6.5
* Improved profile matchups (for matching a SLIC, certificate and serial)
* Added activation checking for Windows 7, Vista and Server 2008
* Added tokens checking for Windows 7 (alerts the user, repair is manual so that later on down the line this loader will never frankenbuild your system itself!)
* Added error handling should UAC fail to elevate the application
* Added Asus SLIC, certificate and Home Premium serial
* Added new GRLDR beta 0.93 from zsmin

Version 1.6.4
* Fixed a missing serial issue when run as a standalone
* Added checking to elevate to an administrator only when run on Vista or Windows 7
* Corrected a typo found during an uninstall

Version 1.6.3
* Fixed a missing serial issue caused by the new bios type detection feature
* Fixed an issue which would cause the application to start hidden behind other windows

Version 1.6.2
* UAC control reworked
* Changed the default loader to zsmin's
* Bios type detection now assigns a SLIC, certificate and if possible a serial to match
* Added leaked Dell Home Premium key

Version 1.6.1
* Fixed Windows Vista version detection
* Added new Dell Windows 7 Professional key
* Added new GRLDR beta 0.91 from zsmin

Version 1.6
* Fixed Windows version detection (name spaces were off)
* Added support for Windows 7 Home Premium
* Compressed the internals a litte so the executable size has been shaved just a little

Version 1.5.9
* Added new GRLDR beta 0.90 from zsmin
* Fixed missing OS information on unsupported OS's

Version 1.5.8
* Keys and certificates now use internals when external files cannot be found (this means you can run just the executable as a standalone application)
* Added future OS key support (via Keys.ini)
* Changed how an unsupported OS is displayed
* Added new GRLDR beta 8c from zsmin

Version 1.5.7
* Fixed unicode text string issue which caused activation to fail
* Fixed title assignment for unsupported operating systems
* Added new GRLDR beta 8b from zsmin

Version 1.5.6
* Full recode so that debugging is easier for me and performance and reliability is better for you
* User interface redesigned for simplicity
* Added new GRLDR beta 8 from zsmin (Thanks go to him)
* Added external certificate support for bios modders
* Added external key input support
* Added argument support

Version 1.5.5
* Improved error handling even more
* Rewrote drive mounting code (should fix the x64 mounting issue and letter assignment)
* Mac users should now automatically have the experimental loader option selected for them
* Tweaked UI layout just a little (width was off)
* Fixed other minor issues

Version 1.5.4
* Tweaked free drive letter handling just a little
* Corrected a typo on the experimental loader option
* Corrected Windows Vista version ID

Version 1.5.3
* Fixed a rare issue that would select a network drive as a free drive letter
* Performing an uninstall now restores to the default Windows 7/Vista bootsect (wasn't required, but some machines need this!)
* Performing an uninstall now inserts trial keys so you will have x amount of days remaining (On Windows 7)
* Upgraded support for error handling (errors get logged to the system event viewer)
* The loader window will now start centered when launched
* Added a custom file icon (Thanks to my friend Logie)
* Added support for Starter, HomeBasicN and BusinessN versions of Windows Vista
* Upgraded experimental GRLDR to beta 6 (Thanks to zsmin)
* Added another GRLDR for older Dell and HP machines to try (the older loader option)
* Cleaned up code in general

Version 1.5.2
* Fixed a rare issue which could cause a nil object exception
* The window title will now change to a more suiting "Windows Vista Loader v1.5.2 - By Daz" when run on Windows Vista

Version 1.5.1
* Updated GRLDR v0.4.4 to beta version 4 (Thanks to zsmin)

Version 1.5
* Fix to prevent hangs at boot when each OS needs it's own active partition exclusive while other primaries are set to hidden. Every other loader has this bug! (Thanks to endeavor for working with me to fix this issue)
* Can now activate both Windows 7 and Windows Vista, just run the loader on either OS
* Optional new beta GRLDR v0.4.4 can be used on Mac or Windows (New GRLDR created by zsmin, boots Windows 7 on a Mac much faster)
* Updates to GRLDR v0.4.4 to become dynamic and allow slic change
* Fixed UI font sizes for users who have changed their system font

Version 1.4
* Added x64 support
* Drive letter assignment is now automatic
* Changed how the key input is handled
* Made UI a little more user friendly

Version 1.3
* Added brand support to the loader creator
* Added certificate and serial install only for bios modded users
* Added new Ultimate and Professional keys
* The loader now automatically displays keys only for your installed version of Windows 7

Version 1.2
* UAC settings modified in manifest
* Added future support for Windows 7 Professional

Version 1.1
* Silent certificate and key installs
* Fixed file overwriting issue
* Lists some BIOS information



##########################################################################
#   8   -   Arguments
##########################################################################
/silent
 Turns on silent mode

/restart
 Restart the OS after install (used with /silent)

/norestart
 Prevents system restart after successful installation

/preactivate
 This just helps the loader decide on it's environment

/bios
 Force the application to install just the certificate and serial

/loader
 Force the application to install the loader

/relocate
 This tries to prevent the loader from relocating the RSDP to EBDA

/disable4
 This will prevent the loader from using type 4 memory

/disable3
 This will prevent the loader from using type 3 memory

/legacy
 This will install the loader using the legacy mode

/ignore
 The loader will ignore the systems existing SLIC

/swap
 Install the loader without changing your systems boot code

/k=XXXXX-XXXXX-XXXXX-XXXXX-XXXXX
 Set the Windows 7/2008/Vista key

/c=
 Set the certificate (use the name of a certificate from the certificates folder or from the SLIC list)

/s=
 Set the SLIC (Acer, Advent, Alienware, AOC, Aquarius, Asus, AT Computers, BEKO, BenQ, BGH e-Nova, ByteSpeed, Casper, CCE, Chuangzhicheng, CompUX, Crea, Dealin, Dell, Digimer, Equus, Excimer, EXO, Exper, EXTRA Computer GmbH, Founder, FSC, Fujitsu, Genuine, Gigabyte, Haier, Hannspree, Hasee, HCL, Higrade, HP, Hyrican, Ideal, Impression Computers, INSYS, Itautec, Jetway, Jooyon, Kouziro, Kraftway, KSystems, Lanix, Lenovo, LG, MA Technology, Medion, Megaware, Midern, MiTAC, MSI, Mustek, NEC, Nokia, Olidata, ONKYO, Panasonic, Paradigit, Paragon, Philco, Positivo, PowerSpec, Prolink, Qbex, Quanmax, RM Education, Samsung, Seneca, Shuttle, Sony, Stone, Synnex, Systemax, Tangent, Tarox, Tongfang, Toshiba, Trigem, Twinhead, Velocity, Vestel, Viewsonic, Viliv, Western Digital, Wortmann, Xplore, Zoostorm)

======
* If you don't set the certificate it will default to your BIOS's model
* If you don't set the SLIC it will default to your BIOS's model
* If you don't set the key it will default to your BIOS's model and the correct one for the OS (Ultimate, Professional, Starter or Home Premium)
* You can use these arguments via SetupComplete.cmd to pre-activate Windows 7/Vista/Server 2008
======

Example:
"D:\Windows Loader.exe" /silent /restart /k=342DG-6YJR8-X92GV-V7DCV-P4K27 /c=Acer /s=Acer


SetupComplete.cmd Example:

@ECHO OFF
%~dp0"Windows Loader.exe" /silent /preactivate
cd %~dp0
attrib -R -A -S -H *.*
SHUTDOWN /R /T 5
RMDIR /S /Q "%WINDIR%\Setup\Scripts"
exit



##########################################################################
#   9   -   Extra
##########################################################################
If a certificate or SLIC is released and I have not put out a new version of my application simply create two folders, one called "Certificates" and another called "SLICs".

In each folder put the files you want to add support for, just be sure you label the files like this:

*Certificates folder*
Acer.XRM-MS
Advent.XRM-MS
Alienware.XRM-MS
Asus.XRM-MS


*SLICs folder*
Acer.BIN
Advent.BIN
Alienware.BIN
Asus.BIN


When using external files all preset internals will be ignored. This is a cleaner approach for users who want to build their own list without my presets getting in the way.



Special thanks:
BobSheep, zsmin & Woota!?

Thanks:
Everyone who supports this project, you're all the reason I'm still working on it.
