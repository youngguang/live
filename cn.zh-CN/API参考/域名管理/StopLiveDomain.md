# StopLiveDomain {#concept_88329_zh .concept}

停用某个直播域名，将DomainStatus变更为offline。

停用该直播域名后，该条直播域名信息仍保留，针对直播域名的请求系统将做自动回源处理。

## 请求参数 {#section_k4f_qm1_dfb .section}

|参数|类型|是否必选|示例值|描述|
|:-|:-|:---|:--|:-|
|Action|String|是|StopLiveDomain|操作接口名，系统规定参数取值：StopLiveDomain|
|DomainName|String|是|live.yourdomain.com|直播域名|

## 返回参数 {#section_p4f_qm1_dfb .section}

|名称|类型|示例值|描述|
|:-|:-|:--|:-|
|RequestId|String|324AEFFF-308C-4DA7-8CD3-01B277B98F28|请求ID|

## 示例 {#section_zcx_4j1_dfb .section}

请求示例

```
/?DomainName=live.yourdomain.com
&AccessKeyId=XxlctR6mMqO6mhXxX
&Action=StopLiveDomain
&<公共请求参数> 
```

正常返回示例

JSON格式

```
{
    "RequestId":"324AEFFF-308C-4DA7-8CD3-01B277B98F28"
}
```

异常返回示例

JSON格式

```
{
    "Code":"InternalError",
    "HostId":"live.aliyuncs.com",
    "Message":"The request processing has failed due to some unknown error.",
    "RequestId":"6EBD1AC4-C34D-4BE1-963E-B688A228BE31"
}
```

## 错误码 {#section_v4f_qm1_dfb .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/live)

