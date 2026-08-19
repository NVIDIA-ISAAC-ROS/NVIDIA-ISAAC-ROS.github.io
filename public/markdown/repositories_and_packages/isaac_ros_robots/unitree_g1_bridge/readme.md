# `unitree_g1_bridge`

## Overview

`unitree_g1_bridge` is a lightweight ROS 2 package that bridges standard
[/cmd_vel](https://docs.ros2.org/latest/api/geometry_msgs/msg/Twist.html)
(`geometry_msgs/Twist`) messages to the Unitree G1 humanoid robot’s
sport-mode API (`/api/sport/request`).

The bridge enables any Nav2-compatible planner or teleoperation tool to drive
the G1 without modification, translating the velocity commands into the
binary sport-mode protocol that the robot’s onboard controller expects.

In addition to velocity forwarding, the node exposes `~/standup`,
`~/damp`, and `~/zero_torque` services for safe finite state machine (FSM)-based standup
sequencing, emergency stop, and full motor power-off, allowing external nodes
or operators to bring the robot from a powered-off state into active
balance-walk mode in a single service call.

---

## Documentation

Visit the [Isaac ROS Documentation](https://nvidia-isaac-ros.github.io/repositories_and_packages/isaac_ros_robots/unitree_g1_bridge/index.html) to learn how to use this package.

---

## Latest

Update 2026-08-18: Compatibility and integration updates for the Isaac ROS 4.6.0 release
