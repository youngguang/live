# DescribeCasterScenes {#reference2606 .reference}

查询场景信息列表。

## 请求参数 {#section_k4f_qm1_dfb .section}

|参数|类型|是否必选|描述|
|:-|:-|:---|:-|
|Action|String|是|操作接口名，系统规定参数，取值：DescribeCasterScenes|
|CasterId|String|是|导播台ID|
|SceneId|String|否|场景ID|

## 返回参数 {#section_p4f_qm1_dfb .section}

|名称|类型|描述|
|:-|:-|:-|
|RequestId|String|该条任务请求ID|
|SceneList|\[\]Scene|场景信息列表|

Scene

|名称|类型|描述|
|:-|:-|:-|
|SceneId|String|场景ID。|
|SceneName|String|场景名称。|
|OutputType|Integer|是否正式输出。-   0：输出预监
-   1：输出正式

|
|LayoutId|String|布局ID。|
|StreamUrl|String|输出流地址。|
|ComponentIds|\[\]String|组件Id列表。|
|Status|Integer|场景状态。 -   0：关闭
-   1：开启

|
|StreamInfos|StreamInfo\[\]|播放地址列表。|

StreamInfo

|名称|类型|描述|
|:-|:-|:-|
|TranscodeConfig|String|转码配置。l-   sd：标清
-   lld：流畅
-   lud：超清
-   lhd：高清

|
|VideoFormat|String|格式 flv，mp4，m3u8|
|OutputStreamUrl|String|播放地址|

## 示例 {#section_zcx_4j1_dfb .section}

请求示例

```
 https://live.aliyuncs.com?Action=DescribeCasterScenes&CasterId=80787064-1c94-4dc1-85ce-9409960a9bf0&<公共请求参数>
```

返回示例

JSON格式

```
{
    "RequestId": "CF60DB6A-7FD6-426E-9288-122CC1A52FA7",
    "SceneList": [{
            "SceneId": "b5f8c837-ceeb-424f-b30b-68e94e864995",
            "SceneName": "scene1",
            "LayoutId": "37cb2f8b-f152-4338-b928-6704f71dbf41",
            "StreamUrl": "rtmp://XXXXXX/XXXXXX/b5447c21fcfe444c9e9b6f7ba208f141",
            "OutputType": 0,
      "Status": 1
        },
        {
            "SceneId": "86f661ee-c893-4aae-a852-ccacf2001dad",
            "SceneName": "scene2",
            "StreamUrl": "rtmp://XXXXXX/XXXXXX/37087ce7a76e424bbb61e8b5eefe76ed",
            "OutputType": 1,
      "Status": 1,
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
        }
    ]
}
```

## 特殊错误码 {#section_w32_ln3_dfb .section}

|错误代码|描述|Http 状态码|语义|
|:---|:-|:-------|:-|
|IllegalOperation|Permission Denied|401|无权访问导播台|
|InvalidCaster.NotFound|Caster is not found.|404|指定导播台不存在|
|InternalError|The request processing has failed due to some unknown error, exception or failure.|500|内部错误|
|InvalidConfiguration.NotFound|DomainName is not configured|404|域名配置无效或尚未配置，请先配置域名|

