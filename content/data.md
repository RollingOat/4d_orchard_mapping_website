We include the raw data in the format of rosbags here. We also release the groud truth on fruit counts and sizes as reported in the paper.


### File Structure

├── Carlifornia <br>
├── Maryland<br>
│   ├── apple<br>
│   ├── calibration<br>
│   ├── cherry<br>
│   └── peach<br>
├── Pennsylvania<br>
│   ├── apple<br>
│   ├── calibration<br>
│   └── pear<br>
├── ground_truth<br>
│   └── size_gt<br>
├── images_labels<br>
│   ├── 2024-05-24-10-45-08_apple<br>
│   ├── 2024-06-12-12-08-14_apple<br>
│   ├── 2024-07-04-10-15-00_apple<br>
│   ├── 2024-07-19-11-22-12_apple<br>
│   ├── 2024-08-13-12-08-14_apple<br>
│   └── june_11_peaches<br>
└── yolo_models<br>

### Raw Data

<div style="text-align: justify">
Raw rosbags are kept in folders <em>Carlifornia/, Maryland/, Pennsylvania/</em>. Inside those folders, fruits of different kinds are kept seperately in its own folder along with a calibration folder.  

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

**How to get the point cloud?**

1. install and compile [ouster-ros](https://github.com/ouster-lidar/ouster-ros).
2. install and compile [faster-lio](https://github.com/gaoxiang12/faster-lio). Use the provided launch file (mapping_ouster128_with_driver.launch), metadata files (ouster_metadata.json, ouster_metadata_UCMERCED.json), and config file (ouster128.yaml).

**How to calibrate on your own?**

Interested Users can do calibration using [kalibr](https://github.com/ethz-asl/kalibr). The kalibr reuqired config files (aprilgrid.yaml) can be found in Downloads. 

You can also go to the [git repo](https://github.com/RollingOat/4d-orchard-mapping-dataset) for more details on running faster-lio and kalibr. 

### Images and Segmentation Labels

We labeled one season of peaches (June 11) and four seasons of apples (june 11, july 4th, july 19th, Aug 13th). We used [anylabeling](https://github.com/vietanhdev/anylabeling) as the labeling tool. Each labeled image has a corresponding json file. You can use the provided script **PrepareImagesForTraining.py** to extract labelled images and its json files and convert those json files to yolo format. This script will also automatically seperate images and labels into train and validation for model training.

### Yolov8 Models

In this folder, we put our trained yolov8 models.

### Ground Truth

In this folder, we provide the ground truths for fruit counts of one row of apples from one season, sizes of fruits from our test data.

### Questions? 

Thank you for your interest. For any questions, you can open an issue in this [git repository](https://github.com/RollingOat/4d-orchard-mapping-dataset)
