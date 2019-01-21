# Ingest URL and streaming URL \(Encoding\) {#concept_vnm_ptx_wfb .concept}

Alibaba Cloud’s ApsaraVideo Live service provides stream ingestion and live streaming service which are triggered. You are not required to create resource, but create an ingest domain and a streaming domain that have completed ICP filing, CNAME configuration and authorization. And you can quickly get the corresponding ingest URL and streaming URL based on URL splicing rules. This article introduces the splicing method of the ingest URL and the streaming URL of the live activities which perform encoding.

**Note:** 

-   This article introduces how to get the spliced URLs manually. You can also get the ingest URL and the streaming URL in the console. For more information, see [Configure edge ingestion](reseller.en-US/User Guide (New console)/Configure push streaming and live streaming/Configure edge ingestion.md#).
-   If you want to create multiple live activities , you can also splice the ingest URL and the streaming URL in bulk. For more information, see [Create multiple live activities](reseller.en-US/User Guide (New console)/Configure push streaming and live streaming/Create multiple live activities.md#).
-   If you don't configure encoding service for your live activities, for more information about the splicing rules of ingest URL and streaming URL, see [Ingest URL and streaming URL \(Original\)](reseller.en-US/User Guide (New console)/Configure push streaming and live streaming/Ingest URL and streaming URL/Ingest URL and streaming URL (Original).md#).
-   In this article, the ingest URL and the streaming URL in the example are for your reference only. You can follow the splicing rules to get your own ingest URL and streaming URL by using your ingest domain, streaming domain, Application Name, Stream Name and the authentication string obtained by authentication.

## Prerequisites {#section_rx2_vkx_wfb .section}

Perform the following operations to get the authorized ingest URL and streaming URL:

-   Add a domain name

    You must first created an ingest domain and a streaming domain that have completed ICP filing. For more information, see [Add a domain name](reseller.en-US/User Guide (New console)/Domain names management/Manage a domain name/Add a domain name.md#).

-   Configure CNAME

    After adding a domain, you must configure the CNAME for it to take effect. For more information about how to configure CNAME, see [Configure CNAME](reseller.en-US/User Guide (New console)/Domain names management/Configure CNAME.md#).

-   Associate domain names

    After adding domain names, you must associate the ingest domain and the streaming domain before you perform stream ingestion and live streaming operations. For more information, see [Associate domain names](reseller.en-US/User Guide (New console)/Domain names management/Manage a domain name/Associate domain names.md#).

-   Configuration authentication

    The authorization function is enabled by default. We recommend that you keep it enabled; otherwise, a risk of bootlegging may occur. If you want to disable authentication function, contact your business manager or open a ticket You can use the default authentication configuration, or you can customize authentication. For more information, see [Configure authentication](reseller.en-US/User Guide (New console)/Domain names management/Access control/Configuration authentication.md#).

    **Note:** If you want to disable the authentication function due to special scenarios, open a ticket. For more information about how to get unauthorized ingest URL and streaming URL, see [Ingest URL and streaming URL \(Original\)](reseller.en-US/User Guide (New console)/Configure push streaming and live streaming/Ingest URL and streaming URL (Not authenticated)/Ingest URL and streaming URL (Original).md#) and [Ingest URL and streaming URL \(Encoding\)](reseller.en-US/User Guide (New console)/Configure push streaming and live streaming/Ingest URL and streaming URL (Not authenticated)/Ingest URL and streaming URL (Encoding).md#).


## How do I get encoding ingest URL? {#section_esh_wyx_wfb .section}

-   Generation rules of ingest URL

    ApsaraVideo Live service supports ingest URL in RTMP format only.

    The ingest URL format is `RTMP://ingest domain name/AppName/StreamName? authentication string`

-   Examples

    Example: the ingest domain is `push.aliyunlive.com`, the Application Name is app, the Stream Name is stream, and the authentication key is 123, then the ingest URL is `RTMP://push.aliyunlive.com/app/stream? auth_key=timestamp-rand-uid-md5hash`


## How do I get encoding streaming URL? {#section_g4t_p5c_bfb .section}

You must first configure encoding. ApsaraVideo Live supports default encoding and custom encoding. After you configure encoding and obtain the ID, you can generate the encoding streaming URL based on the generation rules.

1.  Configure encoding templates.
    -   Configure default encoding
        1.  Log on to the [ApsaraVideo Live console](https://partners-intl.aliyun.com/login-required#/live).
        2.  Click **Domains**.
        3.  Select the **Streaming Domain**, and click **Stream Settings**.
        4.  In **Encoding Settings**, select **Default**, and click **Add**.

            ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/23686/154806368837638_en-US.png)

    -   Configure custom encoding
        1.  Log on to the ApsaraVideo Live console.
        2.  Click **Domains**.
        3.  Select the **Streaming Domain**, and click **Stream Settings**.
        4.  In **Encoding Settings**, select **Custom**, and click **Add**.

            ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/23686/154806368837640_en-US.png)

2.  Get ID.
    -   Get the ID in the ApsaraVideo Live console.

        You can obtain the corresponding template ID by following the previous steps.

    -   Get the ID by using API.

        You can call the `DescribeLiveStreamTranscodeInfo` interface, and the system returns the template ID. For more information, see [DescribeLiveStreamTranscodeInfo](https://www.alibabacloud.com/help/zh/doc-detail/45048.htm?spm=a2c63.p38356.b99.112.786d7e67D5ejMm).

        In addition, users can customize encoding settings based on added fields. For more information about getting custom ID, see [AddCustomLiveStreamTranscode](https://www.alibabacloud.com/help/zh/doc-detail/66944.htm?spm=a2c63.p38356.b99.110.6b2f81477s8SMF).

3.  Generation rules of encoding URL.

    -   Streaming URL supports RMTP, FLV, and HLS formats. For encoding URLs in different formats, you must add `_templateid` following `StreamName`.
        -   RTMP format:`rtmp://streaming domain name/AppName/StreamName{_templateid}? authentication string`
        -   FLV format:`http://streamingdomain /AppName/StreamName{_templateid}.flv? authentication string`
        -   HLS format:`http://streamingdomain /AppName/StreamName{_templateid}.m3u8? authentication string`

            **Note:** M3u8 encoding URL is already supported. If you have more requirements, open a ticket.

    -   Examples

        For example, the streaming domain name is `play.aliyunlive.com`, the Application Name is app, the Stream Name is stream, and the authentication key is 456, then the streaming URL is:

        -   RTMP-based streaming URL `rtmp://play.aliyunlive.com/app/stream_sd? auth_key=timestamp-rand-uid-md5hash`
        -   FLV-based streaming URL `http://play.aliyunlive.com/app/stream_sd.flv? auth_key=timestamp-rand-uid-md5hash`
        -   HLS-based streaming URL `http://play.aliyunlive.com/app/stream_sd.m3u8? auth_key=timestamp-rand-uid-md5hash`
    Authentication field description, see [Democode](../../../../../reseller.en-US/Best Practices/Live video security/Authentication code example.md#).

    |Field|Description|
    |:----|:----------|
    |timestamp|expire time, positive integer, fixed length 10, seconds measured from 1970-01-01. Used to control expire time, integer of 10 digits, expire time 1800s.|
    |rand|random number, we recommend that you use UUID \(not including hyphen“-”, for example, 477b3bbc253f467b8def6711128c7bec format\)|
    |uid|not used yet \(set to 0\)|
    |md5hash|verification string calculated according to md5 algorithm, lowercase letters and digits \(0-9 and a-z\) are supported, fixed length 32|


