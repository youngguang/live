# Public parameters {#concept_50284_zh .concept}

Public parameters refers to the parameters that every interface call uses, including public request parameters and public response parameters.

## Public request parameters { .section}

Public request parameters refer to the request parameters that every interface uses.

|Parameters|Type|Required|Description|
|:---------|:---|:-------|:----------|
|Version|String|Yes|API version.-   The format is YYYY-MM-DD.
-   The current version is 2016-11-01.

|
|AccessKeyId|String|Yes|The Key ID provided by Alibaba Cloud for you to access services.|
|Signature|String|Yes|The request signature. See [Signature](reseller.en-US/API Reference/APIs invoke/Signature.md#) for the signature calculation method.|
|SignatureMethod|String|Yes|The mode of the signature. HMAC-SHA1 is supported currently.|
|Timestamp|String|Yes|The timestamp to request.-   The date format follows the ISO8601 standard and uses UTC time.
-   Format: YYYY-MM-DDThh:mm:ssZ.
-   Example: 2014-11-11T12:00:00Z \(equivalent to 20:00:00 on November 11, 2014, Beijing time\).

|
|SignatureVersion|String|Yes|Signature algorithm version. The current version is 1.0.|
|SignatureNonce|String|Yes|The unique random number that is used to prevent network replay attacks. You must use different random numbers for different requests.|
|ResourceOwnerAccount|String|No|The resource owner account for this API request, that is the login user name. For more information about using this parameter, see [RAM resource authorization](reseller.en-US/API Reference/API authentication rules.md#).\( You can only use this parameter in the Action of the RAM in which the live resources can be authorized, or the request is rejected.\)|
|Format|String|No|Type of value returned, JSON and XML supported. Default value: XML.|

## Examples { .section}

```
https://live.aliyuncs.com/
? Format=xml
&Version=2016-11-01
&Signature=Pc5WB8gokVn0xfeu%2FZV%2BiNM1dgI%3D
&SignatureMethod=HMAC-SHA1
&SignatureNonce=15215528852396
&SignatureVersion=1.0
&AccessKeyId=key-test
&Timestamp=2012-06-01T12:00:00Z
…

```

## Public response parameters { .section}

Each time you make a call to an API, the system returns a unique identification code \(RequestId\), regardless whether the request is successful.

## Examples { .section}

-   XMLexample

    ```
    <? xml version="1.0" encoding="UTF-8"? >
    <! --Result Root Node-->
    <Interface Name+Response>
    <! --Return Request Tag-->
    <RequestId>4C467B38-3910-447D-87BC-AC049166F216</RequestId>
    <! --Response Result Data-->
    </Interface Name+Response>
    
    ```

-   JSON example

    ```
    {
    "RequestId": "4C467B38-3910-447D-87BC-AC049166F216",
    /* Returned data*/
    }
    
    ```


