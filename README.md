# 用于在linux中安装3dsystems的Touch hid-usb
## 环境
ubuntu 20.04
ROS noetic
## 参考链接
### 3d systems的sdk和相关软件包：
https://support.3dsystems.com/s/article/OpenHaptics-for-Linux-Developer-Edition-v34?language=en_US
### 相关ROS包：
https://github.com/bharatm11/Geomagic_Touch_ROS_Drivers?tab=readme-ov-file
### 相关资料
https://blog.csdn.net/weixin_52725622/article/details/134164760?ops_request_misc=elastic_search_misc&request_id=3076085918ab8f971541a5865617cba6&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~ElasticCommercialInsert~search_v2-2-134164760-null-null.142^v102^pc_search_result_base5&utm_term=ubuntu%E5%AE%89%E8%A3%85TouchDriver&spm=1018.2226.3001.4187

https://blog.csdn.net/m0_73225361/article/details/137425971?ops_request_misc=elastic_search_misc&request_id=3076085918ab8f971541a5865617cba6&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduend~default-1-137425971-null-null.142^v102^pc_search_result_base5&utm_term=ubuntu%E5%AE%89%E8%A3%85TouchDriver&spm=1018.2226.3001.4187
## 安装步骤
### 安装openhaptics
`cd openhaptics_3.4-0-developer-edition-amd64`
`chmod +x install`
`./install`
### 安装TouchDriver
1. `cd TouchDriver_2024_09_19/bin`
2. 将bin中可执行文件复制到系统目录/usr/bin中
`sudo cp Touch_AdvancedConfig /usr/bin/`
`sudo cp TouchCheckup /usr/bin/`
`sudo cp Touch_HeadlessSetup /usr/bin/`
3. `cd ..`
`chmod +x install_haptic_driver`
`./install_haptic_driver`
## 验证
`cd TouchDriver_2024_09_19/bin`
`chmod +x Touch_AdvancedConfig`
`chmod +x TouchCheckup`
执行：
`./Touch_AdvancedConfig`
`./TouchCheckup`
以获得相关Touch设备的信息。
# 配置相关ROS包
1. 
`sudo apt-get update`
`sudo apt-get install --no-install-recommends freeglut3-dev g++ libdrm-dev libexpat1-dev libglw1-mesa libglw1-mesa-dev libmotif-dev libncurses5-dev libraw1394-dev libx11-dev libxdamage-dev libxext-dev libxt-dev libxxf86vm-dev tcsh unzip x11proto-dri2-dev x11proto-gl-dev x11proto-print-dev`
> ubuntu 20.04 没有x11proto-print-dev包，可以直接不装
`mkdir -p Touch_ws/src`
`cd Touch_ws/src`
`git clone https://github.com/bharatm11/Geomagic_Touch_ROS_Drivers.git`
`cd ..`
`catkin_make`
`source ./devel/setup.bash`
2. 
`roslaunch omni_common omni_state.launch `
可以从话题中查看数据，注意如果新开bash需要source。
