# Ingest URL and streaming URL \(Transcoding\) {#concept_txp_k1z_lfb .concept}

In some special scenes, the authorization operation must be disabled. This article introduces how to splice the transcoding streaming URL and the corresponding ingest URL when the authentication function is disabled.

**Note:** 

-   This article introduces how to get the spliced URLs manually. You can also get the ingest URL and the streaming URL in the console. For more information, see [Configure edge ingestion](reseller.en-US/User Guide (New console)/Configure push streaming and live streaming/Configure edge ingestion.md#).
-   If you want to create multiple live activities , you can also splice the ingest URL and the streaming URL in bulk. For more information , see [Create multiple live activities](reseller.en-US/User Guide (New console)/Configure push streaming and live streaming/Create multiple live activities.md#).
-   If you don't configure transcoding service for your live activities, for more information about the splicing rules of ingest URL and streaming URL, see [Ingest URL and streaming URL \(Original\)](reseller.en-US/User Guide (New console)/Configure push streaming and live streaming/Ingest URL and streaming URL (Not authenticated)/Ingest URL and streaming URL (Original).md#).
-   In this article, the ingest URL and the streaming URL in the example are for your reference only. You can follow the splicing rules to get your own ingest URL and streaming URL by using your ingest domain name, streaming domain name, AppName, StreamName and the authentication string obtained by authentication.

## Prerequisites {#section_rx2_vkx_wfb .section}

Perform the following operations to get the ingest URL and streaming URL:

-   Create a domain name

    You must first created an ingest domain name and a streaming domain name that have completed ICP filing. For more information, see Create a domain name.

-   Configure CNAME

    After creating a domain name, you must configure the CNAME for it to take effect. For more information about how to configure CNAME, see [Configure CNAME](reseller.en-US/User Guide (New console)/Domain names management/Configure CNAME.md#).

-   Associate domain names

    After creating domain names, you must associate the ingest domain name and the streaming domain name before you perform push streaming and live streaming operations. For more information, see [Associate domain names](reseller.en-US/User Guide (New console)/Domain names management/Manage a domain name/Associate domain names.md#).


## How do I get transcoding ingest URL? {#section_hyt_qf5_xfb .section}

-   Splicing rules of ingest URL

    ApsaraVideo Live service supports ingest URL in RTMP format only.

    The ingest URL format is `RTMP://Ingest Domain nName/AppName/StreamName`

-   Examples

    For example, the Ingest Domain Name is `push.aliyunlive.com`, AppName is app, StreamName is stream, and the ingest URL is `RTMP://push.aliyunlive.com/app/stream`


## How do I get transcoding streaming URL? {#section_f5s_5f5_xfb .section}

You must first configure transcoding. ApsaraVideo Live supports universal transcoding and custom transcoding. Each transcoding provides Narrowband HDTM. After you configure transcoding and obtain the template ID, you can splice the transcoding streaming URL based on the splicing rules.

1.  Configure transcoding templates.
    -   Configure universal transcoding
        1.  Click **Domain Names**.
        2.  Select the **Streaming Domain Name**, and click **Manage Templates**.
        3.  In **Transcoding**, select **Universal Transcoding**, and click **Add**.

            ![](images/33020_en-US.png)

    -   Configure custom transcoding
        1.  Log on to the ApsaraVideo Live console.
        2.  Click **Domain Names**.
        3.  Select the **Streaming Domain Names**, and click **Manage Templates**.
        4.  In **Transcoding**, select **Custom Transcoding**, and click **Add**.

            ![](images/33034_en-US.png)

2.  Get template ID.
    -   Get the template ID in the ApsaraVideo Live console.

        You can obtain the corresponding template ID by following the previous steps.

    -   Get the template ID by using API.

        You can call the `DescribeLiveStreamTranscodeInfo` interface, and the system returns the template ID. For more information, see [DescribeLiveStreamTranscodeInfo](https://www.alibabacloud.com/help/doc-detail/45048.htm?spm=a2c63.p38356.b99.88.704a42bdIcY4xm).

        In addition, users can customize template based on added fields. For more information about getting custom template ID, see [AddCustomLiveStreamTranscode](https://www.alibabacloud.com/help/doc-detail/66944.htm?spm=a2c63.p38356.b99.86.678a652324n3ps).

3.  Splicing rules of transcoding URL.
    -   Streaming URL supports RMTP, FLV, and HLS formats. For transcoding URLs in different formats, you must add `_templateid` following `StreamName`.
        -   `RTMP://Streaming Domain Name/AppName/StreamName{_templateid}?`
        -   `FLV://Streaming Domain Name/AppName/StreamName{_templateid}.flv?`
        -   `HLS://Streaming Domain Name/AppName/StreamName{_templateid}.m3u8?`
    -   Examples

        For example, the Streaming Domain Name is `play.aliyunlive.com`, the AppName is app, the StreamName is stream, and the authentication key is 456, then the streaming URL is:

        -   RTMP-based streaming URL `RTMP://play.aliyunlive.com/app/stream_sd`
        -   FLV-based streaming URL `FLV://play.aliyunlive.com/app/stream_sd.flv?`
        -   HLS-based streaming URL `HLS://play.aliyunlive.com/app/stream_sd.m3u8`
        **Note:** M3u8 transcoding URL is already supported. If you have more requirements, open a ticket.


