# UpdateLiveSnapshotDetectPornConfig {#reference1973 .reference}

更新审核配置接口。

## 请求参数 {#section_k4f_qm1_dfb .section}

|参数|类型|是否必选|示例值|描述|
|:-|:-|:---|:--|:-|
|Action|String|是|UpdateLiveSnapshotDetectPornConfig|系统规定参数。取值：UpdateLiveSnapshotDetectPornConfig|
|AppName|String|是|testApp|App名，支持`*`表示全部。|
|DomainName|String|是|www.yourdomain.com|用户域名。|
|Interval|Integer|否|5| 采样间隔。

 取值范围：5-3600秒

 |
|OssBucket|String|否|test123|OSS存储bucket名称。|
|OssEndpoint|String|否|oss-cn-shanghai.aliyuncs.com|OSS域名。|
|OssObject|String|否|\{AppName\}/\{StreamName\}/\{Date\}/\{Hour\}/\{Minute\}*\{Second\}.jpg*|保存涉黄涉政等违规图片的对象模板，如不明确给出，默认为\{AppName\}/\{StreamName\}/\{Date\}/\{Hour\}/\{Minute\}\{Second\}.jpg。|
|Scene.N|RepeatList|否|porn| 检测场景，包括“porn”、“terrorism”、“ad”、“live”。

 默认值：“porn”

 |

## 返回参数 {#section_p4f_qm1_dfb .section}

|名称|类型|示例值|描述|
|:-|:-|:--|:-|
|RequestId|String|16A96B9A-F203-4EC5-8E43-CB92E68F4CD8|该条任务请求ID|

## 示例 {#section_zcx_4j1_dfb .section}

请求示例

```
 https://live.aliyuncs.com/?Action=UpdateLiveSnapshotDetectPornConfig&DomainName=live.aliyunlive.com&AppName=xxx&Interval=30<公共请求参数>
```

**说明：** 关于公共请求参数详细内容，参见 [公共请求参数](cn.zh-CN/API参考/调用方式/公共参数.md#)。

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

## 错误码 {#section_xm4_2kh_dfb .section}

 [查看本产品错误码](https://error-center.aliyun.com/status/product/live) 

