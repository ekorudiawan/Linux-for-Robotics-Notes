# Linux-for-Robotics-Notes
All notes about configuring Linux system for robotics application

## Setting Persistent Devices Name
Change USB camera name from /dev/video* to static name
```bash
cp ./script/99-usb-camera.rules /etc/udev/rules.d/
sudo udevadm control --reload-rules
sudo udevadm trigger
```

Change U2D2 name from /dev/ttyUSB* to static name
```bash
cp ./scripts/88-U2D2.rules /etc/udev/rules.d/
sudo udevadm control --reload-rules
sudo udevadm trigger
```

## Change Latency Timer Linux
Check latency timer
```bash
cat /sys/bus/usb-serial/devices/ttyUSB0/latency_timer
```

Make FTDI chip possible for a 2MBps baud rate
```bash
echo 1 | sudo tee /sys/bus/usb-serial/devices/ttyUSB0/latency_timer
```

## Autorun Script
Run specific script when USB devices plugin
```bash
```

## Calibrating Camera in ROS2
Install package usb_cam on ROS2
```bash
sudo apt install ros-humble-usb-cam
```
Run and view camera
```bash
ros2 run usb_cam usb_cam_node_exe
ros2 run image_view image_view image:=/image_raw
```
Getting calibration file

Rectifying calibration file
```bash
ros2 run image_proc image_proc
```

## Isolating specific CPU cores for real-time process
ref https://forums.developer.nvidia.com/t/allow-only-one-proccess-to-run-on-specific-core/157315/5
## Unsolve problem

