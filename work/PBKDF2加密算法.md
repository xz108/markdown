# PBKDF2加密算法
## 做过网站的人都知道用户密码必须经过加密的,其中用的最普遍的就是MD5加密了.但是随着彩虹桥技术的兴起,MD5加密已经不再安全.今天小编就要介绍一种全新的,安全的加密算法:PBKDF2
PBKDF2算法通过多次hash来对密码进行加密。原理是通过password和salt进行hash，然后将结果作为salt在与password进行hash，多次重复此过程，生成最终的密文。此过程可能达到上千次，逆向破解的难度太大，破解一个密码的时间可能需要几百年，所以PBKDF2算法是安全的.
### encode()
   
```java
	/**
	 * PBKDF2加密
	 * @author knight
	 * @param plain 明文
	 * @return String 密文
	 */
	public static String encode(String plain) {
		//1.生成随机盐salt
		byte[] salt = EncryptUtil.generateSalt(32);
		//2.随机盐HEX加密
		String encodeHex = EncryptUtil.encodeHex(salt);
		//3.明文和随机盐一起SHA1运算1024次
		byte[] sha1 = EncryptUtil.sha1(plain.getBytes(), salt, 1024);
		//4.对运算结果进行HEX加密
		String ciperText = EncryptUtil.encodeHex(sha1);
		//4.加密后的随机盐和加密后的明文生成密文
		String finalText=encodeHex+ciperText;
		return finalText;
	} 
```
decode()
```java
/**
	 * PBKDF2解密
	 * @param plain 明文
	 * @param ciper 密文
	 * @return flag 对比结果
	 */
	public static boolean decode(String plain,String ciper) {
		boolean flag=false;
		//1.截取随机盐
		String saltHex = ciper.substring(0, 32*2);
		//2.随机盐解密
		byte[] salt = EncryptUtil.decodeHex(saltHex);
		//3.明文和随机盐一起SHA1运算1024次
		byte[] sha1 = EncryptUtil.sha1(plain.getBytes(), salt, 1024);
		//4.对运算结果进行HEX加密
		String ciperText = EncryptUtil.encodeHex(sha1);
		//5.生成密文
		String finalCiper=saltHex+ciperText;
		if(finalCiper.equals(ciper)) {
			flag=true;
		}
		return flag;
	}
```  
