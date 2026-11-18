# Isaac ROS Grasping

NVIDIA-accelerated grasp generation from segmented point clouds.

## Overview

GraspGenX generates ranked grasp candidates from segmented point clouds using
native C++/CUDA preprocessing and TensorRT inference. Its standalone quickstart
builds CUDA point clouds from registered depth and object masks, runs inference,
and displays the resulting gripper poses in RViz.

---

## Documentation

Refer to the [Isaac ROS Documentation](https://nvidia-isaac-ros.github.io/repositories_and_packages/isaac_ros_grasping/index.html) to learn how to use this repository.

---

## Packages

* [`isaac_ros_graspgenx`](https://nvidia-isaac-ros.github.io/repositories_and_packages/isaac_ros_grasping/isaac_ros_graspgenx/index.html)
  * [Quickstart](https://nvidia-isaac-ros.github.io/repositories_and_packages/isaac_ros_grasping/isaac_ros_graspgenx/index.html#quickstart)
  * [Troubleshooting](https://nvidia-isaac-ros.github.io/repositories_and_packages/isaac_ros_grasping/isaac_ros_graspgenx/index.html#troubleshooting)
  * [API](https://nvidia-isaac-ros.github.io/repositories_and_packages/isaac_ros_grasping/isaac_ros_graspgenx/index.html#api)
* [`isaac_ros_graspgenx_interfaces`](https://nvidia-isaac-ros.github.io/repositories_and_packages/isaac_ros_grasping/isaac_ros_graspgenx_interfaces/index.html)
* [`isaac_ros_graspgenx_models_install`](https://nvidia-isaac-ros.github.io/repositories_and_packages/isaac_ros_grasping/isaac_ros_graspgenx_models_install/index.html)
  * [Using Hugging Face checkpoints](https://nvidia-isaac-ros.github.io/repositories_and_packages/isaac_ros_grasping/isaac_ros_graspgenx_models_install/index.html#using-hugging-face-checkpoints)

## Latest

Update 2026-11-16: Initial release of GraspGenX for single-object and batch grasp generation
