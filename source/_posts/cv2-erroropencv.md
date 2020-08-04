---
title: 运行cv2.xfeatures2d.SIFT_create()时报错
date: 2019-08-23 11:32:14
tags: [Python, OpenCv]
categories: 教程
---

# 异常
错误代码
```
cv2.error: OpenCV(3.4.3) C:\projects\opencv-python\opencv_contrib\modules\xfeatures2d\src\sift.cpp:1207: error: (-213:The function/feature is not implemented) This algorithm is patented and is excluded in this configuration; Set OPENCV_ENABLE_NONFREE CMake option and rebuild the library in function 'cv::xfeatures2d::SIFT::create'
```
貌似是该算法被申请了专利还是咋的，将opencv版本退到3.4.2即可解决

# 解决方法
```
pip install opencv-python==3.4.2.16
pip install opencv-contrib-python==3.4.2.16
```

# 附件
相关连接
 - https://www.jianshu.com/p/0f8185a1616f
 - https://blog.csdn.net/weixin_43167047/article/details/82841750