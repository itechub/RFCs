# 1. 介绍

[rfc7159]: https://tools.ietf.org/html/rfc7159
[jws]: https://tools.ietf.org/html/rfc7519#ref-JWS
[jwe]: https://tools.ietf.org/html/rfc7519#ref-JWE

JSON Web Token（JWT）是一种紧凑的声明表现格式，它适用于空间受限的环境，例如 HTTP 的授权头部和 URI 查询参数。JWTs 将声明编码为 JSON [[RFC7159][rfc7159]] 对象进行传输，该对象作为 JSON Web 签名（JWS, JSON Web Signature）[[JWS][jws]] 的有效载荷，或是 JSON Web 加密（JSE, JSON Web Encryption）[[JWE][jwe]] 的明文表示，从而使得声明数据可以在伴随着**消息认证码**（MAC, Message Authentication Code）时被数字签名并确保完整性。JWTs 只有 **JWS 紧凑序列化**及 **JWE 紧凑序列化**两种呈现形式。

JWT 的推荐发音和英语单词“jot”一致。

## 1.1. 用语约定

[rfc2119]: https://tools.ietf.org/html/rfc2119

本文档中的关键字 "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED", "NOT RECOMMENDED", "MAY" 以及 "OPTIONAL" 的释义和 “用于指示需求级别的 RFC 文件关键字”[[RFC2119][rfc2119]] 中的描述一致。当单词为全大写时才将其视为一个 RFC 关键字。
