# Custom transcoding {#concept_qcp_f3n_cfb .concept}

## Configure custom transcoding {#section_c45_lnn_cfb .section}

You can customize the transcoding resolution, frame rate, bit rate, and other parameters based on your actual video output requirements.

1.  Log on to the [ApsaraVideo Live console](https://partners-intl.aliyun.com/login-required#/live).
2.  Click **Domain Names**.
3.  Select the Streaming Domain Name, and click **Manage Templates**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21253/154510422211724_en-US.png)

4.  In **Transcoding**, select **Custom Transcoding**, and click **Add**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21253/154510422211725_en-US.png)

5.  In **Transcoding Template**, add custom transcoding parameters.
    -   **AppName**: The application name of the transcoding templates.

        **AppName** can be the same under the same domain name and in the same template type, but the **Template ID** cannot be the same.

    -   **Resolution**: the resolution of the output video.
        -   Different resolution levels correspond to different prices. The resolution levels are as follows:
            -   LD: \(640x480\) and below

            -   SD: \(1280x720\) and below

            -   HD: \(1920x1080\) and below

            -   2K: \(2560x1440\) and below

            -   4K: \(3840x2160\) and below

        -   Resolution level determination rules: The output specifications are determined by whether the long and short edges of the output video resolution fall within the range defined by the output specifications. Take the output specification SD \(1280x720\) as an example:
            -   If the long edge of the resolution of the output video is less than or equal to 1280, and the short edge is less than or equal to 720, the video belongs to the output specification.

            -   If the long edge of the resolution of the output video exceeds 1280, or the short edge exceeds 720, this output video belongs to a higher specification.

        -   After adding the template, you can access the transcoding stream of a specified resolution by adding Template ID parameter at the end of the output streaming URL.
    -   **Video Bitrate**: The Bitrate specified by the resolution.

        The bit rate are as follows:

        -   LD: 100 ~ 800kbps

        -   SD: 200 ~ 1500kbps

        -   HD: 500 ~ 4000kbps

        -   2K: 2000 ~ 8000kbps

        -   4K: 4000 ~ 30000kbps

    -   **Video Frame Rate**: The output video frame rate, the value of which is less than or equal to the input video frame rate.

    -   **Template ID**: The ID of the transcoding template.

**Note:** **Template ID** is included in the streaming URL. When you customize template ID, we recommend that you do not configure a template ID different from the template ID of the universal transcoding.


## View custom transcoding {#section_szm_mrn_cfb .section}

You can view which transcoding template are used in the current streams in **Streams**.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21253/154510422211727_en-US.png)

