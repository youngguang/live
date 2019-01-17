# Configure edge ingestion {#concept_czp_fxj_bfb .concept}

The edge ingestion function preferentially pushes your video streams to the optimal CDN node to ensure that users can access the best uplink network. Besides, it can minimize such problems as video lagging and slow pull streaming caused by uplink transmission.

1.  Log on to the [ApsaraVideo Live console](https://partners-intl.aliyun.com/login-required#/live).
2.  Add an ingest domain name.
    1.  Click **Domains** \> **Add Domain**.
    2.  Enter ingest domain information.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20691/154771588811570_en-US.png)

    3.  Click **Next**, and the ingest domain is created successfully.
    4.  Click **Back to Domain List**.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20691/154771588811571_en-US.png)

3.  Create a streaming domain.
    1.  In **Domains**, click **Add Domain**.
    2.  Enter streaming domain information.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20691/154771588811572_en-US.png)

        **Note:** The Ingest Domain and the Streaming Domain must be in the same region so that you can associate the two domain names.

4.  Configure CNAME.

    You must configure CNAME for the ingest domain and the streaming domain respectively. For more information, see [Configure CNAME](reseller.en-US/User Guide (New console)/Domain names management/Configure CNAME.md#).

5.  Associate the Ingest Domain and the Streaming Domain.
    1.  In **Domains**, select the created **Streaming Domain**, and click **Domain Settings**.
    2.  In**Basic Settings**, click **Stream Ingest Information**, and click **Not configured** following**Stream Ingest Information**.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20691/154771588811574_en-US.png)

    3.  Select the **Ingest Domain**, click **OK**, and return to the home page of the ApsaraVideo Live console.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20691/154771588811575_en-US.png)

6.  Generate ingest URL and streaming URL.
    1.  Click **Stream Management** \> **URL Generator**.
    2.  Select the **Streaming Domain** and **Ingest Domain**.
    3.  Enter **Application Name** and **Stream Name**, and click **Generate URLs**.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20691/154771588811576_en-US.png)

    4.  Copy the URLs to stream ingest and live streaming tools for ingestion and playback.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20691/154771588811577_en-US.png)


