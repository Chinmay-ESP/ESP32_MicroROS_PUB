# Micro-ROS with ESP32 using PlatformIO

This repository demonstrates the implementation of Micro-ROS on an ESP32 development board using the PlatformIO environment. The project features a ROS2 publisher that transmits integer messages (`std_msgs/msg/Int32`) to a specified ROS2 topic.

## Prerequisites

### Software Requirements
- [PlatformIO](https://platformio.org/) installed in VS Code
- [Micro-ROS](https://micro.ros.org/) library
- ROS2 installed on a compatible system
- Serial transport setup for communication between ESP32 and ROS2

### Hardware Requirements
- ESP32 development board
- USB cable for programming and serial communication

## Installation

1. **Clone the Repository**
   ```sh
   git clone https://github.com/Chinmay-ESP/ESP32_MicroROS_PUB.git
   cd ESP32_MicroROS_PUB
   ```

2. **Install Dependencies**
   Open the project in VS Code and allow PlatformIO to automatically install the required dependencies.

3. **Configure Micro-ROS Serial Transport**
   Ensure the correct serial transport setup for ESP32:
   ```cpp
   set_microros_serial_transports(Serial);
   ```

4. **Build and Upload the Code**
   ```sh
   pio run --target upload
   ```

## Project Overview

### Core Components
- **Publisher**: Publishes an integer message to the ROS2 topic `micro_ros_platformio_node_publisher`.
- **Timer**: Executes a callback function every second, incrementing and publishing the integer value.
- **Executor**: Manages asynchronous execution of callbacks.

### Key Functionality
- **Setup Function (`setup()`)**:
  - Initializes the Micro-ROS node, publisher, timer, and executor.
- **Loop Function (`loop()`)**:
  - Executes the Micro-ROS executor to manage message publishing.

## Running the ROS2 Node

To subscribe to the published messages, execute the following command on your ROS2 machine:
```sh
ros2 topic echo /micro_ros_platformio_node_publisher
```

## Troubleshooting

- If the Micro-ROS agent is not running, start it using:
  ```sh
  ros2 run micro_ros_agent micro_ros_agent serial --dev /dev/ttyUSB0 -b 115200
  ```
- Ensure the correct USB port is configured in `platformio.ini`.
- Verify ROS2 and Micro-ROS installations are correctly configured.

