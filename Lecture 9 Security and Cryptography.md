## entropy
随机度：bit=log2(所有可能数)
使用物理工具（字典+骰子...）获得随机度

## Hash Function
1.难以由密文得到明文
2.不同明文很少生成相同密文（collision resisitant）
sha1：转换为160位的密码
可以用于判断两个文件是否内容一致
镜像网站下载
commitment scheme
保证值在确认前后不会发生变化

## key derivation functions
慢速确认密码：避免暴力突破

### 对称加密
key generate (randomized)->key
encrypt(plaintext, key)->ciphertext
decrypt(ciphertext, key)->plaintext

passphrese->kdf->key
key+paintext->encrypt->ciphertext

数据库中存储加密后的用户密码
hash(passwd+salt)
每个库的salt不同，无法通过查表破解


### 非对称加密
usage 1:
key generate (randomized)->public_key, private_key
encrypt(plaintext, public_key)->ciphertext
decrypt(ciphertext, private_key)->plaintext

usage 2:
sign(message, private_key)->signature
verify(message, signature, public_key)->checkout y/n

RSA
加密邮件 
PGP

## Hybrid Encryption
对称加密更快
使用非对称加密交换对称加密的key