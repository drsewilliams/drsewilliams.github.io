---
layout: default
title: System Set Up
parent: Processing
nav_order: 1
parent: Modelling
---

# Set up a new Ubuntu/Carp system
{: .no_toc }

### Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Background
System set up using an HP ...

## Initial system configuration
```bash
sudo apt update
sudo apt upgrade
sudo apt install openssh-server
sudo systemctl status ssh
sudo ufw allow ssh
sudo apt-get install build-essential git cmake
```

## Carp installation
```bash
sudo mkdir /usr/local/bin/CME/1.1
```
Download carp package from [https://carp.medunigraz.at/carpentry/cme.linux.tar.gz](https://carp.medunigraz.at/carpentry/cme.linux.tar.gz)

```bash
cd Downloads/cme-1.1-linux/
sudo ./install_linux.sh
```
When prompted, choose ```/usr/local/CME/1.1``` as the installation location

### Add carp executables to the path
```bash
vi ~/.profile
or
vi ~/.bashrc
```
At the bottom of the file, add the following text.
```bash
# load carp paths
source /usr/local/CME/1.1/config.sh
```

## Meshalyzer installation (manual)
Meshalyzer installation did not work for me via the install script so I followed the manual instructions instead.
```bash
apt-get update && apt-get install -y --no-install-recommends ca-certificates fluid freeglut3-dev g++ git libfltk1.3-dev libglew-dev libglu1-mesa-dev libpng-dev make
git clone https://git.opencarp.org/openCARP/meshalyzer.git
cd meshalyzer/
make
```

Launch meshalyzer with
```bash
./meshalyzer
```

move the meshalyzer directory to /usr/local/meshalyzer
```bash
mv meshalyzer/ /usr/local/meshalyzer
```

create a symbolic link so that meshalyzer is on the path
```bash
ln -s /usr/local/meshalyzer/meshalyzer /usr/local/bin/meshalyzer
```

create a symbolic link so that carputils can access meshalyzer
```bash
sudo ln -s /usr/local/meshalyzer/meshalyzer /usr/local/CME/1.1/bin/meshalyzer
```
## move the tutoirials to the home directory
```bash
sudo mv /usr/local/CME/1.1/tutorials /home/stw11/
sudo chown -R stw11:stw11 ./tutorials/
```

## bind python to python3
```bash
sudo ln -s /usr/bin/python3 /usr/bin/python
```

## Finishing up
Test that all programs run:
```bash
bench
carpentry
meshtool
meshalyzer
```

## Instal cgal
```bash
sudo apt-get install libcgal-dev
```

## Troubleshooting
may need to provide access to the bench license file
```bash
sudo chmod 777 /usr/local/CME/1.1/license.bin
```
