### 合同接入指南
---

**简要描述：** 

- 业务背景
   因业务需求，企业的产品中需嵌入工猫管家电子签约功能，确认C端用户先签约（成为合法兼职员工），形成劳务关系，再提现（发薪）。

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

**参数列表：**

| 参数名 | 必选 | 类型 | 说明 |
| :--- | :--- | :--- | --- |
| name | 是 | string | 姓名 |
| mobile | 是 | string | 手机号 |
| certificateType| 是 | string | 证件类型 1:身份证 |
| idNumber| 是 | string | 证件号 |
| bankNum| 是 | string | 银行卡号 |
| bankName| 否 | string | 银行名称 |
| workNumber| 否 | string | 工号，可作为用户唯一标识 |
| extraParam| 否 | string | 附言参数，由传入方提供，回调时将原样返还，可以用来做用户数据标识。数据量大时建议使用jsonString格式传输 |



{% method %}
**请求地址示例：** 

- 加密前
https://contract-qa.gongmall.com/url_contract.html?companyId=xMEQMG&name=王星星&mobile=15212345678&idNumber=620402198709215456&bankName=招商银行&bankNum=6214830100799652

- 加密后
https://contract-qa.gongmall.com/url_contract.html?companyId=xMEQMG&data=lbrMBX7iME/iutEdBZKq/+dzI6EBnU0WwKQU1r5NEJ42evQt+RuqSa+8rk9BvRuYbT9jWJBQOo3kUw+48+MHVLv3SDWIFEgT6DNhKVQaEwmcOe2rhPtgF4NLALMkoGfoFglg57fJgmnUnLjIoyRGYQ==

- 备注
https://contract-qa.gongmall.com/url_contract.html?companyId=xMEQMG
是我们根据系统生成的公司的唯一请求地址，后面的参数信息需要调用方按名称传给我们，用于生成合同和提现匹配。&之后的参数根据appkey+appSecret组合MD5大写作为秘钥，采用AES加密算法(算法中初始化向量IV采用16位的0)，最后将加密后的字符串作为data的值拼接在url请求到工猫，加密算法请参照不同语言示例

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
    static {
        fixKeyLength();
    }
    /**
     * 针对AES算法密钥长度限制进行hack
     */
    @SuppressWarnings({ "rawtypes", "unchecked" })
    private static void fixKeyLength() {
        String errorString = "Failed manually overriding key-length permissions.";
        int newMaxKeyLength;
        try {
            if ((newMaxKeyLength = Cipher.getMaxAllowedKeyLength("AES")) < 256) {
                Class c = Class.forName("javax.crypto.CryptoAllPermissionCollection");
                Constructor con = c.getDeclaredConstructor();
                con.setAccessible(true);
                Object allPermissionCollection = con.newInstance();
                Field f = c.getDeclaredField("all_allowed");
                f.setAccessible(true);
                f.setBoolean(allPermissionCollection, true);
                c = Class.forName("javax.crypto.CryptoPermissions");
                con = c.getDeclaredConstructor();
                con.setAccessible(true);
                Object allPermissions = con.newInstance();
                f = c.getDeclaredField("perms");
                f.setAccessible(true);
                ((Map) f.get(allPermissions)).put("*", allPermissionCollection);
                c = Class.forName("javax.crypto.JceSecurityManager");
                f = c.getDeclaredField("defaultPolicy");
                f.setAccessible(true);
                Field mf = Field.class.getDeclaredField("modifiers");
                mf.setAccessible(true);
                mf.setInt(f, f.getModifiers() & ~Modifier.FINAL);
                f.set(null, allPermissions);
                newMaxKeyLength = Cipher.getMaxAllowedKeyLength("AES");
            }
        } catch (Exception e) {
            throw new RuntimeException(errorString, e);
        }
        if (newMaxKeyLength < 256)
            throw new RuntimeException(errorString); // hack failed
    }
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
{% endmethod %}