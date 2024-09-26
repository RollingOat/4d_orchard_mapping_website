### File Structure

### Raw Data

<div style="text-align: justify">
Raw rosbags are kept in folders <em>Carlifornia/, Maryland/, Pennsylvania/</em>. Inside those folders, fruits of different kinds are kept seperately in its own folder. 

Each folder contains the following fruits:
* Carlifornia: pistachio 
* Maryland: apple, peach, cherry
* Pennsylvania: apple, pear

Each ros bag contains the following useful topics:
* /Odometry: nav_msgs/Odometry
* /ouster/imu_packets: ouster_ros/PacketMsg
* /ouster/lidar_packets: ouster_ros/PacketMsg
* /rsense/color/image_raw: sensor_msgs/Image
* /spinnaker/image_raw: sensor_msgs/Image

We also recorded GPS in our rosbag, but it has lower localization accuracy than the odometry
* /ublox/fix: sensor_msgs/NavSatFix
* /ublox/fix_velocity: geometry_msgs/TwistWithCovarianceStamped
</div>

#### How to get the point cloud?

You can run [faster-lio](https://github.com/gaoxiang12/faster-lio). Follow the link to compile faster-lio on your local machine. Change the 

### Images and Segmentation Labels

We labeled one season of peaches (June 11) and four seasons of apples (june 11, july 4th, july 19th, Aug 13th). We used [anylabeling](https://github.com/vietanhdev/anylabeling) as the labeling tool. Each labeled image has a corresponding json file. You can use the provided script to convert json file to yolo format. 

### Processing Scripts

Some useful image processing and file format conversion scripts.

### Yolov8 Models

In this folder, we put our trained yolov8-l models

### Ground Truth

In this folder, we provide the ground truths for fruit counts of one row of apples, sizes of fruits from our test data.
