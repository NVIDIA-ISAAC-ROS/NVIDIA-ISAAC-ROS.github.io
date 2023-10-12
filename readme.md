# Isaac ROS Image Segmentation

Hardware-accelerated, deep learned semantic image segmentation

![image](https://media.githubusercontent.com/media/NVIDIA-ISAAC-ROS/.github/main/resources/isaac_ros_docs/repositories_and_packages/isaac_ros_image_segmentation/isaac_ros_image_segmentation_example.png/)![image](https://media.githubusercontent.com/media/NVIDIA-ISAAC-ROS/.github/main/resources/isaac_ros_docs/repositories_and_packages/isaac_ros_image_segmentation/isaac_ros_image_segmentation_example_seg.png/)

## Overview

[Isaac ROS Image Segmentation](https://github.com/NVIDIA-ISAAC-ROS/isaac_ros_image_segmentation/blob/main/README.md) contains a ROS 2 package to produce semantic image segmentation.
`isaac_ros_unet` provides a method for classification of an input image at the pixel level.
Each pixel of the input image is predicted to belong to a set of defined classes.
Classification is performed with GPU acceleration running DNN inference on a U-NET architecture model.
The output prediction can be used by perception functions to understand where each
class is spatially in a 2D image or fuse with a corresponding depth location in a 3D scene.

A trained model based on
the [U-NET](https://en.wikipedia.org/wiki/U-Net) architecture is
required to produce a segmentation mask. Input images may need to be
cropped and resized to maintain the aspect ratio and match the input
resolution of the U-NET DNN; image resolution may be reduced to improve
DNN inference performance, which typically scales directly with the
number of pixels in the image.

Image segmentation provides more information and uses more compute than
object detection to produce classifications per pixel, whereas object
detection classifies a simpler bounding box rectangle in image
coordinates. Object detection is used to know if, and where spatially in
a 2D image, the object exists. On the other hand, image segmentation is used to know which
pixels belong to the class. One application is using the segmentation result, and fusing it with the corresponding depth
information in order to know an object location in a 3D scene.

## Isaac ROS NITROS Acceleration

This package is powered by [NVIDIA Isaac Transport for ROS (NITROS)](https://developer.nvidia.com/blog/improve-perception-performance-for-ros-2-applications-with-nvidia-isaac-transport-for-ros/), which leverages type adaptation and negotiation to optimize message formats and dramatically accelerate communication between participating nodes.

## Packages

* [`isaac_ros_unet`](nvidia-isaac-ros.github.io/repositories_and_packages/isaac_ros_image_segmentation/isaac_ros_unet/index.html)
  * [Quickstart](nvidia-isaac-ros.github.io/repositories_and_packages/isaac_ros_image_segmentation/isaac_ros_unet/index.html#quickstart)
  * [Try More Examples](nvidia-isaac-ros.github.io/repositories_and_packages/isaac_ros_image_segmentation/isaac_ros_unet/index.html#try-more-examples)
  * [API](nvidia-isaac-ros.github.io/repositories_and_packages/isaac_ros_image_segmentation/isaac_ros_unet/index.html#api)

## Latest

Update 2023-05-25: Performance improvements.

## DNN models

A U-NET model is required to use isaac_ros_unet.
[NGC](https://catalog.ngc.nvidia.com/models) provides pre-trained models for use in your robotics application.
NGC pre-trained models can be fine-tuned for your application using TAO used in the examples
on this page. [PeopleSemSegNet](https://catalog.ngc.nvidia.com/orgs/nvidia/teams/tao/models/peoplesemsegnet) provides a pre-trained model for best-in-class,
real-time people segmentation.
You can train your own U-NET architecture models or download pre-trained models
from one of the many model zoo’s available online for use with isaac_ros_unet.

Click [here](nvidia-isaac-ros.github.io/concepts/dnn_inference/model_preparation.html) for more information on how to use NGC models.

This package has been validated against the following NGC models:

| Model Name                                                                                                                                              | Use Case                                              |
|---------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------|
| [PeopleSemSegNet ShuffleSeg](https://catalog.ngc.nvidia.com/orgs/nvidia/teams/tao/models/peoplesemsegnet/files?version=deployable_shuffleseg_unet_v1.0) | Semantically segment people inference at a high speed |
| [PeopleSemSegNet](https://catalog.ngc.nvidia.com/orgs/nvidia/teams/tao/models/peoplesemsegnet/files?version=deployable_vanilla_unet_v2.0)               | Semantically segment people                           |

## Performance

| Sample Graph<br/><br/>                                                                                                                                               | Input Size<br/><br/>     | AGX Orin<br/><br/>                                                                                                                                             | Orin NX<br/><br/>                                                                                                                                             | Orin Nano 8GB<br/><br/>                                                                                                                                        | x86_64 w/ RTX 4060 Ti<br/><br/>                                                                                                                                  |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [TensorRT Graph](https://gitlab-master.nvidia.com/isaac_ros/isaac_ros_benchmark/-/blob/dev/scripts//isaac_ros_unet_graph.py)<br/><br/><br/>PeopleSemSegNet<br/><br/> | 544p<br/><br/><br/><br/> | [385 fps](https://gitlab-master.nvidia.com/isaac_ros/isaac_ros_benchmark/-/blob/dev/results/isaac_ros_unet_graph-agx_orin.json)<br/><br/><br/>6.9 ms<br/><br/> | [210 fps](https://gitlab-master.nvidia.com/isaac_ros/isaac_ros_benchmark/-/blob/dev/results/isaac_ros_unet_graph-orin_nx.json)<br/><br/><br/>8.3 ms<br/><br/> | [142 fps](https://gitlab-master.nvidia.com/isaac_ros/isaac_ros_benchmark/-/blob/dev/results/isaac_ros_unet_graph-orin_nano.json)<br/><br/><br/>13 ms<br/><br/> | [827 fps](https://gitlab-master.nvidia.com/isaac_ros/isaac_ros_benchmark/-/blob/dev/results/isaac_ros_unet_graph-nuc_4060ti.json)<br/><br/><br/>4.0 ms<br/><br/> |

## Supported Platforms

This package is designed and tested to be compatible with ROS 2 Humble running on [Jetson](https://developer.nvidia.com/embedded-computing) or an x86_64 system with an NVIDIA GPU.

#### NOTE
Versions of ROS 2 earlier than Humble are **not** supported. This package depends on specific ROS 2 implementation features that were only introduced beginning with the Humble release.

| Platform   | Hardware                                                                                                                                                                                            | Software                                                                                                      | Notes                                                                                                                                                                                   |
|------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Jetson     | [Jetson Orin](https://www.nvidia.com/en-us/autonomous-machines/embedded-systems/jetson-orin/) [Jetson Xavier](https://www.nvidia.com/en-us/autonomous-machines/embedded-systems/jetson-agx-xavier/) | [JetPack 5.1.1](https://developer.nvidia.com/embedded/jetpack)                                                | For best performance, ensure that [power settings](https://docs.nvidia.com/jetson/archives/r34.1/DeveloperGuide/text/SD/PlatformPowerAndPerformance.html) are configured appropriately. |
| x86_64     | NVIDIA GPU                                                                                                                                                                                          | [Ubuntu 20.04+](https://releases.ubuntu.com/20.04/) [CUDA 11.8+](https://developer.nvidia.com/cuda-downloads) |                                                                                                                                                                                         |

### Docker

To simplify development, we strongly recommend leveraging the Isaac ROS Dev Docker images by following [these steps](nvidia-isaac-ros.github.io/getting_started/dev_env_setup.html).
This will streamline your development environment setup with the correct versions of dependencies on both Jetson and x86_64 platforms.

#### NOTE
All Isaac ROS Quickstarts, tutorials, and examples have been designed with the Isaac ROS Docker images as a prerequisite.

### Customize your Dev Environment

To customize your development environment, reference [this guide](nvidia-isaac-ros.github.io/getting_started/customizing_dockerfiles.html).

## Troubleshooting

### Isaac ROS Troubleshooting

For solutions to problems with Isaac ROS, please check [here](nvidia-isaac-ros.github.io/troubleshooting/index.html).

### Deep Learning Troubleshooting

For solutions to problems with using DNN models, please check [here](nvidia-isaac-ros.github.io/troubleshooting/deep_learning.html).

## Updates

| Date       | Changes                                                                                                                                                                                                                                                                                                                              |
|------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 2023-05-25 | Performance improvements                                                                                                                                                                                                                                                                                                             |
| 2023-04-05 | Source available GXF extensions                                                                                                                                                                                                                                                                                                      |
| 2022-10-19 | Updated OSS licensing                                                                                                                                                                                                                                                                                                                |
| 2022-08-31 | Update to be compatible with JetPack 5.0.2                                                                                                                                                                                                                                                                                           |
| 2022-06-30 | Removed frame_id, queue_size and tensor_output_order parameter. Added network_output_type parameter (support for sigmoid and argmax output layers). Switched implementation to use NITROS. Removed support for odd sized images. Switched tutorial to use PeopleSemSegNet ShuffleSeg and moved unnecessary details to other READMEs. |
| 2021-11-15 | Isaac Sim HIL documentation update                                                                                                                                                                                                                                                                                                   |
| 2021-10-20 | Initial release                                                                                                                                                                                                                                                                                                                      |
