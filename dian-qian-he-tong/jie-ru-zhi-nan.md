### 合同接入指南
---

**简要描述：** 

- 业务背景
   因业务需求，企业的产品中需嵌入工猫管家电子签约功能，确认C端用户先签约（成为合法兼职员工），形成服务合作关系，再提现（发薪）。

**电签功能对接：** 
- 业务对接完成后，需销售主管向工猫总部为该企业开通电签功能。

申请材料包括：
1）企业基本信息
 企业名称，企业简称，合作企业，地址信息（包括省，市，区，详细地址），企业联系人，联系电话，邮箱，税率，管理费
 
2）企业合同模板
 企业按要求填写劳务合同模板条款，交给销售主管，发送至总部邮箱support@gongmall.com申请开通电签功能。
 
  技术人员会根据邮件内容，为新公司上线合同功能做好准备工作，然后回复邮件。
  
- 说明

企业可通过将定制链接地址嵌入到产品流程中，打开地址，传入电子签约所需参数，直接进入合同信息采集页面，员工确认无误后，进入下一步，进行合同签署。
    1、使用银行卡提现：进行签约时，需要进行姓名、身份证、银行卡3要素校验，必须保证为同一人才可以签约 （企业所有用户都需要使用银行卡）
     2、使用支付宝提现：进行签约时，需要进行姓名、身份证、2要素校验，必须保证为同一人才可以签约 （企业所有用户都需要使用支付宝）
暂不支持部分用户使用银行卡，部分用户使用支付宝

**参数列表：**

| 参数名 | 必选 | 类型 | 说明 |
| :--- | :--- | :--- | --- |
| name | 是 | string | 姓名 |
| mobile | 是 | string | 手机号 |
| certificateType| 是 | string | 证件类型 1:身份证 |
| idNumber| 是 | string | 证件号 |
| bankNum| 是 | string | 银行卡号/ 支付宝账户|
| bankName| 否 | string | 银行名称,最长50位 |
| workNumber| 否 | string | 工号,最长50位，可作为用户唯一标识 |
| reserveMobile| 否 | string | 银行卡预留手机号 |
| extraParam| 否 | string | 附言参数，最长500位,由传入方提供，数据量大时建议使用jsonString格式传输。|

{% method %}

extraParam的作用：
    1、回调时将原样返还，可以用来做用户数据标识。
    2、如果电签成功后配置的返回地址需要加动态参数则可以作为动态参数传入(工猫对参数作：
    let encodeExtraParam=encodeURIComponent(extraParam) 操作)，如原返回地址：https://www.example.com/?data=1,如需要返回动态参数，地址将更新为：https://www.example.com/?data=1&extraParam=1234
对返回地址的动态参数extraParam解码后可正常使用（不使用动态参数）,解码方式:

{% sample lang="java" %}
** extraParam动态参数处理：**

```
贵司提供的返回地址uri（如https://www.example.com/?data=1）拼接上&extraParam=encodeExtraParam即url=
https://www.example.com/?data=1&extraParam=encodeExtraParam，并使用decodeURIComponent(extraParam)方法进行解密即可
```
{% sample lang="c#" %}

** extraParam动态参数处理：**

```
贵司提供的返回地址uri（如https://www.example.com/?data=1）拼接上&extraParam=encodeExtraParam即url=
https://www.example.com/?data=1&extraParam=encodeExtraParam，并使用decodeURIComponent(extraParam)方法进行解密即可
```
{% sample lang="php" %}

** extraParam动态参数处理：**

```
贵司提供的返回地址uri（如https://www.example.com/?data=1）拼接上&extraParam=encodeExtraParam即url=
https://www.example.com/?data=1&extraParam=encodeExtraParam，并使用decodeURIComponent(extraParam)方法进行解密即可
```


{% endmethod %}

{% method %}
**请求示例：** 

- 加密前
https://contract-qa.gongmall.com/url_contract.html?companyId=xMEQMG&positionId=AVRKkP&name=王星星&mobile=15212345678&bankName=招商银行&bankNum=6214830100799652&idNumber=620402198709215456&extraParam=1234

- 加密后
https://contract-qa.gongmall.com/url_contract.html?companyId=xMEQMG&positionId=AVRKkP&data=lbrMBX7iME/iutEdBZKq/+dzI6EBnU0WwKQU1r5NEJ5rbYgHK7i7XR2+FPpFmU+BGQ50/PPLyR6Jb2O7FDn6dUjmF3zrrRwPVinQAtmZJU/O8BCGGZxpTM/W1FAW9SHzhAMu4yIETj4u5W2n5uOQ0OSjQSREm4zMl93nw/fuFFQ=

- 备注
https://contract-qa.gongmall.com/url_contract.html?companyId=xMEQMG&positionId=AVRKkP
是我们根据系统生成的公司的唯一请求地址（如果贵司为：不同职位签约不同合同，那么可以根据职位传入positionId），后面的参数信息需要调用方按名称传给我们，用于生成合同和提现匹配。&之后的参数根据appkey+appSecret组合MD5大写作为秘钥，采用AES加密算法(算法中初始化向量IV采用16位的0)，最后将加密后的字符串作为data的值拼接在url请求到工猫，加密算法请参照不同语言示例

### 测试数据：
[1]appkey+appsecret:  061f449a73644770bdbe5a7598f2de74aa233864d1f9204ac3aee5d19969e9ba    
[2]md5(32位): ED7CB552C6DBDBAD71ED6F339C1CF21D      
[3]待加密内容:  name=王星星&mobile=15212345678&bankName=招商银行&bankNum=6214830100799652&idNumber=620402198709215456&extraParam=1234

[4]加密结果： lbrMBX7iME/iutEdBZKq/+dzI6EBnU0WwKQU1r5NEJ5rbYgHK7i7XR2+FPpFmU+BGQ50/PPLyR6Jb2O7FDn6dUjmF3zrrRwPVinQAtmZJU/O8BCGGZxpTM/W1FAW9SHzhAMu4yIETj4u5W2n5uOQ0OSjQSREm4zMl93nw/fuFFQ=

{% sample lang="java" %}
** AES加密算法示例(JAVA)：**

```java
import java.lang.reflect.Constructor;
import java.lang.reflect.Field;
import java.lang.reflect.Modifier;
import java.util.Map;
import javax.crypto.Cipher;
import javax.crypto.spec.IvParameterSpec;
import javax.crypto.spec.SecretKeySpec;
import org.apache.commons.codec.binary.Base64;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;
public class AESEncryptUtil {
    private static final Logger logger = LoggerFactory.getLogger(AESEncryptUtil.class);
    private static final String UTF8 = "UTF-8";
    private static final String AES_ALG = "AES";
    private static final String AES_CBC_PCK_ALG = "AES/CBC/PKCS5Padding";
    private static final byte[] AES_IV = initIv(AES_CBC_PCK_ALG);
   /**
    *使用此加密方式，请将JDK已经升级至jdk8u191及以上版本
    */
     
    /**
     * AES加密
     * 
     * @param content
     * @param encryptType
     * @return
     */
    public static String aesEncrypt(String content, String aesKey) {
        return aesEncrypt(content, aesKey, UTF8);
    }
    /**
     * AES解密
     * 
     * @param content
     * @param encryptType
     * @return
     */
    public static String aesDecrypt(String content, String aesKey) {
        return aesDecrypt(content, aesKey, UTF8);
    }
    /**
     * AES加密
     * 
     * @param content
     * @param aesKey
     * @param charset
     * @return
     */
    public static String aesEncrypt(String content, String aesKey, String charset) {
        try {
            Cipher cipher = Cipher.getInstance(AES_CBC_PCK_ALG);
            IvParameterSpec iv = new IvParameterSpec(AES_IV);
            cipher.init(Cipher.ENCRYPT_MODE,
                new SecretKeySpec(Base64.decodeBase64(aesKey.getBytes()), AES_ALG), iv);
            byte[] encryptBytes = cipher.doFinal(content.getBytes(charset));
            return new String(Base64.encodeBase64(encryptBytes));
        } catch (Exception e) {
            logger.error("AES加密失败：Aescontent = " + content + "; charset = " + charset, e);
            return null;
        }
    }
    /**
     * AES解密
     * 
     * @param content
     * @param key
     * @param charset
     * @return
     */
    public static String aesDecrypt(String content, String aesKey, String charset) {
        try {
            Cipher cipher = Cipher.getInstance(AES_CBC_PCK_ALG);
            IvParameterSpec iv = new IvParameterSpec(AES_IV);
            cipher.init(Cipher.DECRYPT_MODE, new SecretKeySpec(Base64.decodeBase64(aesKey.getBytes()),
                AES_ALG), iv);
            byte[] cleanBytes = cipher.doFinal(Base64.decodeBase64(content.getBytes()));
            return new String(cleanBytes, charset);
        } catch (Exception e) {
            logger.error("AES解密失败：Aescontent = " + content + "; charset = " + charset, e);
            return null;
        }
    }
    /**
     * 初始向量的方法, 全部为0. 针对AES算法的话,IV值一定是128位的(16字节).
     *
     * @param fullAlg
     * @return
     */
    private static byte[] initIv(String fullAlg) {
        try {
            Cipher cipher = Cipher.getInstance(fullAlg);
            int blockSize = cipher.getBlockSize();
            byte[] iv = new byte[blockSize];
            for (int i = 0; i < blockSize; ++i) {
                iv[i] = 0;
            }
            return iv;
        } catch (Exception e) {
            int blockSize = 16;
            byte[] iv = new byte[blockSize];
            for (int i = 0; i < blockSize; ++i) {
                iv[i] = 0;
            }
            return iv;
        }
    }
}

```

{% sample lang="c#" %}
** AES加密算法示例(C#)：**

```c#
using System;
using System.Collections.Generic;
using System.Text;
using System.Security.Cryptography;
using System.IO;
namespace Gongmall.Util
{
    public class AESEncryptUtil
    {
        /// <summary>
        /// 128位0向量
        /// </summary>
        private static byte[] AES_IV = initIv(16);
        /// <summary>
        /// AES 加密
        /// </summary>
        /// <param name="encryptKey"></param>
        /// <param name="bizContent"></param>
        /// <param name="charset"></param>
        /// <returns></returns>
        public static string AesEncrypt(string encryptKey, string bizContent) => AesEncrypt(encryptKey, bizContent, Encoding.UTF8.BodyName);
        /// <summary>
        /// AES 加密
        /// </summary>
        /// <param name="encryptKey"></param>
        /// <param name="bizContent"></param>
        /// <param name="charset"></param>
        /// <returns></returns>
        public static string AesEncrypt(string encryptKey, string bizContent, string charset)
        {
            Byte[] keyArray = Convert.FromBase64String(encryptKey);
            Byte[] toEncryptArray = null;
            if (string.IsNullOrEmpty(charset))
            {
                toEncryptArray = Encoding.UTF8.GetBytes(bizContent);
            }
            else
            {
                toEncryptArray = Encoding.GetEncoding(charset).GetBytes(bizContent);
            }
            System.Security.Cryptography.RijndaelManaged rDel = new System.Security.Cryptography.RijndaelManaged();
            rDel.Key = keyArray;
            rDel.Mode = System.Security.Cryptography.CipherMode.CBC;
            rDel.Padding = System.Security.Cryptography.PaddingMode.PKCS7;
            rDel.IV = AES_IV;
            System.Security.Cryptography.ICryptoTransform cTransform = rDel.CreateEncryptor(rDel.Key, rDel.IV);
            Byte[] resultArray = cTransform.TransformFinalBlock(toEncryptArray, 0, toEncryptArray.Length);
            return Convert.ToBase64String(resultArray);
        }
        /// <summary>
        /// AES解密
        /// </summary>
        /// <param name="encryptKey"></param>
        /// <param name="bizContent"></param>
        /// <param name="charset"></param>
        /// <returns></returns>
        public static string AesDencrypt(string encryptKey, string bizContent) => AesDencrypt(encryptKey, bizContent, Encoding.UTF8.BodyName);
        /// <summary>
        /// AES解密
        /// </summary>
        /// <param name="encryptKey"></param>
        /// <param name="bizContent"></param>
        /// <param name="charset"></param>
        /// <returns></returns>
        public static string AesDencrypt(string encryptKey, string bizContent, string charset)
        {
            Byte[] keyArray = Convert.FromBase64String(encryptKey);
            Byte[] toEncryptArray = Convert.FromBase64String(bizContent);
            System.Security.Cryptography.RijndaelManaged rDel = new System.Security.Cryptography.RijndaelManaged();
            rDel.Key = keyArray;
            rDel.Mode = System.Security.Cryptography.CipherMode.CBC;
            rDel.Padding = System.Security.Cryptography.PaddingMode.PKCS7;
            rDel.IV = AES_IV;
            System.Security.Cryptography.ICryptoTransform cTransform = rDel.CreateDecryptor(rDel.Key, rDel.IV);
            Byte[] resultArray = cTransform.TransformFinalBlock(toEncryptArray, 0, toEncryptArray.Length);
            if (string.IsNullOrEmpty(charset))
            {
                return Encoding.UTF8.GetString(resultArray);
            }
            else
            {
                return Encoding.GetEncoding(charset).GetString(resultArray);
            }
        }
        /// <summary>
        /// 初始化向量
        /// </summary>
        /// <param name="blockSize"></param>
        /// <returns></returns>
        private static byte[] initIv(int blockSize)
        {
            byte[] iv = new byte[blockSize];
            for (int i = 0; i < blockSize; i++)
            {
                iv[i] = (byte)0x0;
            }
            return iv;
        }
    }
}

```

{% sample lang="php" %}
** AES加密算法示例(PHP)：**

```php#
    //data为AES加密数据
        $plaintext  = urldecode(http_build_query($data));
    //加密key由配置的appKey与appSecret生成
        $key = strtoupper(md5($this->appKey . $this->appSecret));
    //偏移量
        $size = 16;$iv = str_repeat("\0",$size);
    // 添加Padding，使用//PKCS5Padding
        $padding = $size - strlen($plaintext) % $size;
        $plaintext .= str_repeat(chr($padding), $padding);
    //使用AES-192-CBC进行加密
        $encrypted = openssl_encrypt($plaintext, 'AES-192-CBC',base64_decode($key),OPENSSL_RAW_DATA | OPENSSL_ZERO_PADDING, $iv);
    //加密结果
        $contractUrl = $this->contractUrl."&data=".base64_encode($encrypted);
    return $contractUrl;

```
{% endmethod %}