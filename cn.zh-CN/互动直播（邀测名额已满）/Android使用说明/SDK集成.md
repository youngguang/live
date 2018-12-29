# SDK集成 {#concept_pbf_t5b_pfb .concept}

本文介绍互动直播Android系统SDK集成。

请您参考下图导入SDK库文件：

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20909/154061481114337_zh-CN.png)

## SDK要求 {#section_w2y_vvb_pfb .section}

1.  Android系统要求: Android 4.3+。
2.  CUP架构支持ARM64和ARMV7。
3.  最小支持的Android API版本为18， 目标版本为23。

## 操作步骤 {#section_lr3_yvb_pfb .section}

1.  创建Android工程 。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20909/154061481114338_zh-CN.png)

2.  复制aar和jar文件到您工程的libs文件夹下，如下图所示：

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20909/154061481114339_zh-CN.png)

3.  配置grade文件，包含本地lib库、IM库和Http相关库。

    ```
    dependencies {
            implementation fileTree(dir: 'libs', include: ['*.aar'])
            implementation fileTree(dir: 'libs', include: ['*.jar'])
            implementation 'org.eclipse.paho:org.eclipse.paho.client.mqttv3:1.1.0'
            implementation 'org.apache.httpcomponents:httpcore:4.4.1'
    }
    ```

4.  重新编译工程。

