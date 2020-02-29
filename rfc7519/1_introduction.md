# 1.Introduction

   JSON Web Token (JWT) is a compact claims representation format
   intended for space constrained environments such as HTTP
   Authorization headers and URI query parameters.  JWTs encode claims
   to be transmitted as a JSON [[RFC7159](https://tools.ietf.org/html/rfc7159)] object that is used as the
   payload of a JSON Web Signature (JWS) [[JWS](https://tools.ietf.org/html/rfc7519#ref-JWS)] structure or as the
   plaintext of a JSON Web Encryption (JWE) [[JWE](https://tools.ietf.org/html/rfc7519#ref-JWE)] structure, enabling
   the claims to be digitally signed or integrity protected with a
   Message Authentication Code (MAC) and/or encrypted.  JWTs are always
   represented using the JWS Compact Serialization or the JWE Compact
   Serialization.

   The suggested pronunciation of JWT is the same as the English word
   "jot".

## 1.1.  Notational Conventions

   The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT",
   "SHOULD", "SHOULD NOT", "RECOMMENDED", "NOT RECOMMENDED", "MAY", and
   "OPTIONAL" in this document are to be interpreted as described in
   "Key words for use in RFCs to Indicate Requirement Levels" [[RFC2119](https://tools.ietf.org/html/rfc2119)].
   The interpretation should only be applied when the terms appear in
   all capital letters.
