# Create multiple live activities {#concept_tls_2gk_5fb .concept}

A live video activity requires an ingest URL. Alibaba Cloud ApsaraVideo Live supports creating activity of a triggered type. You can create multiple live activities on the basis of the activity creation rules without using APIs.

**Note:** **Terms in the console have been updated, and we will update the documentation as soon as possible. We are sorry for any inconvenience caused**.

## Descriptions {#section_xyf_qnk_5fb .section}

Ingest URL can be created in batches according to the rules, and live activities can be performed simultaneously. When performing multiple live activities, note that each domain can process a limited number of concurrent streams. A maximum of 20 concurrent streams and 10 transcoding streams are allowed for each domain name. Therefore, before performing live activities in batches, you must check whether the current stream limitation meets your requirements. If it does not meet your requirements, You can contact us by [Opening a ticket](https://selfservice.console.aliyun.com/ticket/createIndex?spm=5176.200001.0.0.qpYMOn).

## Create multiple ingest URLs {#section_i5v_sgk_5fb .section}

A live video service URL consists of three levels of live video management units, namely the domain name \(Domain\), application \(APPName\) and live stream \(StreamName\). You can create multiple applications \(APPName\) under each domain name \(Domain\), and multiple live streams \(StreamName\) under each application.

**Note:** For more information about the splicing rules of the ingest URL, see [Ingest URL and streaming URL](../reseller.en-US/User Guide (New console)/Configure push streaming and live streaming/Ingest URL and streaming URL/Ingest URL and streaming URL (Original).md#).

AppName and StreamName can be customized. Different values generate different ingest URL and streaming URLs.

-   You can create multiple live streams under one app.

    Examples

    For example, an application is named "live", you can create multiple live streams under "live". The ingest URL is:

    rtmp://Ingest Domain Name/\{live\}/\{1\}? authentication string

    rtmp//Ingest Domain Name/\{live\}/\{2\}? authentication string

    rtmp://Ingest Domain Name/\{live\}/\{3\}? authentication string

    **Note:** The authorization string is an encrypted string obtained based on the authentication algorithm.

-   You can also create multiple live streams for the application.

    **Note:** ApsaraVideo Live determines whether the live stream is unique based on stream name \(StreamName\) instead of application name \(AppName\). If you set a different application name, you must also make sure that the stream name is different to ensure that the final live stream is different.

    Examples

    rtmp://Ingest Domain Name/\{live1\}/\{Stream1\}? authentication string

    rtmp://Ingest Domain Name/\{live2\}/\{Stream2\}? authentication string

    rtmp://Ingest Domain Name/\{live3\}/\{Stream3\}? authentication string


## Create multiple streaming URLs {#section_gjs_hlk_5fb .section}

The rules of streaming URLs and the rules of ingest URLs are the same, and the application name \(AppName\) and stream name \(StreamName\) of the streaming URLs correspond to the application name \(AppName\) and stream name \(StreamName\) of the ingest URLs.

**Note:** For more information about the splicing rules of a single streaming URL, see [Ingest URL and streaming URL](../reseller.en-US/User Guide (New console)/Configure push streaming and live streaming/Ingest URL and streaming URL/Ingest URL and streaming URL (Original).md#).

Examples

The ingest URL is:

rtmp://Ingest Domain Name/\{live\}/\{3\}? authentication string

The corresponding streaming URL is:

http://Streaming Domain Name/\{live\}/\{3\}?authentication string

http://Streaming Domain Name/\{live\}/\{3\}.flv?authentication string

http://Streaming Domain Name/\{live\}/\{3\}.m3u8?authentication string

## How do I get a URL after I enable transcoding? {#section_elb_lnk_5fb .section}

**Universal Transcoding**

The streaming URL is spliced by using different parameters. The transcoding streaming URL consists of the original URL and template IDs.

URL format is `Streaming Domain Name`+`AppName`+`StreamName`+`_`+`Template name`.

|Template name|LD|SD|HD|UHD|
|:------------|:-|:-|:-|:--|
|Narrowband HDTM template ID|ld|sd|hd|ud|

Examples

If the template name of the standard template is **sd**, you can create streaming URLs in batches as follows:

RTMP format: rtmp://Streaming Domain Name/\{AppName\}/\{StreamName\} \_sd? authentication string

FLV format: http://Streaming Domain Name/\{AppName\}/\{StreamName\} \_sd.flv? authentication string

HLS format: hls://Streaming Domain Name/\{AppName\}/\{StreamName\} \_sd.m3u8? authentication string

**Custom transcoding**

You can also customize transcoding as needed. You must configure the template name of custom transcoding **Template ID** in the console.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/63384/154598815434437_en-US.png)

The splicing rules of multiple streaming URLs are as follows:

RTMP format: rtmp://Streaming Domain Name/\{AppName\}/\{StreamName\} \_templateID? authentication string

FLV format: http://Streaming Domain Name/\{AppName\}/\{StreamName\} \_templateID.flv? authentication string

HLS format: http://Streaming Domain Name/\{AppName\}/\{StreamName\} \_template ID.m3u8? authentication string

