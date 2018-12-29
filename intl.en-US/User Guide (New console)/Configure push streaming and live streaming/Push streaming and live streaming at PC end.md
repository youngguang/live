# Push streaming and live streaming at PC end {#concept_ufx_jn3_bfb .concept}

You can use push streaming tools for PC end to push video streams to Alibaba Cloud live center for content processing and distribution. You can set videos that are pushed to Alibaba Cloud live center based on your needs so that the videos can be used in different scenarios. Perform the following steps to complete streaming and play at PC end.

**Note:** **Terms in the console have been updated, and we will update the documentation as soon as possible. We are sorry for any inconvenience caused**.

## Prepare tools and environment {#section_hd5_vpc_bfb .section}

Push streaming and live streaming tools

-   Push streaming tool: You can use OBS push streaming tool for ingestion. You can download OBS at [OBS official download website](https://obsproject.com/download?spm=a2c4g.11186623.2.3.FRgTS8).
-   Live streaming tool: You can use VLC media player to playback video. You can download VLC media player at [VLC media player official download website](http://www.videolan.org/vlc/?spm=a2c4g.11186623.2.3.HA1ICZ).

Network environment

Network type comparison

|Network type|Advantage|Disadvantage|
|:-----------|:--------|:-----------|
|Wired network|Stable|Not convenient|
|Wi-Fi|Convenient|Not stable|

-   Wired network is relatively more stable than Wi-Fi, the signal is not easily disturbed. Therefore, we recommend that you use a wired network if conditions permit.
-   Wi-Fi is is relatively more convenient than wired network. Therefore, if you perform live activity, we recommend that you use Wi-Fi.

Uplink bandwidth detection

ApsaraVideo Live requires a good network environment which can ensure watching fluency. Uplink bandwidth depends on the video quality and resolution. If the video quality is better, the resolution is higher, and the requirement for the uplink bandwidth is higher. We recommend that you use [Speedtest](http://www.speedtest.net/) to test the uplink bandwidth condition of your current network.

**Note:** We recommend that your uplink bandwidth is not lower than 1Mbps.

## Get ingest URL and streaming URL {#section_gw4_2qc_bfb .section}

Perform the following steps to get ingest URL and streaming URL:

1.  You must have performed ICP filing for your domain names.

    For more information about creating a domain name, see Create a domain name.

2.  Configure a domain name.

    After creating a domain name, you must configure CNAME for the ingest domain name and the streaming domain name, and associate both domain names. For more information, see and [Configure CNAME](reseller.en-US/User Guide (New console)/Domain names management/Configure CNAME.md#), [Associate domain names](reseller.en-US/User Guide (New console)/Domain names management/Manage a domain name/Associate domain names.md#).

3.  Configure authentication.

    Authentication function is enabled by default. The authentication key is assigned randomly, the expire time is 30 minutes. If the time exceeds expire time, the authentication becomes invalid. You can also custom authentication based on your needs, such as configure the expire times of the ingest URL and streaming URL. For more information, see [Configure authentication](reseller.en-US/User Guide (New console)/Domain names management/Access control/Configuration authentication.md#).

4.  Configure the optional function.
    -   You can choose to configure the anti-theft chain feature to limit the availability of live video distribution resources. For more information, see [Configure anti-leech](reseller.en-US/User Guide (New console)/Domain names management/Access control/Configure anti-leech.md#).
    -   You can configure IP blacklist to prevent an IP from accessing your CDN domain name. For more information, see [Configure IP blacklist](reseller.en-US/User Guide (New console)/Domain names management/Access control/Configure IP blacklist.md#).
    -   You can configure HTTPS secure acceleration to prevent the hidden danger of sensitive information from leakage. For more information, see [Configure HTTPS secure acceleration](reseller.en-US/User Guide (New console)/Domain names management/Configure HTTPS secure acceleration.md#).
    -   You can also configure notification URL so as to receive prompt feedback when the push streaming succeeds or the stream is disconnected successfully. For more information, see [Notification URL](reseller.en-US/User Guide (New console)/Streams Management/Ingest Callback URL.md#).
5.  Get ingest UTL and streaming URL.

    You can get ingest URL and streaming URL in ApsaraVideo Live console. For more information, see [Configure edge ingestion](reseller.en-US/User Guide (New console)/Configure push streaming and live streaming/Configure edge ingestion.md#).


## Configure and perform live streaming {#section_e5p_ytc_bfb .section}

Perform the following steps to complete live streaming operations:

1.  Install the OBS push streaming tool you have downloaded.
2.  Get the ingest URL.

    You can get the ingest URL in the ApsaraVideo Live console. For more information, see [Configure edge ingestion](reseller.en-US/User Guide (New console)/Configure push streaming and live streaming/Configure edge ingestion.md#).

3.  Configure the basic parameters, and use the streaming URL for streaming operation.

## Configure and view stream playback {#section_onk_15c_bfb .section}

Perform the following steps to complete stream playback operations:

1.  Install the VLC media player you have downloaded.
2.  Get the streaming URL.

    You can get the streaming URL in the ApsaraVideo Live console. For more information, see [Configure edge ingestion](reseller.en-US/User Guide (New console)/Configure push streaming and live streaming/Configure edge ingestion.md#).

3.  Use the VLC to play the video.

