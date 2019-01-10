# Pure live audio and live video {#concept_bmy_hl3_bfb .concept}

Alibaba Cloud supports pure live audio and live video. You can push pure live audio streams or pure live video streams to Alibaba Cloud video center. You can also directly play pure live audio streams or pure live video streams.

-   Streaming

    Audio and video streaming based on RTMP protocol are supported.

-   Stream play
    -   You can add parameters at the end of the address to separately play pure audio or pure video streams.
        -   Play audio only: onlyaudio＝1
        -   Play video only: onlyvideo＝1
    -   Examples
        -   `RTMP format: rtmp://domain name/APPName/Streamname?onlyaudio=1`
        -   `FLV format: http://domain name/APPName/Streamname.flv?onlyaudio=1`

            **Note:** Only stream play addresses in FLV format and RTMP format are supported.

-   Scenarios
    -   Audio and video streaming

        `rtmp://streaming domain name/APPName/Streamname?`

    -   Enter pure audio or video addresses, and you can play pure audio or video stream.
        -   Play audio only: `RTMP format: rtmp://stream play domain name/APPName/Streamname?onlyaudio=1`
        -   Play video only: `FLV format: http://stream play domain name/APPName/Streamname.flv?onlyvideo=1`

