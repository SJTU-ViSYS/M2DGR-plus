# M2DGR-plus
extension and update of M2DGR: a Multi-modal and Multi-scenario SLAM Dataset for Ground Robots 

## First Author: [Jie Yin](https://github.com/sjtuyinjie?tab=repositories)
<div align=center>
<img src=https://github.com/sjtuyinjie/M2DGR-plus/tree/main/fig/car2.jpg" width="800px">

</div>
<p align="center">Figure 1. Sample Images</p>




## NOTICE
### We strongly recommend that the newly proposed SLAM algorithm be tested on our data, because our data has following features:
1. A  rich pool of sensory information including vision, lidar, IMU, GNSS,event, thermal-infrared images and so on
2. Various scenarios in real-world environments including lifts, streets, rooms, halls and so on.
3. Our dataset brings great challenge to existing SLAM algorithms including LIO-SAM and ORB-SLAM3. If your proposed algorihm outperforms SOTA systems on M2DGR, your paper will be much more convincing and valuable.







## 1.LICENSE
This work is licensed under MIT license. International License and is provided for academic purpose. If you are interested in our project for commercial purposes, please contact us on 1195391308@qq.com for further communication. 

If you face any problem when using this dataset, feel free to propose an issue. And if you find our dataset helpful in your research, simply give this project a 
. 

The paper has been accepted by both [RA-L](https://www.ieee-ras.org/publications/ra-l/) and [ICRA 2022](https://icra2022.org/). A preprint version of the paper in [Arxiv](https://arxiv.org/abs/2112.13659) and [IEEE RA-L](https://ieeexplore.ieee.org/document/9664374).If you use M2DGR in an academic work, please cite:
~~~
@ARTICLE{9664374,
  author={Yin, Jie and Li, Ang and Li, Tao and Yu, Wenxian and Zou, Danping},
  journal={IEEE Robotics and Automation Letters}, 
  title={M2DGR: A Multi-sensor and Multi-scenario SLAM Dataset for Ground Robots}, 
  year={2021},
  volume={},
  number={},
  pages={1-1},
  doi={10.1109/LRA.2021.3138527}}
~~~



## 2.SENSOR SETUP
### 2.1 Acquisition Platform
Physical drawings and schematics of the ground robot is given below. The unit of the figures is centimeter.

<div align=center>
<img src="https://github.com/sjtuyinjie/mypics/blob/main/newcar4.png" width="800px">
</div>

<p align="left">Figure 2. The GAEA Ground Robot Equipped with a Full Sensor Suite.The directions of the sensors are marked in different colors,red for X,green for Y and blue for Z.</p>









### 2.2 Sensor parameters

All the sensors and track devices and their most important parameters are listed as below:

* **LIDAR** Velodyne VLP-32C, 360 Horizontal Field of View (FOV),-30 to +10 vertical FOV,10Hz,Max Range 200 m,Range Resolution 3 cm, Horizontal Angular Resolution 0.2°.  

* **RGB Camera** FLIR Pointgrey CM3-U3-13Y3C-CS,fish-eye lens,1280*1024,190 HFOV,190 V-FOV, 15 Hz  
* **GNSS** Ublox M8T, GPS/BeiDou, 1Hz  
* **Infrared Camera**,PLUG 617,640*512,90.2 H-FOV,70.6 V-FOV,25Hz;  
* **V-I Sensor**,Realsense d435i,RGB/Depth 640*480,69H-FOV,42.5V-FOV,15Hz;IMU 6-axix, 200Hz  
* **Event Camera** Inivation DVXplorer, 640*480,15Hz;  
* **IMU**,Handsfree A9,9-axis,150Hz;  
* **GNSS-IMU** Xsens Mti 680G. GNSS-RTK,localization precision 2cm,100Hz;IMU 9-axis,100 Hz;  
* **Laser Scanner** Leica MS60, localization 1mm+1.5ppm  
* **Motion-capture System** Vicon Vero 2.2, localization accuracy 1mm, 50 Hz;

The rostopics of our rosbag sequences are listed as follows:

* LIDAR: `/velodyne_points` 

* RGB Camera: 
`/camera/left/image_raw/compressed `,  
`/camera/right/image_raw/compressed `,  
`/camera/third/image_raw/compressed `,  
`/camera/fourth/image_raw/compressed `,  
`/camera/fifth/image_raw/compressed `,  
`/camera/sixth/image_raw/compressed `,  
`/camera/head/image_raw/compressed `  
* GNSS Ublox M8T:  
`/ublox/aidalm `,  
`/ublox/aideph `,  
`/ublox/fix `,  
`/ublox/fix_velocity `,  
`/ublox/monhw `,  
`/ublox/navclock `,  
`/ublox/navpvt `,  
`/ublox/navsat `,  
`/ublox/navstatus `,  
`/ublox/rxmraw `  


* Infrared Camera:`/thermal_image_raw ` 
* V-I Sensor:  
`/camera/color/image_raw/compressed `,  
`/camera/imu`
* Event Camera:  
`/dvs/events`,  
`/dvs_rendering/compressed`
* IMU: `/handsfree/imu `
 

## 3.DATASET SEQUENCES


**We make public ALL THE SEQUENCES with their GT now.**

<div align=center>

<img src="https://github.com/sjtuyinjie/mypics/blob/main/dynamic.gif" width="400px">
</div>

<p align="left">Figure 3. A sample video with fish-eye image(both forward-looking and sky-pointing),perspective image,thermal-infrared image,event image and lidar odometry</p>


An overview of M2DGR is given in the table below:
Scenario|Street|Circle|Gate|Walk|Hall|Door|Lift|Room|Roomdark|TOTAL
--|:--|:--:|--:|--:|--:|--:|--:|--:|--:|--:
Number | 10|2|3|1|5|2|4|3|6|36
Size/GB|590.7|50.6| 65.9|21.5| 117.4 |46.0|112.1|45.3|171.1|1220.6
Duration/s |7958 | 478| 782 |291 |1226|588|1224|275|866|13688
Dist/m |7727.72| 618.03| 248.40|263.17|845.15|200.14|266.27|144.13|395.66|10708.67
Ground Truth  |RTK/INS |RTK/INS |RTK/INS |RTK/INS |Leica |Leica |Leica |Mocap|Mocap| ---



### 3.1 Outdoors

<div align=center>
<img src="https://github.com/sjtuyinjie/mypics/blob/main/forgithub/outdoor.png" width="400px">
<p align="center">Figure 4. Outdoor Sequences:all trajectories are mapped in different colors.</p>
  


Sequence Name|Collection Date|Total Size|Duration|Features|Rosbag|GT
--|:--|:--:|--:|--:|--:|--:
gate_01|2021-07-31|16.4g|172s|dark,around gate|[Rosbag](https://sjtueducn-my.sharepoint.com/:u:/g/personal/594666_sjtu_edu_cn/ET3mU1rvdTpEl8VYvC25q7YB5pmPQlwru0jBbQ9iu0oAMA?e=LrKUpJ)|[GT](https://sjtueducn-my.sharepoint.com/:t:/g/personal/594666_sjtu_edu_cn/EfipLVtlRChHvwklkDPylPgBSIQry0_JdfqH-6DaxWCaNA?e=idVsY4)
gate_02|2021-07-31|27.3g|327s|dark,loop back|[Rosbag](https://sjtueducn-my.sharepoint.com/:u:/g/personal/594666_sjtu_edu_cn/EY7fHSh4NnxBvemze1JS8TEBy5beLh_xlJ6mdi2IYmeY9w?e=xIcvDe)|[GT](https://sjtueducn-my.sharepoint.com/:t:/g/personal/594666_sjtu_edu_cn/ETaXuADPMrNKlFn6pI9aqeoBmcgHr86fIsvDBB6cSaTBLA?e=gzaHPW)
gate_03|2021-08-04|21.9g|283s|day|[Rosbag](https://sjtueducn-my.sharepoint.com/:u:/g/personal/594666_sjtu_edu_cn/EUthdjvVIVdFmFxR82jzVqUBQTpsfvvb26pYtb0yj-_hlw?e=6MWwmJ)|[GT](https://sjtueducn-my.sharepoint.com/:t:/g/personal/594666_sjtu_edu_cn/ETj90pEu4PBDpYIoI0nWEAMBiWU68VXMXpU7MKwWnpdXxA?e=1KLdX3)


Sequence Name|Collection Date|Total Size|Duration|Features|Rosbag|GT
--|:--|:--:|--:|--:|--:|--:
Circle_01|2021-08-03|23.3g|234s|Circle|[Rosbag](https://sjtueducn-my.sharepoint.com/:u:/g/personal/594666_sjtu_edu_cn/EUVwex_LapBFrWV4ZtXocoYBE29aoQkPVdwWGhSFcioEtQ?e=YRRV9L)|[GT](https://sjtueducn-my.sharepoint.com/:t:/g/personal/594666_sjtu_edu_cn/EUlLxD27cGFArKGnpwkGrgEBr9FVGaSojLGVhJSNKaLLqQ?e=Bkptlj)
Circle_02|2021-08-07|27.3g|244s|Circle|[Rosbag](https://sjtueducn-my.sharepoint.com/:u:/g/personal/594666_sjtu_edu_cn/EeVG96IFCfxDlDLH8xefa3EBEMjCm4_8__V8JZ4ivMGoww?e=FVgjhB)|[GT](https://sjtueducn-my.sharepoint.com/:t:/g/personal/594666_sjtu_edu_cn/EfVe45nxzepBsZSFp-yzqRMBpg_PYdZVS1L3FOYqA8WdcA?e=5BcVrA)

Sequence Name|Collection Date|Total Size|Duration|Features|Rosbag|GT
--|:--|:--:|--:|--:|--:|--:
street_01|2021-08-06|75.8g|1028s|street and buildings,night,zigzag,long-term|[Rosbag](https://sjtueducn-my.sharepoint.com/:u:/g/personal/594666_sjtu_edu_cn/EavjoipiTMRIjUvmodSGGsoB8rg0_pOkp6pqDScr8h4zvQ?e=OjtWkL)|[GT](https://sjtueducn-my.sharepoint.com/:t:/g/personal/594666_sjtu_edu_cn/ES2todVoF5VGmLo8WwKxcRYB4nyw6-zNR86I4BxAPnv_wg?e=ZtalWi)
street_02|2021-08-03|83.2g|1227s|day,long-term|[Rosbag](https://sjtueducn-my.sharepoint.com/:u:/g/personal/594666_sjtu_edu_cn/EQj5QBBHONpFj-hlvXOQBr0BM0NP9nhNuw-X9UtwOMMuNw?e=ZrxudN)|[GT](https://sjtueducn-my.sharepoint.com/:t:/g/personal/594666_sjtu_edu_cn/EfOmlQh5BvJAorfLiI7orFgBJRR94rEjU163lvWgLAlA2Q?e=Z7mAcd)
street_03|2021-08-06|21.3g|354s|night,back and fourth,full speed|[Rosbag](https://sjtueducn-my.sharepoint.com/:u:/g/personal/594666_sjtu_edu_cn/EQU95R6TOAZIkaoFuHJLU-kB9qJEIDeEsECB3Gjc9Nmx8A?e=J1AKwY)|[GT](https://sjtueducn-my.sharepoint.com/:t:/g/personal/594666_sjtu_edu_cn/EQ4l4FNo69dPjWco2Pk8Zy4BuPWTFUGQHOv2KdO4MbTv2g?e=ZZf9ok)
street_04|2021-08-03|48.7g|858s|night,around lawn,loop back|[Rosbag](https://sjtueducn-my.sharepoint.com/:u:/g/personal/594666_sjtu_edu_cn/Ea72BxSXFYhDrp_FGNlJ2ukBx3CQSlv0Wah5nFUJtIntrw?e=4rwi7H)|[GT](https://sjtueducn-my.sharepoint.com/:t:/g/personal/594666_sjtu_edu_cn/EadWM6nH74hBusYGre63WRcB0fM_ynkFJu2ibpSWtr5P-w?e=K7FJzV)
street_05|2021-08-04|27.4g|469s|night,staight line|[Rosbag](https://sjtueducn-my.sharepoint.com/:u:/g/personal/594666_sjtu_edu_cn/EUClV6vL2zhAicOwwO1WiroBK-fPzTu8K8NtMfgdMAxIqw?e=r50mNo)|[GT](https://sjtueducn-my.sharepoint.com/:t:/g/personal/594666_sjtu_edu_cn/EYrYgnp716xKo0-wcyVX2Z4BTnbbZuQrwYgaJIzREs923Q?e=gcGt7I)
street_06|2021-08-04|35.0g|494s|night,one turn|[Rosbag](https://sjtueducn-my.sharepoint.com/:u:/g/personal/594666_sjtu_edu_cn/EZ4HAXvNQXRCgRKSLpE3yX0BsM24PkXwAd-NopVc7ueNzA?e=oUw91h)|[GT](https://sjtueducn-my.sharepoint.com/:t:/g/personal/594666_sjtu_edu_cn/ETFW7vEEmp9JvJiVZef0wooBN9r7mt8jj1WmVdzzNiIp7A?e=67FHW4)
street_07|2021-08-06|77.2g|929s|dawn,zigzag,sharp turns|[Rosbag](https://sjtueducn-my.sharepoint.com/:u:/g/personal/594666_sjtu_edu_cn/EfScTXrKjAdGg1w9xZ-yZgIBWu9gIswakQToN9guMPatQQ?e=YvjAUg)|[GT](https://sjtueducn-my.sharepoint.com/:t:/g/personal/594666_sjtu_edu_cn/EefcYHlgA-RJiTl1jZl9r4ABr2YcrmTX7InDG_W6cHHrFQ?e=NQB203)
street_08|2021-08-06|31.2g|491s|night,loop back,zigzag|[Rosbag](https://sjtueducn-my.sharepoint.com/:u:/g/personal/594666_sjtu_edu_cn/EdgojePkM2ZNszS6JM80D90B-2q68wWQ1vZijzeaH-IQrw?e=iwVIiX)|[GT](https://sjtueducn-my.sharepoint.com/:t:/g/personal/594666_sjtu_edu_cn/Ecv4IRMW5rBPn22pxW-xEYQBGinyVxrP6htbpS3HGnOpiA?e=TJXzJz)
street_09|2021-08-07|83.2g|907s|day,zigzag|[Rosbag](https://sjtueducn-my.sharepoint.com/:u:/g/personal/594666_sjtu_edu_cn/Ee5hiGAdou5OvPI_xeOHBh4BtRntB8-5qLXqCuXhXNB-Yw?e=wEkptw)|[GT](https://sjtueducn-my.sharepoint.com/:t:/g/personal/594666_sjtu_edu_cn/EXb__m3Z0wdLkv_ybnXDOlUBVV41XM8_G1yHNO9oZKJE1w?e=xaZBGo)
street_010|2021-08-07|86.2g|910s|day,zigzag|[Rosbag](https://sjtueducn-my.sharepoint.com/:u:/g/personal/594666_sjtu_edu_cn/EfcpNeq8p-NLp7kCkaz0WugBf1c9TGtDbVBDy2QHF5rPvQ?e=lpnnAJ)|[GT](https://sjtueducn-my.sharepoint.com/:t:/g/personal/594666_sjtu_edu_cn/ETWkYfjfaP5PuMUJmbHsLS0Btby-9W7V9n4bfob9DGP-pw?e=iOGOBW)
walk_01|2021-08-04|21.5g|291s|day,back and fourth|[Rosbag](https://sjtueducn-my.sharepoint.com/:u:/g/personal/594666_sjtu_edu_cn/EZn2REI4E2BLurJXTaTDpYcBIMOoO3CKh9dsPbcMeMYTKg?e=R4cSKy)|[GT](https://sjtueducn-my.sharepoint.com/:t:/g/personal/594666_sjtu_edu_cn/EfNamQlwIeRGl0-gjktD1UEBMpXSWScVLL7VL1WUPiInhw?e=zmbJNp)
</div>




## 4. CONFIGURERATION FILES
For convenience of evaluation, we provide configuration files of some well-known SLAM systems as below:

[A-LOAM](https://github.com/sjtuyinjie/toolkit/blob/main/config_files/aloam/aloam_velodyne_HDL_32.launch),



## 5.DEVELOPMENT TOOLKITS
### 5.1 Extracting Images
* For rosbag users, first make image view
~~~
roscd image_view
rosmake image_view
sudo apt-get install mjpegtools
~~~

open a terminal,type roscore.And then open another,type
~~~
rosrun image_transport republish compressed in:=/camera/color/image_raw raw out:=/camera/color/image_raw respawn="true"
~~~
* For non-rosbag users,just take advantage of following script  [export_tum](https://github.com/sjtuyinjie/toolkit/blob/main/export_tum.py),[export_euroc](https://github.com/sjtuyinjie/toolkit/blob/main/export_euroc.py) and [get_csv](https://github.com/sjtuyinjie/toolkit/blob/main/img2csv.py) to get data in formats of Tum or EuRoC.

### 5.2 Evaluation
We use open-source tool [evo](https://github.com/MichaelGrupp/evo) for evalutation.
To install evo,type
~~~
pip install evo --upgrade --no-binary evo
~~~
To evaluate monocular visual SLAM,type
~~~
evo_ape tum street_07.txt your_result.txt -vaps
~~~
To evaluate LIDAR SLAM,type
~~~
evo_ape tum street_07.txt your_result.txt -vap
~~~
To test GNSS based methods,type
~~~
evo_ape tum street_07.txt your_result.txt -vp
~~~

### 5.3 Calibration
For camera intrinsics,visit [Ocamcalib](http://sites.google.com/site/scarabotix/ocamcalib-toolbox) for omnidirectional model.
visit [Vins-Fusion](https://github.com/HKUST-Aerial-Robotics/VINS-Fusion) for pinhole and MEI model.
use [Opencv](https://opencv.org/) for Kannala Brandt model

For IMU intrinsics,visit [Imu_utils](https://github.com/gaowenliang/imu_utils)

For extrinsics between cameras and IMU,visit [Kalibr](https://github.com/ethz-asl/kalibr)
For extrinsics between Lidar and IMU,visit [Lidar_IMU_Calib](https://github.com/APRIL-ZJU/lidar_IMU_calib) 
For extrinsics between cameras and Lidar, visit [Autoware](https://github.com/Autoware-AI/autoware.ai) 



