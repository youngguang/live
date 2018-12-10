# ModifyCasterVideoResource {#reference1531 .reference}

修改视频资源。

## 请求参数 {#section_k4f_qm1_dfb .section}

|参数|类型|是否必选|描述|
|:-|:-|:---|:-|
|Action|String|是|操作接口名，系统规定参数，取值：ModifyCasterVideoResource|
|CasterId|String|是|导播台ID|
|ResourceId|String|是|资源ID|
|ResourceName|String|否|视频源名称|
|LiveStreamUrl|String|否|直播流地址|
|MaterialId|String|否|素材Id|
|VodUrl|String|否|点播文件地址，当且仅当资源为文件视频，且视频文件未导入素材库时使用，仅限mp4、flv、ts、mov格式。|
|RepeatNum|Integer|否|仅对文件视频有效，表示播放完后重复继续播放的次数。-   默认值：0，表示不重复播放。
-   -1：表示一直循环重复。

|
|BeginOffset|Integer|否|仅对文件视频有效，BeginOffset值大于0，表示从相对于首帧的偏差时间作为开始读取的位置。单位：毫秒

\(ms\)|
|EndOffset|Integer|否|仅对文件视频有效。-   EndOffset值大于0时，表示从相对于首帧的偏差时间为结束读取的位置。
-   EndOffset值小于0时，表示相对于最后一帧的偏差时间作为结束读取的位置。
-   单位：\(ms\)

|

## 返回参数 {#section_p4f_qm1_dfb .section}

|名称|类型|描述|
|:-|:-|:-|
|RequestId|String|该条任务请求ID|

## 示例 {#section_zcx_4j1_dfb .section}

请求示例

```
 https://live.aliyuncs.com?Action=ModifyCasterVideoResource&CasterId=80787064-1c94-4dc1-85ce-9409960a9bf0&ResourceId=05ab713c-676e-49c0-96ce-cc408da1b314&ResourceName=re-Name&aterialId=80787064-1c94-4dc1-85ce-940987362536&<公共请求参数>
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
|InvalidParameter.Malformed|Specified parameter LiveStreamUrl, MaterialId can’t be both empty.|400|素材与直播流配置同时为空|
|InvalidLiveStreamUrl.Malformed|Specified parameter LiveStreamUrl is invalid.|400|流地址信息为空字符|
|InvalidMaterialId.Malformed|Specified parameter MaterialId is invalid.|400|素材信息为空字符|
|InvalidResource.NotFound|Resource is not found.|404|指定资源不存在|
|InternalError|The request processing has failed due to some unknown error, exception or failure.|500|内部错误|

