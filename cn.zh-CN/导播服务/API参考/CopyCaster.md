# CopyCaster {#reference1073 .reference}

复制导播台，复制指定导播台并返回新导播台实例。

## 请求参数 {#section_k4f_qm1_dfb .section}

|参数|类型|是否必选|描述|
|:-|:-|:---|:-|
|Action|String|是|操作接口名，系统规定参数。取值：CopyCaster|
|SrcCasterId|String|是|原导播台Id。|
|CasterName|String|是|新导播台名称。|
|ClientToken|String|是|用于保证请求的幂等性。由客户端生成该参数值，要保证在不同请求间唯一，最大不值过 64 个 ASCII 字符。|

## 返回参数 {#section_p4f_qm1_dfb .section}

|名称|类型|描述|
|:-|:-|:-|
|RequestId|String|该条任务请求Id|
|CasterId|String|新导播台ID|

## 示例 {#section_zcx_4j1_dfb .section}

请求示例

```
 https://live.aliyuncs.com?Action=CopyCaster&SrcCasterId=a2b8e671-2fe5-4642-a2ec-bf93880e1a49&CasterName=coco-caster&ClientToken=53200b81-b761-4c10-842a-a0726d972293&<公共请求参数>
```

返回示例

```
{
    "RequestId": "16A96B9A-F203-4EC5-8E43-CB92E68F4CD8",
    "CasterId": "1909f043-e3d3-49e9-82d6-4329ec4a0293"
}
```

## 特殊错误码 {#section_dwd_vph_dfb .section}

|错误代码|描述|Http 状态码|语义|
|:---|:-|:-------|:-|
|IllegalOperation|Permission Denied|401|无权访问导播台|
|InvalidCaster.NotFound|Caster is not found.|404|指定导播台不存在|
|ResourceNumberExceed|Number of resource exceeded video norm|500|导播台资源超限|
|InternalError|The request processing has failed due to some unknown error, exception or failure.|500|内部错误|
|CopyCaster.Timeout|CopyCaster timeout, retry again with the same Token|408|导播台复制超时，请使用当前ClientToken重试|

