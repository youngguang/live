# SDK使用 {#concept_xsv_qwb_pfb .concept}

本文介绍如何使用SDK进行直播互动。

SDK的基本使用流程包括以下几步：

1.  配置互动直播间参数；
2.  初始化；
3.  登录
4.  创建或进入房间（开始推流或拉流）；
5.  主播实时调整推流参数；
6.  主播与观众互动；
7.  直播间管控
8.  退出房间；
9.  登出；
10. 释放。

相关接口的使用请您参考以下内容。

## 配置互动直播间参数 {#section_d1m_wwb_pfb .section}

AlivcInteractiveLiveRoomConfig为互动直播间的配置参数类，每个属性参数会有一个对应的默认值，默认值和参数范围请您参考API文档或注释，您可以根据需求修改对应的属性值。在直播过程中实时修改参数可参见AlivcInteractiveLiveRoom类提供的属性和方法。

在需要使用互动直播的类里面，引入头文件

```
import
      com.alivc.live.room.interactive.config.AlivcInteractiveLiveRoomConfig
```

初始化房间配置，示例代码如下：

```
AlivcInteractiveLiveRoomConfig roomConfig = new AlivcInteractiveLiveRoomConfig();
```

1.  直播间配置

    直播间的基本配置包含点赞间隔和播放媒体类型等，示例代码如下：

    ```
    roomConfig.setReportLikeInterval(1000);
    roomConfig.setPlayResolution(AlivcResolutionMode.RESOLUTION_HD);
    roomConfig.setPlayUrlType(AlivcPlayUrlType.HLS);
    ```

2.  环境配置

    阿里云的互动直播目前支持的线上环境区域有上海，新加坡，您需要根据业务范围选择对应的区域，默认为上海区域。

    **说明：** 选择的区域必须和控制台配置域名选择的区域对应。

    AlivcInteractiveLiveRoomConfig中region是用于设置对应的区域，默认为上海区域。其定义如下：

    ```
    public enum AlivcLiveRegion {
        REGION_SHANGHHAI,
        REGION_SINGAPORE,
        REGION_USERDEFINE
    }
    ```

    当region设置为REGION\_SHANGHHAI或者REGION\_SINGAPORE时，SDK会自动切换到对应的上海或新加坡环境，REGION\_USERDEFINE为扩展的自定义区域，当有新的区域部署时，如果您想使用新的区域又不需要更新SDK的话，设置region 为REGION\_USERDEFINE， 此时必须要设置AlivcInteractiveLiveRoomConfig 中 imHost 和 ilvbHost，而使用REGION\_SHANGHHAI或者REGION\_SINGAPORE时不需要设置**imHost**和 **ilvbHost**。

    ```
    //设置区域为上海环境
    roomConfig.region = AlivcLiveRegion.REGION_SHANGHHAI;
    ```

3.  推流配置

    推流相关配置有美颜、分辨率和暂停图片等，示例代码如下：

    ```
    roomConfig.setBeautyOn(true);
    roomConfig.setPushResolutionMode(AlivcResolutionMode.RESOLUTION_LD);
    roomConfig.setPausePushImage(url);
    ```


## 互动直播间的基础使用 {#section_j2l_3zb_pfb .section}

1.  初始化

    首先，初始化互动直播间，appId必须要传。如果config为null，SDK会初始化一个默认的config，示例代码如下：

    ```
    AlivcInteractiveLiveRoom alivcILiveRoom = AlivcLiveRoomManager.getLiveRoom();
        mAlivcLiveRoomConfig = new AlivcInteractiveLiveRoomConfig();
        alivcILiveRoom.init(context, AppConstants.APP_ID, mAlivcLiveRoomConfig);
    ```

2.  登录

    使用STS登录互动直播，STS信息需要用户的业务服务通过OpenAPI获取下发给客户端。示例代码如下：

    ```
    //里面对应的值得从服务端获取
    AlivcSts sts = new AlivcSts();
    sts.setStsAccessKey("xxxx");
    sts.setStsSecretKey("xxxx");
    sts.setStsExpireTime("xxxx");
    sts.setStsSecurityToken("xxxx");
    alivcILiveRoom.login(sts);
    ```

3.  进入房间

    使用roomId、userInfo（必须有用户ID）和用户角色登录直播间，示例代码如下：

    ```
    alivcLiveRole = AlivcLiveRole.ROLE_HOST;
    alivcLiveRole = AlivcLiveRole.ROLE_AUDIENCE;
    alivcILiveRoom.enter(roomId, userId, userDesc, alivcLiveRole,
            new IAlivcCallback<AlivcRoomInfo, AlivcCommonError>() {
                @Override
                public void onSuccess(AlivcRoomInfo alivcEnterRoomResult){
               }
       @Override
       public void onFailure(AlivcCommonError alivcCommonError) {
       }
    });
    ```

4.  暂停

    主播端暂停推流，一般在App切后台时调用。主播切后台，观众端仍然可以收到主播的声音。示例代码如下：

    ```
    alivcILiveRoom.pause();
    ```

5.  恢复

    主播端恢复推流，一般在App切前台时调用。示例代码如下：

    ```
    alivcILiveRoom.resume();
    ```

6.  退出房间

    在主播和观众退出直播间时调用。示例代码如下：

    ```
    alivcILiveRoom.quit(new IAlivcCallback<AlivcCommonSuccess, AlivcCommonError>() {
                @Override
                public void onSuccess(AlivcCommonSuccess alivcQuitRoomResult) {
                }
                @Override
                public void onFailure(AlivcCommonError alivcCommonError) {
                }
    });
    ```

7.  释放

    直播间不再使用时需释放资源，销毁直播间，示例代码如下：

    ```
    alivcILiveRoom.release();
    ```


## 主播实时调节推流参数 {#section_wdv_yzb_pfb .section}

1.  美颜调节

    在直播的过程中直播可实时调节美颜，提供了档位设置和参数微调。示例代码如下：

    ```
    AlivcBeautyParams params = new AlivcBeautyParams();
    //param vaule range from 1 to 100
    param.beautyBuffing = 30;
    param.beautyRuddy = 30;
    param.beautyCheekPink = 50;
    param.beautyBigEye = 55;
    param.beautySlimFace = 44;
    param.beautyShortenFace = 70;
    param.beautyWhite = 32;
    alivcILiveRoom.setBeautyBeautyParams(param);
    ```

2.  摄像头相关

    摄像头相关的操作包括摄像头切换、是否自动对焦、手动对焦、缩放、闪光灯操作等，示例代码如下：

    ```
    alivcILiveRoom.switchCamera();
    alivcILiveRoom.setAutoFocus(true);
    alivcILiveRoom.focusCameraAtAdjustedPoint(x, y, true);
    alivcILiveRoom.setZoom(2);
    alivcILiveRoom.getMaxZoom();
    alivcILiveRoom.getCurrentZoom();
    alivcILiveRoom.setFlash(true);
    ```


## 主播与观众的互动 {#section_zjq_21c_pfb .section}

1.  点赞

    向直播间发送点赞消息，建议在客户端上汇总点赞次数，1-2秒发送一次。示例代码如下：

    ```
    alivcILiveRoom.sendLike(1, new IAlivcCallback<AlivcCommonSuccess, AlivcCommonError>() {
          @Override
          public void onSuccess(AlivcCommonSuccess o) {
          }
          @Override
          public void onFailure(AlivcCommonError iError) {
          }
    });
    ```

2.  获取点赞信息

    获取直播间的点赞数，在进入直播间获取，后面累积的点赞数通过监听点赞消息在端上累加实现，示例代码如下：

    ```
    alivcILiveRoom.getLikeCount(new IAlivcCallback<Long, AlivcCommonError>() {
                @Override
                public void onSuccess(Long alivcGetDigCountResult) {
                }
                @Override
                public void onFailure(AlivcCommonError alivcCommonError) {
                }
            });
    ```

3.  发送聊天信息

    向聊天室发送文本消息，发送消息时可以自定义用户信息，通过userData来传递，示例代码如下：

    ```
    alivcILiveRoom.sendChatMessage(message, new IAlivcCallback<AlivcCommonSuccess, AlivcCommonError>() {
        @Override
        public void onSuccess(AlivcCommonSuccess o) {
        }
        @Override
        public void onFailure(AlivcCommonError iError) {
        }
    });
    ```


## 直播间管控 {#section_f5w_n1c_pfb .section}

1.  禁言

    选择某个用户进行禁言，被禁言的对象则不能发送聊天消息。可设置禁言时长，示例代码如下：

    ```
    alivcILiveRoom.forbidChat(userId, durationTime, new IAlivcCallback<AlivcCommonSuccess, AlivcCommonError>() {
         @Override
         public void onSuccess(AlivcCommonSuccess s) {
         }
         @Override
         public void onFailure(AlivcCommonError alivcCommonError) {
         }
    });
    ```

2.  取消禁言

    在被禁言期间，可选择对某用户解除禁言，解除后恢复聊天消息发送，示例代码如下：

    ```
    alivcILiveRoom.allowChat(userId, new IAlivcCallback<AlivcCommonSuccess, AlivcCommonError>() {
        @Override
        public void onSuccess(AlivcCommonSuccess s) {
        }
        @Override
        public void onFailure(AlivcCommonError alivcCommonError) {
        }
    });
    ```

3.  获取历史聊天记录

    获取最近的20条聊天记录，通常在进入直播间时获取，示例代码如下：

    ```
    alivcILiveRoom.getHistoryChatMessage(new IAlivcCallback<List<AlivcChatHistoryMsg>, AlivcCommonError>() {
         @Override
         public void onSuccess(List<AlivcChatHistoryMsg> alivcChatHistoryMsgs) {
         }
         @Override
         public void onFailure(AlivcCommonError alivcCommonError) {
         }
    });
    ```


## 鉴权监听处理 {#section_yh4_v1c_pfb .section}

为了避免STS过期造成接口不能调用，在sts过期前1分钟进行即将回调，可以在此回调里面获取最新的sts信息，进行更新。sts过期时触发过期回调，如果没有提前更新可以通过此接口进行错误处理和sts更新，示例代码如下：

```
alivcILiveRoom.setAuthListener(new IAlivcAuthListener() {
            @Override
            public void onSTSTokenExpired(Object o, AlivcSts alivcSts) {
                //Ststoken is expired
            }
            @Override
            public void onStsTokenCloseExpire(Object o, AlivcSts alivcSts) {
                //ststoken is about to expire
            }
        });
```

## 网络监听处理 {#section_c15_y1c_pfb .section}

主要网络监听包括：网络差、开始重连、恢复重连和重连成功等，可根据业务需求在各自的回调里进行处理，示例代码如下：

```
alivcILiveRoom.setNetworkListener(new IAlivcNetworkListener() {
            @Override
            public void onNetworkPoor(Object o) {
            }
            @Override
            public void onNetworkRecovery(Object o) {
            }
            @Override
            public void onReconnectStart(Object o) {
            }
            @Override
            public void onReconnectFail(Object o) {
            }
            @Override
            public void onReconnectSucceed(Object o) {
            }
            @Override
            public void onSendDataTimeout(Object o) {
            }
            @Override
            public void onConnectFail(Object o) {
            }
});
```

## 错误监听处理 {#section_hgy_1bc_pfb .section}

互动直播间的错误回调，可以根据错误码处理对应的错误，示例代码如下：

```
alivcILiveRoom.setErrorListener(new IAlivcErrorListener() {
            @Override
            public void onSystemError(Object o, AlivcCommonError alivcCommonError) {
            }
            @Override
            public void onSDKError(Object o, AlivcCommonError alivcCommonError) {
            }
});
```

## 通知监听处理 {#section_jfc_dbc_pfb .section}

1.  互动直播消息监听

    互动直播间的消息监听主要包含：聊天消息、点赞消息、自定义消息、用户进入房间、系统消息通知等。

    ```
    alivcILiveRoom.setInteractiveNotifyListener(new IAlivcInteractiveNotifyListener() {
            @Override
            public void onNotifyChatMsg(Object o, String s, String s1, String s2) {
            }
            @Override
            public void onNotifyCustomMsg(Object o, String s) {
            }
            @Override
            public void onNotifyLike(Object o, int i) {
            }
            @Override
            public void onNotifyUserJionRoom(Object o, String s, String s1) {
            }
            @Override
            public void onNotifyNotice(Object o, String s) {
            }
            @Override
            public void onNotifyUserNotice(Object o, String s) {
            }
    });
    ```

2.  直播间通知

    直播间的通知主要包含：踢出用户时、房间销毁时、用户登录/登出房间、禁播的通知等。

    ```
    alivcILiveRoom.setLiveRoomNotifyListener(new IAlivcLiveRoomNotifyListener() {
                    @Override
                    public void onNotifyKickoutUser(Object o, String s, String s1) {
                    }
                    @Override
                    public void onNotifyRoomDestroyed(Object o) {
                    }
                    @Override
                    public void onNotifyUserLogin(Object o, AlivcLiveRole alivcLiveRole, String s) {
                    }
                    @Override
                    public void onNotifyUserLogout(Object o, AlivcLiveRole alivcLiveRole, String s) {
                    }
                    @Override
                    public void onForbidStream(Object o, String s) {
                    }
                });
    ```


