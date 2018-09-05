# Encrypt & Decrypt



```java
package javaapplication8;

import javax.crypto.Cipher;
import javax.crypto.spec.SecretKeySpec;

import java.util.Base64; //Java 8
//import sun.misc.BASE64Decoder; //Java 6
/**
 *
 * @author Doris.Pang
 */
public class JavaApplication8 {

        // 加密
    public static String Encrypt(String sSrc, String sKey) throws Exception {
        if (sKey == null) {
            System.out.print("Key为空null");
            return null;
        }
        // 判断Key是否为16位
        if (sKey.length() != 16) {
            System.out.print("Key长度不是16位");
            return null;
        }
        byte[] raw = sKey.getBytes("utf-8");
        SecretKeySpec skeySpec = new SecretKeySpec(raw, "AES");
        Cipher cipher = Cipher.getInstance("AES/ECB/PKCS5Padding");//"算法/模式/补码方式"
        cipher.init(Cipher.ENCRYPT_MODE, skeySpec);
        byte[] encrypted = cipher.doFinal(sSrc.getBytes("utf-8"));

        return Base64.getEncoder().encodeToString(encrypted);
    }
    
    
        // 解密
    public static String Decrypt(String sSrc, String sKey) throws Exception {
        try {
            // 判断Key是否正确
            if (sKey == null) {
                System.out.print("Key为空null");
                return null;
            }
            // 判断Key是否为16位
            if (sKey.length() != 16) {
                System.out.print("Key长度不是16位");
                return null;
            }
            byte[] raw = sKey.getBytes("utf-8");
            SecretKeySpec skeySpec = new SecretKeySpec(raw, "AES");
            Cipher cipher = Cipher.getInstance("AES/ECB/PKCS5Padding");
            cipher.init(Cipher.DECRYPT_MODE, skeySpec);
            byte[] encrypted1 = Base64.getDecoder().decode(sSrc);//先用base64解密 // Java 8
            //byte[] encrypted1 = new BASE64Decoder().decodeBuffer(sSrc); // Java 6
            try {
                byte[] original = cipher.doFinal(encrypted1);
                String originalString = new String(original,"utf-8");
                return originalString;
            } catch (Exception e) {
                System.out.println(e.toString());
                return null;
            }
        } catch (Exception ex) {
            System.out.println(ex.toString());
            return null;
        }
    }
    
    
    /**
     * @param args the command line arguments
     */
    public static void main(String[] args) throws Exception {
        String cKey = "j7S2xJ54YuHsFUeN";
        
        // 需要加密的字串
        String cSrc = "www.gowhere.so";
        System.out.println(cSrc);
        // 加密
        String enString = JavaApplication8.Encrypt(cSrc, cKey);
        System.out.println("加密后的字串是：" + enString);        
        
        // 解密
        String DeString = JavaApplication8.Decrypt(enString, cKey);
        System.out.println("解密后的字串是：" + DeString);
    }
    
}
```



Reference: 

[https://www.cnblogs.com/chen-lhx/p/5817161.html](https://www.cnblogs.com/chen-lhx/p/5817161.html)

[https://stackoverflow.com/questions/47075678/desede-ecb-nopadding-base64](https://stackoverflow.com/questions/47075678/desede-ecb-nopadding-base64)



