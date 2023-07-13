# Hello Robot Stretch RE1 Guide

![](RackMultipart20230713-1-s17mt6_html_eb2b339f2f4225f4.png)

Wo Wei Lin, Zach Osman, Chloe Lam, William Yao. Special thanks to: Jivko Sinapov, Ron Lasser, Dave Lillethun

###


### Tools

**Website:**

[https://docs.hello-robot.com/0.2/](https://docs.hello-robot.com/0.2/)

**Official Github Repositories:**

Default

[https://github.com/hello-robot/stretch\_ros](https://github.com/hello-robot/stretch_ros)

[https://github.com/hello-robot/stretch\_ros/tree/master/stretch\_description](https://github.com/hello-robot/stretch_ros/tree/master/stretch_description)

Adding tools to URDF Model

[https://github.com/hello-robot/stretch\_tool\_share](https://github.com/hello-robot/stretch_tool_share)

**Python API**

[https://docs.hello-robot.com/0.2/stretch-tutorials/stretch\_body/](https://docs.hello-robot.com/0.2/stretch-tutorials/stretch_body/)

### Start Stretch

Password: hello2020

**Calibrate Robot Before Use:**

1. stretch\_robot\_home.py
2. stretch\_robot\_stow.py

**Teleoperating Stretch:**

rosservice call /switch\_to\_navigation\_mode

rosrun teleop\_twist\_keyboard teleop\_twist\_keyboard.py cmd\_vel:=stretch/cmd\_vel

NOTE: The controller is not set up due to previous issues with the robot.

### Creating and Setting Up Map

**Official 2D Navigation Stack:**

[https://docs.hello-robot.com/0.2/stretch-tutorials/ros1/example\_13/](https://docs.hello-robot.com/0.2/stretch-tutorials/ros1/example_13/)

[https://github.com/hello-robot/stretch\_ros/blob/master/stretch\_navigation/README.md](https://github.com/hello-robot/stretch_ros/blob/master/stretch_navigation/README.md)

**Official 3D Navigation Stack:**

[https://github.com/hello-robot/stretch\_ros/tree/master/stretch\_funmap](https://github.com/hello-robot/stretch_ros/tree/master/stretch_funmap)

Setting up funmap:

1. Ssh in the hello robot: ssh hello-robot@10.0.60.32
2. On Robot: export ROS\_IP = 10.0.60.32
  1. Do on every terminal that is a robot!
3. On PC: export ROS\_IP = "ip of PC"
4. On PC: export ROS\_MASTER\_URI = [http://10.0.60.32:11311](http://10.0.60.32:11311/)
5. On Robot: run launch file that we want
  1. Roslaunch stretch\_core stretch\_driver.launch
    1. May be unnecessary? UNECeSSARYSSS
  2. roslaunch stretch\_funmap mapping.launch
    1. Exit from rviz window

- On PC: Example with funmap
- rviz -d `rospack find stretch_funmap`/rviz/stretch\_mapping.rviz
  - Follow tutorial: press space [https://github.com/hello-robot/stretch\_ros/blob/master/stretch\_funmap/README.md](https://github.com/hello-robot/stretch_ros/blob/master/stretch_funmap/README.md)
- Move it 1 meter and press space again to rerun mapping

### RVIZ

- Global fixed frame is /map
- Add pointcloud2 and marker array too see the map after you make it
  - You make the map by pressing space btw
  - Github link above is good for map

Rostopic echo move\_base /current\_goal

Rostopic echo /clicked\_point

### Using the Camera

[https://docs.hello-robot.com/0.2/stretch-tutorials/ros1/perception/](https://docs.hello-robot.com/0.2/stretch-tutorials/ros1/perception/)

NOTE: THE CAMERA IS TURNED 90 DEGREES. MUST TRANSFORM THE IMAGE.

- Startup Camera: roslaunch stretch\_core d435i\_low\_resolution.launch

### Gazebo

NOTE: Gazebo uses MoveIt!, but the real life robot uses FUNMAP as MoveIt! Isn't supported. Real robot uses move\_base like the turtlebot or the python API can be used.

[https://docs.hello-robot.com/0.2/stretch-tutorials/ros1/gazebo\_basics/](https://docs.hello-robot.com/0.2/stretch-tutorials/ros1/gazebo_basics/)

### Battery Management

[https://docs.hello-robot.com/0.2/stretch-hardware-guides/docs/battery\_maintenance\_guide\_re1/](https://docs.hello-robot.com/0.2/stretch-hardware-guides/docs/battery_maintenance_guide_re1/)

**Summary:**

Battery starts in standby, which is lit up orange and looks like the power symbol. To change the modes, hold on the gray button. If it cannot rotate through all the modes, it is likely you need to unplug the charger and wait for it to discharge. Then, take robot off the dock and wait a little. Then replug everything back in and try again. Sometimes, it takes 2-5 tries to get it working. A fully charged robot running a high CPU load can run approximately 2 hours before requiring a recharge.

**When turned off:** 12V AGM

The **12V AGM** charge mode expects the battery voltage to be above 10.5-11V in order to operate.

**When turned on:** 12V Supply

When there are **battery issues** : refer to the guide below.

[https://forum.hello-robot.com/t/stretch-turns-off-computer-while-running-at-around-12-4v/624?u=bshah](https://forum.hello-robot.com/t/stretch-turns-off-computer-while-running-at-around-12-4v/624?u=bshah)

This is a temporary fix. I think the battery might need to be replaced if it persists.

**Battery Level:**

Run: stretch\_robot\_battery\_check.py

![](RackMultipart20230713-1-s17mt6_html_d966a0d780618ab7.png)
