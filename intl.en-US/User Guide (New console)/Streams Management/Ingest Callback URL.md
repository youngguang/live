# Ingest Callback URL {#concept_84943_zh .concept}

Ingest callback URL is mainly used to call back stream status information in real time and promptly notify users about the push streaming results.

You can add a callback URL of your background server in the console to Alibaba Cloud, so that when the stream status changes, Alibaba Cloud can send a GET request to your server using the HTTP interface and send you the real-time feedback on whether the video streaming succeeds or fails.

## Attentions { .section}

-   Principle: The real-time stream status feedback is implemented through GET requests sent to the user’s server through the HTTP interface. The user server returns 200 responses to the interface.

    You do not have to identify the URL if normal access is allowed. The following requirements are imposed on the URL responses: In case of access time-out, the URL can be retried. The current time-out duration is 5 seconds, the number of retries is 5, and the interval is 1 second.

-   It supports the HTTPS address authorized by the certificate authority.
-   If you use an Ingest Domain Name to push a stream, that is, Edge Ingestion, configure the Ingest callback URL on the Ingest Domain Name. If you use a Streaming Domain Name to push the stream, that is the Standard Ingestion, we will generate a standard ingestion URL for you, and push the stream directly to the live center, and you can configure the Ingest callback URL on the Streaming Domain Name. This article takes configuring Ingest callback URL in Edge Ingestion as an example to introduces how to configure Ingest callback URL.

## Procedure { .section}

1.  Log on to the [ApsaraVideo Live console](https://partners-intl.aliyun.com/login-required#/live).
2.  Click **Domain Names**.
3.  Select the Streaming Domain Name and click **Configure**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20717/154512701111800_en-US.png)

4.  In **Basic Settings** \> **Stream Pushing Information**, select the **Ingest Callback URL** following ingest URL, and click the edit icon at the right side of **Not Configured**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20717/154512701111801_en-US.png)

    **Note:** If you select Standard Ingestion, select **Ingest Callback URL** of Streaming Pushing Information for configuration.

5.  In **Configure Callback URL**, enter the callback URL.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20717/154512701111802_en-US.png)


## Examples { .section}

```
https://live.aliyunlive.com/pub? action=publish & app=xc.cdnpe.com & appname=test01 & id=test01 & ip=42.120.74.183 & node=cdnvideocenter010207116011.cm3

```

|Parameters|Value description|
|:---------|:----------------|
|time|Unix timestamp|
|usrargs|User push streaming parameters|
|action|Publish indicates push streaming, and publish\_done indicates completion of push streaming.|
|app|The default value is the custom streaming domain name. If no streaming domain name is bound, it is the playback domain name.|
|appname|Application name.|
|id|Stream name.**Note:** You must convert stream name to lowercase.

|
|node|The name of the node or machine in the CDN that receives the stream.|
|IP|IP address of the client that pushes the stream.|

