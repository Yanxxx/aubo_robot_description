AUBO Robot Description (Modified)
A ROS/ROS2 package containing the URDF and simplified 3D models for the AUBO i3, i5, and i7 series collaborative robot arms.

This is a modified version of the official AUBO robot description package. Please use at your own risk.

About This Package
This package provides the robot description files (.urdf, .xacro, .stl) for the AUBO Robotics family of manipulators. It is intended to be used with motion planning libraries like MoveIt and for visualization in tools like RViz.

Key Modifications
The primary modification in this version is the simplification of the 3D model (mesh) files.

Original Models: High-polygon meshes, detailed for visual accuracy.

Modified Models: Low-polygon meshes, optimized for performance.

This simplification significantly improves computation efficiency for tasks like motion planning and collision detection, which can be critical for real-time applications.

Installation

Clone the repository into the src folder of your catkin or colcon workspace:

# For ROS1
cd ~/catkin_ws/src
git clone [https://github.com/your-username/aubo_description.git](https://github.com/your-username/aubo_description.git)

# For ROS2
cd ~/ros2_ws/src
git clone [https://github.com/your-username/aubo_description.git](https://github.com/your-username/aubo_description.git)

Build your workspace:

# For ROS1
cd ~/catkin_ws && catkin_make

# For ROS2
cd ~/ros2_ws && colcon build

Usage
You can load the robot model by including the aubo_upload.launch.py (ROS2) or aubo_i5_upload.launch (ROS1) file in your own launch files. This will load the robot_description parameter onto the ROS Parameter Server.

Example (ROS2 Launch File)
from launch import LaunchDescription
from launch.actions import IncludeLaunchDescription
from launch.launch_description_sources import PythonLaunchDescriptionSource
from ament_index_python.packages import get_package_share_directory

def generate_launch_description():
    aubo_description_launch = IncludeLaunchDescription(
        PythonLaunchDescriptionSource([
            get_package_share_directory('aubo_description'),
            '/launch/aubo_upload.launch.py'
        ])
    )

    return LaunchDescription([
        aubo_description_launch
        # ... your other nodes
    ])

Disclaimer
This is a modified version of the official software and is not endorsed or supported by AUBO Robotics. The changes to the 3D models may affect the accuracy of collision checking in simulation. The user assumes all risks associated with the use of this software.

License
This package is released under the BSD-3-Clause License. See the LICENSE file for more details.
