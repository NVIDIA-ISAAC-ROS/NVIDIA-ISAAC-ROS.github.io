# Isaac ROS SIPL Camera

ROS 2 camera driver nodes for NVIDIA SIPL cameras with zero-copy GPU-accelerated
image publishing through NITROS.

<div align="center"><a class="reference internal image-reference" href="https://media.githubusercontent.com/media/NVIDIA-ISAAC-ROS/.github/release-4.5/resources/isaac_ros_docs/repositories_and_packages/isaac_ros_sipl_camera/eagle_stereo_rectify_foxglove_visual.jpg/"><img alt="image" src="https://media.githubusercontent.com/media/NVIDIA-ISAAC-ROS/.github/release-4.5/resources/isaac_ros_docs/repositories_and_packages/isaac_ros_sipl_camera/eagle_stereo_rectify_foxglove_visual.jpg/" width="800px"/></a></div>

---

## Overview

Isaac ROS SIPL Camera provides ROS 2 camera
driver nodes for NVIDIA SIPL (Sensor Input Processing Library) cameras with
zero-copy GPU-accelerated image publishing through NITROS.

SIPL is NVIDIA’s modular camera framework for Jetson, providing a unified API
and driver model that exposes hardware accelerated ISP for continuous
image streaming from sensors. See
[Introduction to SIPL](https://docs.nvidia.com/jetson/archives/r38.4/DeveloperGuide/SD/CameraDevelopment/CoECameraDevelopment/SIPL-for-L4T/Introduction-to-SIPL.html)
and the [UDDF (SIPL) drivers](https://docs.nvidia.com/holoscan/sensor-bridge/latest/uddf_drivers.html)
used to integrate sensors.

[CoE](https://docs.nvidia.com/jetson/archives/r38.4/DeveloperGuide/SD/CameraDevelopment/CoECameraDevelopment/SIPL-for-L4T/CoE-Solution-Overview.html)
is the next-generation Ethernet-based camera transport enabling high-performance,
flexible, and scalable camera integration using standard Ethernet networks.

The [Holoscan Sensor Bridge (HSB)](https://docs.nvidia.com/holoscan/sensor-bridge/latest/index.html)
is the CSI-to-Ethernet bridge hardware that turns MIPI/GMSL sensors into CoE
cameras and tunnels their control and image data over Ethernet.

Key features include:

- **Zero-copy CoE image data path** from Ethernet (MGBE) to application buffers via hardware DMA, then through hardware-accelerated ISP to CUDA-mapped buffers for ROS publishing
- **Mono and stereo camera nodes** with independent capture threads per sensor
- **Zero-copy publisher subscriber** messaging in ROS with NITROS
- **Camera calibration importing** to publish accurate intrinsics in ROS `camera_info` for rectification and downstream perception
- **REP-103 static TF publication** to define camera and optical frames based on imported calibration data

### Known Limitations

> [!Note]
> SIPL support for JetPack and CoE stereo cameras is in early development
> and is expected to improve in future releases. There are limitations of the framework
> that apply as of the current release.

The following known limitations apply:

1. **Calibration from file import only**: The driver does not yet support
   extracting calibration data from the Eagle camera EEPROM. Import the
   calibration files to the ROS nodes as described in the
   [Isaac ROS SIPL Camera](https://nvidia-isaac-ros.github.io/repositories_and_packages/isaac_ros_sipl_camera/isaac_ros_sipl_camera/index.html) documentation.
2. **No stereo synchronization**: Stereo capture does not synchronize frames
   or ISP auto-control between left and right sensors. Timestamps of a stereo
   image pair may differ.
3. **ISP output formats**: The node supports only native NV12 or NV24 output
   from the ISP. Use the `ImageFormatConverterNode` included in the example
   launch files for other formats.

---

## Documentation

Please visit the [Isaac ROS Documentation](https://nvidia-isaac-ros.github.io/repositories_and_packages/isaac_ros_sipl_camera/index.html) to learn how to use
this repository.

---

## Latest

Update 2026-04-30: Compatibility and integration updates for the Isaac ROS 4.4.0 release

## Supported Platforms

This package is designed and tested to be compatible with ROS 2 Jazzy running on [Jetson](https://developer.nvidia.com/embedded-computing).

| Platform   | Hardware                                                                                      | Software                                                     | Storage          | Notes                                                                                                                                                                              |
|------------|-----------------------------------------------------------------------------------------------|--------------------------------------------------------------|------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Jetson     | [Jetson Thor](https://www.nvidia.com/en-us/autonomous-machines/embedded-systems/jetson-thor/) | [JetPack 7.1](https://developer.nvidia.com/embedded/jetpack) | 128+ GB NVMe SSD | For best performance, ensure that [power settings](https://docs.nvidia.com/jetson/archives/r38.4/DeveloperGuide/SD/PlatformPowerAndPerformance.html) are configured appropriately. |
