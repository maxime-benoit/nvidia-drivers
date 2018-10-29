# Nvidia Quadro K620 Deep Learning Drivers Configuration with Ubuntu 18.04
Deep Learning Configuration for Nvidia Quadro K620 with Ubuntu 18.04 From Scratch

### 1. Install Ubuntu

### 2. Configure Proxy

If you are using a proxy, you should configure apt as shown :

    $ sudo touch /etc/apt/apt.conf.d/proxy.conf
    $ sudo vi /etc/apt/apt.conf.d/proxy.conf

Add the following lines to the proxy.conf file :

    Acquire::http::Proxy "http://user:password@proxy.server:port/";
    Acquire::https::Proxy "http://user:password@proxy.server:port/";
    
(and add to bashrc)

### 3. Install Ubutnu Essentials

    $ sudo apt update
    $ sudo apt install build-essential

### 4. Blacklist Nouveau Kernel

    $ sudo vi /etc/modprobe.d/blacklist-nouveau.conf

Add the following lines :
    
    blacklist nouveau
    options nouveau modeset=0
    
Regenerate Kernel

    $ sudo update-initramfs -u
    
And reboot 
    $ sudo reboot

### 5. Check ubuntu-driver

In order to check available drivers you can type 

    $ sudo ubuntu-drivers devices

    == /sys/devices/pci0000:00/0000:00:02.0/0000:02:00.0 ==
    modalias : pci:v000010DEd000013BBsv0000103Csd00001098bc03sc00i00
    vendor   : NVIDIA Corporation
    model    : GM107GL [Quadro K620]
    driver   : nvidia-driver-390 - distro non-free recommended
    driver   : nvidia-340 - distro non-free
    driver   : xserver-xorg-video-nouveau - distro free builtin

nvidia-driver-390 is recommended, you can install it with 

    $ sudo ubuntu-drivers devices


Sources : 
https://forum.ubuntu-fr.org/viewtopic.php?id=2030740
https://linuxconfig.org/how-to-install-the-nvidia-drivers-on-ubuntu-18-04-bionic-beaver-linux
https://linuxconfig.org/how-to-disable-nouveau-nvidia-driver-on-ubuntu-18-04-bionic-beaver-linux
https://askubuntu.com/questions/841876/how-to-disable-nouveau-kernel-driver
