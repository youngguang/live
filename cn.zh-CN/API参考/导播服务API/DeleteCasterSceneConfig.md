# DeleteCasterSceneConfig {#concept_m44_lgk_pfb .concept}

清除指定场景配置信息。

## 请求参数 {#section_fpc_sfk_pfb .section}

|参数|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是|操作接口名，系统规定参数，取值：DeleteCasterSceneConfig|
|CasterId|String|是|导播台Id|
|SceneId|String|是|场景Id|
|Type|String|是| -   Component-清除组件配置
-   Layout-清除布局配置
-   All-清除组件和布局配置

 |

## 返回参数 {#section_wct_5fk_pfb .section}

|参数|类型|描述|
|:-|:-|:-|
|RequestId|String|该条任务请求Id|

## 示例 {#section_rs2_xfk_pfb .section}

请求示例

```
https://live.aliyuncs.com?Action=DeleteCasterSceneConfig&CasterId=a2b8e671-2fe5-4642-a2ec-bf93880e1a49&SceneId=21926b36-7dd2-4fde-ae25-51b5bc8e52d8&Type=Component&<公共请求参数>
```

返回示例

```
{
    "RequestId": "16A96B9A-F203-4EC5-8E43-CB92E68F4CD8",
}
```

## 特殊错误码 {#section_w2f_zfk_pfb .section}

|错误代码|描述|Http状态码|语义|
|:---|:-|:------|:-|
|PermissionDenied|Permission Denied|401|无权访问导播台|
|InvalidCaster.NotFound|Caster is not found.|404|指定导播台不存在|
|InvalidScene.NotFound|Scene is not found.|404|指定场景不存在|
|IncorrectSceneStatus|Scene is not started.|400|场景状态不允许当前操作|
|InternalError|InternalError|500|内部错误|

