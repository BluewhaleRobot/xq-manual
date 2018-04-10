# 视频传输

小强的视频也是可以远程传输的。在本地打开一个终端输入

```bash
export ROS_MASTER_URI=http://xiaoqiang-desktop:11311
```

然后在本地系统的/etc/hosts文件内添加小强的ip

```
192.168.X.X  xiaoqiang-desktop
```

输入下述命令开始显示摄像头视频

```bash
rosrun image_view image_view image:=/camera_node/image_raw  _image_transport:=compressed
```

如果一切正常就能够看到当前小强的摄像头画面了。
