# Isaac ROS SIPL Camera

ROS 2 camera driver nodes for NVIDIA SIPL cameras with zero-copy GPU-accelerated
image publishing through NITROS.

<div align="center"><a class="reference internal image-reference" href="https://media.githubusercontent.com/media/NVIDIA-ISAAC-ROS/.github/release-5.1/resources/isaac_ros_docs/repositories_and_packages/isaac_ros_sipl_camera/eagle_stereo_rectify_foxglove_visual.jpg/"><img alt="image" src="https://media.githubusercontent.com/media/NVIDIA-ISAAC-ROS/.github/release-5.1/resources/isaac_ros_docs/repositories_and_packages/isaac_ros_sipl_camera/eagle_stereo_rectify_foxglove_visual.jpg/" width="800px"/></a></div>

---

## Overview

Isaac ROS SIPL Camera provides ROS 2 camera
driver nodes for NVIDIA SIPL (Safe Image Processing Library) cameras with
zero-copy GPU-accelerated image publishing using ROS 2
`rosidl::Buffer`-backed messages and the CUDA buffer backend.

SIPL is NVIDIA’s modular camera framework for Jetson, providing a unified API
and driver model that exposes hardware accelerated ISP for continuous
image streaming from sensors. See
[Introduction to SIPL](https://docs.nvidia.com/jetson/archives/r39.2/DeveloperGuide/SD/CameraDevelopment/SIPLFramework/Introduction-to-SIPL.html)
and the [UDDF (SIPL) drivers](https://docs.nvidia.com/holoscan/sensor-bridge/applications/uddf-drivers)
used to integrate sensors.

SIPL is the primary, streaming-oriented camera framework for Jetson and the long-term
path for new camera framework features, superseding the earlier Argus framework. For a comparison,
see [Camera Development](https://docs.nvidia.com/jetson/archives/r39.2/DeveloperGuide/SD/CameraDevelopment.html)
in the NVIDIA Jetson Linux Developer Guide. Argus will continue to be maintained in JetPack but
the Isaac ROS integration was dropped since Isaac release 4.0.

[CoE](https://docs.nvidia.com/jetson/archives/r39.2/DeveloperGuide/SD/CameraDevelopment/SIPLFramework/SIPL-for-L4T/CoE/CoE-Solution-Overview.html)
is the next-generation Ethernet-based camera transport enabling high-performance,
flexible, and scalable camera integration using standard Ethernet networks.

The [Holoscan Sensor Bridge (HSB)](https://docs.nvidia.com/holoscan/sensor-bridge/getting-started/introduction)
is the CSI-to-Ethernet bridge hardware that turns MIPI/GMSL sensors into CoE
cameras and tunnels their control and image data over Ethernet.

GMSL2 is a high-speed serializer/deserializer link that carries MIPI camera data over
coax. SIPL also drives GMSL deserializers directly, so GMSL cameras such as the Leopard
Imaging Hawk attach to the Jetson on-board.

Key features include:

- **Hardware-accelerated ISP with no host copy** from capture through the Jetson on-chip ISP to CUDA-accessible memory
- **Mono and stereo camera support** with independent capture threads per sensor
- **No GPU-to-host copy between publisher and subscriber** with ROS 2
  `rosidl::Buffer`-backed messages, keeping image data on the GPU between
  compatible ROS nodes
- **Camera calibration importing** to publish accurate intrinsics in ROS `camera_info` for rectification and downstream perception
- **REP-103 static TF publication** to define camera and optical frames based on imported calibration data

### Known Limitations

> [!Note]
> SIPL support for JetPack CoE and GMSL stereo cameras is in early development
> and is expected to improve in future releases. There are limitations of the framework
> that apply as of the current release.

The following known limitations apply:

1. **Calibration from file import only**: The provided camera drivers do not yet support
   extracting calibration data from the camera EEPROM. Import the
   calibration files to the ROS nodes as described in the
   [Isaac ROS SIPL Camera](https://nvidia-isaac-ros.github.io/repositories_and_packages/isaac_ros_sipl_camera/isaac_ros_sipl_camera/index.html) documentation.
2. **ISP output formats**: The node supports only native NV12 or NV24 output
   from the ISP. Use the `ImageFormatConverterNode` included in the example
   launch files for other formats.
3. **Limited multi-link capture**: The [Sensing cameras](https://nvidia-isaac-ros.github.io/getting_started/sensors/sensing_thor_setup.html)
   support concurrent capture from an S56C stereo camera and SHF3L cameras through one `SiplMultiCameraNode`. Other reference
   cameras documented in this package are not yet supported.
4. **Stereo frames have age differences**: A known behavior in SIPL synchronized stereo grouping can result in one sensor’s frames arriving
   several frame periods older than the other sensor’s frames in the pair even though frames arrived together. The issue
   occurs when the frame synchronization pulse starts before the sensors power up. With the [Sensing camera drivers](https://nvidia-isaac-ros.github.io/getting_started/sensors/sensing_thor_setup.html)
   which uses `osc_manual` frame synchronization mode by default, expect a difference of one or more frame periods.
5. **HSB camera configurations conflict with the same config name**: As of the Jetson Linux (L4T) R39.2 release,
   the SIPL query parser treats each CoE transport’s camera config name as a globally unique key,
   so it rejects configurations that bind more than one Holoscan Sensor Bridge (HSB) transport to
   the same config name. This prevents multiple HSB camera configurations from loading. As a workaround,
   assign a unique camera config name to each HSB transport instead of reusing one name across multiple HSBs.

---

## Documentation

Please visit the [Isaac ROS Documentation](https://nvidia-isaac-ros.github.io/repositories_and_packages/isaac_ros_sipl_camera/index.html) to learn how to use
this repository.

---

## Latest

Update 2026-11-16: Added Sensing S56C stereo and SHF3L YUV422 camera support on Jetson Thor, mixed-camera capture, and image resizing with scaled CameraInfo. Fixed launches with an empty stereo_pairs list

## Supported Platforms

This package is designed and tested to be compatible with ROS 2 Lyrical running on [Jetson](https://developer.nvidia.com/embedded-computing).

| Platform   | Hardware                                                                                                                                                                                        | Software                                                     | Storage          | Notes                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------|------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Jetson     | [Jetson Thor](https://www.nvidia.com/en-us/autonomous-machines/embedded-systems/jetson-thor/) and [Jetson Orin](https://www.nvidia.com/en-us/autonomous-machines/embedded-systems/jetson-orin/) | [JetPack 7.2](https://developer.nvidia.com/embedded/jetpack) | 128+ GB NVMe SSD | For best performance, ensure that power settings are configured appropriately for your platform: [Jetson Thor power settings](https://docs.nvidia.com/jetson/archives/r39.2/DeveloperGuide/SD/PlatformPowerAndPerformance/JetsonThor.html) or [Jetson Orin power settings](https://docs.nvidia.com/jetson/archives/r39.2/DeveloperGuide/SD/PlatformPowerAndPerformance/JetsonOrinNanoSeriesJetsonOrinNxSeriesAndJetsonAgxOrinSeries.html). |
