# PC端推流与播放 {#concept_ufx_jn3_bfb .concept}

您可以通过PC端的推流工具将视频流推送至阿里云平台进行视频的内容处理及分发。推送至阿里云中心的视频可以根据您的需求进行设置，从而适用于不同的应用场景。请您按照以下步骤完成PC端的推流与播放。

## 准备工具和环境 {#section_hd5_vpc_bfb .section}

推流和播放工具

-   推流工具：您可以使用OBS推流工具进行推流。下载地址见 [OBS官方下载地址](https://obsproject.com/download?spm=a2c4g.11186623.2.3.FRgTS8)。
-   播放工具：您可以使用VLC播放器来播放视频。下载地址见 [VLC media player官方下载地址](http://www.videolan.org/vlc/?spm=a2c4g.11186623.2.3.HA1ICZ)

网络环境

网络类型比较

|网络类型|优势|劣势|
|:---|:-|:-|
|有线网|稳定|不够便捷|
|Wi-Fi|便捷|不稳定|

-   有线网络相对Wi-Fi来说比较稳定，信号不易受干扰。因此，如果条件允许，建议您使用有线网络。
-   Wi-Fi相对有线网络来说比较便捷。因此，如果是活动直播，建议您使用 Wi-Fi。

上行带宽检测

视频直播对网络环境要求较高，良好的网络环境可以保证直播观看时的流畅度。上行带宽，取决于视频质量、分辨率。视频质量越好，分辨率越高，对上行带宽的要求就越高。建议您使用网速测试工具 [Speedtest](http://www.speedtest.net/) 测试您当前网络的上行带宽情况。

**说明：** 建议您的上行带宽不低于 1Mbps。

## 获取推流与播流地址 {#section_gw4_2qc_bfb .section}

获取推流与播流地址，您需要按照以下步骤完成操作：

1.  您需要有已经备案的域名。

    详情参见 [添加域名](https://help.aliyun.com/document_detail/84922.html)。


1.  2.  配置域名。

    添加域名之后，您需要分别对推流域名和播流域名进行CNAME解析，并将推流域名和播流域名进行关联。详情参见 [解析CNAME](https://help.aliyun.com/document_detail/84929.html)、[关联域名](https://help.aliyun.com/document_detail/84922.html)。

3.  配置鉴权。

    鉴权功能默认为开启状态，鉴权key随机分配，有效时长 30 分钟。超过有效时间，鉴权失效。您还可以根据需要进行自定义鉴权，分别设置推流地址和播流地址的过期时间。参见 [配置鉴权](https://help.aliyun.com/document_detail/85018.html)。

4.  配置可选功能。
    -   您可以选择配置防盗链功能，来限制视频直播的分发资源被访问的情况。参见 [配置防盗链](https://help.aliyun.com/document_detail/84745.html)。
    -   您可以配置IP黑名单，来限制某一IP访问您的加速域名。参见 [配置 IP 黑名单](https://help.aliyun.com/document_detail/85015.html)。
    -   您可以根据需求配置转码、录制、截图等。参见 [配置转码](https://help.aliyun.com/document_detail/84939.html)、[直播录制存储至OSS](https://help.aliyun.com/document_detail/84931.html)、[配置截图](https://help.aliyun.com/document_detail/84940.html)。
    -   您可以配置HTTPS安全加速功能，来避免敏感信息泄露等安全隐患。参见 [配置HTTPS安全加速](https://help.aliyun.com/document_detail/84930.html)。
    -   您还可以配置推断流回调功能，以便在推流状态发生变化时，及时收到阿里云将视频流推送成功、断流成功的状态实时反馈。参见 [推断流回调](https://help.aliyun.com/document_detail/84943.html)。
5.  获取推流地址和播流地址。

    您可以在视频直播新版控制台获取推流地址和播流地址。参见 [配置边缘推流](https://help.aliyun.com/document_detail/84746.html)。


## 推流设置与操作 {#section_e5p_ytc_bfb .section}

请您按照以下步骤完成推流操作：

1.  按照文档说明安装已经下载的OBS推流工具。
2.  获取推流地址。

    您可以在新版控制台获取直播推流地址。参见 [配置边缘推流](https://help.aliyun.com/document_detail/84746.html)。

3.  配置软件基本参数并进行使用获取的推流地址进行推流操作。参见 [OBS推流工具](https://help.aliyun.com/document_detail/45212.html)。

## 播放设置与查看 {#section_onk_15c_bfb .section}

请您按照以下步骤完成播流操作：

1.  按照文档说明安装已经下载的VLC播流工具。
2.  获取播流地址。

    您可以在新版控制台获取直播播流地址。参见 [配置边缘推流](https://help.aliyun.com/document_detail/84746.html)。

3.  使用VLC播放器来播放视频。参见 [VLC播放器](https://help.aliyun.com/document_detail/52142)。

