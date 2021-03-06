# PHP中接口签名验证

## 概览

工作中，我们时刻都会和接口打交道，有的是调取他人的接口，有的是为他人提供接口，在这过程中肯定都离不开签名验证。

在设计签名验证的时候，一定要满足以下几点：

- 可变性：每次的签名必须是不一样的。
- 时效性：每次请求的时效性，过期作废。
- 唯一性：每次的签名是唯一的。
- 完整性：能够对传入数据进行验证，防止篡改。

## 单向散列加密

#### 定义

把任意长的输入串变化成固定长的输出串，并且由输出串难以得到输入串，这种方法称为单项散列加密。

#### 常用算法

- MD5
- SHA
- MAC
- CRC

#### 优点

**以 MD5 为例。**

- 方便存储：加密后都是固定大小（32位）的字符串，能够分配固定大小的空间存储。
- 损耗低：加密/解密对于性能的损耗微乎其微。
- 文件加密：只需要32位字符串就能对一个巨大的文件验证其完整性。
- 不可逆：大多数的情况下不可逆，具有良好的安全性。

#### 缺点

- 存在暴力破解的可能性，最好通过加盐值的方式提高安全性。

#### 应用场景

- 用于敏感数据，比如用户密码，请求参数，文件加密等。

#### 推荐密码的存储方式

**password_hash()** 使用足够强度的单向散列算法创建密码的哈希（hash）。

PHP 手册地址：

http://php.net/manual/zh/function.password-hash.php

## 对称加密

#### 定义

同一个密钥可以同时用作数据的加密和解密，这种方法称为对称加密。

#### 常用算法

- DES
- AES

AES 是 DES 的升级版，密钥长度更长，选择更多，也更灵活，安全性更高，速度更快。

#### 优点

算法公开、计算量小、加密速度快、加密效率高。

#### 缺点

发送方和接收方必须商定好密钥，然后使双方都能保存好密钥，密钥管理成为双方的负担。

#### 应用场景

相对大一点的数据量或关键数据的加密。

#### AES

AES 加密类库在网上很容易找得到，请注意类库中的 `mcrypt_encrypt` 和 `mcrypt_decrypt` 方法！

在 PHP7.2 版本中已经被弃用了，在新版本中使用 `openssl_encrypt` 和 `openssl_decrypt` 两个方法。

## 非对称加密

#### 定义

需要两个密钥来进行加密和解密，这两个秘钥分别是公钥（public key）和私钥（private key），这种方法称为非对称加密。

#### 常用算法

- RSA

#### 优点

与对称加密相比，安全性更好，加解密需要不同的密钥，公钥和私钥都可进行相互的加解密。

#### 缺点

加密和解密花费时间长、速度慢，只适合对少量数据进行加密。

#### 应用场景

适合于对安全性要求很高的场景，适合加密少量数据，比如支付数据、登录数据等。

#### RSA 与 RSA2

| 算法名称 | 标准名称      | 备注                                      |
| -------- | ------------- | ----------------------------------------- |
| RSA2     | SHA256WithRSA | 强制要求RSA密钥的长度至少为2048           |
| RSA      | SHA1WithRSA   | 对RSA密钥的长度不限制，推荐使用2048位以上 |

RSA2 比 RSA 有更强的安全能力。

蚂蚁金服，新浪微博 都在使用 RSA2 算法。

创建公钥和私钥：

```
openssl genrsa -out private_key.pem 2048openssl rsa -in private_key.pem -pubout -out public_key.pem
```

执行上面命令，会生成 `private_key.pem` 和 `public_key.pem` 两个文件。

![img](D:\write\php\images\rsa2class.jpg)

示例代码：

![img](D:\write\php\images\rsa2demo.jpg)

#### JS-RSA

**JSEncrypt** ：用于执行OpenSSL RSA加密、解密和密钥生成的Javascript库。

Git源：https://github.com/travist/jsencrypt

**应用场景：**

我们在做 WEB 的登录功能时一般是通过 Form 提交或 Ajax 方式提交到服务器进行验证的。

为了防止抓包，登录密码肯定要先进行一次加密（RSA），再提交到服务器进行验证。

一些大公司都在使用，比如淘宝、京东、新浪 等。

示例代码就不提供了，Git上提供的代码是非常完善的。

## 密钥安全管理

这些加密技术，能够达到安全加密效果的前提是 **密钥的保密性**。

实际工作中，不同环境的密钥都应该不同（开发环境、预发布环境、正式环境）。

那么，应该如何安全保存密钥呢？

#### 环境变量

将密钥设置到环境变量中，每次从环境变量中加载。

#### 配置中心

将密钥存放到配置中心，统一进行管理。

#### 密钥过期策略

设置密钥有效期，比如一个月进行重置一次。

**在这里希望大佬提供新的思路 ~**







## 扩展

一、在 HTTP 和 RPC 的选择上，可能会有一些疑问，RPC框架配置比较复杂，明明用HTTP能实现为什么要选择RPC？

下面简单的介绍下 HTTP 与 RPC 的区别。

**传输协议：**

- HTTP 基于 HTTP 协议。
- RPC 即可以 HTTP 协议，也可以 TCP 协议。

HTTP 也是 RPC 实现的一种方式。

**性能消耗：**

- HTTP 大部分基于 JSON 实现的，序列化需要时间和性能。
- RPC 可以基于二进制进行传输，消耗性能少一点。

推荐一个像 JSON ，但比 JSON 传输更快占用更少的新型序列化类库 **MessagePack**。

官网地址：https://msgpack.org/

还有一些服务治理、负载均衡配置的区别。

**使用场景：**

比如浏览器接口、APP接口、第三方接口，推荐使用 HTTP。

比如集团内部的服务调用，推荐使用 RPC。

RPC 比 HTTP 性能消耗低，传输效率高，服务治理也方便。

推荐使用的 RPC 框架：**Thrift**。

二、动态令牌

简单介绍下几种动态令牌，感兴趣的可以深入了解下。

OTP：One-Time Password 一次性密码。

HOTP：HMAC-based One-Time Password 基于HMAC算法加密的一次性密码。

TOTP：Time-based One-Time Password 基于时间戳算法的一次性密码。

使用场景：

- 公司VPN登录双因素验证
- 服务器登录动态密码验证
- 网银、网络游戏的实体动态口令牌
- 银行转账动态密码
- ...

## 转自  訢亮 [新亮笔记](javascript:void(0);) https://mp.weixin.qq.com/s/13uyYs08gtNAMrbgqSCHEw