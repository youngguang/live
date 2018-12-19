# Getting started {#concept_iyv_3nj_bfb .concept}

This article describes how to quickly use ApsaraVideo Live service to perform push streaming and live streaming operations.

## Prerequisites {#section_y5s_rnj_bfb .section}

-   Domain names that have completed ICP filing.

    Alibaba Cloud provides live service. You must prepare domain names that have completed ICP filing. For more information, see ICP Filing Process.


-   Push streaming tool and live streaming tool
    -   PC-end push streaming/live streaming tool

        Many PC-end push streaming tools are available in the market. You can select one based on your needs. This article takes OBS as an example to introduce live activity process for you.

    -   Mobile-end push streaming tool/live streaming tool

        Alibaba Cloud provides push streaming SDK and player SDK demo. You can use the Demo for push streaming and live streaming operations.


## Procedure {#section_agl_tnj_bfb .section}

1.  Log on to the [ApsaraVideo Live console](https://partners-intl.aliyun.com/login-required#/live).
2.  Add an **Ingest Domain Name**. For more information, see[Add a domain name](reseller.en-US/User Guide (New console)/Domain names management/Manage a domain name/Create a domain name.md#).
3.  Add a **Streaming Domain Name**. For more information, see [Add a domain name](reseller.en-US/User Guide (New console)/Domain names management/Manage a domain name/Create a domain name.md#).

    -   Ingest Domain Name: In the live service, you can use the Ingest Domain Name to splice the ingest URL. For more information, see [Ingest URL and streaming URL](../../../../reseller.en-US/User Guide (New console)/Configure push streaming and live streaming/Ingest URL and streaming URL/Ingest URL and streaming URL (Original).md#).
    -   Streaming Domain Name: In the live service, you can use the Streaming Domain Name to splice the streaming URL. For more information, see [Ingest URL and streaming URL](../../../../reseller.en-US/User Guide (New console)/Configure push streaming and live streaming/Ingest URL and streaming URL/Ingest URL and streaming URL (Original).md#).

        **Note:** You must add the Ingest Domain Name and the Streaming Domain Name. After adding the domain names, you must associate the Ingest Domain Name and the Streaming Domain Name.

    -   Accelerated Area: Area where the domain name can implement acceleration.
    When you configure the domain names successfully, the system automatically configures CDN acceleration function. And you can use the live acceleration function after you configure CNAME.

4.  Configure CNAME. For more information, see [Configure CNAME](reseller.en-US/User Guide (New console)/Domain names management/Configure CNAME.md#).
5.  Associate the Ingest Domain Name and the Streaming Domain Name. For more information, see [Associate Domain Names](reseller.en-US/User Guide (New console)/Domain names management/Manage a domain name/Associate domain names.md#).
6.  Generate ingest URL and streaming URL. For more information, see [Edge ingestion](reseller.en-US/User Guide (New console)/Configure push streaming and live streaming/Configure edge ingestion.md#)- **Generate ingest URL and streaming URL**.
7.  Push streaming. You can use the Alibaba Cloud push streaming SDK or the third-party push streaming software \(for example, OBS\) to perform push streaming operation. You can also perform push streaming operation at mobile end and mobile end.

    **Push streaming at PC end**: This document takes OBS as an example to introduce live activity process for you. For more information about OBS download and configuration, see [Push streaming and live streaming at PC end](../../../../reseller.en-US/User Guide (New console)/Configure push streaming and live streaming/Push streaming and live streaming at PC end.md#). **Push streaming at mobile end**: For more information, see [Push streaming and live streaming at mobile end](../../../../reseller.en-US/User Guide (New console)/Configure push streaming and live streaming/Push streaming and live streaming at mobile end.md#).

8.  Live streaming.

    You can playback the live stream at PC end, and mobile end.

    Live streaming at PC end:

    -   Use the web player to playback the live stream

        Copy the streaming URL to web player, and click **Play**.

         

    -   Preview videos in Alibaba Cloud console

        You can log on to the [ApsaraVideo Live console](https://partners-intl.aliyun.com/login-required#/live), and click **Live Management** \> **Streams** \> **Live URLs**to get and view the streaming URL. For more information, see [View a live stream](reseller.en-US/User Guide (New console)/Streams Management/View a live stream.md#).

    Live streaming at mobile end:

    For more information, see [Push streaming and live streaming at mobile end](../../../../reseller.en-US/User Guide (New console)/Configure push streaming and live streaming/Push streaming and live streaming at mobile end.md#).


