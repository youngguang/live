# DescribeCasterStreamUrl {#reference2547 .reference}

查询导播台流信息列表。

## 请求参数 {#section_k4f_qm1_dfb .section}

|参数|类型|是否必选|描述|
|:-|:-|:---|:-|
|Action|String|是|操作接口名，系统规定参数，取值：DescribeCasterStreamUrl|
|CasterId|String|是|导播台Id|

## 返回参数 {#section_p4f_qm1_dfb .section}

|名称|类型|描述|
|:-|:-|:-|
|RequestId|String|该条任务请求Id|
|CasterId|String|导播台Id|
|CasterStreams|\[\]CasterStream|导播台流信息列表|

CasterStream

|名称|类型|描述|
|:-|:-|:-|
|SceneId|String|场景Id|
|StreamUrl|String|输出流地址|
|OutputType|Integer|是否正式输出。-   0：输出预览
-   1：输出正式

|
|StreamInfos|StreamInfo\[\]|播放地址列表|

StreamInfo

|名称|类型|描述|
|:-|:-|:-|
|TranscodeConfig|String|转码配置。-   lsd：标清
-   lld：流畅
-   lud：超清
-   lhd：高清

|
|VideoFormat|String|格式 flv，rtmp，m3u8。|
|OutputStreamUrl|String|播放地址。|

## 示例 {#section_zcx_4j1_dfb .section}

请求示例

```
 https://live.aliyuncs.com?Action=DescribeCasterStreamUrl&CasterId=a2b8e671-2fe5-4642-a2ec-bf93880e1a49&<公共请求参数>
```

返回示例

```
{
    "RequestId": "16A96B9A-F203-4EC5-8E43-CB92E68F4CD8",
    "CasterId": "a2b8e671-2fe5-4642-a2ec-bf93880e1a49",
    "CasterStreams": [
        {
            "StreamUrl": "rtmp://XXXXXX/caster/1975ee99db904ebb83908d43bc878188?auth_key=1506396160-0-0-063397072a9980fd418d43eb00e02e09",
            "SceneId": "23ca74e0-aca3-4e7a-8561-9d96f525dd4a",
            "OutputType": 1,
            "StreamInfos": [
                {
                    "VideoFormat": "flv",
                    "OutputStreamUrl": "http://XXXXXX/caster/fb628e2469f94f2aa2c0c219af8b2527_lld.flv?auth_key=1506396160-0-0-7de771a77102680861853af862d5eaf0",
                    "TranscodeConfig": "lld"
                },
                {
                    "VideoFormat": "rtmp",
                    "OutputStreamUrl": "rtmp://XXXXXX/caster/fb628e2469f94f2aa2c0c219af8b2527_lld?auth_key=1506396160-0-0-77ed32cd82ed32ccd51a832b5765814c",
                    "TranscodeConfig": "lld"
                },
                {
                    "VideoFormat": "m3u8",
                    "OutputStreamUrl": "http://XXXXXX/caster/fb628e2469f94f2aa2c0c219af8b2527.m3u8?auth_key=1506396160-0-0-d51f0512dcf76aa749f79f53ae6421d2",
                    "TranscodeConfig": "lld"
                }
            ]
        },
        {
            "StreamUrl": "rtmp://XXXXXX/caster/3a2e3cf978f3496f96d44e28b54295fa?auth_key=1506396160-0-0-6182084bd33e93a72029764f5cfbdc21",
            "SceneId": "9445dbed-7aef-4cae-925f-8a3a026fc120",
            "OutputType": 0
        }
    ]
}
```

## 特殊错误码 {#section_w32_ln3_dfb .section}

|错误代码|描述|Http 状态码|语义|
|:---|:-|:-------|:-|
|IllegalOperation|Permission Denied|401|无权访问导播台|
|InvalidCaster.NotFound|Caster is not found.|404|指定导播台不存在|
|InvalidScene.NotFound|Scene is not found.|404|指定场景不存在|
|InternalError|The request processing has failed due to some unknown error, exception or failure.|500|内部错误|

