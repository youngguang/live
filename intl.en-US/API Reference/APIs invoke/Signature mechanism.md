# Signature mechanism {#concept_50286_zh .concept}

Alibaba Cloud performs identity authentication for every access request. Therefore, you must contain the signature information in the request no matter whether you submit a request through the HTTP or HTTPS protocol. The requester identity is verified using symmetric encryption of the`Access Key ID`and`Access Key Secret`. The`Access Key ID` and `Access Key Secret` are officially issued to visitors by Alibaba Cloud \(you can apply for and manage them on the Alibaba Cloud official website\). In specific,the`Access Key ID` indicates the identity of the visitor.The`Access Key Secret`is the secret key used to encrypt the signature string and to verify the signature string on the server. It must be kept strictly confidential and only be known to Alibaba Cloud and the user.

**Note:** Alibaba Cloud offers SDKs and third-party SDKs in different languages, which free you of the trouble of coding the signature algorithm. For more information about Alibaba SDK, see[Alibaba Cloud SDK](https://developer.aliyun.com/sdk).

## Signature operation { .section}

When you visit a server, the following method is used to sign the request: 1.

1.  The Canonicalized Query String is constructed using the request parameters.
    1.  Sort parameters.

        All the request parameters \(including the public request parameters and user-defined parameters with given request interfaces, but excluding the`Signature`parameter mentioned in the public request parameters\) are sorted alphabetically by the parameter name.

        **Note:** Note:When a request is submitted using the GET method, these parameters are the parameter section of the request URI \(that is, the section in the URI following? and connected by &\).

    2.  Encode parameters.

        The name and value of each request parameter are encoded. The names and values must adoptUTF-8 characters for URL encoding. The URL encoding rules are as follows:

        -   The characters A-Z, a-z, 0-9, and -, \_, ., ~ are not encoded.

        -   Other characters are encoded into the`%XY`format, with`XY`representing the characters’ ASCII code in hexadecimal notation. For example, the English double quotation marks \(‘’\) are encoded as`%22`.

        -   Extended UTF-8 characters are encoded into the`%XY%ZA…` format.

        -   The English space \( \) is encoded as`%20`, rather than the plus sign \(+\).

            This encoding method and the commonly-used`application/x-www-form-urlencoded` MIME type \(such as`java.net.URLEncoder`in Java library\) are similar, but have differences. If this encoding method is used, use the method of standard library to encode, and then replace the plus signs \(+\) in the encoded strings with`%20`, the asterisks \(\*\) with`%2A`, and change`%7E`back to the tilde \(~\) to get the encoded string described in the previous rules. This algorithm can be achieved bu using the following method:

            ```
            private static final String ENCODING = "UTF-8";
            
            private static String percentEncode(String value) throws UnsupportedEncodingException {
            return value ! = null ? URLEncoder.encode(value, ENCODING).replace("+", "%20").replace("*", "%2A").replace("%7E", "~") : null;
            }
            
            ```

    3.  Connect the encoded parameter names and values with the English equals sign \(=\).
    4.  Then, sort the parameter name and value pairs connected by equal signs in alphabetical order and connect them with the&symbol to produce the Canonicalized Query String.
2.  Construct the string for signature calculation using the canonicalized query string in the previous step according to the following rules.

    ```
    StringToSign=
    HTTPMethod + “&” +
    percentEncode(“/”) + ”&” +
    percentEncode(CanonicalizedQueryString)
    
    ```

    Wherein,

    -    `HTTPMethod`is the HTTP method used for request submission, for example, GET.

    -    `percentEncode(“/”)`is the encoded value \(%2F\) of the character/, which is obtained according to the URL encoding rules described in 1.ii.

    -    `percentEncode(CanonicalizedQueryString)`is the Canonicalized Query String \(constructed in Step 1\) that is encoded according to the URL encoding rules described in 1.ii.

3.  Use the previous signature string to calculate the signature’s HMAC value based on RFC2104 definitions.

    **Note:** The key used for signature calculation is the Access Key Secret held by the user plus the&character \(ASCII:38\), and the SHA1 hashing algorithm is used.

4.  Encode the previous HMAC value into a string based on Base64 encoding rules to obtain the signature value \(Signature\).
5.  Add the obtained signature value to the request parameters as the Signature parameter to sign the request.

    **Note:** Note: URL encoding is required to be performed for the obtained signature value based on the [RFC3986](https://tools.ietf.org/html/rfc3986)rule, like in the case of other parameters, before the signature value is submitted to the live server as the final request parameter value.


## Example {#section_xkk_fdv_cfb .section}

Take DescribeLiveSnapshotConfig as an example, the request URL before signing is as follows:

```language-ini
http://live.aliyuncs.com/?Format=XML&SignatureMethod=HMAC-SHA1&Action=DescribeLiveSnapshotConfig&AccessKeyId=testid&RegionId=cn-shanghai&ServiceCode=live&DomainName=test.com&AppName=test&SignatureNonce=c2fe8fbb-2977-4414-8d39-348d02419c1c&Version=2016-11-01&SignatureVersion=1.0&Timestamp=2017-06-14T09:51:14Z

```

The StringToSign is:

```language-ini
GET&%2F&AccessKeyId%3Dtestid&Action%3DDescribeLiveSnapshotConfig&AppName%3Dtest&DomainName%3Dtest.com&Format%3DXML&RegionId%3Dcn-shanghai&ServiceCode%3Dlive&SignatureMethod%3DHMAC-SHA1&SignatureNonce%3Dc2fe8fbb-2977-4414-8d39-348d02419c1c&SignatureVersion%3D1.0&Timestamp%3D2017-06-14T09%253A51%253A14Z&Version%3D2016-11-01

```

Assume the `Access Key Id`is testid, the`Access Key Secret`is testsecret, and the Key used for HMAC calculation is testsecret&, the calculated signature value is:

```language-ini
3I5a3myPjp8FXWT4rvxX5pKb/aw=

```

The signed request URL is \(note the added Signature parameter\):

```language-ini
http://live.aliyuncs.com/?Format=XML&SignatureMethod=HMAC-SHA1&Signature=3I5a3myPjp8FXWT4rvxX5pKb%2Faw%3D&Timestamp=2017-06-14T09%3A51%3A14Z&Action=DescribeLiveSnapshotConfig&AccessKeyId=testid&RegionId=cn-shanghai&ServiceCode=live&DomainName=test.com&AppName=test&SignatureNonce=c2fe8fbb-2977-4414-8d39-348d02419c1c&Version=2016-11-01&SignatureVersion=1.0

```

