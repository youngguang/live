# DeleteCasterLayout {#reference846 .reference}

删除布局数据。

## 请求参数 {#section_k4f_qm1_dfb .section}

|参数|类型|是否必选|描述|
|:-|:-|:---|:-|
|Action|String|是|操作接口名，系统规定参数，取值：DeleteCasterLayout|
|CasterId|String|是|导播台Id|
|LayoutId|String|是|布局Id|

## 返回参数 {#section_p4f_qm1_dfb .section}

|名称|类型|描述|
|:-|:-|:-|
|RequestId|String|该条任务请求Id|
|CasterId|String|导播台Id|
|LayoutId|String|布局Id|

## 示例 {#section_zcx_4j1_dfb .section}

请求示例

```
 https://live.aliyuncs.com?Action=DeleteCaster&CasterId=a2b8e671-2fe5-4642-a2ec-bf93880e1a49&LayoutId=21926b36-7dd2-4fde-ae25-51b5bc8e52d8&<公共请求参数>
```

返回示例

```
{
    "RequestId": "16A96B9A-F203-4EC5-8E43-CB92E68F4CD8",
    "CasterId": "a2b8e671-2fe5-4642-a2ec-bf93880e1a49",
    "LayoutId": "21926b36-7dd2-4fde-ae25-51b5bc8e52d8"
}
```

## 特殊错误码 {#section_w32_ln3_dfb .section}

|错误代码|描述|Http 状态码|语义|
|:---|:-|:-------|:-|
|IllegalOperation|Permission Denied|401|无权访问导播台|
|InvalidLayout.NotFound|Layout is not found.|404|找不到该布局|
|InternalError|The request processing has failed due to some unknown error, exception or failure.|500|内部错误|

