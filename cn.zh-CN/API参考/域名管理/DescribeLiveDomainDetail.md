# DescribeLiveDomainDetail {#concept_88333_zh .concept}

获取指定直播域名配置的基本信息。

## 请求参数 {#section_dry_4l1_dfb .section}

|参数|类型|是否必选|示例值|描述|
|:-|:-|:---|:--|:-|
|Action|String|是|DescribeLiveDomainDetail|操作接口名，系统规定参数DescribeLiveDomainDetail|
|DomainName|String|是|live.yourdomain.com|直播域名名称|

## 返回参数 {#section_jry_4l1_dfb .section}

|名称|类型|示例值|描述|
|:-|:-|:--|:-|
|RequestId|String|09ABE829-6CD3-4FE0-AFEE-556113E29727|请求ID|
|DomainDetail| | |直播域名名称|
|  └GmtCreated|String|2018-07-27T06:51:25Z|创建时间|
|  └GmtModified|String|2018-08-07T06:51:25Z|最近修改时间|
|  └DomainStatus|String|online| 直播域名运行状态。

 取值意义：

 - online表示启用；

 - offline表示停用；

 - configuring表示配置中。

 |
|  └Cname|String|live.yourdomain.com.m.test.net|为直播域名生成的一个CNAME域名，需要在域名解析服务商处将直播域名CNAME解析到该域名。|
|  └DomainName|String|live.yourdomain.com|直播域名。|
|  └LiveDomainType|String|liveVideo|直播域名类型。|
|  └Region|String|cn-shanghai|域名所在区域。|
|  └Description|String|test|域名备注，说明信息。|
|  └SSLProtocol|String|on| 是否开启ssl证书。

 - on表示开启；

 - off表示关闭。

 |
|  └SSLPub|String|xxxxxxxxxxxxpublickey|如果开启https，此处为证书公钥。|
|  └Scope|String|domestic| 加速区域。

 返回值范围：domestic，overseas，global。

 |
|  └CertName|String|testCertName|如果开启https，此处为证书名称。|

## 示例 {#section_zcx_4j1_dfb .section}

请求示例

```
 /?Action=DescribeLiveDomainDetail
&DomainName=live.yourdomain.com
&AccessKeyId=XxlctR6mMqO6mhXxX
&Action=DescribeLiveDomainDetail
&<公共请求参数>
```

正常返回示例

JSON格式

```
{
    "DomainDetail":{
        "Cname":"bb.test.com.scdn7mhp.com",
        "DomainName":"bb.test.com",
        "DomainStatus":"online",
        "GmtCreated":"2017-11-27T06:51:25Z",
        "GmtModified":"2017-11-27T06:51:26Z",
        "LiveDomainType":"liveVideo",
        "Region":"cn-beijing",
        "Scope":"domestic"
    },
    "RequestId":"09ABE829-6CD3-4FE0-AFEE-556113E29727"
}
```

异常返回示例

JSON格式

```
{
    "Code":"InternalError",
    "HostId":"live.aliyuncs.com",
    "Message":"The request processing has failed due to some unknown error.",
    "RequestId":"6EBD1BC4-C34D-4BE1-963E-B688A228BE31"
}
```

