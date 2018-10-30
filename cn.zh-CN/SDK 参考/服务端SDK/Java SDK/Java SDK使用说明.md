# Java SDK使用说明 {#concept_sxg_xwd_qfb .concept}

本文介绍Java SDK使用说明。请您按照以下步骤进行操作。

## 操作步骤 { .section}

1.  引入SDK

    请在pom.xml文件中增加以下依赖，准确的SDK版本号，参见 [阿里云开发工具包（SDK）](https://develop.aliyun.com/tools?spm=5176.136436.765261.185.1N8eiu#sdk)。

    ```
    <dependencies>
     <dependency>
        <groupId>com.aliyun</groupId>
        <artifactId>aliyun-java-sdk-live</artifactId>
        <version>2.3.0</version>
     </dependency>
    </dependencies>
    ```

2.  初始化Client

    SDK通过IAcsClient的instance来完成openAPI的调用。因此，在您发起调用前，请先初始化IAcsClient实例。示例代码如下：

    ```
    public void init() throws ClientException {
         IClientProfile profile = DefaultProfile.getProfile("cn-shanghai", "<your accessKey>", "<your accessSecret>");
         //DefaultProfile.addEndpoint("cn-shanghai", "cn-shanghai", "live", "live.aliyuncs.com"); //添加自定义endpoint。
         client = new DefaultAcsClient(profile);
         //System.setProperty("http.proxyHost", "127.0.0.1"); //此设置用于设置代理，可用fiddler拦截查看http请求，便于调试。  
         //System.setProperty("http.proxyPort", "8888");
     }
    ```

3.  初始化请求

    发起API调用前，先初始化对应的请求的request实例，DescribeLiveSnapshotConfig（查询截图配置）接口为例，示例代码如下：

    ```
    public void requestInitSample() {
         DescribeLiveSnapshotConfigRequest describeLiveSnapshotConfigRequest = new DescribeLiveSnapshotConfigRequest();
         describeLiveSnapshotConfigRequest.setDomainName("live.aliyunlive.com");
         //describeLiveSnapshotConfigRequest.setProtocol(ProtocolType.HTTPS); //指定访问协议
         //describeLiveSnapshotConfigRequest.setAcceptFormat(FormatType.JSON); //指定api返回格式
         //describeLiveSnapshotConfigRequest.setMethod(MethodType.POST); //指定请求方法
         //describeLiveSnapshotConfigRequest.setRegionId("cn-shanghai");//指定要访问的Region,仅对当前请求生效，不改变client的默认设置。
         try {
             HttpResponse httpResponse = client.doAction(describeLiveSnapshotConfigRequest);
             System.out.println(httpResponse.getUrl());
             System.out.println(new String(httpResponse.getContent()));
             //todo something.
         } catch (ServerException e) {
             e.printStackTrace();
         } catch (ClientException e) {
             e.printStackTrace();
         }
     }
    }
    ```

4.  发起openAPI调用并解析结果

    利用上一步初始化好的IAcsClient，您可以发起openAPI调用。IAcsClient提供了两种类型的调用结果返回，一种方式是通过调用doAction方法获取取得原始的API调用结果，即返回HttpResponse类型的结果。示例代码如下：

    ```
    public void invokeSample() {
         DescribeLiveSnapshotConfigRequest describeLiveSnapshotConfigRequest = new DescribeLiveSnapshotConfigRequest();
         describeLiveSnapshotConfigRequest.setDomainName("live.aliyunlive.com");
         try {
             HttpResponse httpResponse = client.doAction(describeLiveSnapshotConfigRequest);
             System.out.println(httpResponse.getUrl());
             System.out.println(new String(httpResponse.getContent()));
             //todo something else.
         } catch (ServerException e) {
             e.printStackTrace();
         } catch (ClientException e) {
             e.printStackTrace();
         }
     }
    ```

    另一种方式，通过调用getAcsResponse方法，获取反序列化后的对象，示例代码如下：

    ```
    public void invokeSample() {
         DescribeLiveSnapshotConfigRequest describeLiveSnapshotConfigRequest = new DescribeLiveSnapshotConfigRequest();
         describeLiveSnapshotConfigRequest.setDomainName("live.aliyunlive.com");
         try {
             DescribeLiveSnapshotConfigResponse describeLiveSnapshotConfigResponse = client.getAcsResponse(describeLiveSnapshotConfigRequest);
             //todo something.
         } catch (ServerException e) {
             e.printStackTrace();
         } catch (ClientException e) {
             e.printStackTrace();
         }
     }
    ```


## 异常类型 {#section_wwf_wxd_qfb .section}

-   当http status≥200且<300，表示API调用成功。

-   当http status≥300且<500，SDK抛ClientException，表示客户端错误。

-   当http status≥500，SDK抛ServerException，表示服务器端错误。


