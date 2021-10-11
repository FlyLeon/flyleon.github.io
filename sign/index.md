# 安卓程序签名

> 下面讲的是如何为我们的删除现有Apk签名并重新签名！我们后续的教程使用的是'Uber Apk Signer，所以本闻讲解的是使用'Uber Apk Signer'对项目进行签名！

## 去除签名
- 将后缀apk改为zip
- 删除签名 
 
删除目录中'META_INF"目录除'MAIFEST.MF'文件。

- 改回后缀

## 生成自签名
‘keytool -genkey -alias my_alias -keyalg RSA -validity 20000 -keystore yurname.keystore‘

## 下载'Uber Apk Signer'      
'git clone --depth=1 https://github.com/patrickfav/uber-apk-signer.git'

## 自签名
'java -jar uber-apk-signer.jar -a /path/to/apks --ks /path/release.jks' --ksAlias my_alias'
