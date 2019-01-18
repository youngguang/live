# Stream pulling {#concept_swt_qrs_cfb .concept}

Through the stream pulling, you can pull the third-party live streaming URL to the live center of Alibaba Cloud for content distribution, and push the stream to the desired node.

1.  Log on to the [ApsaraVideo Live console](https://partners-intl.aliyun.com/login-required#/live).
2.  Click **Domains**.
3.  Select the Streaming Domain, and click **Stream Settings**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21292/154780016111779_en-US.png)

4.  In the left-side navigation pane, click **Stream Pulling Settings**.
5.  Click **Add**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21292/154780016137582_en-US.png)

6.  In **Stream Pulling Settings**, enter streaming pulling setting parameters.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21292/154780016211781_en-US.png)

    -   **Application Name**: the name of the application.

        When the **Application Name** must be the same with the **Application Name** specified in the ingest URL for the setting to take effect.

        **Note:** Through the live pull-stream, you can pull the third-party live streams to the live center of Alibaba Cloud for content distribution, and push the stream to the desired node.

    -   **Stream Name**: The name of the stream.
    -   **Source URLs**: the third-party streaming URLs, support one-on-one stream pulling. You can also add multiple source URLs.

        -   RTMP, HLS, and FLV streaming URLs are supported.
        -   The next source URL is accessed automatically when you disconnect from the current live stream.
    -   **Start Time/End Time**: the interval between the start time and the end time must be within 7 days. The end time must be later than the current time.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21292/154780016211782_en-US.png)

    After setting the pull-stream, if the third-party streaming URLs have begun to play, you can view the streaming URLs processed in the live center in **Stream Management** \> **Ingest Endpoints**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21292/154780016211783_en-US.png)


