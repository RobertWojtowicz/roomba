# RPiRoomba

## 1. Introduction
This project is based on the following projects:
- https://github.com/pomeroyb/Create2Control
- https://github.com/silvanmelchior/RPi_Cam_Web_Interface

## 2. How does this work?
## 3. Build hardware

## 4. Preparing Linux system
- download Raspberry Pi OS (32-bit) Lite system image: https://downloads.raspberrypi.org/raspios_lite_armhf_latest;
- upload system to the microSD card, e.g. using Win32 Disk Imager, all you need is a 4 GB microSD card with UHS-1 speed class;
- to enable ssh create blank text file called “ssh” wtihout txt extension on the boot partition;
- to enable WiFi connection create text file "wpa_supplicant.conf" on the boot partition based on an example from this repository;
- on the boot partition replace or edit config.txt file based on an example from this repository;
- to disable HDMI (to reduce the power consumption) you must replace or edit rc.local file based on an example from this repository.

## 5. Installing RPi-CAM-Web-Interface
To install RPi-CAM-Web-Interface, run the following commands:
- sudo apt-get install git;
- git clone https://github.com/silvanmelchior/RPi_Cam_Web_Interface.git;
- cd RPi_Cam_Web_Interface;
- ./install.sh;
- in the configuration menu, clear the "xCam subfolder" option, add the user in "xUser:" admin and the password "xPassword:" and select OK;
- when the installation is complete you can delete folder, rm -rf RPi_Cam_Web_Interface;

## 6. Configuring scripts
