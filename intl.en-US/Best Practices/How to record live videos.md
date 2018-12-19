# How to record live videos {#concept_ip4_zm3_bfb .concept}

## Recording by scenarios {#section_fm5_33c_bfb .section}

You can perform recording configuration based on your needs and different scenarios.

-   Recording at specified time

    You can use API to control the start time and end time of recording, so as to record at the specified time. For more information, see AddLiveAppRecordConfig.

-   Recording based on your needs

    You can configure a callback URL to exactly control the recording method of each stream. For more information, see On-demand recording.

-   Manual recording

    The manual recording is disabled by default. You can use the API to record videos. For more information, see Manual recording.


## Recording based on storage position { .section}

Store live recordings to OSS

The live recordings stored to OSS can serve the purpose of storage and playback. For more information, see Store live recordings to OSS.

-   If you want to preview and manage your recorded videos, you can preview and manage in the recording management list in the ApsaraVideo live console or in OSS console. For more information, see View recorded files.

-   If you want to deliver recorded videos, you can log on to the OSS console to configure a CDN domain name. CDN delivers your videos stored in OSS to nodes across China. And users can access the nearest nodes to read files, which not only improves the access speed and experience of edge users, but also effectively saves the overall network cost. For more information, see Configure OSS.


**Note:** 

-   You can record videos in flv format, mp4 format, and hls format.
-   The recorded videos are original videos.
-   You can index and edit the recorded hls files to quickly splice m3u8 video clips.

-   The information of recorded files are stored for 6 months by default. Within 6 months, you can use API or the console to view recorded files. If the storage time exceeds 6 months, you must go to OSS to get data.

