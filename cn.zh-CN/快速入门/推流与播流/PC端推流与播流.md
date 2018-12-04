# PC端推流与播流 {#concept_ccv_kwb_yfb .concept}

视频直播使用边缘推流，优先将视频推流至最优CDN节点，保证您访问的都是最佳的上行网络，减少因上行传输带来的卡顿、拉流缓慢的问题。请您按照以下步骤进行推流和播流操作。

## 前提条件 {#section_j5h_mwh_yfb .section}

**推流和播放工具**

-   推流工具：下载并安装推流工具。本文以使用OBS推流工具为例说明。下载地址见 [OBS官方下载地址](https://obsproject.com/download?spm=a2c4g.11186623.2.3.FRgTS8)。
-   播放工具：下载并安装播流工具。本文以使用VLC播放器为例说明。下载地址见 [VLC media player官方下载地址](http://www.videolan.org/vlc/?spm=a2c4g.11186623.2.3.HA1ICZ)

## 推流 {#section_ubx_vwh_yfb .section}

1.  登录 [视频直播控制台](https://live.console.aliyun.com/#/live/domains)。
2.  单击 **直播管理** \> **地址生成器**。
3.  选择您创建的 **播流域名** 和关联的 **推流域名**。
4.  输入 **AppName** 和 **StreamName**。
5.  单击 **开始生成**。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/65174/154391691433185_zh-CN.png)

    您可以获得推流地址和播流地址。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/65174/154391691433187_zh-CN.png)

6.  下载并安装OBS推流工具。

    关于OBS推流工具配置及使用，详情参见 [OBS推流工具](https://help.aliyun.com/document_detail/45212.html)。

    您需要将鉴权后的推流地址分两部分输入 **URL** 与 **流秘钥** 中。

    -   **URL**：填写包含**AppName**前的地址，
    -   **流名称**：填写包含**StreamName**后的地址。
    以推流地址`rtmp://push.aliyunlive.com/app/stream?auth_key=1543302081-0-0-9c6e7c8190c10bdfb3c0************`为例，

    -   URL：填写`rtmp://push.aliyunlive.com/app/`，
    -   流名称：填写`stream?auth_key=1543302081-0-0-9c6e7c8190c10bdfb3c0************`

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/65174/154391691433188_zh-CN.png)

    **说明：** 以上推流地址示例由推流域名、AppName、StreamName和鉴权串组成，您需要根据实际情况，替换成您自己的AppName、StreamName和相应的鉴权串。


## 播流 {#section_imm_g13_yfb .section}

1.  下载并安装VLC播放器。

    关于VLC播放器使用，参见 [VLC播放器](https://help.aliyun.com/document_detail/52142.html?spm=a2c4g.11186623.6.863.5f8d1445E3P7Eh)。

2.  打开VLC播放器。
3.  单击 **媒体** \> **打开网络串流\(N\)。**。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/65174/154391691433189_zh-CN.png)

4.  根据推流操作**步骤6** 获取播流地址。
5.  在 **请输入网络URL** 中，输入播流地址并单击播放。

    以播流地址`rtmp://play.aliyunlive.com/app/stream?auth_key=1543300311-0-0-d47ce016332bf280cf275********`为例，将播流地址复制到URL的输入框并单击 **播放** 即可。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/65174/154391691433190_zh-CN.png)

    **说明：** 以上播流地址示例由播流域名、AppName、StreamName和鉴权串组成，您需要根据实际情况，替换成您自己的AppName、StreamName和相应的鉴权串。


