:orphan:
:nosearch:

===========
|repo_name|
===========

NVIDIA Isaac Transport for ROS package for hardware-acceleration friendly movement of messages.

.. figure:: :ir_lfs:`<resources/isaac_ros_docs/repositories_and_packages/isaac_ros_nitros/image5-1.gif>`
    :width: 600px
    :align: center

Overview
--------

**NITROS is deprecated.** Isaac ROS nodes now use ROS 2 messages with ``rosidl::Buffer`` fields and
the CUDA buffer backend, which are native ROS 2 Lyrical features. NITROS type adaptation and
negotiation, Managed NITROS, CUDA with NITROS, PyNITROS, and the NITROS Bridge APIs will be removed
in a future Isaac ROS release. Node-level compatibility is maintained, but applications that call
NITROS APIs directly require source-level migration. Refer to
:doc:`From NITROS to rosidl::Buffer </concepts/rosidl_buffer/nitros_migration>` for the migration
guide, and :doc:`rosidl::Buffer and Buffer Backends </concepts/rosidl_buffer/index>` for the
replacement architecture.

`Isaac ROS NITROS <https://github.com/NVIDIA-ISAAC-ROS/isaac_ros_nitros>`_ now contains the vendor
packages that distribute NVIDIA's precompiled SDKs to other Isaac ROS repositories, along with the
remaining NITROS Bridge converter.

-----------------------------------------------------------------------------------------------------------------------------

Documentation
-------------

Please visit the `Isaac ROS Documentation <https://nvidia-isaac-ros.github.io>`_ to learn how to use
this repository.

-----------------------------------------------------------------------------------------------------------------------------

Packages
--------

* ``cuapriltags_vendor``: Vendor package for the precompiled NVIDIA cuAprilTags SDK.
* ``cumotion_vendor``: Vendor package for the precompiled NVIDIA cuMotion SDK.
* ``cuvslam_vendor``: Vendor package for the precompiled NVIDIA cuVSLAM SDK.
* ``isaac_ros_nitros_bridge_ros2``: Converter between NITROS bridge messages and ROS 2 messages.

Latest
------

.. latest_update::

    .. list-table::
       :header-rows: 1

       * - Date
         - Changes
       * - :ir_release_date_iso:`<5.0.0>`
         - Deprecated NITROS in favor of ``rosidl::Buffer`` and the CUDA buffer backend

.. |repo_name| replace:: Isaac ROS NITROS
