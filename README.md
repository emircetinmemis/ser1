# SER-01 States & Behaviours 

## Setup Instructions

### 1. Battery Simulation

```bash
ros2 launch robile_safety_system battery_only.launch.py
```

### 2. Smash or Behaviour Trees Simulation

```bash 
ros2 launch robile_safety_system smach_only.launch.py
```

$$or$$

```bash 
ros2 launch robile_safety_system bt_only.launch.py
```

### 3. Combined Simulation

```bash
ros2 launch robile_safety_system safety_smach.launch.py
```

$$or$$

```bash
ros2 launch robile_safety_system safety_bt.launch.py
```

## Demo Video
 
[![IMAGE ALT TEXT HERE](https://img.youtube.com/vi/12EEkJe1wfI/0.jpg)](https://youtu.be/12EEkJe1wfI)