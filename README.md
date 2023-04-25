# Robot_Mounted_with_Aruco_Marker

This repository show how to mounted a aruco marker on a robot.


## Package.xml
you need to make the media file visable by gazebo_media, so put the following line in your package.xml (turtlebot3_descriptions/package.xml)
```
<depend>gazebo_ros</depend>
  <export>
    <gazebo_ros gazebo_media_path="${prefix}/media"/>
  </export >
```
## URDF or Xacro
Make the aruco marker image show on your robot, you need to add following line
```
  <gazebo reference="aruco_link">
    <material>aruco_fam4x4_1000_id25_sdf/Image</material>
  </gazebo>
```

Add the Aruco marker fixed above your robot. you can change the xyz to your desired position
```
  </link>
    <joint name="aruco_joint" type="fixed">
      <origin xyz="0 0 0" rpy="0 0 0"/>
      <parent link="base_link"/>
      <child link="aruco_link"/>
    </joint>
    <link name="aruco_link">
      <inertial>
            <mass value="0"/>
            <origin xyz="-0.019662 0.011643 0.5"/>
            <inertia
              ixx="0.01042" ixy="0.001177" ixz="-0.0008871"
              iyy="0.01045" iyz="0.0002226"
              izz="0.01817"/>
      </inertial>
      <visual>
        <origin xyz="0 0 0.4" rpy="0 0 0"/>
        <geometry>
          <box size="0.36 0.36 0"/>
        </geometry>
      </visual>
    </link>
```
## 
![Screenshot from 2023-03-02 20-20-39](https://user-images.githubusercontent.com/55338365/222607929-c03e0f9f-5a5e-4ba9-afb6-4604b660a917.png)
