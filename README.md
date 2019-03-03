# HackRFOne-Stuff
This repository contains different projects using the HackRF One software defined radio platform.

## Setup a development environment
In the following, I describe how to setup a bootable USB stick with a persistent Ubuntu 18.04 and basic tools like GNU Radio and HackRF one Tools under Windows 10. I assume that you have downloaded the Ubuntu 18.04 iso file to `/c/path/to/ubuntu-18.04.1-desktop-amd64.iso` and that you have Virtual Box installed.
Now execute the following steps:
1)  Start Virtual Box and create a new virtual machine of type *Linux* and version *Ubuntu (64-bit)*. The name you give it doesn't matter, because we will delete it after we created the bootable usb stick. When the dialog asks you what kind of hard disk it should create, choose *"Do not add a virtual hard disk"*. It will show a warning, but you can ignore it.
2)  Start the just created new virtual machine. When it prompts you to select start-up disk, choose the *ubuntu-18.04.1-desktop-amd64.iso* and click start. After the virtual machine has booted to the ubuntu welcome screen, connect a usb stick with at least 32 GB to your pc. At the bottom of the window of your virtual machine, search for a usb stick symbol and click it. Choose the usb stick you just connected to your pc. Then click the *Install Ubuntu* button and install Ubuntu on that usb stick.
3)  After you have completed the installation, close the virtual machine, delete it. Reboot your pc and go into its bios. Choose the usb stick as boot device. Now Ubuntu 18.04 should start from your usb stick. If you have a Dell XPS 15 Laptop like me, Ubuntu 18.04 will hang up while booting because a NVidia driver is missing. If that is the case, press the *"e"* key while you are in the GRUB bootloader. Add `nouveau.modeset=0` to the line that starts with `linux`. Press *ctrl+x* to start Ubuntu. After Ubuntu has started completely, open a terminal and update the NVIDIA driver with `sudo apt-get install nvidia-driver-390`. Now Ubuntu shouldn't have problems with the graphics driver anymore and you can reboot normally.
4)  Now we install HackRF One Tools using `sudo apt-get install hackrf`. We can test if everything went well by plugging in the HackRF One and executing `hackrf_info`.
4) Afterwards we install GNU Radio using `sudo apt-get install gnuradio` or using pybombs as described [here](https://github.com/gnuradio/pybombs) or [here](http://sodera.de/pybombs-erleichtert-das-leben/) and GrOsmoSDR using `sudo apt-get install gr-osmosdr`. Now GNU Radio Companion can be started by executing `gnuradio-companion`.