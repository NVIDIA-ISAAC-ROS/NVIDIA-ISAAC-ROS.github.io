# Isaac ROS Physical AI

Application-level bringup packages for deploying whole-body control and teleoperation on humanoid robots.

## Overview

Isaac ROS Physical AI provides application-level
bringup packages for deploying whole-body control and teleoperation on humanoid robots.

The current release supports the Unitree G1 with:

- **AGILE locomotion**: Whole-body control policy for balance and walking
- **Bimanual inverse kinematics**: Real-time IK for both arms using cuMotion
- **Finger control**: Hand tracking from an XR headset
- **XR teleoperation**: End-effector and locomotion control using an XR headset with
  [Isaac Teleop](https://nvidia.github.io/IsaacTeleop)

Both MuJoCo simulation and real hardware are supported.

For a fine-tuned GR00T policy deployed end-to-end — teleoperate, record,
convert to LeRobot, fine-tune GR00T N, export via LEAPP, deploy — see the
[Isaac for Physical AI reference workflow](https://nvidia-isaac-ros.github.io/reference_workflows/isaac_for_physical_ai/index.html).

---

## Documentation

Please visit the [Isaac ROS Documentation](https://nvidia-isaac-ros.github.io/repositories_and_packages/isaac_ros_physical_ai/index.html) to learn how to use this repository.

---

## Packages

* [`isaac_ros_data_flywheel`](https://nvidia-isaac-ros.github.io/repositories_and_packages/isaac_ros_physical_ai/isaac_ros_data_flywheel/index.html)
* [`isaac_ros_unitree_g1_gr00t`](https://nvidia-isaac-ros.github.io/repositories_and_packages/isaac_ros_physical_ai/isaac_ros_unitree_g1_gr00t/index.html)
  * [Overview](https://nvidia-isaac-ros.github.io/repositories_and_packages/isaac_ros_physical_ai/isaac_ros_unitree_g1_gr00t/index.html#overview)
  * [Tutorial: Deploy a Fine-Tuned GR00T Policy](https://nvidia-isaac-ros.github.io/repositories_and_packages/isaac_ros_physical_ai/isaac_ros_unitree_g1_gr00t/index.html#tutorial-deploy-a-fine-tuned-gr00t-policy)
  * [Real-Hardware Prerequisite Details](https://nvidia-isaac-ros.github.io/repositories_and_packages/isaac_ros_physical_ai/isaac_ros_unitree_g1_gr00t/index.html#real-hardware-prerequisite-details)
  * [API](https://nvidia-isaac-ros.github.io/repositories_and_packages/isaac_ros_physical_ai/isaac_ros_unitree_g1_gr00t/index.html#api)
  * [Troubleshooting](https://nvidia-isaac-ros.github.io/repositories_and_packages/isaac_ros_physical_ai/isaac_ros_unitree_g1_gr00t/index.html#troubleshooting)
* [`isaac_ros_unitree_g1_recorder`](https://nvidia-isaac-ros.github.io/repositories_and_packages/isaac_ros_physical_ai/isaac_ros_unitree_g1_recorder/index.html)
  * [Overview](https://nvidia-isaac-ros.github.io/repositories_and_packages/isaac_ros_physical_ai/isaac_ros_unitree_g1_recorder/index.html#overview)
  * [Tutorial: Record Demonstrations](https://nvidia-isaac-ros.github.io/repositories_and_packages/isaac_ros_physical_ai/isaac_ros_unitree_g1_recorder/index.html#tutorial-record-demonstrations)
  * [API](https://nvidia-isaac-ros.github.io/repositories_and_packages/isaac_ros_physical_ai/isaac_ros_unitree_g1_recorder/index.html#api)
  * [Troubleshooting](https://nvidia-isaac-ros.github.io/repositories_and_packages/isaac_ros_physical_ai/isaac_ros_unitree_g1_recorder/index.html#troubleshooting)
* [`isaac_ros_unitree_g1_teleop_bringup`](https://nvidia-isaac-ros.github.io/repositories_and_packages/isaac_ros_physical_ai/isaac_ros_unitree_g1_teleop_bringup/index.html)
  * [Overview](https://nvidia-isaac-ros.github.io/repositories_and_packages/isaac_ros_physical_ai/isaac_ros_unitree_g1_teleop_bringup/index.html#overview)
  * [Tutorial: Unitree G1 XR Teleop](https://nvidia-isaac-ros.github.io/repositories_and_packages/isaac_ros_physical_ai/isaac_ros_unitree_g1_teleop_bringup/index.html#tutorial-unitree-g1-xr-teleop)
  * [API](https://nvidia-isaac-ros.github.io/repositories_and_packages/isaac_ros_physical_ai/isaac_ros_unitree_g1_teleop_bringup/index.html#api)
  * [Troubleshooting](https://nvidia-isaac-ros.github.io/repositories_and_packages/isaac_ros_physical_ai/isaac_ros_unitree_g1_teleop_bringup/index.html#troubleshooting)

## Latest

Update 2026-07-06: Support CloudXR runtime without Docker
