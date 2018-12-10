# DescribeCasterSceneAudio {#concept_zb4_zmd_pfb .concept}

查询场景音频配置信息。

## 请求参数 {#section_wbs_wdd_pfb .section}

|参数|类型|是否必选|描述|
|:-|:-|:---|:-|
|Action|String|是|操作接口名，系统规定参数，取值：DescribeCasterSceneAudio|
|CasterId|String|是|导播台Id|
|SceneId|String|是|场景Id|

## 返回参数 {#section_fz3_12d_pfb .section}

|参数|类型|描述|
|:-|:-|:-|
|RequestId|String|该条任务请求Id。|
|AudioLayers|\[\]audioLayer|Audiolayer配置列表。|
|MixList|\[\]String|位置关联列表。与AudioLayers顺序保持一致。

|
|FollowEnable|Integer|是否启用音频跟随。默认启用音频跟随。

-   0：混音模式，
-   1：音频跟随视频模式。

|

## 示例 {#section_l4v_c2d_pfb .section}

请求示例

```
https://live.aliyuncs.com?Action=DescribeCasterSceneAudio&CasterId=97df6b7f-3490-47d2-ac50-883387654365&SceneId=97df6b7f-3490-47d2-ac50-883390876576&<公共请求参数>
返回示例
```

返回示例

```
{
    "RequestId": "97df6b7f-3490-47d2-ac50-8833e1b64597",
    "Content": {
      "MixList": [
          "1"
      ],
      "AudioLayers": [
          {
              "ValidChannel": "all",
              "VolumeRate": 1
          }
      ],
      "FollowEnable": 1
    }
}
```

## 特殊错误码 {#section_ktw_22d_pfb .section}

|错误代码|描述|Http状态码|语义|
|:---|:-|:------|:-|
|PermissionDenied|Permission Denied|401|无权访问导播台|
|InvalidCaster.NotFound|Caster is not found|404| |
|InvalidSceneId.Malformed|SceneId is mandatory for this action.|场景ID为空| |
|InvalidScene.NotFound|Scene is not found|404|指定场景不存在|
|InternalError|The request processing has failed due to some unknown error, exception or failure.|500|内部错误|

