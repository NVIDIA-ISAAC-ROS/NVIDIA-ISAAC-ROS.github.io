# Isaac ROS Benchmark

Performance benchmarking for NVIDIA-accelerated Isaac ROS packages.

<div align="center"><a class="reference internal image-reference" href="https://media.githubusercontent.com/media/NVIDIA-ISAAC-ROS/.github/main/resources/isaac_ros_docs/repositories_and_packages/isaac_ros_benchmark/r2b_turtlebot_takeoff.gif/"><img alt="image" src="https://media.githubusercontent.com/media/NVIDIA-ISAAC-ROS/.github/main/resources/isaac_ros_docs/repositories_and_packages/isaac_ros_benchmark/r2b_turtlebot_takeoff.gif/" width="800px"/></a></div>

## Overview

Isaac ROS Benchmark builds upon the
[ros2_benchmark](https://github.com/NVIDIA-ISAAC-ROS/ros2_benchmark)
to provide configurations to benchmark Isaac ROS graphs. Performance
results that measure Isaac ROS for throughput, latency, and utilization
enable robotics developers to make informed decisions when designing
real-time robotics applications. The Isaac ROS performance results can
be independently verified, as the method, configuration, and data input
used for benchmarking are provided.

The `ros2_benchmark` playback node plug-in, for type adaptation and
negotiation, is provided for
[NITROS](https://github.com/NVIDIA-ISAAC-ROS/isaac_ros_nitros), which
optimizes the performance of message transport costs through
[RCL](https://github.com/ros2/rclcpp) with GPU accelerated graphs of
nodes.

The datasets for benchmarking are explicitly not downloaded by default.
To pull down the standardized benchmark datasets, refer to the
[ros2_benchmark Dataset](https://github.com/NVIDIA-ISAAC-ROS/ros2_benchmark#datasets)
section.

---

## Documentation

Please visit the [Isaac ROS Documentation](https://nvidia-isaac-ros.github.io/repositories_and_packages/isaac_ros_benchmark/index.html) to learn how to use this repository.

---

## Packages

* [`isaac_ros_benchmark`](https://nvidia-isaac-ros.github.io/repositories_and_packages/isaac_ros_benchmark/isaac_ros_benchmark/index.html)
  * [Quickstart](https://nvidia-isaac-ros.github.io/repositories_and_packages/isaac_ros_benchmark/isaac_ros_benchmark/index.html#quickstart)
  * [Troubleshooting](https://nvidia-isaac-ros.github.io/repositories_and_packages/isaac_ros_benchmark/isaac_ros_benchmark/index.html#troubleshooting)

## Latest

Update 2024-12-10: Added new benchmarks

## Performance

| Node<br/><br/>                                             | Input Size<br/><br/>          | AGX Orin<br/><br/>                             | Orin NX<br/><br/>                              | Orin Nano Super 8GB<br/><br/>                  | x86_64 w/ RTX 4090<br/><br/>                    |
|------------------------------------------------------------|-------------------------------|------------------------------------------------|------------------------------------------------|------------------------------------------------|-------------------------------------------------|
| AprilTag Node<br/><br/><br/><br/>                          | 720p<br/><br/><br/><br/>      | 178 fps<br/><br/><br/>6.3 ms @ 30Hz<br/><br/>  | 116 fps<br/><br/><br/>9.4 ms @ 30Hz<br/><br/>  | 123 fps<br/><br/><br/>8.6 ms @ 30Hz<br/><br/>  | 596 fps<br/><br/><br/>0.86 ms @ 30Hz<br/><br/>  |
| Freespace Segmentation Node<br/><br/><br/><br/>            | 576p<br/><br/><br/><br/>      | 3340 fps<br/><br/><br/>1.7 ms @ 30Hz<br/><br/> | 2530 fps<br/><br/><br/>1.5 ms @ 30Hz<br/><br/> | 2140 fps<br/><br/><br/>1.9 ms @ 30Hz<br/><br/> | 3500 fps<br/><br/><br/>0.44 ms @ 30Hz<br/><br/> |
| Depth Segmentation Node<br/><br/><br/><br/>                | 576p<br/><br/><br/><br/>      | 41.4 fps<br/><br/><br/>80 ms @ 30Hz<br/><br/>  | 28.1 fps<br/><br/><br/>98 ms @ 30Hz<br/><br/>  | –<br/><br/><br/><br/>                          | 105 fps<br/><br/><br/>25 ms @ 30Hz<br/><br/>    |
| FoundationPose Pose Estimation Node<br/><br/><br/><br/>    | 720p<br/><br/><br/><br/>      | 1.54 fps<br/><br/><br/>780 ms @ 30Hz<br/><br/> | –<br/><br/><br/><br/>                          | –<br/><br/><br/><br/>                          | 9.56 fps<br/><br/><br/>110 ms @ 30Hz<br/><br/>  |
| DNN Stereo Disparity Node<br/><br/><br/>Full<br/><br/>     | 576p<br/><br/><br/><br/>      | 72.5 fps<br/><br/><br/>17 ms @ 30Hz<br/><br/>  | 42.1 fps<br/><br/><br/>26 ms @ 30Hz<br/><br/>  | –<br/><br/><br/><br/>                          | 350 fps<br/><br/><br/>2.1 ms @ 30Hz<br/><br/>   |
| DNN Stereo Disparity Node<br/><br/><br/>Light<br/><br/>    | 288p<br/><br/><br/><br/>      | 304 fps<br/><br/><br/>5.9 ms @ 30Hz<br/><br/>  | 143 fps<br/><br/><br/>9.6 ms @ 30Hz<br/><br/>  | –<br/><br/><br/><br/>                          | 350 fps<br/><br/><br/>1.6 ms @ 30Hz<br/><br/>   |
| Stereo Disparity Node<br/><br/><br/><br/>                  | 1080p<br/><br/><br/><br/>     | 118 fps<br/><br/><br/>11 ms @ 30Hz<br/><br/>   | 78.1 fps<br/><br/><br/>14 ms @ 30Hz<br/><br/>  | 83.8 fps<br/><br/><br/>13 ms @ 30Hz<br/><br/>  | 943 fps<br/><br/><br/>1.6 ms @ 30Hz<br/><br/>   |
| Rectify Node<br/><br/><br/><br/>                           | 1080p<br/><br/><br/><br/>     | 800 fps<br/><br/><br/>2.8 ms @ 30Hz<br/><br/>  | 572 fps<br/><br/><br/>3.3 ms @ 30Hz<br/><br/>  | 595 fps<br/><br/><br/>3.8 ms @ 30Hz<br/><br/>  | 2500 fps<br/><br/><br/>0.57 ms @ 30Hz<br/><br/> |
| TensorRT Node<br/><br/><br/>DOPE<br/><br/>                 | VGA<br/><br/><br/><br/>       | 30.8 fps<br/><br/><br/>37 ms @ 30Hz<br/><br/>  | 15.5 fps<br/><br/><br/>55 ms @ 30Hz<br/><br/>  | 20.8 fps<br/><br/><br/>51 ms @ 30Hz<br/><br/>  | 298 fps<br/><br/><br/>5.3 ms @ 30Hz<br/><br/>   |
| Triton Node<br/><br/><br/>DOPE<br/><br/>                   | VGA<br/><br/><br/><br/>       | 31.2 fps<br/><br/><br/>340 ms @ 30Hz<br/><br/> | 15.5 fps<br/><br/><br/>55 ms @ 30Hz<br/><br/>  | 22.2 fps<br/><br/><br/>490 ms @ 30Hz<br/><br/> | 277 fps<br/><br/><br/>4.7 ms @ 30Hz<br/><br/>   |
| TensorRT Node<br/><br/><br/>PeopleSemSegNet<br/><br/>      | 544p<br/><br/><br/><br/>      | 489 fps<br/><br/><br/>4.6 ms @ 30Hz<br/><br/>  | 258 fps<br/><br/><br/>7.1 ms @ 30Hz<br/><br/>  | 269 fps<br/><br/><br/>6.2 ms @ 30Hz<br/><br/>  | 619 fps<br/><br/><br/>2.2 ms @ 30Hz<br/><br/>   |
| Triton Node<br/><br/><br/>PeopleSemSegNet<br/><br/>        | 544p<br/><br/><br/><br/>      | 216 fps<br/><br/><br/>5.5 ms @ 30Hz<br/><br/>  | 143 fps<br/><br/><br/>8.2 ms @ 30Hz<br/><br/>  | –<br/><br/><br/><br/>                          | 585 fps<br/><br/><br/>2.5 ms @ 30Hz<br/><br/>   |
| DNN Image Encoder Node<br/><br/><br/><br/>                 | VGA<br/><br/><br/><br/>       | 339 fps<br/><br/><br/>13 ms @ 30Hz<br/><br/>   | 375 fps<br/><br/><br/>12 ms @ 30Hz<br/><br/>   | –<br/><br/><br/><br/>                          | 480 fps<br/><br/><br/>6.0 ms @ 30Hz<br/><br/>   |
| Occupancy Grid Localizer Node<br/><br/><br/><br/>          | ~50 sq. m<br/><br/><br/><br/> | 19.6 fps<br/><br/><br/>57 ms @ 30Hz<br/><br/>  | 8.36 fps<br/><br/><br/>130 ms @ 30Hz<br/><br/> | 9.02 fps<br/><br/><br/>120 ms @ 30Hz<br/><br/> | 50.1 fps<br/><br/><br/>8.5 ms @ 30Hz<br/><br/>  |
| H.264 Decoder Node<br/><br/><br/><br/>                     | 1080p<br/><br/><br/><br/>     | 188 fps<br/><br/><br/>7.3 ms @ 30Hz<br/><br/>  | –<br/><br/><br/><br/>                          | –<br/><br/><br/><br/>                          | 596 fps<br/><br/><br/>2.6 ms @ 30Hz<br/><br/>   |
| H.264 Encoder Node<br/><br/><br/>I-frame Support<br/><br/> | 1080p<br/><br/><br/><br/>     | 402 fps<br/><br/><br/>12 ms @ 30Hz<br/><br/>   | –<br/><br/><br/><br/>                          | –<br/><br/><br/><br/>                          | 412 fps<br/><br/><br/>3.2 ms @ 30Hz<br/><br/>   |
| H.264 Encoder Node<br/><br/><br/>P-frame Support<br/><br/> | 1080p<br/><br/><br/><br/>     | 465 fps<br/><br/><br/>11 ms @ 30Hz<br/><br/>   | –<br/><br/><br/><br/>                          | –<br/><br/><br/><br/>                          | 596 fps<br/><br/><br/>2.0 ms @ 30Hz<br/><br/>   |
| Nvblox Node<br/><br/><br/><br/>                            | –<br/><br/><br/><br/>         | 4.94 fps<br/><br/><br/>34.0 ms<br/><br/>       | 4.94 fps<br/><br/><br/>155 ms<br/><br/>        | 4.93 fps<br/><br/><br/>87.4 ms<br/><br/>       | 4.94 fps<br/><br/><br/>200 ms<br/><br/>         |

| Graph<br/><br/>                                                       | Input Size<br/><br/>      | AGX Orin<br/><br/>                             | Orin NX<br/><br/>                              | Orin Nano Super 8GB<br/><br/>                  | x86_64 w/ RTX 4090<br/><br/>                  |
|-----------------------------------------------------------------------|---------------------------|------------------------------------------------|------------------------------------------------|------------------------------------------------|-----------------------------------------------|
| AprilTag Graph<br/><br/><br/><br/>                                    | 720p<br/><br/><br/><br/>  | 178 fps<br/><br/><br/>9.1 ms @ 30Hz<br/><br/>  | 111 fps<br/><br/><br/>11 ms @ 30Hz<br/><br/>   | 120 fps<br/><br/><br/>11 ms @ 30Hz<br/><br/>   | 596 fps<br/><br/><br/>1.4 ms @ 30Hz<br/><br/> |
| Freespace Segmentation Graph<br/><br/><br/><br/>                      | 576p<br/><br/><br/><br/>  | 40.3 fps<br/><br/><br/>79 ms @ 30Hz<br/><br/>  | 27.6 fps<br/><br/><br/>98 ms @ 30Hz<br/><br/>  | 31.8 fps<br/><br/><br/>55 ms @ 30Hz<br/><br/>  | 102 fps<br/><br/><br/>30 ms @ 30Hz<br/><br/>  |
| Centerpose Pose Estimation Graph<br/><br/><br/><br/>                  | VGA<br/><br/><br/><br/>   | 44.8 fps<br/><br/><br/>43 ms @ 30Hz<br/><br/>  | 29.0 fps<br/><br/><br/>51 ms @ 30Hz<br/><br/>  | 29.8 fps<br/><br/><br/>50 ms @ 30Hz<br/><br/>  | 50.2 fps<br/><br/><br/>14 ms @ 30Hz<br/><br/> |
| DOPE Pose Estimation Graph<br/><br/><br/><br/>                        | VGA<br/><br/><br/><br/>   | 27.3 fps<br/><br/><br/>54 ms @ 30Hz<br/><br/>  | 15.2 fps<br/><br/><br/>73 ms @ 30Hz<br/><br/>  | –<br/><br/><br/><br/>                          | 186 fps<br/><br/><br/>12 ms @ 30Hz<br/><br/>  |
| DNN Stereo Disparity Graph<br/><br/><br/>Full<br/><br/>               | 576p<br/><br/><br/><br/>  | 89.8 fps<br/><br/><br/>19 ms @ 30Hz<br/><br/>  | 35.2 fps<br/><br/><br/>34 ms @ 30Hz<br/><br/>  | –<br/><br/><br/><br/>                          | 350 fps<br/><br/><br/>5.8 ms @ 30Hz<br/><br/> |
| DNN Stereo Disparity Graph<br/><br/><br/>Light<br/><br/>              | 288p<br/><br/><br/><br/>  | 184 fps<br/><br/><br/>14 ms @ 30Hz<br/><br/>   | 128 fps<br/><br/><br/>14 ms @ 30Hz<br/><br/>   | –<br/><br/><br/><br/>                          | 350 fps<br/><br/><br/>5.2 ms @ 30Hz<br/><br/> |
| Stereo Disparity Graph<br/><br/><br/><br/>                            | 1080p<br/><br/><br/><br/> | 111 fps<br/><br/><br/>15 ms @ 30Hz<br/><br/>   | 72.2 fps<br/><br/><br/>18 ms @ 30Hz<br/><br/>  | 77.4 fps<br/><br/><br/>18 ms @ 30Hz<br/><br/>  | 692 fps<br/><br/><br/>4.6 ms @ 30Hz<br/><br/> |
| DetectNet Object Detection Graph<br/><br/><br/><br/>                  | 544p<br/><br/><br/><br/>  | 55.4 fps<br/><br/><br/>37 ms @ 30Hz<br/><br/>  | 25.7 fps<br/><br/><br/>45 ms @ 30Hz<br/><br/>  | 33.0 fps<br/><br/><br/>43 ms @ 30Hz<br/><br/>  | 262 fps<br/><br/><br/>11 ms @ 30Hz<br/><br/>  |
| RT-DETR Object Detection Graph<br/><br/><br/>SyntheticaDETR<br/><br/> | 720p<br/><br/><br/><br/>  | 56.5 fps<br/><br/><br/>29 ms @ 30Hz<br/><br/>  | 33.3 fps<br/><br/><br/>40 ms @ 30Hz<br/><br/>  | 37.3 fps<br/><br/><br/>37 ms @ 30Hz<br/><br/>  | 450 fps<br/><br/><br/>5.5 ms @ 30Hz<br/><br/> |
| TensorRT Graph<br/><br/><br/>PeopleSemSegNet<br/><br/>                | 544p<br/><br/><br/><br/>  | 436 fps<br/><br/><br/>10 ms @ 30Hz<br/><br/>   | 212 fps<br/><br/><br/>13 ms @ 30Hz<br/><br/>   | 224 fps<br/><br/><br/>13 ms @ 30Hz<br/><br/>   | 587 fps<br/><br/><br/>3.7 ms @ 30Hz<br/><br/> |
| SAM Image Segmentation Graph<br/><br/><br/>Full SAM<br/><br/>         | 720p<br/><br/><br/><br/>  | 2.22 fps<br/><br/><br/>390 ms @ 30Hz<br/><br/> | –<br/><br/><br/><br/>                          | –<br/><br/><br/><br/>                          | 14.6 fps<br/><br/><br/>74 ms @ 30Hz<br/><br/> |
| SAM Image Segmentation Graph<br/><br/><br/>Mobile SAM<br/><br/>       | 720p<br/><br/><br/><br/>  | 8.40 fps<br/><br/><br/>120 ms @ 30Hz<br/><br/> | 2.22 fps<br/><br/><br/>240 ms @ 30Hz<br/><br/> | 2.22 fps<br/><br/><br/>230 ms @ 30Hz<br/><br/> | 62.5 fps<br/><br/><br/>22 ms @ 30Hz<br/><br/> |

| Live Graph<br/><br/>                                                                                                        | Input Size<br/><br/>                | Nova Carter<br/><br/>                                                                                       |
|-----------------------------------------------------------------------------------------------------------------------------|-------------------------------------|-------------------------------------------------------------------------------------------------------------|
| Data Recorder Live Graph<br/><br/><br/>4 Hawk Cameras<br/><br/>                                                             | 1200p<br/><br/><br/><br/>           | 22.4 fps (per stream avg)<br/><br/><br/>0 dropped frames (avg)<br/><br/>                                    |
| Multicam Visual SLAM Live Graph<br/><br/><br/>4 Hawk Cameras<br/><br/>                                                      | 1200p<br/><br/><br/><br/>           | 30.1 fps<br/><br/><br/><br/>                                                                                |
| DNN Stereo Disparity Live Graph<br/><br/><br/>3 Hawk Cameras<br/><br/><br/>1x Full ESS and 2x Throttled Light ESS<br/><br/> | 1200p<br/><br/><br/><br/><br/><br/> | Full: 30.2 fps<br/><br/><br/>Light: 15.2 fps (avg)<br/><br/><br/><br/>                                      |
| Perceptor Graph<br/><br/><br/>3 Hawk Cameras<br/><br/><br/><br/>                                                            | 1200p<br/><br/><br/><br/><br/><br/> | Nvblox ESDF: 9.45 fps<br/><br/><br/>Nvblox Mesh: 2.63 fps<br/><br/><br/>Visual Odometry: 30.0 fps<br/><br/> |
