# Ingest URL and streaming URL \(Original\) {#concept_ozq_kty_lfb .concept}

The authentication function must be disabled in some special scenarios. This article introduces how to get unauthenticated ingest URL and streaming URL\(original\).

**Note:** 

-   This article introduces how to get the spliced URLs manually. You can also get the ingest URL and the streaming URL in the console. For more information, see [Configure edge ingestion](reseller.en-US/User Guide (New console)/Configure push streaming and live streaming/Configure edge ingestion.md#).
-   If you want to create multiple live activities , you can also splice the ingest URL and the streaming URL in bulk. For more information , see [Create multiple live activities](reseller.en-US/User Guide (New console)/Configure push streaming and live streaming/Create multiple live activities.md#).
-   If you configure encoding service for your live activities, for more information about the generation rules of ingest URL and streaming URL, see [Ingest URL and streaming URL \(Encoding\)](reseller.en-US/User Guide (New console)/Configure push streaming and live streaming/Ingest URL and streaming URL/Ingest URL and streaming URL (Original).md#).
-   In this article, the ingest URL and the streaming URL in the example are for your reference only. You can follow the generation rules to get your own ingest URL and streaming URL by using your ingest domain name, streaming domain name, Application Name, Stream Name and the authentication string obtained by authentication.

## Prerequisites {#section_rx2_vkx_wfb .section}

Perform the following operations to get the ingest URL and streaming URL:

-   Add a domain name

    You must first created an ingest domain and a streaming domain that have completed ICP filing. For more information, see [Add a domain name](reseller.en-US/User Guide (New console)/Domain names management/Manage a domain name/Add a domain name.md#).

-   Configure CNAME

    After adding a domain name, you must configure the CNAME for it to take effect. For more information about how to configure CNAME, see [Configure CNAME](reseller.en-US/User Guide (New console)/Domain names management/Configure CNAME.md#).

-   Associate domain names

    After adding domain names, you must associate the ingest domain and the streaming domain before you perform push streaming and live streaming operations. For more information, see [Associate domain names](reseller.en-US/User Guide (New console)/Domain names management/Manage a domain name/Associate domain names.md#).


## How do I generate original streaming URL? {#section_hlx_4ty_lfb .section}

The streaming URLs are divided into original streaming URL and encoding streaming URL. Original streaming URL is the original video stream without encoding. The splicing rule of URL is `Streaming Domain Name`+`AppName`+`StreamName`

-   Splicing rules of streaming URL

    The streaming URL supports rtmp, FLV, and m3u8 formats as follows:

    -   `RTMP format: rtmp://Streaming Domain Name/AppName/StreamName`
    -   `FLV format: http://Streaming Domain Name/AppName/StreamName.flv`
    -   `M3U8 format: http://Streaming Domain Name/AppName/StreamName.m3u8`
-   Examples

    For example, the streaming domain name is `play.aliyunlive.com`, the Application Name is app, the Stream Name is stream, and the authentication key is 456, then the streaming URL is:

    -   `RTMP format: rtmp://play.aliyunlive.com/app/stream`
    -   `FLV format: http://play.aliyunlive.com/app/stream.flv`
    -   `M3U8 format: http://play.aliyunlive.com/app/stream.m3u8`

        **Note:** M3u8 encoding URL is already supported. If you have more requirements, open a ticket.


## How do I generate an ingest URL? {#section_hsn_yxt_xfb .section}

-   Generation rules of ingest URL

    ApsaraVideo Live service supports ingest URL in RTMP format only.

    The ingest URL format is `RTMP://Ingest Domain Name/APPName/StreamName`

-   Examples

    Example: the ingest domain is `push.aliyunlive.com`, the Application Name is app, the Stream Name is stream, and the authentication key is 123, then the ingest URL is `RTMP://push.aliyunlive.com/app/stream`


