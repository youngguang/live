# SDK使用 {#concept_wx4_lvw_pfb .concept}

本文介绍SDK的基本使用流程。

SDK的基本使用流程如下：

1.  配置推流参数。
2.  创建推流预览视图。
3.  开始推流。
4.  根据业务需求实时调整推流参数。

## 配置推流参数 {#section_hm1_xlx_pfb .section}

您可以使用**AlivcLivePushConfig**配置推流参数，每个属性参数有一个对应的默认值，关于默认值和参数范围，参考API文档或注释。您可以根据需求修改对应的属性值。如您要在推流过程中实时修改参数，参见**AlivcLivePusher**类提供的属性和方法。

-   基本配置

    在需要使用推流器的 **ViewController**中引用头文件 **\#import <AlivcLivePusher/AlivcLivePusherHeader.h\>**，示例代码如下：

    ```
    AlivcLivePushConfig *config = [[AlivcLivePushConfig alloc] init];//初始化推流配置类，也可使用initWithResolution来初始化。
    config.resolution = AlivcLivePushResolution540P;//默认为540P，最大支持720P
    config.fps = AlivcLivePushFPS20; //建议用户使用20fps
    config.enableAutoBitrate = true; // 打开码率自适应，默认为true
    config.videoEncodeGop = AlivcLivePushVideoEncodeGOP_2;//默认值为2，关键帧间隔越大，延时越高。建议设置为1-2。
    config.connectRetryInterval = 2000; // 单位为毫秒，重连时长2s，重连间隔设置不小于1秒，建议使用默认值即可。
    config.previewMirror = false; // 默认为false，正常情况下都选择false即可。
    config.orientation =  AlivcLivePushOrientationPortrait; // 默认为竖屏，可设置home键向左或向右横屏。
    ```

    **说明：** 

    -   以上参数配置有有默认值，建议采用默认值。
    -   综合手机性能和网络带宽要求，建议您采用540P（主流移动直播App基本都采用540P）。
    -   关闭自适应码率后，码率永远固定在初始码率，不会在设定的目标码率和最小码率之间自适应调整，码率永远固定在初始码率。如果网络情况不稳定可能会比较卡顿，请慎用。
-   码控配置

    SDK提供三种推流模式供开发者选择。修改qualityMode参数，具体值如下：

    -   **清晰度优先模式**（**AlivcLivePushQualityModeResolutionFirst**）：SDK内部会对码率参数进行配置，优先保障推流视频的清晰度。
    -   **流畅度优先模式**（**AlivcLivePushQualityModeFluencyFirst**）：SDK内部会对码率参数进行配置，优先保障推流视频的流畅度。
    -   **自定义模式**（**AlivcLivePushQualityModeCustom**）：SDK会根据开发者设置的码率进行配置。
    清晰度优先或流畅度优先模式，示例代码如下：

    ```
    config.qualityMode = AlivcLivePushQualityModeResolutionFirst；// 默认为清晰度优先模式，可设置为流畅度优先模式和自定义模式。
    ```

    **说明：** 选择 **清晰度优先**或 **流畅度优先** 模式时，不需设置**targetVideoBitrate**, **minVideoBitrate**, **initialVideoBitrate**。SDK内部策略会自动保障在网络抖动情况下优先考虑视频清晰度或流畅度。

    自定义模式下，示例代码如下：

    ```
    config.qualityMode = AlivcLivePushQualityModeCustom//设置为自定义模式
    config.targetVideoBitrate = 1200; //  目标码率1200Kbps
    config.minVideoBitrate = 400; //  最小码率400Kbps
    config.initialVideoBitrate = 900; //  初始码率900Kbps
    ```

    设置为自定义模式时，您需自己定义初始码率、最小码率和目标码率。初始码率为开始直播时的码率。最小码率为当网络较差时，码率会逐步减低到最小码率，以减少视频的卡顿。目标码率为当网络较好时，码率会逐步提高到目标码率，以提高视频清晰度。

    自定义模式建议参数：

    |分辨率|targetVideoBitrate|minVideoBitrate|initialVideoBitrate|
    |:--|:-----------------|:--------------|:------------------|
    |360p|800|200|600|
    |480p|1000|300|700|
    |540p|1200|400|900|
    |720p|1500|600|1200|

-   分辨率自适应配置

    开启动态调整推流分辨率功能后，当网络较差时会自动降低分辨率以提高视频的流畅度和清晰度。动态分辨率在某些播放器上可能无法正常播放，阿里云播放器已支持。使用动态分辨率功能时，建议您使用阿里云播放器。

    ```
    config.enableAutoResolution = true; // 打开分辨率自适应，默认为false
    ```

    **说明：** qualityMode只有在清晰度和流畅度优先时生效。自定义模式时，分辨率自适应无效。

-   美颜配置

    阿里云推流SDK提供两种美颜模式：基础美颜和高级美颜。基础美颜支持美白、磨皮和红润。高级美颜支持基于人脸识别的美白、磨皮、红润、大眼、小脸、瘦脸、腮红等功能。高级美颜需设置美颜模式为 **AlivcLivePushBeautyModeProfessional**，并且必须添加 **AlivcLibFaceResource.bundle**人脸资源库到开发工程中。

    基础美颜需要集成美颜库**AlivcLibBeauty.framework**，必须实现**AlivcLivePusherCustomFilterDelegate**中的所有代理回调。

    使用示例代码如下：

    美颜配置代码

    ```
    config.beautyOn = true; // 开启美颜
    config.beautyMode = AlivcLivePushBeautyModeNormal；//设定为基础美颜
    config.beautyWhite = 70; // 美白范围0-100
    config.beautyBuffing = 40; // 磨皮范围0-100
    config.beautyRuddy = 40;// 红润设置范围0-100
    ```

    美颜回调处理代码

    ```
    /**
     外置美颜滤镜创建回调
     */
    - (void)onCreate:(AlivcLivePusher *)pusher context:(void*)context
    {
        [[AlivcLibBeautyManager shareManager] create:context];
    }
    ```

    ```
    /**
     外置美颜滤镜更新参数回调
     */
    - (void)updateParam:(AlivcLivePusher *)pusher buffing:(float)buffing whiten:(float)whiten pink:(float)pink cheekpink:(float)cheekpink thinface:(float)thinface shortenface:(float)shortenface bigeye:(float)bigeye
    {
        [[AlivcLibBeautyManager shareManager] setParam:buffing whiten:whiten pink:pink cheekpink:cheekpink thinface:thinface shortenface:shortenface bigeye:bigeye];
    }
    ```

    ```
    /**
     外置美颜滤镜开关回调
     */
    - (void)switchOn:(AlivcLivePusher *)pusher on:(bool)on
    {
        [[AlivcLibBeautyManager shareManager] switchOn:on];
    }
    ```

    ```
    /**
     通知外置滤镜处理回调
     */
    - (int)onProcess:(AlivcLivePusher *)pusher texture:(int)texture textureWidth:(int)width textureHeight:(int)height extra:(long)extra
    {
        return [[AlivcLibBeautyManager shareManager] process:texture width:width height:height extra:extra];
    }
    ```

    ```
    /**
     通知外置滤镜销毁回调
     */
    - (void)onDestory:(AlivcLivePusher *)pusher
    {
        [[AlivcLibBeautyManager shareManager] destroy];
    }
    ```

    高级美颜必须集成外置人脸检测库**AlivcLibFace.framework** 和人脸检测资源包**AlivcLibFaceResource.bundle**，示例代码如下：

    高级美颜配置代码

    ```
    config.beautyOn = true; // 开启美颜
    config.beautyMode = AlivcLivePushBeautyModeProfessional；//设定为高级美颜
    config.beautyWhite = 70; // 美白范围0-100
    config.beautyBuffing = 40; // 磨皮范围0-100
    config.beautyRuddy = 40;// 红润设置范围0-100
    config.beautyBigEye = 30;// 大眼设置范围0-100
    config.beautyThinFace = 40;// 瘦脸设置范围0-100
    config.beautyShortenFace = 50;// 收下巴设置范围0-100
    config.beautyCheekPink = 15;// 腮红设置范围0-100
    ```

    人脸检测回调处理代码

    ```
    /**
     外置人脸检测创建回调
     */
    - (void)onCreateDetector:(AlivcLivePusher *)pusher
    {
        [[AlivcLibFaceManager shareManager] create];
    }
    ```

    ```
    /**
     外置人脸检测处理回调
     */
    - (long)onDetectorProcess:(AlivcLivePusher *)pusher data:(long)data w:(int)w h:(int)h rotation:(int)rotation format:(int)format extra:(long)extra
    {
         return [[AlivcLibFaceManager shareManager] process:data width:w height:h rotation:rotation format:format extra:extra];
    }
    ```

    ```
    /**
     外置人脸检测销毁回调
     */
    - (void)onDestoryDetector:(AlivcLivePusher *)pusher
    {
        [[AlivcLibFaceManager shareManager] destroy];
    }
    ```

    关于使用第三方美颜滤镜和人脸检测滤镜的方法参考以上步骤，只要调用对应的接口即可。

    **说明：** 我们提供了丰富的美颜参数，建议您在UED同事配合下，调整出最符合自己应用风格的美颜参数。

    以下几组美颜效果比较理想，您可参考下表：

    |档位|磨皮|美白|红润|大眼|瘦脸|收下巴|腮红|
    |:-|:-|:-|:-|:-|:-|:--|:-|
    |一档|40|35|10|0|0|0|0|
    |二挡|60|80|20|0|0|0|0|
    |三挡|50|100|20|0|0|0|0|
    |四挡|40|70|40|30|40|50|15|
    |五档|70|100|10|30|40|50|0|

-   图片推流配置

    为了更好的用户体验，SDK提供了后台图片推流和码率过低时进行图片推流的设置。当SDK在退后台时默认暂停推流视频，只推流音频，此时可以设置图片来进行图片推流和音频推流。例如，在图片上提醒用户“主播离开片刻，稍后回来”。示例代码如下：

    ```
    config.pauseImg = [UIImage imageNamed:@"图片.png"];//设置用户后台推流的图片
    ```

    另外，当网络较差时用户可以根据自己的需求设置推流一张静态图片。设置图片后，SDK检测到当前码率较低时，会推流此图片，避免视频流卡顿。示例代码如下：

    ```
    config.networkPoorImg = [UIImage imageNamed:@"图片.png"];//设置网络较差时推流的图片
    ```

-   水印配置

    SDK提供了添加水印功能，并且最多支持添加多个水印，水印图片必须为png格式图片。示例代码如下：

    ```
    NSString *watermarkBundlePath = [[NSBundle mainBundle] pathForResource:    [NSString stringWithFormat:@"watermark"] ofType:@"png"];//设置水印图片路径
    [config addWatermarkWithPath: watermarkBundlePath
          watermarkCoordX:0.1
          watermarkCoordY:0.1
          watermarkWidth:0.3];//添加水印
    ```

    **说明：** 

    -   coordX、coordY、width为相对值，例如`watermarkCoordX:0.1`表示水印的x值为推流画面的10%位置，即推流分辨率为540\*960，则水印x值为54。
    -   水印图片的高度按照水印图片的真实宽高与输入的width值等比缩放。
    -   要实现文字水印，可以先将文字转换为图片，再使用此接口添加水印。
    -   为了保障水印显示的清晰度与边缘平滑，请您尽量使用和水印输出尺寸相同大小的水印源图片。如输出视频分辨率544\*940, 水印显示的w是0.1f，则尽量使用水印源图片宽度在544\*0.1f=54.4左右。
-   预览显示模式配置

    推流预览显示支持以下三种模式：

    -   ALIVC\_LIVE\_PUSHER\_PREVIEW\_SCALE\_FILL //铺满窗口，视频比例和窗口比例不一致时预览会有变形。
    -   ALIVC\_LIVE\_PUSHER\_PREVIEW\_ASPECT\_FIT //保持视频比例，视频比例和窗口比例不一致时有黑边（默认）。
    -   ALIVC\_LIVE\_PUSHER\_PREVIEW\_ASPECT\_FILL //剪切视频以适配窗口比例，视频比例和窗口比例不一致时会裁剪视频。
    这三种模式可以在AlivcLivePushConfig中设置，也可以在预览中和推流中通过API setpreviewDisplayMode 进行动态设置。

    **说明：** 本设置只对预览显示生效，实际推出的视频流的分辨率和AlivcLivePushConfig中预设置的分辨率一致，并不会因为更改预览显示模式而变化。预览显示模式是为了适配不同尺寸的手机，您可以自由选择预览效果。


## 推流器的使用 {#section_l1b_5qx_pfb .section}

**AlivcLivePusher**为推流SDK的核心类，提供摄像头预览、推流回调、推流控制、推流过程中的参数调节等功能。

-   初始化

    在配置好推流参数后，可以使用推流SDK的**initWithConfig**方法进行初始化。示例代码如下：

    ```
    self.livePusher = [[AlivcLivePusher alloc] initWithConfig:config];
    ```

    **说明：** **AlivcLivePusher**目前不支持多实例，所以一个init必须对应有一个destory。

-   注册推流回调

    推流回调分为三种：Info、Error、Network。Info主要做提示和状态检测使用；Error为错误回调；Network主要为网络相关，注册delegate可接受对应的回调。

    ```
    [self.livePusher setInfoDelegate:self];
    [self.livePusher setErrorDelegate:self];
    [self.livePusher setNetworkDelegate:self];
    ```

-   开始预览

    livePusher对象初始化完成之后，可以进行开始预览操作。预览时需要传入摄像头预览的显示view\(继承自UIView\)。示例代码如下：

    ```
    [self.livePusher startPreview:self.view];
    ```

-   开始推流

    预览成功后才可以开始推流，因此需监听 `AlivcLivePusherInfoDelegate` 的 `onPreviewStarted` 回调，在回调里面添加如下代码：

    ```
    [self.livePusher startPushWithURL:@"推流测试地址(rtmp://......)"];
    ```

    **说明：** 

    -   推流SDK同时提供了异步方法，可调用`startPushWithURLAsync`来实现。
    -   推流SDK支持RTMP的推流地址，阿里云推流地址获取参见 快速开始。
    -   使用正确的推流地址开始推流后，可用播放器（阿里云播放器、ffplay、VLC等）进行拉流测试，拉流地址如何获取参见 快速开始。
-   其他推流控制

    推流控制主要包括开始推流、停止推流、停止预览、重新推流、暂停推流、恢复推流、销毁推流等操作，您可以根据业务需求添加按钮进行操作。示例代码如下：

    ```
    /*正在推流状态下可调用暂停推流。暂停推流后，视频预览和视频推流保留在最后一帧，音频推流继续。*/
    [self.livePusher pause];
    /*暂停状态下可调用恢复推流。恢复推流后，音视频预览与推流恢复正常。*/
    [self.livePusher resume];
    /*推流状态下可调用停止推流，完成后推流停止。*/
    [self.livePusher stopPush];
    /*在预览状态下才可以调用停止预览，正在推流状态下，调用停止预览无效。预览停止后，预览画面定格在最后一帧。*/
    [self.livePusher stopPreview];
    /*推流状态下或者接收到所有Error相关回调状态下可调用重新推流，且Error状态下只可以调用此接口(或者reconnectPushAsync重连)或者调用destory销毁推流。完成后重新开始推流，重启ALivcLivePusher内部的一切资源，包括预览、推流等等restart。*/
    [self.livePusher restartPush];
    /*推流状态下或者接收到AlivcLivePusherNetworkDelegate相关的Error回调状态下可调用此接口, 且Error状态下只可以调用此接口(或者restartPush重新推流)或者调用destory销毁推流。完成后推流重连，重新链接推流RTMP。*/
    [self.livePusher reconnectPushAsync];
    /*销毁推流后，推流停止，预览停止，预览画面移除。AlivcLivePusher相关的一切资源销毁。*/
    [self.livePusher destory];
    self.livePusher = nil;
    /*获取推流状态。*/
    AlivcLivePushStatus status = [self.livePusher getLiveStatus];
    ```

-   美颜实时调整

    推流SDK支持在推流时实时调整美颜参数，根据在参数配置中设置的基础美颜和高级美颜模式，分别调整对应的参数值，示例代码如下：

    ```
    [self.livePusher setBeautyOn:true]; // 实时开启/关闭美颜
    /*基础美颜可实时调整以下参数：*/
    self.livePusher.beautyWhite = 70; // 美白范围0-100
    self.livePusher.beautyBuffing = 40; // 磨皮范围0-100
    self.livePusher.beautyRuddy = 40;// 红润设置范围0-100
    /* 高级美颜除了支持基础美颜参数调整外，还支持以下参数实时调整： */
    self.livePusher.beautyBigEye = 30;// 大眼设置范围0-100
    self.livePusher.beautyThinFace = 40;// 瘦脸设置范围0-100
    self.livePusher.beautyShortenFace = 50;// 小脸设置范围0-100
    self.livePusher.beautyCheekPink = 15;// 腮红设置范围0-100
    ```

-   背景音乐

    推流SDK提供了背景音乐播放、混音、降噪、耳返、静音等功能，背景音乐相关接口在开始预览之后才可调用。示例代码如下：

    ```
    /*开始播放背景音乐。*/
    [self.livePusher startBGMWithMusicPathAsync:musicPath];
    /*停止播放背景音乐。若当前正在播放BGM，并且需要切换歌曲，只需要调用开始播放背景音乐接口即可，无需停止当前正在播放的背景音乐。*/
    [self.livePusher stopBGMAsync];
    /*暂停播放背景音乐，背景音乐开始播放后才可调用此接口。*/
    [self.livePusher pauseBGM];
    /*恢复播放背景音乐，背景音乐暂停状态下才可调用此接口。*/
    [self.livePusher resumeBGM];
    /*开启循环播放音乐*/
    [self.livePusher setBGMLoop:true];
    /*设置降噪开关。打开降噪后，将对采集到的声音中非人声的部分进行过滤处理。可能存在对人声稍微抑制作用，建议让用户自由选择是否开启降噪功能，默认不使用*/
    [self.livePusher setAudioDenoise:true];
    /*设置耳返开关。耳返功能主要应用于KTV场景。打开耳返后，插入耳机将在耳机中听到主播说话声音。关闭后，插入耳机无法听到人声。未插入耳机的情况下，耳返不起作用。*/
    [self.livePusher setBGMEarsBack:true];
    /*混音设置，提供背景音乐和人声采集音量调整。*/
    [self.livePusher setBGMVolume:50];//设置背景音乐音量
    [self.livePusher setCaptureVolume:50];//设置人声采集音量
    /*设置静音。静音后音乐声音和人声输入都会静音。要单独设置音乐或人声静音可以通过混音音量设置接口来调整。*/
    [self.livePusher setMute:isMute?true:false];
    ```

-   摄像头相关操作

    您只能在开始预览之后调用摄像头相关操作，包括推流状态、暂停状态、重连状态等，可操作摄像头切换、闪关灯、焦距、变焦和镜像设置等。未开始预览状态下调用如下接口无效。示例代码如下：

    ```
    /*切换前后摄像头*/
    [self.livePusher switchCamera];
    /*开启/关闭闪光灯，在前置摄像头时开启闪关灯无效*/
    [self.livePusher setFlash:false]; 
    /*焦距调整，即可实现采集画面的缩放功能。传入参数为正数，则放大焦距，传入参数为负数则缩小焦距。*/
    CGFloat max = [_livePusher getMaxZoom];
    [self.livePusher setZoom:MIN(1.0, max)]; 
    /*手动对焦。手动聚焦需要传入两个参数:1.point 对焦的点（需要对焦的点的坐标);2.autoFocus 是否需要自动对焦，该参数仅对调用接口的该次对焦操作生效。后续是否自动对  焦沿用上述自动聚焦接口设置值。*/
    [self.livePusher focusCameraAtAdjustedPoint:CGPointMake(50, 50)  autoFocus:true];
    /*设置是否自动对焦*/
    [self.livePusher setAutoFocus:false];
    /*镜像设置。镜像相关接口有两个，PushMirror推流镜像和PreviewMirror预览镜像。PushMirror设置仅对播放画面生效，PreviewMirror仅对预览画面生效，两者互不影响。*/
    [self.livePusher setPushMirror:false];
    [self.livePusher setPreviewMirror:false];
    ```

-   直播答题功能

    直播答题功能可以通过在直播流里面插入SEI信息，播放器解析SEI来实现。在推流SDK里面提供了插入SEI的接口，在推流状态下，才能调用此接口。示例代码如下：

    ```
    /*
    msg: 需要插入流的SEI消息体，建议是json格式。阿里云播放器SDK可收到此SEI消息，解析后做具体展示。
    repeatCount：发送的帧数。为了保证SEI不被丢帧，需设置重复次数，如设置100，则在接下去的100帧均插入此SEI消息。播放器会对相同的SEI进行去重处理。
    delayTime：延时多少毫秒发送。
    KeyFrameOnly：是否只发关键帧。
    */
    [self.livePusher sendMessage:@"题目信息" repeatCount:100 delayTime:0 KeyFrameOnly:false];
    ```

-   外部音视频输入

    推流SDK支持将外部的音视频源输入进行推流，比如推送一个音视频文件，第三方设备采集的音视频数据等。具体使用如下：

    1.  首先在推流配置里面进行外部音视频输入配置，示例如下：

        ```
        config.externMainStream = true;//开启允许外部流输入
        config.externVideoFormat = AlivcLivePushVideoFormatYUVNV21;//设置视频数据颜色格式定义，这里设置为YUVNV21，可根据需求设置为其他格式。
        config.externMainStream = AlivcLivePushAudioFormatS16;//设置音频数据位深度格式，这里设置为S16，可根据需求设置为其他格式。
        ```

    2.  插入外部视频数据，示例如下：

        ```
        /*只支持外部视频yuv和rbg格式的连续buffer数据，才可以通过sendVideoData接口，发送视频数据buffer、长度、宽高、时间戳、旋转角度*/
        [self.livePusher sendVideoData:yuvData width:720 height:1280 size:dataSize pts:nowTime rotation:0];
        /*如果外部视频数据是CMSampleBufferRef格式，可以使用sendVideoSampleBuffer接口*/
        [self.livePusher sendVideoSampleBuffer:sampleBuffer]
        /*也可以讲 CMSampleBufferRef格式转化为连续buffer后再传递给sendVideoData接口， 以下为转换的参考代码*/
        //获取samplebuffer长度
        - (int) getVideoSampleBufferSize:(CMSampleBufferRef)sampleBuffer {
        if(!sampleBuffer) {
            return 0;
        }
        int size = 0;
        CVPixelBufferRef pixelBuffer = CMSampleBufferGetImageBuffer(sampleBuffer);
        CVPixelBufferLockBaseAddress(pixelBuffer, 0);
        if(CVPixelBufferIsPlanar(pixelBuffer)) {
           int count = (int)CVPixelBufferGetPlaneCount(pixelBuffer);
           for(int i=0; i<count; i++) {
               int height = (int)CVPixelBufferGetHeightOfPlane(pixelBuffer,i);
               int stride =  (int)CVPixelBufferGetBytesPerRowOfPlane(pixelBuffer,i);
               size += stride*height;
           }
        }else {
           int height = (int)CVPixelBufferGetHeight(pixelBuffer);
           int stride = (int)CVPixelBufferGetBytesPerRow(pixelBuffer);
           size += stride*height;
        }
        CVPixelBufferUnlockBaseAddress(pixelBuffer, 0);
        return size;
        }
        //将samplebuffer转化为连续buffer
        - (int) convertVideoSampleBuffer:(CMSampleBufferRef)sampleBuffer toNativeBuffer:(void*)nativeBuffer {
        if(!sampleBuffer || !nativeBuffer) {
           return -1;
        }
        CVPixelBufferRef pixelBuffer = CMSampleBufferGetImageBuffer(sampleBuffer);
        CVPixelBufferLockBaseAddress(pixelBuffer, 0);
        int size = 0;
        if(CVPixelBufferIsPlanar(pixelBuffer)) {
           int count = (int)CVPixelBufferGetPlaneCount(pixelBuffer);
           for(int i=0; i<count; i++) {
               int height = (int)CVPixelBufferGetHeightOfPlane(pixelBuffer,i);
               int stride = (int)CVPixelBufferGetBytesPerRowOfPlane(pixelBuffer,i);
               void *buffer = CVPixelBufferGetBaseAddressOfPlane(pixelBuffer, i);
               int8_t *dstPos = (int8_t*)nativeBuffer + size;
               memcpy(dstPos, buffer, stride*height);
               size += stride*height;
           }
        }else {
           int height = (int)CVPixelBufferGetHeight(pixelBuffer);
           int stride = (int)CVPixelBufferGetBytesPerRow(pixelBuffer);
           void *buffer = CVPixelBufferGetBaseAddress(pixelBuffer);
           size += stride*height;
           memcpy(nativeBuffer, buffer, size);
        }
        CVPixelBufferUnlockBaseAddress(pixelBuffer, 0);
        return 0;
        }
        ```

    3.  插入音频数据，示例如下：

        ```
        /*只支持外部pcm格式的连续buffer数据，sendPCMData，发送音频数据buffer、长度、时间戳*/
        [self.livePusher sendPCMData:pcmData size:size pts:nowTime];
        ```

-   动态贴纸

    SDK实现了在直播流中添加动态贴纸效果，使用此功能可实现动态水印效果。

    -   动态贴纸的制作可参考Demo提供的素材进行简单修改。自己制作动图贴纸的序列帧图片，并打开config.json文件自定义以下参数：

        ```
        "du": 2.04,//播放一遍动画持续的时间
        "n": "qizi",//动图的名称，制作动图时文件夹以动图名称命名，每一张图片以动图名称+序号命名，比如qizi0
        "c": 68.0,//动画帧数，即一个完整动画的图片数量
        "kerneframe": 51,//关键帧，即指定哪一张图片为关键帧，比如demo中指定第51帧为关键帧（需确保51帧是存在的）
        "frameArry": [
                     {"time":0,"pic":0},
                     {"time":0.03,"pic":1},
                     {"time":0.06,"pic":2},
                     ],
        //动画参数，上诉参数即表示第0秒显示第一帧（qizi0），第0.03秒显示第二帧（qizi1）...以此规则填写所有帧的动画
        ```

        **说明：** 其他字段可以直接使用demo提供的json文件中的内容，不需要修改。

    -   添加动态贴纸，示例如下：

        ```
        /*
        waterMarkDirPath：贴纸文件夹路径，必须含json文件
        x,y：显示屏幕位置（0~1.0f)
        w,h：显示屏幕长宽（0~1.0f)
        return : 返回贴纸的vid编号,删除贴纸时需设置vid。
        */
        int vid = [self.livePusher addDynamicWaterMarkImageDataWithPath:path x:x y:y w:w h:h];
        ```

    -   删除动态贴纸，示例如下：

        ```
        [self.livePusher removeDynamicWaterMark:vid];
        ```

-   调试工具

    SDK提供UI调试工具DebugView，用户问题诊断。DebugView为可移动的全局悬浮窗。添加后始终悬浮在视图的最上层。内含推流日志查看、推流性能参数实时检测、推流主要性能折线图表等debug功能。示例代码如下：

    ```
    [AlivcLivePusher showDebugView];//打开调试工具
    ```

    **说明：** 在您的release版本下， 不要调用添加DebugView的接口。

-   其他接口的使用

    ```
    /*在自定义模式下，用户可以实时调整最小码率和目标码率。*/
    [self.livePusher setTargetVideoBitrate:800];
    [self.livePusher setMinVideoBitrate:200]
    /*获取是否正在推流的状态*/
    BOOL isPushing = [self.livePusher isPushing]; 
    /*获取推流地址*/
    NSString *pushURLString = [self.livePusher getPushURL];
    /*获取推流性能调试信息。推流性能参数具体参数和描述参考API文档或者接口注释。*/
    AlivcLivePushStatsInfo *info = [self.livePusher getLivePushStatusInfo];
    /*获取版本号。*/
    NSString *sdkVersion = [self.livePusher getSDKVersion];
    /*设置log级别，根据需求过滤想要的调试信息*/
    [self.livePusher setLogLevel:(AlivcLivePushLogLevelDebug)];
    ```


## Replaykit录屏直播使用 {#section_bnr_5sx_pfb .section}

Replaykit是iOS9上新加的支持屏幕录制的功能，在iOS10中新增了调用第三方的App扩展来直播屏幕内容。使用阿里云直播SDK配合APP扩展可以实现iOS10以上的录屏直播功能。

-   如何创建直播扩展

    上述ReplayKit的录屏是通过App扩展来实现的。App扩展跟普通的App不同, 它不能单独发布, 需要内置在一个普通App中, 称为容器App。但是扩展的执行与容器App完全独立。扩展由宿主App发起请求来启动, 与宿主App进行交互。

    在我们的直播Demo中已经实现了支持录屏直播的App扩展AlivcLiveBroadcast和AlivcLiveBroadcastSetupUI。App中具体创建直播扩展如下：

    在现有工程选择 **New** \> **Target…**，选择 **Broadcast Upload Extension**，如下图：

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/40320/154088466321048_zh-CN.png)

    修改 **Product Name**，勾选 **Include UI Extension**，单击 **Finish**创建直播扩展和直播UI，如下图：

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/40320/154088466321049_zh-CN.png)

    配置直播扩展 **Info.plist**，如下图：

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/40320/154088466321051_zh-CN.png)

    此时扩展已经创建成功，运行APP，会自动将直播扩展和APP一同安装到手机，打开一款支持Replaykit直播的APP，比如游戏TowerDash，单击直播按钮，会弹出直播扩展选择，可以看到刚刚创建的扩展。如下图：

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/40320/154088466321052_zh-CN.png)

-   如何集成直播SDK
    1.  直播扩展中加入**AlivcLivePusher.framework** 和 **AlivcLibRtmp.framework**的依赖。
    2.  修改UI扩展，可以根据需求修改UI扩展的页面原属，配置包含直播地址，分辨率，横竖屏等参数，如下图：

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/40320/154088466321053_zh-CN.png)

    3.  使用AlivcLivePusher来完成直播相关功能，SampleHandle接口中包含了Replaykit录屏直播的所有功能接口，对应的在这些功能接口中调用阿里云直播SDK中**AlivcLivePusher**来实现具体功能。
        -   开始推流

            在**broadcastStartedWithSetupInfo**配置推流参数并实现推流。示例代码如下：

            ```
            - (void)broadcastStartedWithSetupInfo:(NSDictionary<NSString *,NSObject *> *)setupInfo {
            self.pushConfig = [[AlivcLivePushConfig alloc] init];
            self.livePusher = [[AlivcLivePusher alloc];
            self.pushConfig.externMainStream = true;
            [self.livePusher initWithConfig:self.pushConfig];
            [self.livePusher startPushWithURL:pushUrl];
            }
            ```

        -   暂停推流

            在**broadcastPaused**中实现暂停推流功能。示例代码如下：

            ```
            - (void)broadcastPaused {
            [self.livePusher pause];
            }
            ```

        -   恢复推流

            在**broadcastResumed**中实现恢复推流功能。示例代码如下：

            ```
            - (void)broadcastResumed {
            [self.livePusher resume];
            }
            ```

        -   结束推流

            在**broadcastFinished**中实现结束推流功能。示例代码如下：

            ```
            - (void)broadcastFinished {
            [self.livePusher stopPush];
            [self.livePusher destory];
            self.livePusher = nil;
            }
            ```

        -   发送音视频数据

            ```
            - (void)processSampleBuffer:(CMSampleBufferRef)sampleBuffer withType:(RPSampleBufferType)sampleBufferType {
            switch (sampleBufferType) {
             case RPSampleBufferTypeVideo:
                 // Handle video sample buffer
                 [self.livePusher processVideoSampleBuffer:sampleBuffer];
                 break;
             case RPSampleBufferTypeAudioApp:
                 // Handle audio sample buffer for app audio
                  [self.livePusher processAudioSampleBuffer:sampleBuffer withType:sampleBufferType];
                 break;
             case RPSampleBufferTypeAudioMic:
                 // Handle audio sample buffer for mic audio
                 [self.livePusher processAudioSampleBuffer:sampleBuffer withType:sampleBufferType];
                 break;
             default:
                 break;
             }
            }
            ```


## 异常及特殊场景处理 {#section_yz2_b5x_pfb .section}

-   当您收到**AlivcLivePusherErrorDelegate**时：

    -   当出现onSystemError系统级错误，您需要退出直播。

    -   当出现onSDKError错误（SDK错误）时，有两种处理方式，选择其一即可：销毁当前直播，重新创建或调用`restartPush/restartPushAsync`重启`AlivcLivePusher`

    -   您需要特别处理APP没有麦克风权限和没有摄像头权限的回调，APP没有麦克风权限错误码为268455940，APP没有摄像头权限错误码为268455939。

-   当您收到**AlivcLivePusherNetworkDelegate**时：

    -   网速慢时，回调onNetworkPoor，当您收到此回调说明当前网络对于推流的支撑度不足，此时推流仍在继续并没有中断。网络恢复时，回调`onNetworkRecovery`。您可以在此处理自己的业务逻辑，比如UI提醒用户。

    -   网络出现相关错误时，回调`onConnectFail`、`onReconnectError` 或 `onSendDataTimeout`。有两种处理方式，您只需选择其一：销毁当前推流重新创建或调用 `reconnectAsync` 进行重连，建议您重连之前先做网络检测和推流地址检测。

    -   SDK内部每次自动重连或者开发者主动调用 `reconnectAsync` 重连接口的情况下，会回调 `onReconnectStart` 重连开始。每次重连都会对 RTMP 进行重连链接。

        **说明：** RTMP链接建立成功之后会回调 onReconnectSuccess 此时只是链接建立成功，并不意味着可以推流数据成功，如果链接成功之后，由于网络等原因导致推流数据发送失败，SDK会在继续重连。

    -   推流地址鉴权即将过期会回调`onPushURLAuthenticationOverdue`。如果您的推流开启了推流鉴权功能\(推流URL中带有auth\_key\)。我们会对推流URL做出校验。在推流URL过期前约1min，您会收到此回调，实现该回调后，您需要回传一个新的推流URL。以此保证不会因为推流地址过期导致的推流中断。示例代码如下：

```
- (NSString *)onPushURLAuthenticationOverdue:(AlivcLivePusher     *)pusher {
return @"新的推流地址 rtmp://";
}
```

-   当您收到**AlivcLivePusherBGMDelegate**背景音乐错误回调时：
    -   背景音乐开启失败时会回调onOpenFailed，检查背景音乐开始播放接口所传入的音乐路径与该音乐文件是否正确，可调用 `startBGMWithMusicPathAsync`重新播放。

    -   背景音乐播放超时会回调`onDownloadTimeout`，多出现于播放网络URL的背景音乐，提示主播检查当前网络状态，可调用 `startBGMWithMusicPathAsync`重新播放。

-   当网络中断时：

-   短时间断网和网络切换：短时间的网络波动或者网络切换，一般情况下，中途断网时长在AlivcLivePushConfig设置的重连超时时长和次数范围之内，SDK会进行自动重连，重连成功之后将继续推流。若您使用阿里云播放器，建议播放器收到超时通知 `AliVcMediaPlayerPlaybackDidFinishNotification` 之后短暂延时5s后再做重连操作。

-   长时间断网：断网时长在AlivcLivePushConfig设置的重连超时时长和次数范围之外的情况下，SDK自动重连失败，此时会回调 `onReconnectError:error:` 在等到网络恢复之后调用 `reconnectAsync`接口进行重连。同时播放器也要配合做重连操作。

    -   建议您在SDK外部做网络监测。

    -   主播端和播放端在客户端无法进行直接通信，需要配合服务端使用。比如主播端断网，服务端会收到CDN的推流中断回调，此时可以推动给播放端，主播推流中断，播放端在作出相应处理。恢复推流同理。

    -   阿里云播放器重连需要先停止播放在开始播放。调用接口顺序 stop \> prepare \> play 。示例如下：

```
[self.mediaPlayer stop];
AliVcMovieErrorCode err = [self.mediaPlayer prepareToPlay:[NSURL     URLWithString:@"播放地址"]];
if(err != ALIVC_SUCCESS) {
  NSLog(@"play failed,error code is %d",(int)err);
  return;
}
[self.mediaPlayer play];
```

        **说明：** 关于播放器参见 [阿里云播放器使用说明](https://help.aliyun.com/document_detail/61431.html?spm=a2c4g.11186623.2.42.310b592cgeNmuo)。

-   退后台和接听电话

    SDK内部已经做好退后台相关处理，无需您做操作。退入后台SDK默认继续推流音频，视频保留在最后一帧。您需要在APP的**Capablities**中打开**Background Mode**选项，选中**Audio**，**AirPlay and Picture in Picture**。保证APP退后台可以正常采集音频。如图：

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/40320/154088466321055_zh-CN.png)

    如果退后台时不需要保持音频推流，即退入后台停止推流，返回前台继续推流。您可以根据下面两种方式实现。

    -   退后台设置为静音模式。调用 `setMute` 接口 （建议方式），或者，
    -   退后台停止推流，调用 `stopPush` 接口，回到前台继续推流，调用 `startPushWithURL`或者 `startPushWithURLAsync` 接口。

        **说明：** 在此方式下，退后台必须监听 **UIApplicationWillResignActiveNotification**和 **UIApplicationDidBecomeActiveNotification**。其他方式存在风险。

    例如：

    ```
    - (void)addNotifications {
         [[NSNotificationCenter defaultCenter] addObserver:self
                                                  selector:@selector(applicationWillResignActive:)
                                                      name:UIApplicationWillResignActiveNotification
                                               object:nil];
       [[NSNotificationCenter defaultCenter] addObserver:self
                                                     selector:@selector(applicationDidBecomeActive:)
                                                       name:UIApplicationDidBecomeActiveNotification
                                               object:nil]; 
    }
        - (void)applicationWillResignActive:(NSNotification *)notification {
        [self.livePusher stopPush];
    }
       - (void)applicationDidBecomeActive:(NSNotification *)notification {
          [self.livePusher startPushWithURLAsync:pushURL];
    }
    ```

-   播放外部音效

    如果您需要在推流页播放音效音乐等，由于SDK暂时与 `AudioServicesPlaySystemSound` 有冲突，建议您使用 `AVAudioPlayer`，并且在播放后需要更新设置 `AVAudioSession`，AVAudioPlayer播放音效示例代码：

    ```
    - (void)setupAudioPlayer {
       NSString *filePath = [[NSBundle mainBundle] pathForResource:@"sound" ofType:@"wav"];
       NSURL *fileUrl = [NSURL URLWithString:filePath];
      self.player = [[AVAudioPlayer alloc] initWithContentsOfURL:fileUrl error:nil];
      self.player.volume = 1.0;
      [self.player prepareToPlay];
    }
      - (void)playAudio {
        self.player.volume = 1.0;
        [self.player play];
        // 配置AVAudioSession
        AVAudioSession *session = [AVAudioSession sharedInstance];
        [session setMode:AVAudioSessionModeVideoChat error:nil];
        [session overrideOutputAudioPort:AVAudioSessionPortOverrideSpeaker error:nil];
        [session setCategory:AVAudioSessionCategoryPlayAndRecord withOptions:AVAudioSessionCategoryOptionDefaultToSpeaker|AVAudioSessionCategoryOptionAllowBluetooth | AVAudioSessionCategoryOptionMixWithOthers error:nil];
        [session setActive:YES error:nil];
    }
    ```

-   推流过程中改变view的大小

    请遍历您在调用 `startPreview` 或者 `startPreviewAsync` 接口时赋值的UIView。更改预览view的所有subView的frame。例如：

    ```
    [self.livePusher startPreviewAsync:self.previewView];
    for (UIView *subView in [self.previewView subviews]) {
      // ...
    }
    ```

-   iPhoneX适配

    一般场景下，预览view的frame设置为全屏可以正常预览，由于iPhoneX屏幕比例的特殊性，所以iPhoneX下预览view设置为全屏大小会有画面拉伸的现象。建议iPhoneX不要使用全屏大小的view来预览。

-   码率设置

    SDK内部有动态变化码率策略，您可以在AlivcLivePushConfig中修改码率预设值。根据产品需求对于视频分辨率、视频流畅度、视频清晰度的要求不同，对应设置的码率范围也不同，具体参考如下：

    -   视频清晰度：推流码率越高，则视频清晰度越高。所以推流分辨率越大，所需要设置的码率也就越大，以保证视频清晰度。

    -   视频流畅度：推流码率越高，所需要的网络带宽越大。所以在较差的网络环境下，设置较高的码率有可能影响视频流畅度。


## 注意事项 {#section_n2s_lvx_pfb .section}

-   关于包大小
    -   SDK大小为10.7MB。

    -   集成SDK后，ipa包增加大小约为2.8MB。

-   适配机型
    -   iPhone5s及以上版本，iOS8.0及以上版本。
-   功能限制说明
    -   您只能在推流之前设置横竖屏模式，不支持在直播的过程中实时切换。

    -   在硬编模式下，考虑编码器兼容问题分辨率会使用16的倍数，如设定为540p，则输出的分辨率为544\*960，在设置播放器视图大小时需按输出分辨率等比缩放，避免黑边等问题。

-   关于历史版本升级说明
    -   推流SDK V1.3升级至V3.0、连麦SDK升级至推流V3.0+，请下载 [升级说明文档](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/attach/45263/cn_zh/1511185890720/updateDoc_i0S_20171120.zip?spm=a2c4g.11186623.2.44.310b592cgeNmuo&file=updateDoc_i0S_20171120.zip)。

    -   从V3.3.4版开始不支持推流V1.3版兼容，升级时建议您重新接入最新版SDK。


