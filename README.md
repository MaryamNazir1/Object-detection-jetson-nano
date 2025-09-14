# Object-detection-jetson-nano

This repository contains all the processes, commands, and setup instructions required to boot and run object detection models on the **NVIDIA Jetson Nano**.

---

## Table of Contents

1. [Introduction](#introduction)
2. [Hardware Requirements](#hardware-requirements)
3. [Booting the Jetson Nano](#booting-the-jetson-nano)
4. [Initial Setup](#initial-setup)
5. [WiFi Setup](#wifi-setup)
6. [Install Dependencies](#install-dependencies)
7. [Run Object Detection](#run-object-detection)
8. [References](#references)

---

## Introduction

The **Jetson Nano** is a small, powerful computer for AI at the edge. This repo serves as a **step-by-step lab notebook** to:

- Boot Jetson Nano for the first time.
- Set up environment for object detection.
- Run YOLO/other detection models on the Nano.

---

## Hardware Requirements

- NVIDIA Jetson Nano Developer Kit
- microSD Card (32GB UHS-1 recommended)
- USB Keyboard & Mouse
- HDMI Display Monitor
- 5V 4A Power Supply (Barrel Jack recommended)
- USB WiFi dongle or Ethernet connection

---

## Booting the Jetson Nano

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

## Initial Setup

Update and upgrade system packages:

```bash
sudo apt-get update
sudo apt-get upgrade
```

---

## WiFi Setup

If you are using a **USB WiFi dongle**, follow this detailed guide:  
 [Adding WiFi to the NVIDIA Jetson Nano (SparkFun Tutorial)](https://learn.sparkfun.com/tutorials/adding-wifi-to-the-nvidia-jetson/all)

This covers:

- Checking supported WiFi adapters
- Installing necessary drivers
- Connecting to a wireless network

## save the 'wlan0' and 'eth0' ip address for next steps (Setup Headless Mode).
