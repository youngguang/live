# AddLiveDomain {#concept_88327_zh .concept}

添加直播域名，一次只能提交一个域名。

限制条件：

-   创建直播域名之前，必须先开通视频直播服务。

-   直播域名必须已备案完成。


## 请求参数 { .section}

|参数|类型|是否必选|示例值|描述|
|:-|:-|:---|:--|:-|
|Action|String|是|AddLiveDomain| 操作接口名，系统规定参数。

 取值：AddLiveDomain

 |
|DomainName|String|是|live.yourdomain.com| 需要接入直播的域名。

 支持泛域名，以符号“.”开头，如：.a.com。

 |
|LiveDomainType|String|是|liveVideo| 域名业务类型

 取值：liveVideo、liveEdge，分别对应播流域名、边缘推流域名。

 |
|Region|String|是|cn-beijing|直播域名单元化信息。目前单元化信息取值有cn-beijing、cn-shanghai、ap-southeast-1。|
|CheckUrl|String|否|[http://live.yourdomain.com/status.html](http://live.yourdomain.com/status.html)|检查域名是否能正常访问url。|
|Scope|String|否|domestic| 加速区域。

-   取值范围：domestic、overseas、global，分别对应国内、海外、全球。
-   默认domestic。
-   国际用户、国内L3及以上用户设置有效。

 |

## 返回参数 { .section}

|参数|类型|示例值|描述|
|:-|:-|:--|:-|
|RequestId|String|16A96B9A-F203-4EC5-8E43-CB92E68F4CD8|请求ID|

## 示例 { .section}

请求示例

```
/?DomainName=live.yourdomain.com
&LiveDomainType=liveVideo
&Region=cn-beijing
&AccessKeyId=XxlctR6mMqO6mhXxX
&Action=AddLiveDomain
&CheckUrl=http://live.yourdomain.com/status.html
&Scope=domestic
&<公共请求参数>

```

正常返回示例

JSON格式

```language-json
{
	"RequestId":"15C66C7B-671A-4297-9187-2C4477247A74"
}

```

异常返回示例

JSON格式

```language-json
{
	"Code":"InternalError",
	"HostId":"live.aliyuncs.com",
	"Message":"The request processing has failed due to some unknown error.",
	"RequestId":"6EBD1AC4-C34D-4BE1-963E-B688A228BE31"
}

```

## 错误码 { .section}

 [查看本产品错误码](https://error-center.aliyun.com/status/product/live) 

