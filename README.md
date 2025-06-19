# Autonomous Driving System for GEMe2 Vehicle (AutoGem)

For a more detailed information, please visit: [https://htliang517.github.io/projects/AutoGEM](https://htliang517.github.io/projects/AutoGEM)

### How to build the project?

1. Clone the whole repository

   ```
   git clone https://github.com/htliang517/AutoGem.git
   ```
2. Go to current workspace

   ```
   cd AutoGem
   ```
3. Build the project

   ```
   catkin_make
   ```

### How to run the project?

1. Run Vision and controller in **Gazebo S****imulation**

   - Terminal #1 Launch Gazebo Simulation

     ```
     source devel/setup.bash
     roslaunch gem_launch gem_init.launch world_name:="highbay_track.world" x:=-1.5 y:=-21 yaw:=3.1416
     ```
   - Terminal #2 studentVision_gazebo

     ```
     source devel/setup.bash
     rosrun gem_lane_detection studentVision_gazebo.py
     ```
   - Terminal #3 controller

     ```
     source devel/setup.bash
     rosrun gem_controller controller.py
     ```
   - Terminal #4 Run when you reset the gem position

     ```
     source devel/setup.bash
     rosrun gem_controller set_pos.py --x -1.5 --y -21 --yaw 3.1416

     ```
2. Run Vision and controller in GEM

   - Terminal #1 studentVision

     ```
     source devel/setup.bash
     rosrun gem_lane_detection studentVision.py
     ```
   - Terminal #2 gem_controller

     ```
     source devel/setup.bash
     rosrun gem_controller gem_controller.py
     ```
3. Run controller without Vision

   - Terminal in Gazebo: Run predefined_controller (when you do not use controller.py)

   ```
   source devel/setup.bash
   rosrun gem_controller predefined_controller.py

   ```

   - Terminal in GEM: Run predefined_gem_controller (when you do not use gem_controller)

   ```
   source devel/setup.bash
   rosrun gem_controller predefined_gem_controller.py

   ```

### Packages Description

* `gem_controller`
  - Stores all customixrd controller code.
* `gem_lane_detection`
  - Contain main code of lane detection.
* `gem_yolo`
  - Contain main code for YOLO detection.

- `gem_simulator`
  - Cloned from "https://github.com/hangcui1201/POLARIS_GEM_e2_Simulator"

* `teleop_twist_keyboard`
  - Cloned from "https://github.com/ros-teleop/teleop_twist_keyboard"
  - Used for keyboard control

### Debug Solution

```bash
CMake Error at /opt/ros/noetic/share/catkin/cmake/catkinConfig.cmake:83 (find_package):  Could not find a package configuration file provided by "geographic_msgs"
  with any of the following names:    geographic_msgsConfig.cmake
    geographic_msgs-config.cmake
```

`<sol>`

```bash
sudo apt-get install ros-noetic-geographic-msgs
```
