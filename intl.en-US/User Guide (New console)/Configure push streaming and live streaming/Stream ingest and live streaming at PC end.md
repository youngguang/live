# Stream ingest and live streaming at PC end {#concept_ufx_jn3_bfb .concept}

You can use stream ingest tools for PC end to push video streams to Alibaba Cloud live center for content processing and distribution. You can set videos that are pushed to Alibaba Cloud live center based on your needs so that the videos can be used in different scenarios. Perform the following steps to complete stream ingest and playback at PC end.

## Prepare tools and environment {#section_hd5_vpc_bfb .section}

Stream ingest and live streaming tools

-   Stream ingest tool: You can use OBS stream ingest tool for ingestion. You can download OBS at [OBS official download website](https://obsproject.com/download?spm=a2c4g.11186623.2.3.FRgTS8).
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

1.  Add domain names.

    You must have performed ICP filing for your domain names. For more information about adding a domain name, see [Add a domain name](reseller.en-US/User Guide (New console)/Domain names management/Manage a domain name/Add a domain name.md#).

2.  Configure the CNAME of a domain name.

    After adding domain names, you must configure CNAME for the ingest domain and the streaming domain. For more information, see [Configure CNAME](reseller.en-US/User Guide (New console)/Domain names management/Configure CNAME.md#).

3.  Associate domain names.

    After adding domain names, you must configure CNAME for the ingest domain and the streaming domain, and associate both domains. For more information, see [Associate domain names](reseller.en-US/User Guide (New console)/Domain names management/Manage a domain name/Associate domain names.md#).

4.  Configure authentication.

    Authentication function can protect your live video activities from bootlegging. This function is enabled by default. You can use the default configuration, or you can customize the authentication function.

    -   Default authentication: The authentication key is assigned randomly, the expire time is 30 minutes. If the time exceeds expire time, the authentication becomes invalid.
    -   Custom authentication: You can also custom authentication based on your needs, such as configure the expire times of the ingest URL and streaming URL. For more information, see [Configure authentication](reseller.en-US/User Guide (New console)/Domain names management/Access control/Configuration authentication.md#).
5.  Configure the optional function.
    -   You can choose to configure the hotlinking protection function to limit the availability of live video distribution resources. For more information, see [Configure hotlinking protection](reseller.en-US/User Guide (New console)/Domain names management/Access control/Configure hotlinking protection.md#).
    -   You can configure IP address blacklist to prevent an IP from accessing your CDN domain name. For more information, see [Configure IP address blacklist](reseller.en-US/User Guide (New console)/Domain names management/Access control/Configure IP address blacklist.md#).
    -   You can configure HTTPS to prevent the hidden danger of sensitive information from leakage. For more information, see [Configure HTTPS](reseller.en-US/User Guide (New console)/Domain names management/Configure HTTPS.md#).
    -   You can also configure notification URL so as to receive prompt feedback when the push streaming succeeds or the stream is disconnected successfully. For more information, see [Notification URL](reseller.en-US/User Guide (New console)/Streams Management/Ingest Callback URL.md#).
6.  Get ingest UTL and streaming URL.

    You can get ingest URL and streaming URL in ApsaraVideo Live console. For more information, see [Configure edge ingestion](reseller.en-US/User Guide (New console)/Configure push streaming and live streaming/Configure edge ingestion.md#).


## Configure and perform live streaming {#section_e5p_ytc_bfb .section}

Perform the following steps to complete live streaming operations:

1.  Install the OBS stream ingest tool you have downloaded.
2.  Get the ingest URL.

    You can get the ingest URL in the ApsaraVideo Live console. For more information, see [Configure edge ingestion](reseller.en-US/User Guide (New console)/Configure push streaming and live streaming/Configure edge ingestion.md#).

3.  Configure the basic parameters, and use the streaming URL for streaming operation.

## Configure and view stream playback {#section_onk_15c_bfb .section}

Perform the following steps to complete stream playback operations:

1.  Install the VLC media player you have downloaded.
2.  Get the streaming URL.

    You can get the streaming URL in the ApsaraVideo Live console. For more information, see [Configure edge ingestion](reseller.en-US/User Guide (New console)/Configure push streaming and live streaming/Configure edge ingestion.md#).

3.  Use the VLC to play the video.

