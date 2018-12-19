# How to perform overseas live activities {#concept_p4k_2n3_bfb .concept}

Overseas live activities includes two types:

-   Streamer is abroad or in Hong Kong, Macao or Taiwan, and audience is at home and abroad
-   Streamer is at home, and audience is at home and abroad or in Hong Kong, Macao or Taiwan

We provide solutions in different scenarios.

## Streamer is abroad or in Hong Kong, Macao or Taiwan, and audience is at home {#section_vct_mlc_bfb .section}

Problems

The cross-border transmission is unstable, and the live video lagging rate is high.

Solution

ApsaraVideo Live provides global acceleration function, which uses stable leased line to transmits video streams to mainland China. You can use global acceleration function to solve the problems of unstable transmission and high video lagging rate. Perform the following steps to complete the procedure.

1.  Add the domain name in **China East 2 \(Shanghai\)** region.

**Note:** Global acceleration service is provided only in **China East 2 \(Shanghai\)** region. Add your domain name in **China East 2 \(Shanghai\)** region.

2.  In **In Global Acceleration**, configure the global acceleration function. For more information, see [Configure global acceleration](../../../../reseller.en-US/User Guide (New console)/Domain names management/Configure global acceleration.md#).

Attentions

For videos played in mainland China, the domain name must perform ICP registration. For more information, see ICP Registration Support.

## Streamer is abroad or in Hong Kong, Macao or Taiwan, and audience is abroad or in Hong Kong, Macao or Taiwan {#section_oms_k4c_bfb .section}

Problems

-   The audience are from a wide range, which the videos can not cover.
-   The streamer is not in a specific location, and the network transmission is unstable, which leads to bad live video quality.

Solution

Currently, Alibaba Cloud has overseas centers in Germany, Singapore and Japan. We recommend that you select a live center near the streamer, and stream the video streams to the live center nearby.

1.  Edge streaming.

    Alibaba Cloud CDN nodes are distributed across main stream countries across the world. Edge streaming service can push video streams to edge nodes closest to the streamer, and uses the network optimized by Alibaba Cloud to transmit the video streams to the live center. For more information, see [Configure edge ingestion](../../../../reseller.en-US/User Guide (New console)/Configure push streaming and live streaming/Configure edge ingestion.md#).

2.  Real-time network monitoring.
    -   To view the streaming status and the network condition of the streamer and ensure the stability of streams, you can log on to the [ApsaraVideo Live console](https://partners-intl.aliyun.com/login-required#/live), and go to **Live Videos** \> **Streams** \> **Stream Monitor**. For more information, see [View frame rate and bit rate](../../../../reseller.en-US/User Guide (New console)/Streams Management/View frame rate and bit rate.md#).

    -   You can also use API to get frame rate and bit rate. For more information, see [DescribeLiveStreamsFrameRateAndBitRateData](https://www.alibabacloud.com/help/doc-detail/60410.htm?spm=a2c63.p38356.a3.6.39f4df93IWN69m).

Attentions

Alibaba Cloud has rich CDN nodes at home and aborad, covering more than 70 countries and regions in 6 continents. All the main stream carriers support overseas watching. However, when adding a live domain name, you must select **Overseas Acceleration** or **Global Acceleration**.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20641/154520942213735_en-US.png)

## Streamer is at home, and audience is abroad or in Hong Kong, Macao or Taiwan {#section_zsx_bpc_bfb .section}

Problems

-   How can I perform overseas acceleration for domestic videos?
-   How can I ensure the important videos are transmitted to overseas quickly and stably?

Solution

1.  When adding a domain name, select **Overseas Acceleration** or **or Global Acceleration**. For more information about adding a domain name, see[Add a domain name](../../../../reseller.en-US/User Guide (New console)/Domain names management/Manage a domain name/Create a domain name.md#).

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20641/154520942213736_en-US.png)

2.  To transmit video streams to the region where the video watching quality must be ensured, you can log on to the [ApsaraVideo Live console](https://partners-intl.aliyun.com/login-required#/live), and go to **Domain Names** \> **Template Set** \> **Global Acceleration** to enable the global acceleration function, and select Stream play in Acceleration. For more information, see [Configure global acceleration](../../../../reseller.en-US/User Guide (New console)/Domain names management/Configure global acceleration.md#).

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20641/154520942213737_en-US.png)


