# Robot Safety System - SMACH vs Behavior Trees

## Build Instructions

Navigate to your ROS2 workspace and build the packages:
```bash
cd ~/ros_ws
colcon build --symlink-install
source install/setup.bash
```

## Execution Instructions

### Step 1: Launch Gazebo Simulation

Start the Robile robot simulation in Gazebo and RViz:
```bash
ros2 launch robile_gazebo gazebo_4_wheel.launch.py
```

### Step 2: Launch Teleoperation

For manual robot control during testing:
```bash
ros2 run teleop_twist_keyboard teleop_twist_keyboard
```

### Step 3: Launch Battery Simulator

Start the battery simulation node:
```bash
ros2 launch robile_safety_system battery_only.launch.py
```

### Step 4: Launch Safety System

Choose one of the safety implementations:

**Option A: SMACH State Machine Implementation**
```bash
ros2 launch robile_safety_system safety_smach.launch.py
```

**Option B: Behavior Tree Implementation**
```bash
ros2 launch robile_safety_system safety_bt.launch.py
```

## System Behavior

The safety system monitors two conditions:

1. **Low Battery**: When battery level drops below 20%, the robot rotates in place to recharge until reaching 85%.
2. **Collision Detection**: When an obstacle is detected within 0.5m, the robot stops until the obstacle moves beyond 0.75m.

Collision detection has higher priority than battery management.

## Package Structure

- `robile_battery_simulator`: Battery physics simulation
- `robile_safety_smach`: SMACH-based safety implementation
- `robile_safety_bt`: Behavior tree-based safety implementation
- `robile_safety_system`: Launch file orchestration

## Testing

Use the following commands to test system behavior:

**Manually set battery level:**
```bash
ros2 topic pub --once /battery_set std_msgs/msg/Float32 "data: 15.0"
```

**Monitor battery status:**
```bash
ros2 topic echo /battery_level
```

**View robot commands:**
```bash
ros2 topic echo /cmd_vel
```

## Demo Video

[![Demo Video](https://img.youtube.com/vi/12EEkJe1wfI/0.jpg)](https://youtu.be/12EEkJe1wfI)