# 2. 术语

[ref-jws]: https://tools.ietf.org/html/rfc7519#ref-JWS

词组 "JSON Web Signature (JWS)", "Base64url Encoding", "Header
Parameter", "JOSE Header", "JWS Compact Serialization", "JWS
Payload", "JWS Signature", 以及 "Unsecured JWS" 的相关定义可以在 JWS 标准 [[JWS][ref-jws]] 中找到.

[ref-jwe]: https://tools.ietf.org/html/rfc7519#ref-JWE

词组 "JSON Web Encryption (JWE)", "Content Encryption Key
(CEK)", "JWE Compact Serialization", "JWE Encrypted Key", 以及 "JWE
Initialization Vector" 的相关定义可以在 JWE 标准 [[JWE][ref-jwe]] 中找到.

[rfc4949]: https://tools.ietf.org/html/rfc4949

词组 "Ciphertext", "Digital Signature", "Message Authentication
Code (MAC)", 以及 "Plaintext" 的相关定义可以在 "Internet Security
Glossary, Version 2" [[RFC4949][rfc4949]] 中找到.

相关词组的定义标准如下：

## JSON Web Token (JWT)

通过 JWS 或者 JWE 将声明数据集编码成一个字符串 JSON 对象，从而使得声明数据通过加密/非加密方式进行数字签名，或通过 **消息认证码**（MAC, Message Authentication Code）进行数据完整性保护。

## 声明数据集（JWT Claims Set）

一个 JSON 对象，包含一个或多个由 JWT 进行转换的声明数据。

## 声明数据（Claim）

声明数据定义了一个主体的声明信息。通常一个声明数据由一对键值对组成，分别称之为声明域及声明值。

## 声明域（Claim Name）

声明数据中的域部分，通常声明域是一个字符串。

## 声明值（Claim Value）

声明数据中的值部分，通常声明值可以是任意 JSON 对象。

## 嵌套 JWT（Nested JWT）

一个包含嵌套的加密/非加密数字签名的 JWT。在嵌套的 JWTs 中，相对应的，JWT 作为 JWS 的有效载荷，或是 JSE 的明文表示。

## 不安全的 JWT(Unsecured JWT)
该 JWT 包含的声明数据没有进行完整性保护或者加密。

## 抗碰撞命名(Collision-Resistant Name)

[rfc4122]: https://tools.ietf.org/html/rfc4122

抗碰撞命名指的是通过命名空间，从而保证命名空间内相关命名不会与其他命名冲突。相对应的抗碰撞命名空间名包括如下： 域名、ITU-T X.660 及 X.670 中提倡的对象标识(OIDs)定义、全局唯一标识符(UUIDs)[[RFC4122][rfc4122]]。使用管理委托的名称空间时，名称的定义者需要采取合理的预防措施，以确保它们可以控制用于定义名称的名称空间部分。

## StringOrURI

[rfc3986]: https://tools.ietf.org/html/rfc3986

一个 JSON 字符串值，附带以下相关约束。其对应的值可以是任意字符串，但如果该字符串包含 ":" 字符， 那么该字符串必须是一个 URI [[RFC3986][rfc3986]] 格式. StringOrURI 值通常被当作大小写敏感的字符串做对比，对比之前不会做特殊的转换或适配。

## NumericDate

[ref-posix]: https://tools.ietf.org/html/rfc7519#ref-POSIX.1
[rfc3986]: https://tools.ietf.org/html/rfc3339

一个 JSON 数值，用于表示指定 UTC 格式时间与 1970-01-01T00:00:00Z UTC 的差值（以秒为单位，忽略闰秒）。 这与 IEEE Std 1003.1, 2013 Edition [[POSIX.1][ref-posix]] 中 "Seconds Since the Epoch" 的定义一致，其中定义每一天为标准 86400 秒，而不采用非整数型数值进行表示。更多关于 日期/时间 及 UTC 详情请参考 RFC 3339
[[RFC3339][rfc3986]] 文档。