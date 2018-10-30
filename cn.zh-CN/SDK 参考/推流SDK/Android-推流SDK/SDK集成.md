# SDK集成 {#concept_drc_txx_pfb .concept}

本文介绍Android推流SDK的集成。

## SDK信息 {#section_slj_dxk_nfb .section}

下载后的 **SDK** 目录：

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20914/154088455613965_zh-CN.png)

-   **AlivcLivePusherSDK** 目录：不带阿里云播放器。
    -   **aarlibs** 目录：

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20914/154088455613966_zh-CN.png)

    -   **jniLibs** 目录：

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20914/154088455613967_zh-CN.png)

    -   **libs** 目录：

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20914/154088455613968_zh-CN.png)

    -   **obj** 目录\(用于定位底层问题\)：

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20914/154088455613969_zh-CN.png)

-   **AlivcLivePusherSDK+AliyunPlayerSDK** 目录：带阿里云播放器。
    -   **aarlibs** 目录：

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20914/154088455613970_zh-CN.png)

    -   **jniLibs** 目录：

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20914/154088455613971_zh-CN.png)

    -   **libs** 目录：

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20914/154088455613972_zh-CN.png)

    -   **obj** 目录\(用于定位底层问题\)：

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20914/154088455613973_zh-CN.png)

        **说明：** 

        -   集成方式分两种，一种采用aar集成，另一种采用jar包+so集成，选择其一即可。
        -   使用背景音乐功能时必须集成播放器sdk\(AlivcPlayer.aar\)，采用aar集成方式时需要同时引入播放器SDK的aar；采用jar包+so集成时，可以在application层引入播放器SDK的aar。v3.2.0+添加了调试工具\(live-pusher-resources.aar\), 用法同AlivcPlayer.aar。AlivcReporter.aar也使用同样的方法引用。

## 系统要求 {#section_c4f_cyx_pfb .section}

-   SDK支持Android 4.3及以上版本

-   硬件CPU支持ARM64、ARMV7


## 运行环境 {#section_uld_dyx_pfb .section}

-   SDK编译支持Android 4.3及以上版本

-   Android Studio 2.3及以上版本

-   APP开发环境与SDK保持兼容即可。

-   Android SDK Tools: android-sdk\_25.0.0

    -   minSdkVersion 18

    -   targetSdkVersion 23


## SDK集成 {#section_vf2_fyx_pfb .section}

下载SDK包，点击 [SDK下载](https://help.aliyun.com/document_detail/45270.html?spm=a2c4g.11186623.2.30.6284161cvDZvBu)。

1.  Android Studio 新建工程：

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20914/154088455613974_zh-CN.png)

2.  copy JAR包和SO库：

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20914/154088455613975_zh-CN.png)

3.  工程配置：

    ```
    dependencies {
     implementation fileTree(dir: 'libs', include: ['*.jar'])
    }
    ```

    jniLibs 目录为默认so存放位置。如果自己设置位置，需要在app的build.gradle中配置：

    ```
    sourceSets{ 
    main{ 
       jniLibs.srcDirs = ['libs'] 
    } 
    }
    ```

4.  编译工程 Rebuild Project。

