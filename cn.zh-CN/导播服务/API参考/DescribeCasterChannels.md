# DescribeCasterChannels {#concept_k5s_nfk_pfb .concept}

查询导播台通道信息列表。

## 请求参数 {#section_fpc_sfk_pfb .section}

|参数|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是|操作接口名，系统规定参数，取值：DescribeCasterChannels|
|CasterId|String|是|导播台Id|

## 返回参数 {#section_wct_5fk_pfb .section}

|参数|类型|描述|
|:-|:-|:-|
|RequestId|String|该条任务请求Id|
|Channels|\[\]Channel|通道列表|

Channel

|参数|类型|描述|
|:-|:-|:-|
|ChannelId|String|通道位置ID。布局应用通道ID，每个位置至多设置一个视频源，格式需符合“RV01...RV12”|
|ResourceId|String|视频源Id|
|StreamUrl|String|通道输出地址|

## 示例 {#section_rs2_xfk_pfb .section}

请求示例

```
https://live.aliyuncs.com?Action=SetCasterChannel&CasterId=a2b8e671-2fe5-4642-a2ec-bf93880e1a49&<公共请求参数>
```

返回示例

```
{
    "RequestId": "3be7ade8-d907-483c-b24a-0dad4595beaf",
    "Channels": [
        {
            "ChannelId": "RV01",
            "ResourceId":"3be7ade8-d907-483c-b24a-0da827389387",
            "StreamUrl":"http://XXXXXX/XXXXXX/XXXXXXX.flv"
        }
    ]
}
```

## 特殊错误码 {#section_w2f_zfk_pfb .section}

|错误代码|描述|Http状态码|语义|
|:---|:-|:------|:-|
|PermissionDenied|Permission Denied|401|无权访问导播台|
|InvalidCaster.NotFound|Caster is not found.|404|指定导播台不存在|
|InternalError|InternalError|500|内部错误|

