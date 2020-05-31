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

A name in a namespace that enables names to be allocated in a
manner such that they are highly unlikely to collide with other
names.  Examples of collision-resistant namespaces include: Domain
Names, Object Identifiers (OIDs) as defined in the ITU-T X.660 and
X.670 Recommendation series, and Universally Unique IDentifiers
(UUIDs) [[RFC4122][rfc4122]].  When using an administratively delegated
namespace, the definer of a name needs to take reasonable
precautions to ensure they are in control of the portion of the
namespace they use to define the name.


## StringOrURI

[rfc3986]: https://tools.ietf.org/html/rfc3986

A JSON string value, with the additional requirement that while
arbitrary string values MAY be used, any value containing a ":"
character MUST be a URI [[RFC3986][rfc3986]].  StringOrURI values are
compared as case-sensitive strings with no transformations or
canonicalizations applied.

## NumericDate

[ref-posix]: https://tools.ietf.org/html/rfc7519#ref-POSIX.1
[rfc3986]: https://tools.ietf.org/html/rfc3339

A JSON numeric value representing the number of seconds from
1970-01-01T00:00:00Z UTC until the specified UTC date/time,
ignoring leap seconds.  This is equivalent to the IEEE Std 1003.1,
2013 Edition [[POSIX.1][ref-posix]] definition "Seconds Since the Epoch", in
which each day is accounted for by exactly 86400 seconds, other
than that non-integer values can be represented.  See RFC 3339
[[RFC3339][rfc3986]] for details regarding date/times in general and UTC in
particular.
