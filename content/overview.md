## 4D Metric Semantic Mapping of Orchards

<div style="text-align: justify">
we present a 4D spatio-temporal metric-semantic mapping method that fuses data from multiple sensors, including LiDAR, RGB camera, and IMU, to monitor the fruits in an orchard across their growth season, providing information such as fruit counts, sizes, and positions. We achieve a 3.1 percent error in total fruit count estimation for over 1,790 fruits across 60 apple trees, along with accurate size estimation results with a mean error of 1.1 cm. 
</div>


{{< youtube QujF8rruM74 >}}


<!-- ### Citation
Arxiv link to be added -->

### System Diagram

![demo](/4d-system-diagram.png)

<div style="text-align: justify">
System Diagram. Module 1: Our system takes in sensor data from the LiDAR, RGB camera, and Inertial Measurement Unit
(IMU) (green box). Module 2: Object detection and odometry (blue box). First, we use Faster-LIO, a LiDAR-inertial odometry (LIO)
algorithm, to estimate the pose of the sensors and obtain point clouds in the body frame. Meanwhile, we fine-tuned YOLO-v8, an instance
segmentation neural network, on the RGB images to detect and segment fruits. Module 3: LiDAR-RGB fusion for 3D metric-semantic
mapping (orange box). In this module, we track fruits using the Hungarian Assignment algorithm, with the cost function based on the
overlap between the reprojected 3D fruit point cloud and the detected fruit instance masks on the image plane. After fruits are associated,
we minimize the reprojection error of fruit centroids to optimize the fruit positions. Module 4: 4D data association (purple box). This
module takes in the outputs from the previous module across multiple time sessions. Specifically, the inputs of this module consist of
the optimized fruit 3D landmarks and the accumulated point clouds. It first runs the Iterative Closest Point (ICP) algorithm to estimate
the relative transformation between the point clouds of different time sessions and then uses it to transform fruit 3D landmarks into
a common reference frame. Hungarian Assignment algorithm, with a cost function based on the 3D Euclidean distance between fruit
landmarks, is used to associate fruits across multiple time sessions. Module 5: 4D metric-semantic map generation (cyan box). Using
the 4D data association, we can construct a 4D metric-semantic map, acquiring actionable information such as fruit counts, sizes, and
positions throughout the entire growth season.
</div>

### Acknowledgements

<div style="text-align: justify">
We gratefully acknowledge the support of the IoT4Ag Engineering
Research Center funded by the National Science Foundation (NSF) under
NSF Cooperative Agreement Number EEC-1941529, ARL DCIST CRA
W911NF-17-2-0181, NSF Grant CCR-2112665, NIFA grant 2022-67021-
36856, and NVIDIA. We thank Prof. Drew Wilkerson, and the owners of
Hands on Earth and Shaw Orchards for their support in data collection.
</div>
