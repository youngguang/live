# Configure global acceleration {#concept_86585_zh .concept}

Global acceleration is a high-speed circuit between the region where the streamer is located and mainland China.

## Scenario { .section}

-   Streamer at abroad or in Hong Kong, Macao and Taiwan region: The global acceleration function is used to stream video streams to mainland China, and distribute the video streams in mainland China.

-   Streamer in mainland China: The global acceleration function is used to pull and distribute video streams to specified acceleration region.


## Attentions { .section}

-   Global acceleration service is effective for a domain name only in **China East 2 \(Shanghai\)** region.

    Before configuring global acceleration, log on to the [ApsaraVideo Live console](https://partners-intl.aliyun.com/login-required#/live), and confirm the region of the configured domain name in **Domain Names**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20697/154520853321681_en-US.png)

-   If you want to use global acceleration, you must use edge ingestion function. For more information, see [Edge ingestion](../../../../reseller.en-US/Product Introduction/Edge streaming.md#).

    When you associate domain names, the system automatically enable edge ingestion acceleration service. Before configuring global acceleration, confirm that you have associated ingest domain name and streaming domain name in **Domain Names** \> **Configure** \> **Basic Settings** \> **Stream Pushing Information**. For more information about configuring edge ingestion, see [Configure edge ingestion](reseller.en-US/User Guide (New console)/Configure push streaming and live streaming/Configure edge ingestion.md#).

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20697/154520853321682_en-US.png)


## Procedure { .section}

1.  Log on to the ApsaraVideo Live console.
2.  Click **Domain Names**.
3.  Select the Streaming Domain Name, and click **Manage Templates**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20697/154520853321683_en-US.png)

4.  Click **Global Acceleration** \> **Add**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20697/154520853321684_en-US.png)

5.  In **Global Acceleration Instance**, enter global acceleration parameters.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20697/154520853321685_en-US.png)

    -    **AppName** The name of the video app. The **AppName** must be the same with the **AppName**, or the configuration does not take effect. For example, the **AppName** in the ingest URL is **app**, and the **AppName** of the global acceleration must also be **app**.

    -    **StreamName**: The name of the stream. Enter the specified stream name. If you want to record all the streams under the AppName, enter wilcard \(\*\).

        **Note:** **AppName** and **StreamName** parameters support upper case letters, lower case letters, number, hyphen \(-\), underline \(\_\) and period \(.\). The length is limited within 50 characters.

    -    **Accelerated Region**:

        -   **Stream pushing** acceleration: select the region where the streamer is located.

        -   **Streaming** acceleration: select the region where the audience is located.

    The global acceleration is configured successfully.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20697/154520853321686_en-US.png)

    **Note:** If the **StreamName** you configured in Global Acceleration template contains wilcard \(\*\), and multiple streams are configured under the same **AppName**, then all the streams perform the global acceleration configuration by default.


