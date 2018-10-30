# SDK使用 {#concept_zy5_myx_pfb .concept}

本文介绍Android推流SDK的使用。

SDK的基本使用流程如下：

1.  配置推流参数。

2.  创建推流预览视图。

3.  开始推流。

4.  根据业务需求实时调整推流参数。


## 配置推流参数 {#section_fpb_zyx_pfb .section}

您可以使用AlivcLivePushConfig配置推流参数，每个参数有一个对应的默认值。关于默认值和参数范围，参见API文档或注释。您可以根据需求修改对应的属性值。如您要在推流过程中实时修改参数，参见AlivcLivePusher提供的属性和方法。

-   基本配置

    ```
    AlivcLivePushConfig mAlivcLivePushConfig = new AlivcLivePushConfig();//初始化推流配置类
    mAlivcLivePushConfig.setResolution(AlivcResolutionEnum.RESOLUTION_540P);//分辨率540P，最大支持720P
    mAlivcLivePushConfig.setFps(AlivcFpsEnum.FPS_20); //建议用户使用20fps
    mAlivcLivePushConfig.setEnableBitrateControl(true); // 打开码率自适应，默认为true
    mAlivcLivePushConfig.setPreviewOrientation(AlivcPreviewOrientationEnum.ORIENTATION_PORTRAIT); // 默认为竖屏，可设置home键向左或向右横屏。
    mAlivcLivePushConfig.setAudioProfile(AlivcAudioAACProfileEnum.AlivcAudioAACProfileEnum.AAC_LC);//设置音频编码模式
    mAlivcLivePushConfig.setEnableBitrateControl(true);// 打开码率自适应，默认为true
    ```

    **说明：** 

    -   以上参数配置有默认值，建议采用默认值，即您可以进行简单初始化，不做配置。
    -   综合手机性能和网络带宽要求，建议您采用540P（主流移动直播App基本都采用540P）。
    -   关闭自适应码率后，码率永远固定在初始码率，不会在设定的目标码率和最小码率之间自适应调整。如果网络情况不稳定可能会比较卡顿，请慎用。
-   码控配置

    SDK提供三种推流模式供开发者选择。您可按照下列模式修改AlivcQualityModeEnum参数：

    -   **QM\_RESOLUTION\_FIRST 清晰度优先模式**。SDK内部会对码率参数进行配置，优先保障推流视频的清晰度。

    -   **QM\_FLUENCY\_FIRST 流畅度优先模式**。SDK内部会对码率参数进行配置，优先保障推流视频的流畅度。

    -   **QM\_CUSTOM 自定义模式**。SDK会根据开发者设置的码率进行配置。

    清晰度优先或流畅度优先模式，示例代码如下：

    ```
    mAlivcLivePushConfig.setQualityMode(AlivcQualityModeEnum.QM_RESOLUTION_FIRST);
    ```

    **说明：** 选择 **清晰度优先** 或 **流畅度优先** 模式时，不需设置`targetVideoBitrate`,`minVideoBitrate`,`initialVideoBitrate`。SDK内部策略会自动保障在网络抖动情况下优先考虑视频清晰度或流畅度。

    自定义模式，示例代码如下：

    ```
    mAlivcLivePushConfig.setQualityMode(AlivcQualityModeEnum.QM_CUSTOM);
    mAlivcLivePushConfig.setTargetVideoBitrate(1200); //目标码率1200Kbps
    mAlivcLivePushConfig.setMinVideoBitrate(400); //最小码率400Kbps
    mAlivcLivePushConfig.setInitialVideoBitrate(900); //初始码率900Kbps
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

    开启动态调整推流分辨率功能后，当网络较差时会自动降低分辨率以提高视频的流畅度和清晰度。动态分辨率可能在某些播放器上不能正常播放，阿里云播放器已支持。使用动态分辨率功能时，建议您使用阿里云播放器。

    ```
    mAlivcLivePushConfig.setEnableAutoResolution(true); // 打开分辨率自适应，默认为false
    ```

    **说明：** AlivcQualityModeEnum只有在清晰度和流畅度优先时起生效，自定义模式时，分辨率自适应无效。

    阿里云推流SDK提供两种美颜模式：基础美颜和高级美颜。基础美颜支持美白、磨皮和红润。高级美颜支持基于人脸识别的美白、磨皮、红润、大眼、小脸、瘦脸、腮红等功能。高级美颜需设置美颜模式为 `BEAUTY_Professional`，并且必须添加人脸资源库到开发工程中。

    集成美颜功能需要引入美颜库：

    1.  aar方式引入：live-face-beauty\*.aar
    2.  jar+so方式引入：
    标准版美颜：live-beauty.jar + libAliEffectModule.so + liblive-beauty.so;

    专业版美颜：live-beauty.jar + libAliEffectModule.so + liblive-beauty.so + live-face.jar + liblive-face.so + libAliFaceAlignmentModule.so;

    另外需要在代码中设置处理两个回调：

    ```
    /**
    * 人脸识别回调（只接入标准版美颜可不需要调用此接口）
    **/
    mAlivcLivePusher.setCustomDetect(new AlivcLivePushCustomDetect()
    {
       @Override
      public void customDetectCreate() {
          taoFaceFilter = new TaoFaceFilter(getApplicationContext());
          taoFaceFilter.customDetectCreate();
      }
      @Override
      public long customDetectProcess(long data, int width, int height, int rotation, int format, long extra) {
          if(taoFaceFilter != null) {
              return taoFaceFilter.customDetectProcess(data, width, height, rotation, format, extra);
          }
          return 0;
      }
      @Override
      public void customDetectDestroy() {
          if(taoFaceFilter != null) {
              taoFaceFilter.customDetectDestroy();
          }
      }
    });
    /**
    * 美颜回调
    **/
    mAlivcLivePusher.setCustomFilter(new AlivcLivePushCustomFilter() 
    {
       @Override
      public void customFilterCreate() {
          taoBeautyFilter = new TaoBeautyFilter();
          taoBeautyFilter.customFilterCreate();
      }
      @Override
      public void customFilterUpdateParam(float fSkinSmooth, float fWhiten, float fWholeFacePink, float fThinFaceHorizontal, float fCheekPink, float fShortenFaceVertical, float fBigEye) {
          if (taoBeautyFilter != null) {
              taoBeautyFilter.customFilterUpdateParam(fSkinSmooth, fWhiten, fWholeFacePink, fThinFaceHorizontal, fCheekPink, fShortenFaceVertical, fBigEye);
          }
      }
      @Override
      public void customFilterSwitch(boolean on)
      {
          if(taoBeautyFilter != null) {
              taoBeautyFilter.customFilterSwitch(on);
          }
      }
      @Override
      public int customFilterProcess(int inputTexture, int textureWidth, int textureHeight, long extra) {
          if (taoBeautyFilter != null) {
              return taoBeautyFilter.customFilterProcess(inputTexture, textureWidth, textureHeight, extra);
          }
          return inputTexture;
      }
      @Override
      public void customFilterDestroy() {
          if (taoBeautyFilter != null) {
              taoBeautyFilter.customFilterDestroy();
          }
          taoBeautyFilter = null;
      }
    });
    ```

    基础美颜无需集成人脸库，示例代码如下：

    ```
    mAlivcLivePushConfig.setBeautyOn(true); // 开启美颜
    mAlivcLivePushConfig.setBeautyLevel(AlivcBeautyLevelEnum.BEAUTY_Normal);//设定为基础美颜
    mAlivcLivePushConfig.setBeautyWhite(70);// 美白范围0-100
    mAlivcLivePushConfig.setBeautyBuffing(40);// 磨皮范围0-100
    mAlivcLivePushConfig.setBeautyRuddy(40);// 红润设置范围0-100
    ```

    高级美颜必须集成人脸库，示例代码如下：

    ```
    mAlivcLivePushConfig.setBeautyOn(true); // 开启美颜
    mAlivcLivePushConfig.setBeautyLevel(AlivcBeautyLevelEnum.BEAUTY_Professional);//设定为高级美颜
    mAlivcLivePushConfig.setBeautyWhite(70);// 美白范围0-100
    mAlivcLivePushConfig.setBeautyBuffing(40);// 磨皮范围0-100
    mAlivcLivePushConfig.setBeautyRuddy(40);// 红润设置范围0-100
    mAlivcLivePushConfig.setBeautyThinFace(40);// 瘦脸设置范围0-100
    mAlivcLivePushConfig.setBeautyBigEye(30);// 大眼设置范围0-100
    mAlivcLivePushConfig.setBeautyShortenFace(50);// 小脸设置范围0-100
    mAlivcLivePushConfig.setBeautyCheekPink(15);// 腮红设置范围0-100
    ```

    **说明：** 我们提供了丰富的美颜参数，建议您在UED同事配合下，调整出最符合自己应用风格的美颜参数。

    以下几组美颜效果比较理想，您可参考下表：

    |档位|磨皮|美白|红润|大眼|瘦脸|收下巴|腮红|
    |:-|:-|:-|:-|:-|:-|:--|:-|
    |一档|40|35|10|0|0|0|0|
    |二挡|60|80|20|0|0|0|0|
    |三挡|50|100|20|0|0|0|0|
    |四挡|40|70|40|30|40|50|15|
    |五档|70|100|10|30|40|50|0|

    **说明：** 如果您有接入第三方美颜库的需求，可设置setCustomDetect和setCustomFilter回调。其中，

    -   AlivcLivePushCustomDetect回调函数customDetectProcess\(long data、int width、 int height、int rotation、int format、long extra参数\)中返回的参数data是采集数据的指针，第三方美颜库可对数据指针中的数据进行识别或者处理。
    -   AlivcLivePushCustomFilter回调函数customFilterProcess\(int inputTexture、int textureWidth、int textureHeight、long extra参数\)中返回的参数inputTexture是图像的纹理texture，第三方美颜库可对纹理进行处理。如果需要返回一个处理过的纹理texture，则返回texture id。否则，返回原来的inputTexture即可。
-   图片推流配置

    为了更好的用户体验，SDK提供了后台图片推流和码率过低时进行图片推流的设置。当SDK退至后台时默认暂停推流视频，只推流音频，此时可以设置图片来进行图片推流和音频推流。例如，在图片上提醒用户“主播离开片刻，稍后回来”。示例代码如下：

    ```
    mAlivcLivePushConfig.setPausePushImage("退后台png图片路径");//设置用户后台推流的图片
    ```

    另外，当网络较差时您可以根据自己的需求设置推流一张静态图片。设置图片后，SDK检测到当前码率较低时，会推流此图片，避免视频流卡顿。示例代码如下：

    ```
    mAlivcLivePushConfig.setNetworkPoorPushImage("网络差png图片路径");//设置网络较差时推流的图片
    置
    ```

-   水印配置

    SDK提供了添加水印功能，并且最多支持添加多个水印，水印图片必须为png格式图片。示例代码如下：

    ```
    mAlivcLivePushConfig.addWaterMark(waterPath, 0.1, 0.2, 0.3);//添加水印
    ```

    **说明：** 

    -   x、y、width为相对值，例如`x:0.1`表示水印的x值为推流画面x轴的10%位置，即推流分辨率为540\*960，则水印x值为54。

    -   水印图片的高度按照水印图片的真实宽高与输入的width值等比缩放。

    -   要实现文字水印，可以先将文字转换为图片，再使用此接口添加水印。

-   针对其他android设备（非android手机）的配置

    针对有些android设备（如电视盒子等）增加了如下两项配置：

    您可定制化配置摄像头旋转角度：

    ```
    mAlivcLivePushConfig.setPreviewRotation(AlivcPreviewRotationEnum rotation);//摄像头预览旋转角度
    ```

    有些设备摄像头的连续对焦支持不好，sdk提供传感器感应移动实时对焦：

    ```
    mAlivcLivePushConfig.setFocusBySensor(true);
    ```

    **说明：** 两个接口，android手机用户不要调用。

-   预览显示模式配置

    ```
    mAlivcLivePushConfig.setPreviewDisplayMode(AlivcPreviewDisplayMode.ALIVC_LIVE_PUSHER_PREVIEW_ASPECT_FIT);
    ```

    -   AlivcPreviewDisplayMode.ALIVC\_LIVE\_PUSHER\_PREVIEW\_SCALE\_FILL 预览显示时，铺满窗口。当视频比例和窗口比例不一致时，预览会有变形。

    -   AlivcPreviewDisplayMode.ALIVC\_LIVE\_PUSHER\_PREVIEW\_ASPECT\_FIT 预览显示时，保持视频比例。当视频比例与窗口比例不一致时，预览会有黑边。

    -   AlivcPreviewDisplayMode.ALIVC\_LIVE\_PUSHER\_PREVIEW\_ASPECT\_FILL 预览显示时，剪切视频以适配窗口比例。当视频比例和窗口比例不一致时，预览会裁剪视频。

        **说明：** 这三种预览显示模式不影响推流。


## 推流器的使用 {#section_qsb_zyx_pfb .section}

AlivcLivePusher为推流SDK的核心类，提供摄像头预览、推流回调、推流控制、推流过程中的参数调节等功能。

**说明：** 

-   接口的调用需要对接口抛出的异常进行处理，添加 try catch 处理操作。

-   接口调用的顺序必须按照说明的顺序调用，否则会因调用顺序不正确而出现异常。


-   初始化

    在配置好推流参数后，可以使用推流SDK的`init`方法进行初始化。示例代码如下：

    ```
    AlivcLivePusher mAlivcLivePusher = new AlivcLivePusher();
    mAlivcLivePusher.init(mContext, mAlivcLivePushConfig);
    ```

    **说明：** AlivcLivePusher目前不支持多实例，所以一个init必须对应有一个destory。

-   注册推流回调

    推流回调分为三种：Info、Error、Network。Info主要做提示和状态检测使用；Error为错误回调；Network主要为网络相关。用户通过对应的回调通知，当发生对应的类型的事件时，相应的回调函数被触发运行。示例代码如下：

    ```
    /**
      * 设置推流错误事件
      *
      * @param errorListener 错误监听器
      */
    mAlivcLivePusher.setLivePushErrorListener(new AlivcLivePushErrorListener() {
      @Override
      public void onSystemError(AlivcLivePusher livePusher, AlivcLivePushError error) {
          if(error != null) {
              //添加UI提示或者用户自定义的错误处理
          }
      }
      @Override
      public void onSDKError(AlivcLivePusher livePusher, AlivcLivePushError error) {
          if(error != null) {
              //添加UI提示或者用户自定义的错误处理
          }
      }
    });
    /**
    * 设置推流通知事件
    *
    * @param infoListener 通知监听器
    */
    mAlivcLivePusher.setLivePushInfoListener(new AlivcLivePushInfoListener() {
      @Override
      public void onPreviewStarted(AlivcLivePusher pusher) {
          //预览开始通知
      }
      @Override
      public void onPreviewStoped(AlivcLivePusher pusher) {
          //预览结束通知
      }
      @Override
      public void onPushStarted(AlivcLivePusher pusher) {
          //推流开始通知
      }
      @Override
      public void onPushPauesed(AlivcLivePusher pusher) {
          //推流暂停通知
      }
      @Override
      public void onPushResumed(AlivcLivePusher pusher) {
          //推流恢复通知
      }
      @Override
      public void onPushStoped(AlivcLivePusher pusher) {
          //推流停止通知
      }
      @Override
      public void onPushRestarted(AlivcLivePusher pusher) {
          //推流重启通知
      }
      @Override
      public void onFirstFramePreviewed(AlivcLivePusher pusher) {
          //首帧渲染通知
      }
      @Override
      public void onDropFrame(AlivcLivePusher pusher, int countBef, int countAft) {
          //丢帧通知
      }
      @Override
      public void onAdjustBitRate(AlivcLivePusher pusher, int curBr, int targetBr) {
          //调整码率通知
      }
      @Override
      public void onAdjustFps(AlivcLivePusher pusher, int curFps, int targetFps) {
          //调整帧率通知
      }
    });
    /**
    * 设置网络通知事件
    *
    * @param infoListener 通知监听器
    */
    mAlivcLivePusher.setLivePushNetworkListener(new AlivcLivePushNetworkListener() {
      @Override
      public void onNetworkPoor(AlivcLivePusher pusher) {
          //网络差通知
      }
      @Override
      public void onNetworkRecovery(AlivcLivePusher pusher) {
          //网络恢复通知
      }
      @Override
      public void onReconnectStart(AlivcLivePusher pusher) {
          //重连开始通知
      }
      @Override
      public void onReconnectFail(AlivcLivePusher pusher) {
          //重连失败通知
      }
      @Override
      public void onReconnectSucceed(AlivcLivePusher pusher) {
          //重连成功通知
      }
      @Override
      public void onSendDataTimeout(AlivcLivePusher pusher) {
          //发送数据超时通知
      }
      @Override
      public void onConnectFail(AlivcLivePusher pusher) {
          //连接失败通知
      }
    });
    /**
    * 设置背景音乐播放通知事件
    *
    * @param pushBGMListener 通知监听器
    */
    mAlivcLivePusher.setLivePushBGMListener(new AlivcLivePushBGMListener() {
      @Override
      public void onStarted() {
          //播放开始通知
      }
      @Override
      public void onStoped() {
          //播放停止通知
      }
      @Override
      public void onPaused() {
          //播放暂停通知
      }
      @Override
      public void onResumed() {
          //播放恢复通知
      }
      /**
       * 播放进度事件
       *
       * @param progress 播放进度
       */
      @Override
      public void onProgress(final long progress, final long duration) {
      @Override
      public void onCompleted() {
          //播放结束通知
      }
      @Override
      public void onDownloadTimeout() {
          //播放器超时事件，在这里处理播放器重连并且seek到播放位置
      }
      @Override
      public void onOpenFailed() {
          //流无效通知，在这里提示流不可访问
      }
    });
    ```

-   开始预览

    livePusher对象初始化完成之后，可以进行开始预览操作。预览时需要传入摄像头预览的显示SurfaceView。示例代码如下：

    ```
    mAlivcLivePusher.startPreview(mSurfaceView)//开始预览，也可根据需求调用异步接口startPreviewAysnc来实现
    ```

-   开始推流

    预览成功后才可以开始推流，因此需监听 `onPreviewStarted` 回调，在回调里面添加如下代码：

    ```
    mAlivcLivePusher.startPush(mPushUrl);
    ```

    **说明：** 

    -   推流SDK同时提供了异步方法，可调用`startPushAysnc`来实现。

    -   推流SDK支持RTMP的推流地址，阿里云推流地址获取参见 [快速开始](https://help.aliyun.com/document_detail/29957.html?spm=a2c4g.11186623.2.33.6284161cvDZvBu)。

    -   使用正确的推流地址开始推流后，可用播放器\(阿里云播放器、ffplay、VLC等\)进行拉流测试，拉流地址如何获取参见 [快速开始](https://help.aliyun.com/document_detail/29957.html?spm=a2c4g.11186623.2.34.6284161cvDZvBu)。

-   其他推流控制

    推流控制主要包括开始推流、停止推流、停止预览、重新推流、暂停推流、恢复推流、销毁推流等操作，用户可以根据业务需求添加按钮进行操作。示例代码如下：

    ```
    /*正在推流状态下可调用暂停推流。暂停推流后，视频预览和视频推流保留在最后一帧，音频推流继续。*/
    mAlivcLivePusher.pause();
    /*暂停状态下可调用恢复推流。恢复推流后，音视频预览与推流恢复正常。*/
    mAlivcLivePusher.resume();
    /*推流状态下可调用停止推流，完成后推流停止。*/
    mAlivcLivePusher.stopPush();
    /*在预览状态下才可以调用停止预览，正在推流状态下，调用停止预览无效。预览停止后，预览画面定格在最后一帧。*/
    mAlivcLivePusher.stopPreview();
    /*推流状态下或者接收到所有Error相关回调状态下可调用重新推流, 且Error状态下只可以调用此接口(或者reconnectPushAsync重连)或者调用destory销毁推流。完成后重新开始推流，重启ALivcLivePusher内部的一切资源，包括预览、推流等等restart。*/
    mAlivcLivePusher.restartPush();
    /*推流状态下或者接收到AlivcLivePusherNetworkDelegate相关的Error回调状态下可调用此接口, 且Error状态下只可以调用此接口(或者restartPush重新推流)或者调用destory销毁推流。完成后推流重连，重新链接推流RTMP。*/
    mAlivcLivePusher.reconnectPushAsync();
    /*销毁推流后，推流停止，预览停止，预览画面移除。AlivcLivePusher相关的一切资源销毁。*/
    mAlivcLivePusher.destroy();
    ```

-   美颜实时调整

    推流SDK支持在推流时实时调整美颜参数，根据在参数配置中设置的基础美颜和高级美颜模式，分别调整对应的参数值，示例代码如下：

    ```
    mAlivcLivePusher.setBeautyOn(true); // 实时开启/关闭美颜
    /*基础美颜可实时调整以下参数：*/
    mAlivcLivePusher.setBeautyWhite(70);// 美白范围0-100
    mAlivcLivePusher.setBeautyBuffing(40);// 磨皮范围0-100
    mAlivcLivePusher.setBeautyRuddy(40);// 红润设置范围0-100
    /* 高级美颜除了支持基础美颜参数调整外，还支持以下参数实时调整： */
    mAlivcLivePusher.setBeautyThinFace(40);// 瘦脸设置范围0-100
    mAlivcLivePusher.setBeautyBigEye(30);// 大眼设置范围0-100
    mAlivcLivePusher.setBeautyShortenFace(50);// 小脸设置范围0-100
    mAlivcLivePusher.setBeautyCheekPink(15);// 腮红设置范围0-100
    ```

-   背景音乐

    推流SDK提供了背景音乐播放、混音、降噪、耳返、静音等功能，背景音乐相关接口在开始预览之后才可调用。示例代码如下：

    ```
    /*开始播放背景音乐。*/
    mAlivcLivePusher.startBGMAsync(mPath)；
    /*停止播放背景音乐。若当前正在播放BGM，并且需要切换歌曲，只需要调用开始播放背景音乐接口即可，无需停止当前正在播放的背景音乐。*/
    mAlivcLivePusher.stopBGMAsync();
    /*暂停播放背景音乐，背景音乐开始播放后才可调用此接口。*/
    mAlivcLivePusher.pauseBGM();
    /*恢复播放背景音乐，背景音乐暂停状态下才可调用此接口。*/
    mAlivcLivePusher.resumeBGM();
    /*开启循环播放音乐*/
    mAlivcLivePusher.setBGMLoop(true);
    /*设置降噪开关。打开降噪后，将对采集到的声音中非人声的部分进行过滤处理。可能存在对人声稍微抑制作用，建议让用户自由选择是否开启降噪功能，默认不使用*/
    mAlivcLivePusher.setAudioDenoise(true);
    /*设置耳返开关。耳返功能主要应用于KTV场景。打开耳返后，插入耳机将在耳机中听到主播说话声音。关闭后，插入耳机无法听到人声。未插入耳机的情况下，耳返不起作用。*/
    mAlivcLivePusher.setBGMEarsBack(true);
    /*混音设置，提供背景音乐和人声采集音量调整。*/
    mAlivcLivePusher.setBGMVolume(50);//设置背景音乐音量
    mAlivcLivePusher.setCaptureVolume(50);//设置人声采集音量
    /*设置静音。静音后音乐声音和人声输入都会静音。要单独设置音乐或人声静音可以通过混音音 量设置接口来调整。*/
    mAlivcLivePusher.setMute(true);
    ```

-   摄像头相关操作

    您只能在开始预览之后调用摄像头相关操作，包括推流状态、暂停状态、重连状态等，可操作摄像头切换、闪关灯、焦距、变焦和镜像设置等。未开始预览状态下调用如下接口无效。示例代码如下：

    ```
    /*切换前后摄像头*/
    mAlivcLivePusher.switchCamera();
    /*开启/关闭闪光灯，在前置摄像头时开启闪关灯无效*/
    mAlivcLivePusher.setFlash(true); 
    /*焦距调整，即可实现采集画面的缩放功能。缩放范围为[0,getMaxZoom()]。*/
    mAlivcLivePusher.setZoom(5);
    /*手动对焦。手动聚焦需要传入两个参数:1.point 对焦的点（需要对焦的点的坐标);2.autoFocus 是否需要自动对焦，只有本次对焦操作调用该接口时，该参数才生效。后续是否自动对焦沿用上述自动聚焦接口设置值。*/
    mAlivcLivePusher.focusCameraAtAdjustedPoint(x, y, true);
    /*设置是否自动对焦*/
    mAlivcLivePusher.setAutoFocus(true);
    /*镜像设置。镜像相关接口有两个，PushMirror推流镜像和PreviewMirror预览镜像。PushMirror设置仅对播放画面生效，PreviewMirror仅对预览画面生效，两者互不影响。*/
    mAlivcLivePusher.setPreviewMirror(false);
    mAlivcLivePusher.setPushMirror(false);
    ```

-   直播答题功能

    直播答题功能可以通过在直播流里面插入SEI信息、播放器解析SEI来实现。在推流SDK里提供插入SEI的接口后，在推流状态下，才能调用此接口。示例代码如下：

    ```
    /*
    info: 需要插入流的SEI消息体，建议是json格式。阿里云播放器SDK可收到此SEI消息，解析后做具体展示。
    repeat：发送的帧数。为了保证SEI不被丢帧，需设置重复次数，如设置100，则在接下去的100帧均插入此SEI消息。播放器会对相同的SEI进行去重处理。
    delay：延时多少毫秒发送。
    isKeyFrame：是否只发关键帧。
    */
    mAlivcLivePusher.sendMessage("题目信息", 100, 0, false)
    ```

-   外部音视频输入

    推流SDK支持将外部的音视频源输入进行推流，比如推送一个音视频文件，第三方设备采集的音视频数据等。具体使用如下：

    1.  在推流配置里面进行外部音视频输入配置，示例如下：

```
/**
* AlivcImageFormat输入的视频图像格式
* AlivcSoundFormat输入的音频帧格式
* 其他参数：如输出分辨率，音频采样率，通道数等在config里
setResolution，setAudioSamepleRate，setAudioChannels里设置
* 附：输入自定义视频和音频流时，调用inputStreamVideoData，inputStreamAudioData等接口。
*/
mAlivcLivePushConfig.setExternMainStream(true,AlivcImageFormat.IMAGE_FORMAT_YUVNV12, AlivcSoundFormat.SOUND_FORMAT_S16);
```

    2.  插入外部视频数据，示例如下：

        ```
        /**
        *  输入自定义视频流
        *
        * @param data 视频图像byte array
        * @param width 视频图像宽度
        * @param height 视频图像高度
        * @param size 视频图像size
        * @param pts 视频图像pts（μs）
        * @param rotation 视频图像旋转角度
        * 此接口不控制时序，需要调用方控制输入视频帧的时序
        * 附：调用此接口时需要在config中设置setExternMainStream(true,***)
        */
        mAlivcLivePusher.inputStreamVideoData(buffer, 720, 1280, 1280*720*3/2,    System.nanoTime()/1000, 0);
        /**
        *  输入自定义视频流
        *
        * @param dataptr 视频图像native内存指针
        * @param width 视频图像宽度
        * @param height 视频图像高度
        * @param size 视频图像size
        * @param pts 视频图像pts（μs）
        * @param rotation 视频图像旋转角度
        * 此接口不控制时序，需要调用方控制输入视频帧的时序
        * 附：调用此接口时需要在config中设置setExternMainStream(true,***)
        */
        mAlivcLivePusher.inputStreamVideoPtr(long dataptr, int width, int height, int size, long pts, int rotation);
        ```

    3.  插入音频数据，示例如下：

        ```
        /**
        * 输入自定义音频数据
        * @param data 音频数据 byte array
        * @param size
        * @param pts 音频数据pts(μs)
        * 此接口不控制时序，需要调用方控制输入音频帧的时序
        */
        mAlivcLivePusher.inputStreamAudioData(buffer, 2048, System.nanoTime()/1000);
        /**
        * 输入自定义音频数据
        * @param dataPtr 音频数据native内存指针
        * @param size
        * @param pts 音频数据pts(μs)
        * 此接口不控制时序，需要调用方控制输入音频帧的时序
        */
        AlivcLivePusher.inputStreamAudioPtr(long dataPtr, int size, long pts);
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
        /**
        * 添加动态贴纸
        * @param path 贴纸文件路径，必须含config.json
        * @param x 显示起始x位置(0~1.0f)
        * @param y 显示起始y位置(0~1.0f)
        * @param w 显示宽度(0~1.0f)
        * @param h 显示高度(0~1.0f)
        * @return id 贴纸id,删除贴纸时需设置id
        */
        mAlivcLivePusher.addDynamicsAddons("贴纸路径", 0.2f, 0.2f, 0.2f, 0.2f);
        ```

    -   删除动态贴纸，示例如下：

        ```
        mAlivcLivePusher.removeDynamicsAddons(int id);
        ```

-   调试工具

    SDK提供UI调试工具DebugView，用户问题诊断。DebugView为可移动的全局悬浮窗。添加后始终悬浮在视图的最上层。内含推流日志查看、推流性能参数实时检测、推流主要性能折线图表等debug功能。示例代码如下：

    ```
    AlivcLivePusher.showDebugView(context);//打开调试工具
    AlivcLivePusher.hideDebugView(context);//移除调试工具
    ```

    **说明：** 在您的release版本下， 不要调用添加DebugView的接口。

-   其他接口的使用

    ```
    /*在自定义模式下，用户可以实时调整最小码率和目标码率。*/
    mAlivcLivePusher.setTargetVideoBitrate(800);
    mAlivcLivePusher.setMinVideoBitrate(400);
    /*是否支持自动对焦*/
    mAlivcLivePusher.isCameraSupportAutoFocus();
    /*是否支持闪光灯*/
    mAlivcLivePusher.isCameraSupportFlash();
    /*获取是否正在推流的状态*/
    mAlivcLivePusher.isPushing()； 
    /*获取推流地址*/
    mAlivcLivePusher.getPushUrl()；
    /*获取推流性能调试信息。推流性能参数具体参数和描述参考API文档或者接口注释。*/
    mAlivcLivePusher.getLivePushStatsInfo();
    /*获取版本号。*/
     mAlivcLivePusher.getSDKVersion();
    /*设置log级别，根据需求过滤想要的调试信息*/
    mAlivcLivePusher.setLogLevel(AlivcLivePushLogLevelAll);
    /*获取当前sdk状态*/
    AlivcLivePushStats getCurrentStatus();
    /*获取上一个错误码，如无错误返回：ALIVC_COMMON_RETURN_SUCCESS*／
    AlivcLivePushError getLastError();
    ```


## 录屏功能 {#section_ovv_2zx_pfb .section}

-   录屏模式

    录屏有以下三种模式可以选择：

    -   录屏时不开启摄像头：在config中设置权限请求的返回数据即可。

    -   录屏时开启摄像头，主播端有摄像头预览，同样观众端也有摄像头画面（通过录屏录制进去）。

        1.  在config中设置权限请求的返回数据。

        2.  调用StartCamera传入surfaceView。

    -   录屏时开启摄像头，主播端无摄像头预览，观众端有摄像头画面叠加。

        1.  在config中设置权限请求的返回数据。

        2.  调用StartCamera无需传入surfaceView。

        3.  调用startCameraMix传入观众端摄像头画面显示位置。

-   设置开启录屏权限

    录屏采用MediaProjection，需要用户请求权限，将权限请求返回的数据通过此接口设置，即开启录屏模式。录屏情况下，默认不开启摄像头。请在推流配置里面进行配置，示例代码如下：

    ```
    mAlivcLivePushConfig.setMediaProjectionPermissionResultData(resultData)
    ```

-   摄像头预览

    在录屏开启成功后，调用开启/关闭摄像头预览接口，示例代码如下：

    ```
    mAlivcLivePusher.startCamera(surfaceView);//开启摄像头预览
    mAlivcLivePusher.stopCamera();//关闭摄像头预览
    ```

    **说明：** 

    -   录屏模式下摄像头预览surfaceView的长宽建议设置成1：1，这样在屏幕旋转时无需调整surfaceview。

    -   若设置的长宽不为1：1，则需要在屏幕旋转时，调整surfaceView的比例后，stopCamera再startCamera。

    -   如果主播端不需要预览，则surfaceview填为null。

-   摄像头混流

    当主播端不需要摄像头预览，观众端需要的情况可开启混流，主要应用于游戏直播，主播不想玩游戏的时候摄像头画面挡住游戏画面，示例代码如下：

    ```
    /**
    * @param x 混流显示x初始位置(0~1.0f)
    * @param y 混流显示y初始位置(0~1.0f)
    * @param w 混流显示宽度(0~1.0f)
    * @param h 混流显示高度(0~1.0f)
    * @return
    */
    mAlivcLivePusher.startCameraMix(x, y, w, h);//开启摄像头混流
    mAlivcLivePusher.stopCameraMix();//停止摄像头混流
    ```

-   设置屏幕旋转

    录屏模式下，可设置感应的屏幕旋转角度，支持横屏/竖屏录制，示例代码如下：

    ```
    mAlivcLivePusher.setScreenOrientation(0);
    ```

    **说明：** 在横竖屏切换时，需要在应用层监听OrientationEventListener事件，并将旋转角度设置到此接口。

-   隐私设置

    当主播在录屏时要进行密码输入等操作时，主播可以开启隐私保护功能，结束操作后可以关闭隐私，示例代码如下：

    ```
    mAlivcLivePusher.pauseScreenCapture();//开启隐私保护
    mAlivcLivePusher.resumeScreenCapture();//关闭隐私保护
    ```

    **说明：** 暂停录屏，如果在config中设置了setPausePushImage则观众端会在此接口后显示图片。如果没有，则观众端停留在最后一帧。


## 异常及特殊场景处理 {#section_wcv_gzx_pfb .section}

-   当您收到AlivcLivePushErrorListener时：

    -   当出现onSystemError系统级错误时，您需要退出直播。

    -   当出现onSDKError错误（SDK错误）时，有两种处理方式，选择其一即可：销毁当前直播，重新创建或调用`restartPush/restartPushAsync`重启`AlivcLivePusher`。

    -   您需要特别处理APP没有麦克风权限和没有摄像头权限的回调，APP没有麦克风权限错误码为`ALIVC_PUSHER_ERROR_SDK_CAPTURE_CAMERA_OPEN_FAILED`，APP没有摄像头权限错误码为`ALIVC_PUSHER_ERROR_SDK_CAPTURE_MIC_OPEN_FAILED`。

-   当您收到AlivcLivePushNetworkListener时：

    -   网速慢时，回调`onNetworkPoor`，当您收到此回调说明当前网络对于推流的支撑度不足，此时推流仍在继续并没有中断。网络恢复时，回调`onNetworkRecovery`。您可以在此处理自己的业务逻辑，比如UI提醒用户。

    -   网络出现相关错误时，回调`onConnectFail`、`onReconnectError` 或`onSendDataTimeout`。有两种处理方式，您只需选择其一：销毁当前推流重新创建或调用 `reconnectAsync` 进行重连，建议您重连之前先进行网络检测和推流地址检测。

    -   SDK内部每次自动重连或者开发者主动调用 `reconnectAsync` 重连接口的情况下，会回调 `onReconnectStart` 重连开始。每次重连都会对 RTMP 进行重连链接。

        **说明：** RTMP链接建立成功之后会回调 `onReconnectSuccess`此时只是链接建立成功，并不意味着可以推流数据成功，如果链接成功之后，由于网络等原因导致推流数据发送失败，SDK会在继续重连。

    -   推流地址鉴权即将过期会回调`onPushURLAuthenticationOverdue`。如果您的推流开启了推流鉴权功能\(推流URL中带有auth\_key\)。我们会对推流URL做出校验。在推流URL过期前约1min，您会收到此回调，实现该回调后，您需要回传一个新的推流URL。以此保证不会因为推流地址过期而导致推流中断。示例代码如下：

        ```
        String onPushURLAuthenticationOverdue(AlivcLivePusher pusher) {
        return "新的推流地址 rtmp://";
        }
        ```

-   当您收到**AlivcLivePusherBGMListener**背景音乐错误回调时：
    -   背景音乐开启失败时会回调`onOpenFailed`，检查背景音乐开始播放接口所传入的音乐路径与该音乐文件是否正确，可调用 `startBGMAsync`重新播放。

    -   背景音乐播放超时会回调`onDownloadTimeout`，多出现于播放网络URL的背景音乐，提示主播检查当前网络状态，可调用 `startBGMAsync`重新播放。

-   当网络中断时：
    -   短时间断网和网络切换：短时间的网络波动或者网络切换。一般情况下，中途断网时长在**AlivcLivePushConfig**设置的重连超时时长和次数范围之内，SDK会进行自动重连，重连成功之后将继续推流。若您使用阿里云播放器，建议播放器收到超时通知之后短暂延时5s后再做重连操作。

    -   长时间断网：断网时长在**AlivcLivePushConfig**设置的重连超时时长和次数范围之外的情况下，SDK自动重连失败，此时会回调 `onReconnectError` 在等到网络恢复之后调用 `reconnectAsync`接口进行重连。同时播放器也要配合做重连操作。

        -   建议您在SDK外部做网络监测。

        -   主播端和播放端在客户端无法进行直接通信，需要配合服务端使用。比如主播端断网，服务端会收到CDN的推流中断回调，此时可以推动给播放端，主播推流中断，播放端在作出相应处理。恢复推流同理。

        -   阿里云播放器重连需要先停止播放在开始播放。调用接口顺序 stop \> prepareAndPlay。

            ```
            mPlayer.stop();
            mPlayer.prepareAndPlay(mUrl);
            ```

            **说明：** 关于播放器参见 [阿里云播放器使用说明](https://help.aliyun.com/document_detail/61431.html?spm=a2c4g.11186623.2.35.6284161cvDZvBu)。

-   退后台和锁屏
    -   当app退后台或锁屏时，您可调用 AlivcLivePusher 的 pause\(\)/resume\(\)接口暂停/恢复推流。

    -   对于非系统的音视频通话，sdk会采集声音并推送出去，您可以根据业务需求在退后台或锁屏时调用静音接口mAlivcLivePusher.setMute\(true/false\)来决定后台时是否采集音频;

-   码率设置

    SDK内部有动态变化码率策略，您可以在**AlivcLivePushConfig**中修改码率预设值。根据产品需求对于视频分辨率、视频流畅度、视频清晰度的要求不同，对应设置的码率范围也不同，具体参考如下：

    -   视频清晰度：推流码率越高，则视频清晰度越高。所以推流分辨率越大，所需要设置的码率也就越大，以保证视频清晰度。

    -   视频流畅度：推流码率越高，所需要的网络带宽越大。所以在较差的网络环境下，设置较高的码率有可能影响视频流畅度。


## 注意事项 {#section_ttp_fdl_nfb .section}

-   检查混淆，确认已将SDK相关包名加入了不混淆名单

    ```
    -keep class com.alibaba.livecloud.** { *;}
    -keep class com.alivc.** { *;}
    ```

-   接口调用
    -   同步异步接口都可以正常调用，尽量使用异步接口调用，可以避免对主线程的资源消耗。

    -   SDK接口都会在发生错误或者调用顺序不对时 thorws 出异常，调用时注意添加try catch 处理，否则会造成程序的crash。

    -   接口调用顺序。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20914/154088456713976_zh-CN.png)

-   关于包大小
    -   SDK大小：arm64-v8a：11.7M；v7a：9M。

    -   集成SDK后apk会增加约3.6M。

-   功能限制说明
    -   您只能在推流之前设置横竖屏模式，不支持在直播的过程中实时切换。

    -   在推流设定为横屏模式时，需设定界面为不允许自动旋转。

    -   在硬编模式下，考虑编码器兼容问题分辨率会使用16的倍数，如设定为540p，则输出的分辨率为544\*960，在设置播放器视图大小时需按输出分辨率等比缩放，避免黑边等问题。

-   关于历史版本升级说明
    -   推流SDK V1.3升级至 \[V3.0.0-3.3.3\]、连麦SDK升级至推流 \[V3.0.0-3.3.3\]，请下载 [升级说明文档](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/attach/45265/cn_zh/1511187112732/updateDoc_android_20171120.zip?spm=a2c4g.11186623.2.37.6284161cvDZvBu&file=updateDoc_android_20171120.zip)。

    -   从V3.3.4版开始不支持推流V1.3版兼容，升级时建议您重新接入最新版SDK。

    -   推流SDK升级至V3.1.0，如果您未集成阿里云播放器SDK，需注意集成播放器SDK（已包含推流SDK下载包里面）。

    -   推流SDK升级至V3.2.0+，提供包含阿里云播放器的版本和不包含阿里云播放器两个版本。如果您需要背景音乐功能必须集成播放器，否则可以不使用播放器SDK。


