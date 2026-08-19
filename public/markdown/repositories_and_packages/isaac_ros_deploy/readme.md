# Isaac ROS Deploy

ROS 2 packages for deploying LEAPP-exported neural-network policies on real and simulated robots.

## Overview

Isaac ROS Deploy provides ROS 2 packages for
deploying neural-network policies on real and simulated robots. It can support
a variety of robot-control policies, including policies derived from
[reinforcement learning in Isaac Lab](https://isaac-sim.github.io/IsaacLab/main/source/overview/reinforcement-learning/rl_existing_scripts.html)
and vision-language-action (VLA) policies exported through
[nvidia-isaac/gr00t-leapp-export](https://github.com/nvidia-isaac/gr00t-leapp-export),
as long as the policy can be exported as a
[LEAPP](https://nvidia-isaac.github.io/leapp/) bundle.

Isaac ROS Deploy bridges the gap between a Python training stack and a robot
control system: it loads LEAPP bundles, runs ONNX inference through NVIDIA
Triton, maps policy terms onto ROS topics or `ros2_control` interfaces, and
optionally gates outputs through a safety controller.

Use Isaac ROS Deploy when you need to deploy a policy as either a ROS 2 node
graph or inside a `ros2_control` loop.

---

## Documentation

Please visit the [Isaac ROS Documentation](https://nvidia-isaac-ros.github.io/repositories_and_packages/isaac_ros_deploy/index.html) to learn how to use this repository.

---

## Latest

Update 2026-08-18: Added Isaac Sim 6.0 deployment support for Unitree G1 AGILE locomotion
policies
