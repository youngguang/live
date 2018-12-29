# Configure edge ingestion {#concept_czp_fxj_bfb .concept}

The edge ingestion function preferentially pushes your video streams to the optimal CDN node to ensure that users can access the best uplink network. Besides, it can minimize such problems as video lagging and slow pull streaming caused by uplink transmission.

**Note:** **Terms in the console have been updated, and we will update the documentation as soon as possible. We are sorry for any inconvenience caused**.

1.  Log on to the [ApsaraVideo Live console](https://partners-intl.aliyun.com/login-required#/live).
2.  Add an ingest domain name.
    1.  Click **Domain Names** \> **Create**.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20691/154598822011569_en-US.png)

    2.  Enter ingest domain name information.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20691/154598822011570_en-US.png)

    3.  Click **Next**, and the ingest domain name is created successfully.
    4.  Click **Back to Domain Name List**.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20691/154598822011571_en-US.png)

3.  Create a streaming domain name.
    1.  In **Domain Names**, click **Create**.
    2.  Enter streaming domain name information.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20691/154598822011572_en-US.png)

        **Note:** The Ingest Domain Name and the Streaming Domain Names must be in the same region so that you can associate the two domain names.

4.  Configure CNAME.

    You must configure CNAME for the ingest domain name and the streaming domain name respectively. For more information, see [Configure CNAME](reseller.en-US/User Guide (New console)/Domain names management/Configure CNAME.md#).

5.  Associate the Ingest Domain Name and the Streaming Domain Name.
    1.  In **Domain Names**, select the created **Streaming Domain Name**, and click **Configure**.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20691/154598822011573_en-US.png)

    2.  In**Basic Settings**, click **Stream Pushing Information**, and click **Not configured** following**Stream Pushing Information**.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20691/154598822011574_en-US.png)

    3.  Select the **Ingest Domain Name**, click **OK**, and return to the home page of the ApsaraVideo Live console.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20691/154598822011575_en-US.png)

6.  Generate ingest URL and streaming URL.
    1.  Click **Live Management** \> **URL generator**.
    2.  Select the **Streaming Domain Name** and **Ingest Domain Name**.
    3.  Enter **AppName** and **StreamName**, and click **Generate URLs**.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20691/154598822011576_en-US.png)

    4.  Copy the URLs to push streaming and live streaming tools for ingestion and playback.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20691/154598822011577_en-US.png)


