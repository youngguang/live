# AddLivePullStreamInfoConfig {#concept_57734_zh .concept}

添加直播拉流信息，仅支持拉取直播流。 支持rtmp，http，flv格式。

## 请求参数 {#section_k4f_qm1_dfb .section}

|参数|类型|是否必选|示例值|描述|
|:-|:-|:---|:--|:-|
|Action|String|是|AddLivePullStreamInfoConfig|系统规定参数。取值：AddLivePullStreamInfoConfig|
|AppName|String|是|testApp|直播流所属应用名称。|
|DomainName|String|是|live.yourdomain.com|您的拉流域名为用户的播放域名。|
|EndTime|String|是|2017-12-22T08:00:00Z| 拉流结束时间。

 -   UTC格式。
-   StartTime和EndTime时间间隔在7天内，且EndTime超过当前时间。

 |
|SourceUrl|String|是|live.yourdomain.com| 用户的直播流所在的源站。

 多个源站可以填多个地址，用分号分隔。

 |
|StartTime|String|是|2017-12-21T08:00:00Z| 拉流开始时间。

 -   UTC格式
-   StartTime和EndTime时间间隔在7天内

 |
|StreamName|String|是|testStream|直播流名。|

## 返回参数 {#section_p4f_qm1_dfb .section}

|名称|类型|示例值|描述|
|:-|:-|:--|:-|
|RequestId|String|40A4F36D-A7CC-473A-88E7-154F92242566|该条任务请求ID|

## 示例 {#section_zcx_4j1_dfb .section}

请求示例

```
 https://live.aliyuncs.com/?Action=AddLivePullStreamInfoConfig&DomainName=live.aliyunlive.com&AppName=xxx&StreamName=xxx&SourceUrl=xxxx&StartTime=2017-08-28T07:30:30Z&EndTime=2017-08-30T07:45:00Z&<公共请求参数>
```

**说明：** 关于公共请求参数详细内容，请参考 [公共请求参数](cn.zh-CN/API参考/调用方式/公共参数.md#)。

正常返回示例

JSON格式

```
{
    "RequestId":"16A96B9A-F203-4EC5-8E43-CB92E68F4CF8"
}
```

异常返回示例

JSON格式

```
{
    "Code":"InternalError",
    "HostId":"live.aliyuncs.com",
    "Message":"The request processing has failed due to some unknown error.",
    "RequestId":"6EBD1AC4-C34D-4AE1-963E-B688A228BE31"
}
```

## 错误码 {#section_v4f_qm1_dfb .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/live)

