# DeleteLiveDomainMapping {#concept_88783_zh .concept}

删除直播域名播流域名和推流域名映射关系配置。

## 请求参数 {#section_udb_gl1_dfb .section}

|参数|类型|是否必选|描述|
|:-|:-|:---|:-|
|Action|String|是|操作接口名，系统规定参数，取值：DeleteLiveDomainMapping|
|PushDomain|String|是|您的推流域名，域名类型需为liveEdge|
|PullDomain|String|是|您的播流域名，域名类型需为liveVideo|

## 返回参数 {#section_a2b_gl1_dfb .section}

|名称|类型|描述|
|:-|:-|:-|
|RequestId|String|该条任务请求ID|

## 示例 {#section_zcx_4j1_dfb .section}

请求示例

```
 https://live.aliyuncs.com?Action=DeleteLiveDomainMapping&PushDomain=test101.cdnpe.com&PullDomain=test102.cdnpe.com&<公共请求参数>
```

返回示例

JSON格式

```
{
    "RequestId": "16A96B9A-F203-4EC5-8E43-CB92E68F4CD8", 
}
```

## 特殊错误码 {#section_f2b_gl1_dfb .section}

|错误代码|描述|Http 状态码|语义|
|:---|:-|:-------|:-|
|InvalidPushDomain.Miss|The specified value of parameter PushDomain is miss.|400|推流域名缺失|
|InvalidPullDomain.Miss|The specified value of parameter PullDomain is miss.|400|播流域名缺失|
|DomainType.Malformed|Your domain type is not live type.|400|业务类型非直播类型|

