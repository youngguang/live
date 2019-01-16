# Return result {#concept_50285_zh .concept}

The data returned after the API service call adopts a uniform format:

If the returned HTTP status code is 2xx, it indicates the call is a success. If the returned HTTP status code is 4xx or 5xx, then it is a failed call. The two primary formats for the data returned after a successful call are XML and JSON. The external system can customize the returned data format by passing in a parameter in the request, and XML is adopted by default.

**Note:** In the returned examples in this document, we adjusted the format of returned result to make it easier for you to view the content. The actual returned result does not go through the line breaks, indentation, or other layouts.

## Successful results {#section_r2l_tbv_cfb .section}

JSON example

```language-json
{
	"RequestId":"16A96B9A-F203-4EC5-8E43-CB92E68F4CD8"
}

```

## Error results { .section}

When an error occurs in an interface call, no result data is returned. You can see the error code corresponding to each interface and the Error Code Table as follows to locate the cause of the error. When an error occurs in a call, an HTTP status code of 4xx or 5xx is returned for the HTTP request. The returned message body contains the specific error code and error message. The message body also contains a globally unique RequestId and the requested HostId. If you fail to locate the cause of the error, contact our customer service and provide the HostId and RequestId for us to solve the problem as quickly as possible.

JSON example

```language-json
{
	"Code":"InternalError",
	"HostId":"live.aliyuncs.com",
	"Message":"The request processing has failed due to some unknown error.",
	"RequestId":"6EBD1AC4-C34D-4AE1-963E-B688A228BE31"
}

```

## Public error code table { .section}

For more information about error code, see [API error center](https://error-center.aliyun.com/status/product/Public).

