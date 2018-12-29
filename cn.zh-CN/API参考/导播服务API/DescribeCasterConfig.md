# DescribeCasterConfig {#reference2265 .reference}

查询导播台配置信息。

## 请求参数 {#section_k4f_qm1_dfb .section}

|参数|类型|是否必选|描述|
|:-|:-|:---|:-|
|Action|String|是|操作接口名，系统规定参数，取值：DescribeCasterConfig|
|CasterId|String|是|导播台Id|

## 返回参数 {#section_p4f_qm1_dfb .section}

|名称|类型|描述|
|:-|:-|:-|
|RequestId|String|该条任务请求Id。|
|CasterName|String|导播台名称。|
|DomainName|String|域名。|
|TranscodeConfig|TranscodeConfig|转码配置。|
|RecordConfig|RecordConfig|录制配置参数为空时表示不启用录制功能。|
|Delay|Float|延时播放。-   0：禁用延时，
-   大于0：启用延时。

单位：秒|
|UrgentMaterialId|String|备播视频，媒资库素材Id。|
|SideOutputUrl|String|用户自定义导播台旁路输出地址。|
|CallbackUrl|String|用户回调地址。|
|ProgramName|String|轮播台名称。|
|ProgramEffect|Integer|轮播生效标志。-   0：不生效，
-   1：生效。

|
|ChannelEnable|Integer|是否启用Channel。-   0：不启用Channel，
-   1：启用Channel

|

RecordConfig

|参数|类型|描述|
|:-|:-|:-|
|VideoFormat|\[\]videoFormat|录制格式配置|
|OssBucket|String|存储位置|
|Endpoint|String|oss endpoint|

VideoFormat

|参数|类型|描述|
|:-|:-|:-|
|Format|String|录制格式|
|OssObjectPrefix|String|录制文件名|
|SliceOssObjectPrefix|String|切片名称|
|CycleDuration|Integer|录制时长|

TranscodeConfig

|参数|类型|描述|
|:-|:-|:-|
|CasterTemplateId|String|导播台转码模板。lp\_ld：流畅

lp\_sd：标清

lp\_hd：高清

lp\_ud：超清

lp\_ld\_v：竖屏流畅

lp\_sd\_v：竖屏标清

lp\_hd\_v：竖屏高清

lp\_ud\_v：竖屏超清

|
|LiveTemplateIds|\[\]String|直播转码配置。lsd：标清

lld：流畅

lud：超清

lhd：高清自适应转码模板

 daobo-lsd：标清

daobo-lld：流畅

daobo-lud：超清

daobo-lhd：高清

|

## 示例 {#section_zcx_4j1_dfb .section}

请求示例

```
https://live.aliyuncs.com?Action=DescribeCasterConfig&CasterId=a2b8e671-2fe5-4642-a2ec-bf93880e1a49&<公共请求参数> 
```

返回示例

```
{
  "RequestId": "97df6b7f-3490-47d2-ac50-8833e1b64597",
      "CasterName": "coco-caster10",
      "DomainName": "XXXXXX",
      "TranscodeConfig": {
          "CasterTemplate": "lp_hd",
          "LiveTemplate": [
              "lld"
          ]
      },
      "Delay": 0,
      "RecordConfig": {
          "Endpoint": "XXXXXX",
          "OssBucket": "XXXXXX",
          "VideoFormat": [
              {
                  "Format":"flv",
                  "Prefix": "record/{AppName}/{StreamName}",
                  "SlicePrefix":"record/{AppName}/{StreamName}/{UnixTimestamp}",
                  "Interval":3600
               },
              {
                  "Format":"m3u8",
                  "Prefix": "record/{AppName}/{StreamName}",
                  "SlicePrefix":"record/{AppName}/{StreamName}/{UnixTimestamp}",
                  "Interval":3600
               }
          ]
      }
}
```

## 特殊错误码 {#section_w32_ln3_dfb .section}

|错误代码|描述|Http 状态码|语义|
|:---|:-|:-------|:-|
|IllegalOperation|Permission Denied|401|无权访问导播台|
|InvalidCaster.NotFound|Caster is not found|404| |
|InternalError|The request processing has failed due to some unknown error, exception or failure.|500|内部错误|

