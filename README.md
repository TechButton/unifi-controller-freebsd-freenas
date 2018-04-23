unifi-controller-freebsd-freenas
=============

A shell script package that provides the UniFi Controller software.

Purpose
-------

The objective of this project is to develop and maintain a package that provides [Ubiquiti's](http://www.ubnt.com/) UniFi Controller software for the FreeBSD-based jail. 5.8.X Version branch - Not for Production

Status
------

The project now provides two working scripts: an rc script to start and stop the UniFi controller, and an installation script to automatically download and install everything, including the rc script.

Upgrade
-------
Working on the upgrade process - Upgrade to current is working to current unstable 5.8.14 Version - Not for Production

Milestones
----------

Installs snappy java after Unifi Controller is installed to comply with new controller software.



Challenges
----------


Licensing
---------

This project itself is licensed according to the two-clause BSD license.

The UniFi Controller software is licensed as-is with no warranty, according to the README included with the software.

[Ubiquiti has indicated via email](https://github.com/gozoinks/unifi-pfsense/wiki/Tacit-Approval) that acceptance of the EULA on the web site is not required before downloading the software.

Installation
------------

To install the controller software and the rc script:

1. Log in to the jail command line shell as root.
2. Run this one-line command, which downloads the install script from Github and executes it with sh or copy install_unifi.sh file to new file and sh ./filename.sh and your controller will be running when complete.

  ```
    fetch -o install-unifi.sh https://raw.githubusercontent.com/jmkizer/unifi-controller-freebsd-freenas/5.8.X/install-unifi/install-unifi.sh
  ```
Or

  ```
Login with SSH to your FreeNAS (or alternatively go to shell in WebGUI)
type: 'jls' (without ' ' ) and take the note of the # of jail of your Unifi installation
type: jexec # csh' (where # is the number of the jail noted in last step)
type: fetch -o install-unifi.sh https://raw.githubusercontent.com/jmkizer/unifi-controller-freebsd-freenas/5.8.X/install-unifi/install-unifi.sh
type: chmod 755 install-unifi.sh
type: ./install-unifi.sh
  ```


The install script will install dependencies, download the UniFi controller software, make some adjustments, and start the UniFi controller.

Starting and Stopping
---------------------

To start and stop the controller, use the `service` command from the command line.

- To start the controller:

  ```
    service unifi.sh start
  ```
  The UniFi controller takes a few minutes to start. The 'start' command exits immediately while the startup continues in the background.

- To stop the controller:

  ```
    service unifi.sh stop
  ```
  The the stop command takes a while to execute, and then the shutdown continues for several minutes in the background. The rc script will wait until the command received and the shutdown is finished. The idea is to hold up system shutdown until the UniFi controller has a chance to exit cleanly.
  

References
----------
Version 5.8.10 fixes
https://community.ubnt.com/t5/UniFi-Beta-Blog/UniFi-5-8-10-Testing-has-been-released/ba-p/2299020

Thanks to thecodemonk for your hard work, modified from https://github.com/thecodemonk/unifi-pfsense and https://github.com/TechButton/unifi-controller-freebsd-freenas

These sources of information immediately come to mind:

- [UniFi product information page](http://www.ubnt.com/unifi#UnifiSoftware)
- [UniFI download and documentation](http://www.ubnt.com/download#UniFi:AP)
- [UniFi updates blog](http://community.ubnt.com/t5/UniFi-Updates-Blog/bg-p/Blog_UniFi)
- [Unifi Stable build page] (https://community.ubnt.com/t5/UniFi/ct-p/UniFi)
