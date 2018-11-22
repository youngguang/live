# 添加转码SEI信息 {#concept_66945_zh .concept}

添加转码SEI信息。

## 请求参数 {#section_k4f_qm1_dfb .section}

|参数|类型|是否必选|示例值|描述|
|:-|:-|:---|:--|:-|
|Action|String|是|AddTrancodeSEI|系统规定参数。取值：AddTrancodeSEI|
|AppName|String|是|AppName|直播流所属应用名称。|
|Delay|Integer|是|100|接收到命令后的 delay 时间。单位： 毫秒。|
|DomainName|String|是|live.aliyunlive.com|您的加速域名。|
|Pattern|String|是|keyframe|追加到每一个关键帧 / 每一帧。取值：keyframe / frame|
|Repeat|Integer|是|1|重复次数，-1 代表无限。|
|StreamName|String|是|StreamName|流名。|
|Text|String|是|firsttxt|SEI文本。长度限制： 4000 字节。|

## 返回参数 {#section_p4f_qm1_dfb .section}

|名称|类型|示例值|描述|
|:-|:-|:--|:-|
|RequestId|String|40A4F36D-A7CC-473A-88E7-154F92242566|该条任务请求ID|

## 示例 {#section_zcx_4j1_dfb .section}

请求示例

```
 https://live.aliyuncs.com/?Action=AddTrancodeSEI&AppName=AppName&Delay=100&DomainName=live.aliyunlive.com&Pattern=keyframe&Repeat=1&StreamName=StreamName&Text=firsttxt&<公共请求参数>
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
    "RequestId":"16A96B9A-F203-4EC5-8E43-CB92E68F4CD8"
}
```

## 错误码 {#section_v4f_qm1_dfb .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/live)

