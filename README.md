# Blasting_robot


---

## About

This repository hosts the ROS2 workspace for **Velath Engineering's autonomous sandblasting robot**. It includes drivers, description files, simulation assets, teleop control, and SLAM/navigation support. It is built and tested on **Ubuntu 22.04** with **ROS2 Humble**.

Key features:

* Modular package layout
* CAN/Serial-based driver support
* Full simulation in Gazebo
* URDF model with frame transforms
* Navigation2 and SLAM Toolbox integration
* Jetson-optimized perception (YOLOv8-ready)

---

## Repository Layout

```
Blasting_robot/
├── .github/workflows/build.yaml        # GitHub CI workflow
├── docs/jetson_deployment.md           # Jetson install and deploy guide
├── src/
│   ├── velathrobotics_ros2-main/
│   │   ├── velathrobotics_description/     # URDF and meshes
│   │   ├── velathrobotics_driver/          # Main robot driver
│   │   ├── velathrobotics_gazebo/          # Simulation world
│   │   └── velathrobotics_input_manager/   # Joystick/teleop
├── .rosinstall
├── .gitignore
├── LICENSE
└── README.md
```

---

## Installation

### Clone and Build

```bash
mkdir -p ~/velathrobotics_ros2-ws/src
cd ~/velathrobotics_ros2-ws
vcs import src < .rosinstall
colcon build --symlink-install
source install/setup.bash
```

---

## Usage

### Real Robot Launch

```bash
ros2 launch velathrobotics_driver bringup.launch.py
```

### With Joystick Teleop

```bash
ros2 launch velathrobotics_input_manager teleop_launch.py
```

---

## Simulation

### Gazebo Simulation

```bash
ros2 launch velathrobotics_gazebo blasting_sim.launch.py
```

### View URDF in RViz

```bash
ros2 launch velathrobotics_description display.launch.py
```

---

## SLAM and Navigation

### SLAM Toolbox

```bash
ros2 launch velathrobotics_driver slam_launch.py
```

### Nav2 with Map

```bash
ros2 launch velathrobotics_driver navigation_launch.py map_file_name:=/full/path/to/map_file
```

### Note:

* Use `use_sim_time:=true` in simulation
* Transform tree: `base_link -> odom -> map`

---

## Sensor Setup

**Supported sensors**:

* RP Lidar S2
* BNO055 IMU
* Realsense D435 / ZED X (optional)

Edit `velathrobotics_driver/config/accessories.yaml`:

```yaml
rplidar:
  serial_port: "/dev/rplidar"
bno055:
  uart_port: "/dev/bno055"
```

Create a udev rule in `/etc/udev/rules.d/` for sensor aliases.

---

## Jetson Deployment

See full guide in: [`docs/jetson_deployment.md`](docs/jetson_deployment.md)

Highlights:

* JetPack 5.x + ROS2 Humble
* YOLOv8 ONNX/TensorRT inference
* Realtime deployment on Orion NX and Xavier AGX

---

## License

MIT License © Velath Engineering

---



