# RSA Encryption using a public key in Jmeter JSR223 Sampler (Groovy)
 
> 
>def cipher = javax.crypto.Cipher.getInstance('RSA') 
>
>def factory = java.security.KeyFactory.getInstance("RSA")
>
>def PKEY ='' //write your public key here or get it from a variable for your corelation process
>
>def  encodedKeySpec = new java.security.spec.X509EncodedKeySpec(PKEY.decodeBase64())
>
>def publicKey = factory.generatePublic(encodedKeySpec)
>
>cipher.init(javax.crypto.Cipher.ENCRYPT_MODE, publicKey)
>
>String textToEncrypt = '' //write your text to encrypt here or get it from a variable for your 
corelation process
>
>cipherText = cipher.doFinal(textToEncrypt.getBytes()) //cipherText now have your encrypted value
>
>log.info('Encrypted: ' + cipherText.encodeBase64().toString()) // just log the result to view it in log 


## we can use Jmeter User-defined-Variables 

we will have `pubKey` as user defined variable for public key
  `encText` as user defined variable for produced cipherText
  `textToEncrypt` as user defined variable for produced cipherText
 
The code then will be like that : 

> 
>def cipher = javax.crypto.Cipher.getInstance('RSA') 
>
>def factory = java.security.KeyFactory.getInstance("RSA")
>
>def PKEY =vars.get("pubKey") //Getting it from a variable for your corelation process
>
>def  encodedKeySpec = new java.security.spec.X509EncodedKeySpec(PKEY.decodeBase64())
>
>def publicKey = factory.generatePublic(encodedKeySpec)
>
>cipher.init(javax.crypto.Cipher.ENCRYPT_MODE, publicKey)
>
>String textToEncrypt = vars.get("textToEncrypt") //getting the text to encrypt from a variable 
>
>cipherText = cipher.doFinal(textToEncrypt.getBytes()) //cipherText now have your encrypted value
>
>log.info('Encrypted: ' + cipherText.encodeBase64()) // just log the result to view it in log 
>
>vars.put("textToEncrypt",cipherText.encodeBase64().toString())//inserting the ciphertext in user-defined variable textToEncrypt
>


___
### References 
***
>http://www.jmeter-archive.org/JMeter-jsencrypt-using-groovy-td5728601.html
