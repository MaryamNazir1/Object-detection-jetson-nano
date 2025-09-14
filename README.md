# Object-detection-jetson-nano

This repository contains all the processes, commands, and setup instructions required to boot and run object detection models on the **NVIDIA Jetson Nano**.

---

## Table of Contents

1. [Introduction](#introduction)
2. [Hardware Requirements](#hardware-requirements)
3. [Booting the Jetson Nano](#booting-the-jetson-nano)
4. [Initial Setup](#initial-setup)
5. [WiFi Setup](#wifi-setup)
6. [Remote Access (Headless Setup)](#-remote-access-headless-setup)
7. [Install Dependencies](#install-dependencies)
8. [Run Object Detection](#run-object-detection)

---

## 1. Introduction

The **Jetson Nano** is a small, powerful computer for AI at the edge. This repo serves as a **step-by-step lab notebook** to:

- Boot Jetson Nano for the first time.
- Set up environment for object detection.
- Run YOLO/other detection models on the Nano.

---

## 2. Hardware Requirements

- NVIDIA Jetson Nano Developer Kit
- microSD Card (32GB UHS-1 recommended)
- USB Keyboard & Mouse
- HDMI Display Monitor
- 5V 4A Power Supply (Barrel Jack recommended)
- USB WiFi dongle or Ethernet connection

---

## 3. Booting the Jetson Nano

Follow the official NVIDIA guide: [Getting Started with Jetson Nano](https://developer.nvidia.com/embedded/learn/get-started-jetson-nano-devkit#intro).

### Steps:

1. **Download Jetson Nano Developer Kit SD Card Image**

   - Get the latest image from NVIDIA:  
      [Jetson Nano SD Card Image](https://developer.nvidia.com/embedded/downloads)

2. **Flash the microSD Card**

   - Use [balenaEtcher](https://www.balena.io/etcher/) or similar to flash the image to your SD card.

3. **Insert and Boot**

   - Insert the flashed microSD card into the Jetson Nano.
   - Connect keyboard, mouse, HDMI display, and power supply.
   - Power on the device.

4. **Initial Configuration**
   - Follow the on-screen prompts to configure:
     - Language & keyboard layout
     - Username & password
     - WiFi/Ethernet connection

Once complete, your Jetson Nano will be ready to install software and run detection.

---

## 4. Initial Setup

Update and upgrade system packages:

```bash
sudo apt-get update
sudo apt-get upgrade
```

---

## 5. WiFi Setup

If you are using a **USB WiFi dongle**, follow this detailed guide:  
 [Adding WiFi to the NVIDIA Jetson Nano (SparkFun Tutorial)](https://learn.sparkfun.com/tutorials/adding-wifi-to-the-nvidia-jetson/all)

This covers:

- Checking supported WiFi adapters
- Installing necessary drivers
- Connecting to a wireless network
  save the 'wlan0' and 'eth0' ip address for next steps (Setup Headless Mode).

---

## 7. Remote Access (Headless Setup)

You don’t always need a monitor, keyboard, and mouse connected to your Jetson Nano.  
Instead, you can connect remotely and headlessly from another computer.

There are two popular methods: **XRDP** and **VNC**.

## Method 1: XRDP (Remote Desktop Protocol)

On the Jetson Nano terminal, run:

```bash
sudo apt update
sudo apt install xrdp
sudo systemctl enable xrdp
sudo reboot
```

### After Reboot

1. On your **Windows PC**, open **Remote Desktop Connection**.
2. Enter the **IP address or Hostname** of your Jetson Nano.
3. Enter your Jetson Nano login credentials.  
   You now have remote access to your Nano’s desktop.  
   Reference: [XRDP Setup Guide](https://learn.microsoft.com/en-us/windows-server/remote/remote-desktop-services/clients/remote-desktop-clients)

## Method 2: VNC (Virtual Network Computing)

1. Follow this guide to install VNC on Jetson Nano:  
   [VNC Setup Guide](https://developer.nvidia.com/embedded/learn/tutorials/vnc-setup)

2. Once installed, download **VNC Viewer** on your Windows PC:  
   [VNC Viewer Download](https://www.realvnc.com/en/connect/download/viewer/)

3. Enter the **IP address** of your Jetson Nano in **VNC Viewer**.
4. Enter your Jetson Nano login credentials.  
   Your Jetson Nano desktop will appear on your Windows machine.

---

## 8. Environment & OpenCV Setup on Jetson Nano

### I. Setup Python & Virtual Environment

First, install `pip`, create a virtual environment, and verify OpenCV:

```bash
sudo apt-get install python3-pip
pip3 install virtualenv
```

then you can fellow the command to install python 3.8 [python38_install.md](python38_install.md)

otherwise this:

```bash
python3 -m virtualenv -p python3 env --system-site-packages
source env/bin/activate
python -c 'import cv2; print(cv2.__version__)'
```

### II. Swap File & OpenCV (CUDA Compatible)

To enable **swap memory** and install **OpenCV with CUDA acceleration**, you have two options:

1. Follow the detailed commands here: [opencv_swap_setup.md](opencv_swap_setup.md)
2. Or refer to the external guide: [QEngineering – Install OpenCV on Jetson Nano](https://qengineering.eu/install-opencv-on-jetson-nano.html)

## 9. Install PyTorch & Torchvision on Jetson Nano

PyTorch and Torchvision are optimized for Jetson devices with CUDA support.  
Follow the official NVIDIA forum instructions here:  
👉 [PyTorch for Jetson (Official NVIDIA Forum)](https://forums.developer.nvidia.com/t/pytorch-for-jetson/72048)

select the version of each according to jetpack-sdk version and python version..

### install the code editor

```bash
pip install jupyter
```

## 10. Run JetsonYolo.py to detect objects with the camera.

$ python3 JetsonYolo.py
