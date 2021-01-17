![retropie_logo](https://cloud.githubusercontent.com/assets/10035308/21968193/e1670f2a-db46-11e6-8ff7-eb6d7188c9e7.png)

|Version|4.7|
|:---:|:---:|

1. [Hardware](#hardware)
2. [Installation](#installation)
3. [Controller Configuration](#configure-controllers)
4. [EmulationStation](#emulationstation)
5. [Configure Wifi](#wifi)
6. [Installing Additional Emulators](#installing-additional-emulators)
7. [Transferring Roms](#transferring-roms)
8. [Configure Audio (if needed)](#audio)

Congratulations! You have discovered the wonderful world of RetroPie- your entire childhood is within reach! RetroPie is a combination of multiple projects including RetroArch(http://www.libretro.com), EmulationStation[**(link)**](http://www.emulationstation.org), and many others. 

This page is for people just getting started on RetroPie. The easiest way to install RetroPie is the SD image which is a ready to go system built upon top of the Raspberry Pi OS - this is the method described in the following guide. Alternatively, advanced users can install RetroPie manually [**HERE**](Manual-Installation). 

This guide will give you the very basics to get you up and running from a blank SD card to first boot into EmulationStation.

If you hate reading then see this video. Otherwise read on! 

<a href="https://www.youtube.com/watch?v=E1sbnPZ_A8w
" target="_blank"><img src="https://img.youtube.com/vi/E1sbnPZ_A8w/maxresdefault.jpg" 
alt="RetroPie First Installation Video" width="1280" height="400" border="10" /></a>

## [Hardware](https://retropie.org.uk/about/building/)

 * Raspberry Pi (A, A+, B, B+, 2, Zero, 3, 4) - for best performance use a **Raspberry Pi 4**
 * Raspberry Pi Case (optional but recommended)
 * MicroSD Card (see compatible SD card list [**here**](http://elinux.org/RPi_SD_cards))
 * MicroSD Card Reader (optional - for installing RetroPie if your computer doesn't have a SD card slot)
 * HDMI cable or 4 Pole RCA to 3.5mm Cable (HDMI works best)
 * Television or Computer Monitor- really any screen with HDMI or RCA ports
 * Wifi Dongle or Ethernet Cable (Wifi is built-in for the Pi 3/4 model - see wifi dongle compatible list [**here**](http://elinux.org/RPi_USB_Wi-Fi_Adapters))
 * 5V 2A Micro USB Power Supply (2.5A for Pi 3) / 5.1V 3A USB-C for Pi 4
 * USB Keyboard and Mouse (to get things set up or you can use SSH[**(link)**](SSH))
 * USB Game Controller of your choice (or you can get the Control Block[**(link)**](http://blog.petrockblock.com/2014/12/29/controlblock-power-switch-and-io-for-the-raspberry-pi/) to use original SNES controllers)

The simplest way to get most of these components is through a kit such as the Canakit[**(link)**](https://www.amazon.com/gp/product/B01C6Q2GSY/). 

## Installation

### Download
There are currently 3 versions of RetroPie. There is one version for Raspberry Pi 0/1 (Model A, A+, B, B+), a version for Raspberry Pi 2/3 and a version for Raspberry Pi 4. 

Download the SD image for your version of Raspberry Pi from the following page:

**[https://retropie.org.uk/download/](https://retropie.org.uk/download/)**

If you are unsure which version of Raspberry Pi you have, you can count the raspberries on boot:

|Raspberry Pi 0/1 | Raspberry Pi 2/3/4|
| :---: | :---: |
|![rpi1](https://cloud.githubusercontent.com/assets/10035308/21957849/f64fe008-da54-11e6-9a1c-09cb9e87c8f5.png) | ![rpi2](https://cloud.githubusercontent.com/assets/10035308/21957850/f66f2120-da54-11e6-876b-6d7f276c31e3.png)|

If you get the error `Illegal Instruction` when it boots or if it just boots into the terminal, you picked the wrong SD image or the image was corrupted on download or extraction.

### Extract

Once you have downloaded your SD card image you need to extract it using a program such as 7-zip[**(link)**](http://www.7-zip.org/). You will extract the downloaded **.gz** file and the extracted file will be a **.img** file.

To extract from the command line, you can type the following into a Terminal window, placing X with version you downloaded:

`gunzip retropie-4.X.X-rpi2_rpi3.img.gz`

### Install

To install the RetroPie SD image on your MicroSD card. (You may need a MicroSD card reader to plug it into your computer) 

1. For Windows you can use [**Etcher**](https://etcher.io/), [**Win32DiskImager**](http://sourceforge.net/projects/win32diskimager/) or [**Raspberry Pi Imager**](https://www.raspberrypi.org/downloads/)
2. For macOS you can use [**Etcher**](https://etcher.io/), [**Apple Pi Baker**](https://www.tweaking4all.com/hardware/raspberry-pi/applepi-baker-v2/) or [**Raspberry Pi Imager**](https://www.raspberrypi.org/downloads/)
3. For Linux you can use the `dd` command, [**Etcher**](https://etcher.io/) or [**Raspberry Pi Imager**](https://www.raspberrypi.org/downloads/).

See the official Raspberry Pi "WRITING AN IMAGE TO THE SD CARD" [**instructions**](https://www.raspberrypi.org/documentation/installation/installing-images/).

**Note** RetroPie is built on top of Raspberry Pi OS Buster (a Linux based OS for the Raspberry Pi) and as such the partition on the SD card is EXT4 (a linux filesystem). This partition is is not visible on Windows systems, so the card will show up as a smaller size than usual and you won't be able to see everything on the card, but it is all there. You will be able to access the filesystem over the network as described in the transferring roms section below.

If you're updating from a previous version of RetroPie see [**HERE**](Updating-RetroPie).

## Configure Controllers

On first boot your filesystem will be expanded automatically, you will then be welcomed with the following screen- this menu will configure your controls for both EmulationStation and RetroArch Emulators:

![welcomescreen](https://cloud.githubusercontent.com/assets/10035308/9140482/cf42f25c-3cee-11e5-8f91-c1fc1c57175c.png)

Hold down any button on your keyboard or gamepad and the name will appear at the bottom and then open up into a configuration menu:

![welcomescreengamepadname](https://cloud.githubusercontent.com/assets/10035308/9140505/f5c19e38-3cee-11e5-965e-0e4e85ddaf56.png)

Follow the onscreen instructions to configure your gamepad- if you run out of buttons just hold down a button to skip each unused button. **When you get to OK press the button you have configured as "A"**.

![welcomescreengamepadconfigure](https://cloud.githubusercontent.com/assets/10035308/9140518/0263b9c8-3cef-11e5-922f-42f790f3be91.png)

If you wish to configure more than one controller, you can do so from the start menu of EmulationStation. For more details on manual controller configurations see this page [Here](RetroArch-Configuration).

See the following diagrams for reference:

| SNES Controller | 
|:---:|
|![snes_controller](https://cloud.githubusercontent.com/assets/10035308/22185414/f129dc28-e099-11e6-8524-93facf275eda.png)|

| XBox 360 Controller |
|:---:|
|![xbox360_controller](https://cloud.githubusercontent.com/assets/10035308/22185415/f12ff342-e099-11e6-8adb-d18e9c638e94.png)|

| PS3 Controller |
|:---:|
|![ps3_controller](https://cloud.githubusercontent.com/assets/10035308/22185413/f10f27de-e099-11e6-97a4-ecbbc82c9e46.png)|

### Hotkey

The Hotkey button enables you to press it in combination with another button to access functions such as saving, loading, and exiting in emulators. It is suggested to use the **Select** button as the hotkey. The following chart shows the default hotkey combinations. For example, if you chose Select as your Hotkey, that means you hold down Select while pressing the other button to execute the command. 

**Note** Hotkey combinations are specific to the retroarch/libretro based emulators.

|Hotkey Combination | Action|
| :---: | :---: |
| Hotkey+Start | Exit |
| Hotkey+Right Shoulder | Save |
| Hotkey+Left Shoulder | Load |
| Hotkey+Right | Input State Slot Increase |
| Hotkey+Left | Input State Slot Decrease |
| Hotkey+X | RGUI Menu |
| Hotkey+B | Reset |

For more information, see [**Hotkeys**](RetroArch-Configuration#hotkeys)

## EmulationStation

| **Where are the systems?**|
| :---: | 
**When you first see EmulationStation you may wonder why you don't see systems like the SNES or Game Boy- worry not- they are installed on the system, roms just need to be added to their respective rom folders before they will become visible. Transferring roms are described in the following steps.**|
|![firstboot](https://cloud.githubusercontent.com/assets/10035308/16217874/c6bbdb3a-3734-11e6-998f-8cc714a320ce.png)|

## Wifi

If you wish to use wifi to transfer roms over the network rather than a USB stick or Ethernet cable you'll need to setup your wifi- which can also be done from the RetroPie menu in EmulationStation:

| Connect to Wifi Network: |
|:---:|
|![wifi1](https://cloud.githubusercontent.com/assets/10035308/16217941/92b08b8c-3735-11e6-8f20-5d1550af0882.png)|

| Choose your SSID from a list: |
|:---:|
|![wifi2](https://cloud.githubusercontent.com/assets/10035308/16217942/92c5a8a0-3735-11e6-86ed-721c1bb81990.png)|

| Type your Wifi Password (may take a moment to connect) |
|:---:|
|![wifi3](https://cloud.githubusercontent.com/assets/10035308/16217943/92c64c24-3735-11e6-8f62-893f111c5bd2.png)|

|Once configured you will see your IP address|
|:---:|
|![wifi4](https://cloud.githubusercontent.com/assets/10035308/16217944/92cb07fa-3735-11e6-9239-66fba394c669.png)|

For more WiFi configuration options see this [**page**](Wifi)

## Installing additional Emulators
On RetroPie 4.0+, not everything is installed by default. The pre-made images contain the best working emulators for each system supported by the hardware. This should cover everything most users would be doing. Ports like quake and doom and some other emulators like ScummVM can be installed later.

Software can be installed from the RetroPie-Setup script - which is accessible from the RetroPie menu on EmulationStation. Once there you can navigate to "Manage Packages" where you will see various sections. In each section are lists of packages that can be installed (and it will show what is currently installed). Stable additional packages are under the "Optional" section, with more unstable packages listed under experimental. The packages are ordered first by type (emulators / libretro cores / ports), then alphabetically. By selecting a package you can choose to install it, or remove it. Some packages also have additional configurations.

## Transferring Roms

Due to the nature/complexity of Copyright/Intellectual Property Rights Law, which differs significantly from Country to Country, ROMs cannot be provided with RetroPie and must be provided by the user. You should only have ROMs of games that you own. 

There are three main methods of transferring roms: 

### USB
 * (ensure that your USB is formatted to FAT32 or NTFS)
 * first create a folder called `retropie` on your USB stick
 * plug it into the pi and wait for it to finish blinking
 * pull the USB out and plug it into a computer
 * add the roms to their respective folders (in the `retropie/roms` folder)
 * plug it back into the Raspberry Pi
 * wait for it to finish blinking
 * refresh EmulationStation by choosing RESTART EMULATIONSTATION from the start menu

See this video for reference:

<a href="https://www.youtube.com/watch?v=OYMoxvbkYD4
" target="_blank"><img src="https://img.youtube.com/vi/OYMoxvbkYD4/hqdefault.jpg" 
alt="Transferring ROMs using an USB drive" width="640" height="400" border="10" /></a>

### SFTP

**NOTE** you need to enable SSH[**(link)**](SSH) in order for SFTP to work.

* Wired (needs ethernet cable)
* Wireless (needs wifi dongle)
There are many SFTP programs out there, for windows many people use WinSCP[**(link)**](https://winscp.net/eng/download.php) for mac you can use something like Cyberduck[**(link)**](https://cyberduck.io/?l=en)

![winscp](https://cloud.githubusercontent.com/assets/10035308/12865832/7d9afb68-cc75-11e5-81b2-4529991e1821.png)

Default username: **pi** 

Default Password: **raspberry**

You can also log in as root if you wish to change more files than just the roms, but you first need to enable the root password which is explained [**here**](FAQ#why-cant-i-ssh-as-root-anymore)

### Samba-Shares

- if on Windows type `\\retropie` into the computer folder. You can also replace `retropie` with your Raspberry Pi's IP address

![samba](https://cloud.githubusercontent.com/assets/10035308/12865893/d2eab264-cc77-11e5-9ec6-003e13322a5a.png)

- if on MAC OS X open Finder, select "Go" menu and "Connect to Server...". Type `smb://retropie` or `smb://retropie.local` and hit "Connect". Then choose Guest and hit "Connect" again.

## AUDIO

In general RetroPie audio will work out of the box without any tweaking, but if you have audio issues you should follow the instructions on the [**Sound Issues Page**](Sound-Issues) to fix them. You will most likely need to visit the [**Sound Issues Page**](Sound-Issues) if you are using a USB Audio device, or if you are using an aftermarket RPi HAT add-on audio device (such as a Justboom sound card).

## PLAY!

After you've added your roms you need to restart EmulationStation in order for them to show up. You can restart EmulationStation from the start menu, or by rebooting your pi with `sudo reboot`. 

See the rest of the [**docs**](https://retropie.org.uk/docs/) for more detailed information on individual emulators, advanced settings etc. If you still can't figure it out, the RetroPie community is very helpful on the [**forum**](https://retropie.org.uk/forum/). 

**The RetroPie Project is primarily maintained by a few developers who develop the project in their free time. If you have found the RetroPie project useful please consider donating to the project [here](https://retropie.org.uk/donate/). As you become more familiar with RetroPie, pay it forward by helping others on the forum. The RetroPie Project is what it is today because of the many contributions of the community.**

THANK YOU!
