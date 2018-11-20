# 直播录制存储至OSS {#concept_84931_zh .concept}

视频直播服务支持将接收到的源视频流进行录制，支持m3u8（同时会有.ts分片文件）、mp4、flv 格式，也支持周期录制时长的配置，视频文件会保存至您指定的OSS存储位置。在一次推流结束时，自动生成本次推流的录制索引文件（m3u8文件、mp4文件、flv文件）。还支持按您指定的录制开始时间和录制结束时间生成自定义录制索引文件。

在一个直播加速域名下，直播录制配置按直播推流的 **AppName** 和 **StreamName** 进行区分，即相同 **AppName** 和 **StreamName** 下的视频流（Stream）都按此 **AppName** 和 **StreamName** 下的录制配置进行录制。

## 说明 { .section}

-   为了便于您对录制内容进行回看，直播录制的存储位置为OSS bucket或VOD中。本文档以直播录制 **存储至OSS**为例进行说明。

-   如果将录制的视频存储至OSS中，您需要授权视频直播可将视频内容写入OSS。授权后才能将视频存储至指定的OSS bucket中。详情参见 [配置OSS](cn.zh-CN/用户指南/录制管理/录制存储至OSS/配置OSS.md#)。

-   为了避免录制时，因网络抖动或临时断流而导致录制文件被异常截断，系统会延迟断流180s，即如果断流之后在180s内重新推流，系统会默认是同一路录制流，超过180s则认为是两路录制流。


## 创建直播录制 { .section}

1.  登录 [视频直播控制台](https://live.console.aliyun.com/#/live/domains)。
2.  单击 **域名管理**。
3.  选择所需的播流域名，并单击 **模板管理**。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20703/154269552121779_zh-CN.png)

4.  在左侧导航栏中，单击 **录制配置**。
5.  选择 **存储至OSS**。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20703/154269552121780_zh-CN.png)

    **说明：** 使用存储至OSS，您需要授权视频直播可将视频内容写入OSS产品的权限，授权后才能将视频存储至指定的OSS bucket中。详情参见 [配置OSS](cn.zh-CN/用户指南/录制管理/录制存储至OSS/配置OSS.md#)。

6.  添加录制回调。详情参见 [录制回调](cn.zh-CN/用户指南/录制管理/录制回调.md#)。
7.  单击 **添加**，并在 **录制模板**中输入录制配置信息。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20703/154269552121781_zh-CN.png)

    -    **AppName**：视频的应用名称，输入的 **AppName** 必须与直播推流的 **AppName** 保持一致方可生效。如：推流地址中**AppName**设置为`app`，则录制**AppName**也需为`app`。如果您想要进行域名级别录制，输入星号（\*）号即可。
    -    **StreamName**：存储至OSS支持流级别的录制。您只需输入指定的流名称即可。如果您想要进行全部流录制，即该`AppName`下的流全部录制，输入星号（\*）号即可。

        **说明：** **AppName**与**StreamName**参数支持英文，数字，"-"，"\_","."符号，长度限制在50字符以内。

    -    **存储格式**：支持 **flv**、**m3u8**、**mp4**三种格式。
    -    **录制周期**：**录制周期** 范围为15-360分钟，最大支持 6 小时录制。超过 6 小时，系统将按照录制命名规则生成新文件。**ts** 切片时长默认为 30s。
    -    **存储位置**：选择存储位置。

        **说明：** 存储bucket列表中包含标准bucket和媒体bucket。标准bucket是OSS bucket，用于存储。媒体bucket是MPS定制的bucket，存入媒体bucket中的视频，可执行MPS转码任务。目前bucket列表中，未对bucket做区分。如果您需要将视频转成媒体文件，需要自行记住媒体bucket的名称。

        默认的录制存储路径为：

         `m3u8:record/{AppName}/{StreamName}/{EscapedStartTime }_{EscapedEndTime }` 

         `ts:record/{AppName}/{StreamName}/{UnixTimestamp}_{Sequence}` 

         `mp4:record/{AppName}/{StreamName}/{EscapedStartTime }_{EscapedEndTime }` 

         `flv:record/{AppName}/{StreamName}/{EscapedStartTime }_{EscapedEndTime }` 

        例如，截图示例中 **AppName**为 **app**，**StreamName** 为 **stream** 所以录制 **m3u8**、**ts** 的存储路径为：

         `m3u8:record/app/stream/{EscapedStartTime}_{EscapedEndTime }` 

         `ts:record/app/stream/{UnixTimestamp}_{Sequence}` 

        如果默认的录制文件存储路径不满足您的需求，您可通过添加录制API进行修改。

        直播录制为兼容直播推流过程由于网络抖动等问题导致的推流短时间中断，推流中断 **180秒** 内没有恢复推流才会判定此次直播结束。系统会以`{AppName}/{StreamName}/{日期}.m3u8`的默认录制索引文件（m3u8 文件）格式单独存放。

8.  单击 **确定** 完成录制设置。

    由此，本域名下所有 **AppName** 为`app`，**StreamName** 为`stream`的直播流，都会按此规则进行录制。如果您想对录制的文件进行查看，参见 [查看录制文件](cn.zh-CN/用户指南/录制管理/录制存储至OSS/查看录制文件.md#)。

    **说明：** 新配置的录制设置需要重新推流才生效。如果您在配置前已经进行了推流操作，则需要终端当前推流 180 秒以上才能进行新配置的推流操作。


