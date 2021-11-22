# ROS1_cheatsheet

# Create simple package

How to create a simple ROS 1 package.

* Create package folder

```bash
mkdir -p example_pkg_ws/src
cd example_pkg_ws/src
catkin_create_pkg beginner_tutorials std_msgs rospy roscpp
```

* Add the code

```bash
mkdir scripts && cd scripts
wget https://raw.github.com/ros/ros_tutorials/kinetic-devel/rospy_tutorials/001_talker_listener/talker.py
cd ..
```

* Add the following line to `CmakeLists.txt`

```
catkin_install_python(PROGRAMS scripts/talker.py
  DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)
```

* Build

```bash
catkin_make
```

* Run

```
source devel/setup.bash
rosrun beginner_tutorials talker.py
```

