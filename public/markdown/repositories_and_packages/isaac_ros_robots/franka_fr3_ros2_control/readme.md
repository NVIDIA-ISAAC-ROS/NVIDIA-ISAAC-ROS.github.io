# `franka_fr3_ros2_control`

## Overview

`franka_fr3_ros2_control` is the `ros2_control` `SystemInterface` plugin that
drives the real Franka FR3 over the Franka Control Interface (FCI) using
`libfranka`. It owns a dedicated `SCHED_FIFO` thread running the 1 kHz
FCI control loop and exchanges joint-state and command snapshots with the
controller manager’s `read()` / `write()` cycle through lock-free
real-time buffers, so the strict real-time FCI loop is isolated from the
ROS scheduler and the arm can be driven from a stock Ubuntu kernel
without the `PREEMPT_RT` patch.

---

## Documentation

Visit the [Isaac ROS Documentation](https://nvidia-isaac-ros.github.io/repositories_and_packages/isaac_ros_robots/franka_fr3_ros2_control/index.html) to learn how to use this package.

---

## Latest

Update 2026-08-18: Compatibility and integration updates for the Isaac ROS 4.6.0 release
