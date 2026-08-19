# Isaac ROS Teleop

NVIDIA-accelerated teleoperation solutions for robot data collection.

<div align="center"><a class="reference internal image-reference" href="https://media.githubusercontent.com/media/NVIDIA-ISAAC-ROS/.github/release-4.6/resources/isaac_ros_docs/repositories_and_packages/isaac_ros_physical_ai/isaac_ros_unitree_g1_teleop_bringup/unitree-g1-teleop-hero.gif/"><img alt="Isaac ROS Teleop with Unitree G1" src="https://media.githubusercontent.com/media/NVIDIA-ISAAC-ROS/.github/release-4.6/resources/isaac_ros_docs/repositories_and_packages/isaac_ros_physical_ai/isaac_ros_unitree_g1_teleop_bringup/unitree-g1-teleop-hero.gif/" width="520px"/></a></div>

## Overview

Isaac ROS Teleop contains a ROS 2 package for robot data collection.
`isaac_ros_teleop` relies on [Isaac Teleop](https://github.com/NVIDIA/IsaacTeleop), a framework
for high-fidelity ego-centric and robot data collection. `Isaac Teleop` is designed to address the
data bottleneck in robot learning by streamlining device integration, allowing for high-fidelity human
demo data collection, and fosters device and data interoperability.

This repository is focused on using XR headsets for gripper or tri-finger hand manipulation
using the [PICO 4 Ultra](https://www.picoxr.com/global/products/pico4-ultra) or
[Meta Quest 3](https://www.meta.com/quest/quest-3/) headset.

---

## Documentation

Refer to the [Isaac ROS Documentation](https://nvidia-isaac-ros.github.io/repositories_and_packages/isaac_ros_teleop/index.html) to learn how to use this repository.

---

## Packages

* [`isaac_ros_teleop`](https://nvidia-isaac-ros.github.io/repositories_and_packages/isaac_ros_teleop/isaac_ros_teleop/index.html)
  * [Quickstart](https://nvidia-isaac-ros.github.io/repositories_and_packages/isaac_ros_teleop/isaac_ros_teleop/index.html#quickstart)
  * [Troubleshooting](https://nvidia-isaac-ros.github.io/repositories_and_packages/isaac_ros_teleop/isaac_ros_teleop/index.html#troubleshooting)
  * [API](https://nvidia-isaac-ros.github.io/repositories_and_packages/isaac_ros_teleop/isaac_ros_teleop/index.html#api)

## Latest

Update 2026-08-18: Support auto-launching CloudXR via the node and publish head pose.
