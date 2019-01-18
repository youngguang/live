# Ingest URL and streaming URL \(Original\) {#concept_e3z_kn3_bfb .concept}

Alibaba Cloud’s ApsaraVideo Live service provides stream ingestion and live streaming service which are triggered. You are not required to create resource, but create an ingest domain name and a streaming domain name that have completed ICP filing, CNAME configuration and authorization. And you can quickly get the corresponding ingest URL and streaming URL based on URL splicing rules. This article introduces the splicing method of the ingest URL and the streaming URL of the live activities which do not perform encoding.

**Note:** 

-   This article introduces how to get the spliced URLs manually. You can also get the ingest URL and the streaming URL in the console. For more information, see [Configure edge ingestion](reseller.en-US/User Guide (New console)/Configure push streaming and live streaming/Configure edge ingestion.md#).
-   If you want to create multiple live activities , you can also splice the ingest URL and the streaming URL in bulk. For more information , see [Create multiple live activities](reseller.en-US/User Guide (New console)/Configure push streaming and live streaming/Create multiple live activities.md#).
-   If you configure encoding service for your live activities, for more information about the splicing rules of ingest URL and streaming URL, see [Ingest URL and streaming URL \(Encoding\)](reseller.en-US/User Guide (New console)/Configure push streaming and live streaming/Ingest URL and streaming URL/Ingest URL and streaming URL (Encoding).md#).
-   In this article, the ingest URL and the streaming URL in the example are for your reference only. You can follow the splicing rules to get your own ingest URL and streaming URL by using your ingest domain, streaming domain, Application Name, Stream Name and the authentication string obtained by authentication.

## Prerequisites {#section_rx2_vkx_wfb .section}

Perform the following operations to get the authorized ingest URL and streaming URL:

-   Add a domain name

    You must first created an ingest domain and a streaming domain that have completed ICP filing. For more information, see [Add a domain name](reseller.en-US/User Guide (New console)/Domain names management/Manage a domain name/Add a domain name.md#).

-   Configure CNAME

    After adding a domain, you must configure the CNAME for it to take effect. For more information about how to configure CNAME, see [Configure CNAME](reseller.en-US/User Guide (New console)/Domain names management/Configure CNAME.md#).

-   Associate domain names

    After adding domain names, you must associate the ingest domain and the streaming domain before you perform stream ingestion and live streaming operations. For more information, see [Associate domain names](reseller.en-US/User Guide (New console)/Domain names management/Manage a domain name/Associate domain names.md#).

-   Configuration authorization

    The authorization function is enabled by default. We recommend that you keep it enabled; otherwise, a risk of bootlegging may occur. If you want to disable authorization function, contact your business manager or open a ticket You can use the default authorization configuration, or you can customize authorization. For more information, see [Configure authentication](reseller.en-US/User Guide (New console)/Domain names management/Access control/Configuration authentication.md#).

    **Note:** If you want to disable the authentication function due to special scenarios, open a ticket. For more information about how to get unauthorized ingest URL and streaming URL, see [Ingest URL and streaming URL \(Original\)](reseller.en-US/User Guide (New console)/Configure push streaming and live streaming/Ingest URL and streaming URL (Not authenticated)/Ingest URL and streaming URL (Original).md#) and [Ingest URL and streaming URL \(Encoding\)](reseller.en-US/User Guide (New console)/Configure push streaming and live streaming/Ingest URL and streaming URL (Not authenticated)/Ingest URL and streaming URL (Encoding).md#).


## How do I generate an ingest URL? {#section_zjh_j5c_bfb .section}

-   Generation rules of ingest URL

    ApsaraVideo Live service supports ingest URL in RTMP format only.

    The ingest URL format is `RTMP://ingest domain name/AppName/StreamName? authentication string`

-   Example: the ingest domain name is `push.aliyunlive.com`, the Application Name is app, the Stream Name is stream, and the authentication key is 123, then the ingest URL is `RTMP://push.aliyunlive.com/app/stream? auth_key=timestamp-rand-uid-md5hash`

## How do I generate a streaming URL? {#section_wg1_m5c_bfb .section}

-   Generation rules of streaming URL

    Streaming URL support RMTP, FLV, and HLS formats as follows:

    -   `RTMP:rtmp://streaming domain name/AppName/StreamName? authentication string`
    -   `FLV:http://streaming domain name/AppName/StreamName.flv? authentication string`
    -   `HLS:http://streaming domain name/AppName/StreamName.m3u8? authentication string`

        **Note:** M3u8 encoding URL is already supported. If you have more requirements, open a ticket.

-   Examples

    For example, the streaming domain name is `play.aliyunlive.com`, the Application Name is app, the Stream Name is stream, and the authentication key is 456, then the streaming URL is:

    -   `RTMP:rtmp://play.aliyunlive.com/app/stream? auth_key=timestamp-rand-uid-md5hash`
    -   `FLV:http://play.aliyunlive.com/app/stream.flv? auth_key=timestamp-rand-uid-md5hash`
    -   `HLS:http://play.aliyunlive.com/app/stream.m3u8? auth_key=timestamp-rand-uid-md5hash`

