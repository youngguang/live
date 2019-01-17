# Configure premium streaming \(Formerly global acceleration\) {#concept_86585_zh .concept}

Premium streaming is a high-speed circuit between the region where the streamer is located and mainland China.

## Scenario { .section}

-   Streamer at abroad or in Hong Kong, Macao and Taiwan region: The premium streaming function is used to stream video streams to mainland China, and distribute the video streams in mainland China.

-   Streamer in mainland China: The premium streaming function is used to pull and distribute video streams to specified acceleration region.


## Attentions { .section}

-   Premium streaming service is effective for a domain name only in **China \(Shanghai\)** region.

    Before configuring premium streaming, log on to the [ApsaraVideo Live console](https://partners-intl.aliyun.com/login-required#/live), and confirm the region of the configured domain name in **Domains**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20697/154770579337027_en-US.png)

-   If you want to use premium streaming, you must use edge ingestion function. For more information, see [Edge ingestion](../../../../../reseller.en-US/Product Introduction/Edge streaming.md#).

    When you associate domain names, the system automatically enable edge ingestion acceleration service. Before configuring premium streaming, confirm that you have associated ingest domain name and streaming domain name in **Domains** \> **Domain Settings** \> **Basic Settings** \> **Stream Ingest Information**. For more information about configuring edge ingestion, see [Configure edge ingestion](reseller.en-US/User Guide (New console)/Configure push streaming and live streaming/Configure edge ingestion.md#).

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20697/154770579321682_en-US.png)


## Procedure { .section}

1.  Log on to the ApsaraVideo Live console.
2.  Click **Domains**.
3.  Select the Streaming Domain Name, and click **Stream Settings**.
4.  Click **Premium Streaming** \> **Add**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20697/154770579321684_en-US.png)

5.  In **Premium Streaming Acceleration Settings**, enter premium streaming parameters.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20697/154770579321685_en-US.png)

    -    **Application Name** The name of the video app. The **Application Name** must be the same with the **Application Name**, or the configuration does not take effect. For example, the **Application Name** in the ingest URL is **app**, and the **Application Name** of the premium streaming must also be **app**.

    -    **Stream Name**: The name of the stream. Enter the specified stream name. If you want to record all the streams under the Application Name, enter wildcard \(\*\).

        **Note:** **Application Name** and **Stream Name** parameters support upper case letters, lower case letters, number, hyphen \(-\), underline \(\_\) and period \(.\). The length is limited within 50 characters.

    -    **Acceleration Region**:

        -   **Stream Ingest** acceleration: select the region where the streamer is located.

        -   **Live Streaming** acceleration: select the region where the audience is located.

    The premium streaming is configured successfully.

    **Note:** If the **Stream Name** you configured in Premium Streaming contains wildcard \(\*\), and multiple streams are configured under the same **Application Name**, then all the streams perform the premium streaming configuration by default.


