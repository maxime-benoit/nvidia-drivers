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
