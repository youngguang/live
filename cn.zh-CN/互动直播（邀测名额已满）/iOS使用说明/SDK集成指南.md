# SDK集成指南 {#concept_ykv_p3c_pfb .concept}

本文介绍互动直播iOS系统SDK集成。

## 集成环境 {#section_omw_t3c_pfb .section}

-   最低支持的系统版本为iOS8.0。
-   支持的CPU架构包含ARM64, ARMV7, ARMV7s。
-   不支持模拟器版本。
-   不支持bitcode。

## SDK文件说明 {#section_ass_spd_ggb .section}

使用互动直播SDK时需要集成以下所有文件到App工程中。

|名称|说明|
|:-|:-|
|AlivcInteractiveLiveRoomSDK.framework|互动直播间SDK|
|AlivcInteractiveWidgetSDK.framework|互动组件|
|AlivcLiveRoomSDK.framework|直播间组件|
|AlivcUtilsSDK.framework|基础组件|
|AlivcLivePusher.framework|推流SDK|
|AlivcLibRtmp.framework|RTMP组件|
|AlivcLibBeauty.framework|美颜组件|
|AlivcLibFace.framework|人脸检测组件|
|AlivcLibFaceResource.bundle|人脸检测资源文件|
|AliyunPlayerSDK.framework|播放器SDK|
|AliThirdparty.framework|公共组件|
|AliyunLanguageSource.bundle|播放器资源文件|

## 导入SDK {#section_dty_bsd_ggb .section}

1.  下载阿里云官网互动直播iOS版本SDK到本地，解压后找到 **arm** 目录中的所有SDK包。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/24597/154893019135192_zh-CN.png)

2.  在您的App工程项目目录中创建 **AlivcFrameworks** 目录，并将SDK目录中所有文件拷贝至 **AlivcFrameworks** 目录下。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/24597/154893019135197_zh-CN.png)

3.  在App xcode工程项目栏右键选择 **Add Files...**，将 **AlivcFrameworks** 目录添加到工程目录。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/24597/154893019135198_zh-CN.png)

    添加后如下图：

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/24597/154893019235200_zh-CN.png)

4.  SDK为动态库，您需要在工程的**Embedded Binaries**中添加所有freamwork依赖。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/24597/154893019235201_zh-CN.png)

    添加后如下图：

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/24597/154893019235202_zh-CN.png)


## Cocoapods集成SDK {#section_lkn_g5f_qgb .section}

SDK也可以通过Cocoapods集成：

```
source 'https://github.com/CocoaPods/Specs.git'
platform :ios, '8.0'
target 'AlivcLiveDemo' do
pod 'AliyunInteractiveLive'
end
```

Cocospods集成完的代码结构入下：

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/24597/154893019235203_zh-CN.png)

## 设置bitcode {#section_hwx_m5f_qgb .section}

修改App 工程配置，将bitcode 设置为**NO**。

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/24597/154893019235204_zh-CN.png)

## 设置权限 {#section_hwb_r5f_qgb .section}

编辑**info.plist**，申请打开摄像头、麦克风权限。

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/24597/154893019235205_zh-CN.png)

您也可以在 **info.plist** \> **source code** 中，加入以下代码：

```
<key>NSCameraUsageDescription</key>
<string>打开相机</string>
<key>NSMicrophoneUsageDescription</key>
<string>打开麦克风</string>
```

## 设置后台直播 {#section_yj1_y5f_qgb .section}

如果App需要退后台直播，一定要编辑 **info.plist**，开启音视频播放 backgroud mode， 否则，在主播直播中退后台容易导致直播中断。

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/24597/154893019238498_zh-CN.png)

也可以在Xcode可视化界面中进行设置。

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/24597/154893019238500_zh-CN.png)

或者在 **info.plist** \> **source code** 中，加入以下代码：

```
<key>UIBackgroundModes</key>
<array>
<string>audio</string>
</array>
```

