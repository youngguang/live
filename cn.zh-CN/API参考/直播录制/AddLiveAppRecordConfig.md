# AddLiveAppRecordConfig {#concept_35416_zh .concept}

配置 APP 录制，输出内容保存到 OSS 中。

**说明：** 使用录制功能，必须授权直播产品写入OSS的权限。您可以通过控制台进行配置，也可以通过RAM进行权限配置。

-   通过控制台配置：您需要授权视频直播可将视频内容写入OSS产品的权限，授权后才能将视频存储至指定的OSS bucket中。详情参见 [配置OSS](https://help.aliyun.com/document_detail/84932.html#concept-84932-zh)。
-   通过RAM进行权限配置：详情参见 [使用RAM配置子账号访问直播控制台](../../../../cn.zh-CN/用户指南/使用RAM配置子账号访问直播控制台.md#)。

## 请求参数 {#section_k4f_qm1_dfb .section}

|参数|类型|是否必选|示例值|描述|
|:-|:-|:---|:--|:-|
|Action|String|是|AddLiveAppRecordConfig|系统规定参数，取值：AddLiveAppRecordConfig|
|AppName|String|是|test123| 直播流所属应用名称。

 支持通配符\*，代表该域名下所有的 AppName。

 |
|DomainName|String|是|test.com|加速域名。|
|OssBucket|String|是|test123|OssBucket名称。|
|OssEndpoint|String|是|oss-cn-shanghai.aliyuncs.com|OssEndpoint域名。|
|EndTime|String|否|2018-04-16T09:57:21Z| 录制结束时间。

 格式：UTC时间。

 设置时间必须从当前时间开始15天之内的时间，只在流级别录制\(StreamName不为空\)有效，且时间应晚于录制开始时间。

 |
|OnDemand|Integer|否|1|按需录制。

-   0表示关闭。
-   1表示通过HTTP回调方式。
-   2表示通过推流参数方式。

使用1方式时候需要设置OnDemandCallback，否则默认不录制。|
|RecordFormat.N.CycleDuration|Integer|否|1| 周期录制时长。

 单位：秒。

 不填则默认为 1 小时。

 |
|RecordFormat.N.Format|String|否|m3u8| 格式。

 目前支持 m3u8、flv、mp4 周期录制。

 |
|RecordFormat.N.OssObjectPrefix|String|否|record/\{AppName\}/\{StreamName\}/\{EscapedStartTime\}\{EscapedEndTime\}| OSS 存储的录制文件名。

 -   小于 256 byte。
-   支持变量匹配，包含 \{AppName\}、\{StreamName\}、\{EscapedStartTime\}、\{EscapedEndTime\}。
-   例如：record/\{AppName\}/\{StreamName\}/\{EscapedStartTime\}\{EscapedEndTime\}
-   参数值必须要有\{EscapedStartTime\} 和 \{EscapedEndTime\} 变量。
-   默认支持 1 小时周期录制，最小周期时间 15 分钟，最多 6 小时。
-   \{EscapedStartTime\}/\{EscapedEndTime\} 格式为：2006-01-02-15-04-05。
-   推荐使用 Escaped 格式，避免特殊字符在 URL 中带来的一些问题。

 |
|RecordFormat.N.SliceOssObjectPrefix|String|否|record/\{AppName\}/\{StreamName\}/\{UnixTimestamp\}\_\{Sequence \}| 当 format 格式是 m3u8 录制，则需要配置，表示 ts 切片名称。

 -   默认 30 秒一片，小于 256byte。
-   支持变量匹配，包含\{AppName\}、\{StreamName\}、\{UnixTimestamp\}。
-   例如：record/\{AppName\}/\{StreamName\}/\{UnixTimestamp\}。
-   参数值必须包含\{UnixTimestamp\}变量。

 |
|StartTime|String|否|2018-04-10T09:57:21Z| 录制开始时间。

 格式：UTC时间。

 设置时间必须从当前时间开始15天之内的时间, 只在流级别录制\(StreamName不为空\)有效。

 |
|StreamName|String|否|teststream|流名称。|

## 返回参数 {#section_p4f_qm1_dfb .section}

|名称|类型|示例值|描述|
|:-|:-|:--|:-|
|RequestId|String|16A96B9A-F203-4EC5-8E43-CB92E68F4CD8|请求ID|

## 示例 {#section_zcx_4j1_dfb .section}

请求示例

```
 /?AppName=test123
&DomainName=test.com
&OssBucket=test123
&OssEndpoint=oss-cn-shanghai.aliyuncs.com
&Action=AddLiveAppRecordConfig
&RecordFormat.1.Format=m3u8
&AccessKeyId=XxlctR6mMqO6mhXxX
&EndTime=2018-04-16T09:57:21Z
&OnDemand=1
&RecordFormat.1.CycleDuration=1
&RecordFormat.1.OssObjectPrefix=record/{AppName}/{StreamName}/{Sequence}{EscapedStartTime}{EscapedEndTime}
&RecordFormat.1.SliceOssObjectPrefix=record/{AppName}/{StreamName}/{UnixTimestamp}_{Sequence}
&StartTime=2018-04-10T09:57:21Z
&StreamName=teststream
&<公共请求参数>
```

正常返回示例

JSON格式

```
{
    "RequestId":"16A96B9A-F203-4EC5-8E43-CB92E68F4CD8"
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

