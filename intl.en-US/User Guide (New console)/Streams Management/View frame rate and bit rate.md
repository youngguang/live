# View frame rate and bit rate {#concept_84946_zh .concept}

In a live video environment, buffering interference often leaves a biggest impact on the live video streaming. The general cause is poor bandwidth stability of the uplink transmission .

The ApsaraVideo Live console monitors the uplink traffic. You can easily view the uplink transmission status of the live stream to check if there is any problem.

1.  Log on to the [ApsaraVideo Live console](https://partners-intl.aliyun.com/login-required#/live).
2.  Click **Live Management** \> **Streams**.
3.  Select the Streaming Domain Name.
4.  Select the stream status.
5.  Select the time period, the **AppName**, and the **StreamName** of the stream that you want to view.
6.  Click **Stream Monitoring** at the right side of the stream that you want to view.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20718/154520856121851_en-US.png)

7.  View the stream monitoring data.

    In **Stream Monitoring**, you can see **Length**, **Application Name**, **Stream Name**、**Bitrate \(Average\)**, and **Frame Rate \(Average\)**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20718/154520856221852_en-US.png)

    -   Video and audio frame rate

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20718/154520856221853_en-US.png)

    -   Bit rate

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20718/154520856221854_en-US.png)

    On average, the stream monitoring data is updated every minute. You can view the uplink transmission in the Stream Monitoring page.

    When the data status appears to be smooth, the valley and the peak values are comparatively stable. This indicates that the uplink transmission is comparatively stable too. If sharp fluctuations occur, we recommend that you check the stability of the uplink transmission.

    **Note:** You can get the monitoring data about 5 minutes after push streaming, and the system refreshes the monitoring data every one minute. If the push streaming time is short, you can not see the monitoring data.


## Causes of choppy push streaming { .section}

Several factors can cause video playback to buffer incorrectly. The following recommendations are troubleshooting tips that may help resolve streaming issues:

-   Mobile phone configuration.

    Push streaming consumes CPU resources. During the push streaming process, low-end mobile phones with poor hardware configuration may encounter poor quality video if the overall CPU usage exceeds 80%. This affects the video collection and viewing experience on the user terminals.

-   Video collection parameter settings.

    A video must have at least 15 frames per second \(FPS\) or higher to make sure smooth playback. An FPS set lower than this rate may result in unstable video quality. Keep the video frame rate higher than 15 frames per second \(FPS\).

    Although a higher frame rate ensure a smooth video watching process, if the frame rate is set for more than 30 FPS, the image content may not be viewed naturally by most of the viewers. Additionally, a higher frame rate also increases the bandwidth cost of the video transmission. We recommend that you set appropriate video parameters.

-   Network bandwidth.

    Common network factors include:

    -   Network bandwidth size: Confirm the bandwidth size provided by the network operator and whether the bandwidth is sufficient for this live video transmission.
    -   Downlink bandwidth usage: Check whether any data downloading activity occupies the network bandwidth.
    -   System resource usage: Check whether a large number of programs are running in the background, and delete and terminate any unnecessary programs to save the resources.

