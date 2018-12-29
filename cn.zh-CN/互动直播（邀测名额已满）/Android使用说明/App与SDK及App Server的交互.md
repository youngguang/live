# App与SDK及App Server的交互 {#concept_srm_g5b_pfb .concept}

本文介绍App与SDK及App Server的交互过程。

经典的互动直播交互如下图所示。

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20909/154061479314336_zh-CN.png)

-   无论主播还是观众，都是从**init** \> **getRamSTS** \> **login** \> **enterRoom** 开始。
-   在进入房间之后，主播可以调节推流的设置，也可以和观众进行互动；观众也可以选择和主播进行互动。
-   最后主播和观众可以选择离开房间，调用**leaveRoom** \> **release**。

