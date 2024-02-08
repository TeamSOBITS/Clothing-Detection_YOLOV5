<a name="readme-top"></a>

[JP](README.md) | [EN](template_readme_en.md)

[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Stargazers][stars-shield]][stars-url]
[![Issues][issues-shield]][issues-url]
<!-- [![License][license-shield]][license-url] -->

# Clothing Detection_YOLOv5

# 服装検出

<!-- レポジトリの概要 -->
## 概要

YOLOv5を用いて服装の検出を行います。

<!-- [![Product Name Screen Shot][product-screenshot]](https://example.com) -->
<!-- <img width="100%" src="https://raw.githubusercontent.com/ultralytics/assets/main/im/banner-yolo-vision-2023.png"></a> -->
<img width="100%" src="https://raw.githubusercontent.com/ultralytics/assets/main/yolov5/v70/splash.png"></a>

YOLOv5🚀は，ultralyticsによって公表されている物体検出パッケージです．
yolov5_rosは，YOLOv5をROS上で実行するROSパッケージです．
YOLOv5🚀の使用方法の詳細は<a href="https://docs.ultralytics.com/yolov5">YOLOv5 Docs</a>で確認することができます．

<p align="right">(<a href="#readme-top">上に戻る</a>)</p>

<!-- セットアップ -->
## 環境構築

### 環境条件

* OS: Ubuntu20.04
* ROS distribution: noetic
* Python: 3.8.10
* Pytorch: 1.13.1
* Package: sobit_common
### インストール方法

1. yolov5_rosをworkspace上にclone
   ```
   cd catkin_ws/src/
   git clone https://github.com/TeamSOBITS/yolov5_ros.git
   ```
2. sobit_commonのインストール
   ```
   cd catkin_ws/src/
   git clone https://github.com/TeamSOBITS/sobit_common.git
   ```
3. yolov5_ros/srcにyolov5の公式パッケージをインストール
   ```
   cd catkin_ws/src/
   git clone https://github.com/ultralytics/yolov5.git
   ```
4. 必要なpythonモジュールをインストール
   ```
   cd catkin_ws/src/yolov5_ros/src/yolov5
   python3 -m pip install --upgrade pip
   python3 -m pip install -r requirements.txt
   python3 -m pip uninstall utils
   ```
<p align="right">(<a href="#readme-top">上に戻る</a>)</p>

<!-- 実行・操作方法 -->
## 実行・操作方法

<!-- デモの実行方法やスクリーンショットがあるとわかりやすくなるでしょう -->
### 実行方法
* weightsファイルの準備
**weightsファイルはfolk先にあるデータセットを用いて学習を行ってください。
  ```
  weights_df2 : deepfashion2
  weights_modanet : modanet

  launch 38行　value="" : df2 or modanet 設定
  ```

* clothing-detection: clothing_detect.launchを実行します．
   ```
   roslaunch clothing-detection_YOLOV5 clothing_detect.launch
   ```
### 使用Topic
* 使用msg一覧
   ```
   Boundingbox (sobits_msgs)
   BoundingBoxes (sobits_msgs)
   StringArray (sobits_msgs)
   ObjectPose (sobits_msgs)
   ObjectPoseArray (sobits_msgs)
   Image (sensor_msgs)
   CompressedImage (sensor_msgs)
   ```

* Subscribe Topics
   ```
   '/camera/rgb/image_raw'(sensor_msgs/Image): YOLOv5への入力画像
   ```
* Publish Topics
   ```
   'output_topic'(yolov5/clothes_detections_list): 服装の推論結果のリスト
   'output_image_topic'(yolov5/clothes_image_out): 服装の推論結果の画像
   ```
