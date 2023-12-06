# Clothing Detection
# 服装検出
![img1](img/result.png)

本家のREADMEは[こちら](doc/README.md)

## How To Setup

```bash
$ cd ~/catkin_ws/src
$ git clone https://gitlab.com/TeamSOBITS/clothing_detection.git
$ cd clothing_detection
$ bash install.sh
```

## How To Use

```bash
$ roslaunch clothing_detection clothing_detect_ros.launch
```


### Publications:
 * /rosout [rosgraph_msgs/Log]
 * /clothing_detection/detect_result [sensor_msgs/Image]
 * /clothing_detection/clothes_num [std_msgs/UInt8]
 * /clothing_detection/clothes_rect [sobit_common_msg/BoundingBoxes]
 * /clothing_detection/clothes_name [sobit_common_msg/StringArray]

### Subscriptions:
 * /camera/rgb/image_raw [sensor_msgs/Image]
 * /clothing_detection/detect_ctrl [std_msgs/Bool]
 
 
### Weightsファイルについて
Githubに移行する際に,pushが100MBの制限を設けられたため,応急処置として新サーバに上げました
/Personal/49th/okuma/clothing_detection　の中にあります
git cloneした後,weightsファイルを/clothing_detection/yolo/weightsの中に移動して使用してください
