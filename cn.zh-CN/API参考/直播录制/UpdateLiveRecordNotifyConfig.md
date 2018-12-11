# UpdateLiveRecordNotifyConfig {#reference1379 .reference}

更新域名级别录制回调配置。

## 请求参数 {#section_k4f_qm1_dfb .section}

|参数|类型|是否必选|示例值|描述|
|:-|:-|:---|:--|:-|
|Action|String|是|UpdateLiveRecordNotifyConfig|系统规定参数。取值：UpdateLiveRecordNotifyConfig|
|DomainName|String|是|test.com|加速域名。|
|NeedStatusNotify|Boolean|否|false| 是否需要录制任务状态回调，可取值true/false。

 默认值：false

 |
|NotifyUrl|String|否|[http://www.yourdomain.cn/examplecallback.action](http://www.yourdomain.cn/examplecallback.action)| 回调url地址。

 -   必须以 http:// 或 https:// 开头。
-   需要做 url encode。

 |

## 返回参数 {#section_p4f_qm1_dfb .section}

|名称|类型|示例值|描述|
|:-|:-|:--|:-|
|RequestId|String|16A96B9A-F203-4EC5-8E43-CB92E68F4CD|该条任务请求 ID|

## 示例 {#section_zcx_4j1_dfb .section}

请求示例

```
https://live.aliyuncs.com/?Action=UpdateLiveRecordNotifyConfig&DomainName=test101.cdnpe.com&NotifyUrl=http://xxx<公共请求参数> 
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

## 错误码 {#section_u2r_ykc_dfb .section}

 [查看本产品错误码](https://error-center.aliyun.com/status/product/live) 

