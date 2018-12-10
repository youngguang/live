# SetCasterChannel {#concept_mz5_xdk_pfb .concept}

采用视频源同步模式时需要将视频资源设置到通道中。

## 请求参数 {#section_ip3_c2k_pfb .section}

|参数|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是|操作接口名，系统规定参数，取值：SetCasterChannel|
|CasterId|String|是|导播台Id。|
|ChannelId|String|是|通道Id。-   布局画面的引用编号，每个通道位置至多设置一个资源，数量受限于导播台创建时的通道路数。
-   格式符合“RV01...RV12”。

|
|ResourceId|String|是|视频源Id。|
|SeekOffset|Integer|否|仅对文件视频有效，直播源无效，必须大于0，表示从相对于首帧的偏差时间作为开始读取的位置。单位：毫秒\(ms\)

|
|PlayStatus|Integer|否|仅对文件视频有效，直播源无效。播放状态：

-   1：播放，
-   0：暂停。

默认为：1：播放

|

## 返回参数 {#section_upw_32k_pfb .section}

|参数|类型|描述|
|:-|:-|:-|
|RequestId|String|该条任务请求Id|

## 示例 {#section_vjq_x2k_pfb .section}

请求示例

```
https://live.aliyuncs.com?Action=SetCasterChannel&CasterId=a2b8e671-2fe5-4642-a2ec-bf93880e1a49&ChannelId=RV01&ResourceId=16A96B9A-F203-4EC5-8E43-CB92E68F4CD8&<公共请求参数>
```

返回示例

```
{
    "RequestId": "16A96B9A-F203-4EC5-8E43-CB92E68F4CD8",
}
```

## 特殊错误码 {#section_lwx_1fk_pfb .section}

|错误代码|描述|Http状态码|语义|
|:---|:-|:------|:-|
|PermissionDenied|Permission Denied|401|无权访问导播台|
|InvalidCaster.NotFound|Caster is not found.|404|指定导播台不存在|
|DuplicateLocationID|LocationId is duplicate.|400|资源ID已存在|
|ResourceOfChannelExist|Resource has been set to channel already|400|指定资源已存在于某个通道中|
|InternalError|InternalError|500|内部错误|
|InvalidResource.NotFound|Resource is not found.|404|指定资源不存在|

