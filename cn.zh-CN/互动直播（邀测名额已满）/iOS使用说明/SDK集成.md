# SDK集成 {#concept_ykv_p3c_pfb .concept}

本文介绍互动直播iOS系统SDK集成。

## 集成环境 {#section_omw_t3c_pfb .section}

-   最低支持的系统版本为iOS8.0。
-   支持的CPU架构包含ARM64, ARMV7, ARMV7s。
-   依赖的系统库 `SystemConfiguration.framework`， `libresolv.tbd`， `MobileCoreServices.framework`，`libresolv.9.tbd`。![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/24595/154088430214381_zh-CN.png)
-   直播用到的SDK包

    含`AliThirdparty.framework`，`AlivcInteractiveLiveRoomSDK.framework`，`AlivcInteractiveWidgetSDK.framework`，`AlivcLibBeauty.framework`，`AlivcLibFace.framework`，`AlivcLibRtmp.framework`，`AlivcLivePusher.framework`，`AlivcLiveRoomSDK.framework`，`AlivcUtilsSDK.framework`，`AliyunPlayerSDK.framework`，`AliRTCSdk.framework`。![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/24595/154088430214382_zh-CN.png)

-   直播用到的资源文件包

    含`AlivcLibFaceResource.bundle`和`AliyunLanguageSource.bundle`。![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/24595/154088430314383_zh-CN.png)


## 操作步骤 {#section_xqd_cjc_pfb .section}

1.  创建一个xcode工程。
2.  添加依赖。

    选中 **target** \> **Build Phases** \> **Link Binary With Libraries**，单击**+**，添加`SystemConfiguration.framework`、`libresolv.tbd`、`MobileCoreServices.framework`和`libresolv.9.tbd`系统库，如下图所示：![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/24595/154088430314384_zh-CN.png)

3.  添加互动直播所需要的frameWork和资源bundle。

    选中`AliThirdparty.framework`、`AlivcInteractiveLiveRoomSDK.framework`、`AlivcInteractiveWidgetSDK.framework`、`AlivcLibBeauty.framework`、`AlivcLibFace.framework`、`AlivcLibRtmp.framework`、`AlivcLivePusher.framework`、`AlivcLiveRoomSDK.framework`、`AlivcUtilsSDK.framework`、`AliRTCSdk.framework`和`AliyunPlayerSDK.framework`直接拖到工程目录下，并勾选**Copy items if needed**选项，这样在对应的**Link Binary With Libraries**以及**Copy Bundle Resources**下分别能看到您添加的framework和bundle资源。

4.  选择**target** \> **Build Settings** \> **Enable Bitcode**，设置为**No**。

