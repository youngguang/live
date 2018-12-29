# SetCasterSceneConfig {#reference1042 .reference}

全量设置场景配置，清空场景配置，并将布局信息设置并生效至指定场景。

## 请求参数 {#section_k4f_qm1_dfb .section}

|参数|类型|是否必选|描述|
|:-|:-|:---|:-|
|Action|String|是|操作接口名，系统规定参数，取值：SetCasterSceneConfig|
|CasterId|String|是|导播台ID|
|SceneId|String|是|场景ID|
|LayoutId|String|是|布局ID|
|ComponentIds|String\[\]|是|组件ID列表，数组内按照由下至上的顺序排列组件|

## 返回参数 {#section_p4f_qm1_dfb .section}

|名称|类型|描述|
|:-|:-|:-|
|RequestId|String|该条任务请求ID|

## 示例 {#section_zcx_4j1_dfb .section}

请求示例

```
 https://live.aliyuncs.com?Action=SetCasterSceneConfig&CasterId=80787064-1c94-4dc1-85ce-9409960a9bf0&SceneId=242b4e2c-c30f-4442-85ba-2e3e4e3dec1b&LayoutId=0c6da077-f037-49e8-8440-3be133938359&<公共请求参数>
```

返回示例

JSON格式

```
{
    "RequestId": "CF60DB6A-7FD6-426E-9288-122CC1A52FA7"
}
```

## 特殊错误码 {#section_w32_ln3_dfb .section}

|错误代码|描述|Http 状态码|语义|
|:---|:-|:-------|:-|
|IllegalOperation|Permission Denied|401|无权访问导播台|
|InvalidCaster.NotFound|Caster is not found.|404|指定导播台不存在|
|InvalidScene.NotFound|Scene is not found.|404|指定场景不存在|
|IncorrectSceneStatus|Scene is not started.|400|场景状态不允许当前操作|
|InvalidLayout.NotFound|Layout is not found.|404|指定布局不存在|
|InternalError|The request processing has failed due to some unknown error, exception or failure.|500|内部错误|

