# 状态检查

组装完成之后就可以开始使用小强了。打开小强主机开关，等待主机蓝色灯亮起。小强左侧电源数据显示正常（电池电压合理使用范围是10V以上，当电池电压小于10V时小强会自动关机）。

通过ssh远程连接，其中xxx.xxx.xxx.xxx是小强的IP

```bash
ssh xiaoqiang@xxx.xxx.xxx.xxx
```

检查程序是否正常运行，执行以下指令
```bash
rostopic list
```

正常情况下会显示出当前的所有ROS topic.

```bash
/ORB_SLAM/Camera
/ORB_SLAM/Frame
/camera_node/image_raw
/orb_scale/scaleStatus
/rosout
/rosout_agg
/system_monitor/report
/tf
/usb_cam/brightness
/xqserial_server/Odom
/xqserial_server/Power
```

如果没有正常显示topic，可以尝试重启service。

```bash
sudo service startup restart
```

查看系统状态
```bash
rostopic echo /system_monitor/report
```

如果正常，则显示如下
```bash
imageStatus: True
odomStatus: True
orbStartStatus: False
orbInitStatus: False
orbScaleStatus: False
brightness: 0
power: 12.34432
```

其中imageStatus表示摄像头是否工作正常。odomStatus表示底层驱动时候工作正常。Orb相关的三个变量是视觉导航相关的状态，可以不用管（如果对这方面感兴趣可以在论坛里进行交流）。brightness是摄像头的亮度，power是当前电池的电压值，如果无法读取则是0.
