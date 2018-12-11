# DeleteLiveDomain {#concept_88328_zh .concept}

删除已添加的直播域名。

**说明：** 请慎重操作（建议您在进行域名删除前到域名解析服务商处恢复域名A记录），以免导致删除操作后此域名不可访问。 DeleteLiveDomain调用成功后将删除本条直播域名的全部相关记录，对于仅需要暂停使用该直播域名，推荐您使用StopLiveDomain接口。

## 请求参数 { .section}

|参数|类型|是否必选|示例值|描述|
|:-|:-|:---|:--|:-|
|Action|String|是|DeleteLiveDomain|操作接口名，系统规定参数取值：DeleteLiveDomain|
|DomainName|String|是|live.yourdomain.com|要删除的域名|

## 返回参数 {#section_j2r_nk1_dfb .section}

|名称|类型|示例值|描述|
|:-|:-|:--|:-|
|RequestId|String|94E3559F-7B6A-4A5E-AFFD-44E2A208A249|请求ID|

## 示例 {#section_zcx_4j1_dfb .section}

请求示例

```
 /?DomainName=live.yourdomain.com
&Action=DeleteLiveDomain
&<公共请求参数>
```

正常返回示例

JSON格式

```
{
    "RequestId":"94E3559F-7B6A-4A5E-AFFD-44E2A208A249"
}
```

异常返回示例

JSON格式

```
{
    "Code":"InternalError",
    "HostId":"live.aliyuncs.com",
    "Message":"The request processing has failed due to some unknown error.",
    "RequestId":"6EBD1AC5-C34D-4BE1-963E-B688A228BE31"
}
```

## 错误码 {#section_eb2_qk1_dfb .section}

 [查看本产品错误码](https://error-center.aliyun.com/status/product/live) 

