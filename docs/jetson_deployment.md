#  Jetson Deployment Guide for Velath Blasting Robot

This guide explains how to deploy the ROS2 stack on **Jetson Orion NX**, **Xavier AGX**, or **Nano** with GPU-accelerated inference (YOLOv8 + ROS2).

---

## 🔧 System Setup

### OS

- Ubuntu 22.04 (Jetpack 5.1+ for Xavier)
- ROS2 Humble

### Packages

```bash
sudo apt update && sudo apt install -y \
  python3-colcon-common-extensions \
  python3-pip \
  python3-vcstool \
  ros-humble-desktop \
  ros-humble-tf2-ros \
  ros-humble-nav2-bringup \
  ros-humble-robot-localization \
  libopencv-dev
