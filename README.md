# RPiRoomba

## 1. Introduction
This project is based on the following projects:
- https://github.com/pomeroyb/Create2Control
- https://github.com/silvanmelchior/RPi_Cam_Web_Interface

## 2. How does this work?


## 3. Build hardware
- create your own PCB according to the project files: roomba_led_pcb_v1.sch, roomba_led_pcb_v1.brd, roomba_main_pcb_v1.sh, roomba_main_pcb_v1.brd from this repository (files location: rpiroomba/pcb/), example of finished PCBs below:
![alt text](https://github.com/RobertWojtowicz/rpiroomba/blob/master/pic/01_main_PCB.jpg)
![alt text](https://github.com/RobertWojtowicz/rpiroomba/blob/master/pic/02_LED_PCB.jpg)
- prepare the aluminium housing - heat sink for CPU Raspberry Pi and high power LED chip, similar to the picture (dimensions approx: 36 mm x 65 mm):
- add a thermal pad under the high power LED chip and the CPU Raspberry Pi to dissipate the heat to the aluminium case;
![alt text](https://github.com/RobertWojtowicz/rpiroomba/blob/master/pic/04_wiring_RPI_CAM.jpg)
- the hinges come from the elements of the electric cube;
- metric screws with a diameter of 2 mm were used to connect the parts;
- reduce the current on the LED driver from 700 mA to 230 mA (too high power causes unreadable view);
- isolate the Raspberry Pi and camera pins from accidental short circuits, as shown in the following picture:
![alt text](https://github.com/RobertWojtowicz/rpiroomba/blob/master/pic/03_RPI_PCB_isolation.jpg)

The following parts are required:
- Modules: 1x DC/DC step-down MP1584EN, 1x Raspberry Pi Zero W V1.1, 1x Raspberry Pi NoIR Camera V2, 1x LED driver PT4115:
![alt text](http://www.dareltek.pl/pliki/P4115adj2b.jpg)
- 1x Camera adaptor (cable) from official case Raspberry Pi Zero;
- 1x Micro servo TowerPro MG90S;
- 1x SMD 1206 high power LED chip, 3W IR 850 Nm;
- 1x SMD 1206 resettable polymeric fuse 500 mA;
- 1x SMD 1206 resistors: 15 Ohm, 120 Ohm, 390 Ohm, 1 kOhm;
- 3x SMD 1206 zener diode 3.3 V;
- 1x 40 pin, 2.54 mm, single in line, 20 mm long, header male;
- 1x 40 pin, 2.54 mm, single in line, right angle, header male.

## 4. Preparing Linux system (tested on current kernel 5.4.83+ )
- download Raspberry Pi OS (32-bit) Lite system image: https://downloads.raspberrypi.org/raspios_lite_armhf_latest;
- upload system to the microSD card, e.g. using Win32 Disk Imager, all you need is a 4 GB microSD card with UHS-1 speed class;
- to enable ssh create blank text file called “ssh” wtihout txt extension on the boot partition;
- to enable WiFi connection create text file "wpa_supplicant.conf" on the boot partition based on an example from this repository (file location: rpiroomba/rpi/boot/);
- on the boot partition replace or edit "config.txt" file based on an example from this repository (file location: /rpi/boot/;
- to disable HDMI (to reduce the power consumption) you must replace or edit "rc.local" file based on an example from this repository (file location: rpiroomba/rpi/etc/);
- install modules: sudo apt-get install python-pip, sudo pip install pyserial.

## 5. Installing RPi-CAM-Web-Interface (tested on current version 6.6.13)
To install RPi-CAM-Web-Interface, run the following commands:
- sudo apt-get install git;
- git clone https://github.com/silvanmelchior/RPi_Cam_Web_Interface.git;
- cd RPi_Cam_Web_Interface;
- ./install.sh;
- in the configuration menu, clear the "xCam subfolder" option, add the user in "xUser:" admin and the password "xPassword:" and select OK;
- when the installation is complete you can delete folder, rm -rf RPi_Cam_Web_Interface.
- change the parameters in the browser under Camera Settings to: Load Preset: HD-ready 720p, Rotation: Rotate_270, Preview quality: Quality: 10, Width 1280, Divider: 1, for example picture of RPI Cam interface:
![alt text](https://github.com/RobertWojtowicz/rpiroomba/blob/master/pic/08_roomba_RPI_Cam.png)

## 6. Configuring scripts
Create a roomba folder in /var/www directory and then copy the files, e.g. using WinSCP:
- command.php;
- config.json;
- create2api.py;
- jquery-3.5.1.min.js;
- roomba.py;
- submit.js;
- in /var/www directory, you should replace index.html from this repository;
- grant permissions for user-data: sudo usermod -a -G gpio www-data, sudo usermod -a -G dialout www-data.

