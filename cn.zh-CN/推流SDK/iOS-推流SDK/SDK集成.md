# SDK集成 {#concept_cbx_ysw_pfb .concept}

本文介绍iOS推流SDK的SDK集成。

## SDK信息 {#section_d4s_ctw_pfb .section}

您可以在阿里云官网更新，参见 [SDK下载](cn.zh-CN/SDK 参考/SDK下载.md#)。

下载后的SDK目录结构如下：

-   **依赖播放器版本**：包含 `AlivcLibRtmp.framework`、`ALivcLivePusher.framework`两个推流动态库和 `AlivcLibFaceResource.bundle`人脸资源库，同时包含 `AliyunPlayerSDK.framework`播放器动态库和 `AliyunLanguageSource.bundle`播放器资源库。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/40318/154088463621028_zh-CN.png)

-   **不依赖播放器版本**：包含

    `AlivcLibRtmp.framework`

    、

    `ALivcLivePusher.framework`

    两个推流动态库和

    `AlivcLibFaceResource.bundle`

    人脸资源库。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/40318/154088463621029_zh-CN.png)

    **说明：** 

    -   推流SDK中包含背景音乐相关功能。如果您需要使用该功能，要使用依赖播放器SDK的版本；如果您不需要背景音乐功能，则使用不依赖播放器SDK的版本即可。

    -   **AlivcLibFaceResource.bundle**是人脸识别资源文件，如果您需要使用美颜的人脸识别高级功能，则必须导入开发工程；反之则不需要。

    -   每个版本均包含 **arm**和 **arm&simulator** 两套SDK，**arm**仅支持真机调试。**arm&simulator**支持真机+模拟器调试。项目在release上线的时候必须使用**arm**版本。


## 系统要求 {#section_dtd_mtw_pfb .section}

-   SDK支持iOS 8.0及以上版本系统

-   硬件CPU支持ARMv7、ARMv7s、ARM64


## 开发环境 {#section_b5x_mtw_pfb .section}

-   SDK编译环境Xcode 8.0及以上版本

-   Xcode运行环境OS X 10.10 及以上版本


## 导入SDK {#section_svj_3vw_pfb .section}

-   手动导入

    示例开发环境为Xcode9.0。

    1.  新建SDK测试工程 **Single View App** \> **DemoPush** 。
    2.  将`AlivcLibRtmp.framework`和`AlivcLivePusher.framework`两个动态库、`AlivcLibFaceResource.bundle`一个人脸识别资源库以及`AliyunPlayerSDK.framework`和`AliyunLanguageSource.bundle`两个播放器库拖入您的Xcode工程中。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/40318/154088463621030_zh-CN.png)

        如果您不需要依赖播放器SDK的版本，则只需要将`AlivcLibRtmp.framework`和`AlivcLivePusher.framework`两个动态库以及`AlivcLibFaceResource.bundle`人脸识别资源库拖入您的工程即可。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/40318/154088463621031_zh-CN.png)

        后续将以依赖播放器版本的SDK进行演示。

    3.  按图示勾选 **Copy items if needed**。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/40318/154088463621032_zh-CN.png)

    4.  导入SDK成功之后，在 **Xcode** \> **General** \> **Embedded Binaries**中添加SDK依赖。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/40318/154088463621033_zh-CN.png)

        添加依赖成功后如图所示：

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/40318/154088463621034_zh-CN.png)

    5.  在 **Build Phases** \> **Copy Bundle Resources** 中添加资源文件依赖。

        **说明：** 资源文件添加成功后，才能使用人脸识别相关功能。否则调用人脸识别相关接口无效。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/40318/154088463621035_zh-CN.png)

    6.  在 **Building Setting** \> **Enable Bitcode** 修改为 **NO**。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/40318/154088463621037_zh-CN.png)

    7.  在**Info.plist**文件中添加麦克风和摄像头权限`Privacy - Microphone Usage Description`、`Privacy - Camera Usage Description`。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/40318/154088463621038_zh-CN.png)

    8.  配置iOS开发证书，选择测试真机，单击 **Run**，提示 **Buidling Success**，SDK添加成功。
-   Cocoapods导入

    1.  修改Podfile。
        -   依赖播放器版本

            添加如下语句至您的 **Podfile**文件中。

            ```
            pod 'AlivcLivePusherWithPlayer'
            ```

        -   不依赖播放器版本

            添加如下语句至您的 **Podfile** 文件中。

            ```
            pod 'AlivcLivePusher'
            ```

    2.  执行 **pod install**。

        ```
        pod install :每次您编辑您的Podfile（添加、移除、更新）的时使用
        ```

    3.  关闭**bitcode**。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/40318/154088463721040_zh-CN.png)

    4.  配置 **Info.plist**。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/40318/154088463721041_zh-CN.png)


