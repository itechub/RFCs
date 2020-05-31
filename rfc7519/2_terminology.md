# 2. Terminology

[ref-jws]: https://tools.ietf.org/html/rfc7519#ref-JWS

The terms "JSON Web Signature (JWS)", "Base64url Encoding", "Header
Parameter", "JOSE Header", "JWS Compact Serialization", "JWS
Payload", "JWS Signature", and "Unsecured JWS" are defined by the JWS
specification [[JWS][ref-jws]].

[ref-jwe]: https://tools.ietf.org/html/rfc7519#ref-JWE

The terms "JSON Web Encryption (JWE)", "Content Encryption Key
(CEK)", "JWE Compact Serialization", "JWE Encrypted Key", and "JWE
Initialization Vector" are defined by the JWE specification [[JWE][ref-jwe]].

[rfc4949]: https://tools.ietf.org/html/rfc4949

The terms "Ciphertext", "Digital Signature", "Message Authentication
Code (MAC)", and "Plaintext" are defined by the "Internet Security
Glossary, Version 2" [[RFC4949][rfc4949]].

These terms are defined by this specification:

## JSON Web Token (JWT)

A string representing a set of claims as a JSON object that is
encoded in a JWS or JWE, enabling the claims to be digitally
signed or MACed and/or encrypted.

## JWT Claims Set

A JSON object that contains the claims conveyed by the JWT.

## Claim

A piece of information asserted about a subject.  A claim is
represented as a name/value pair consisting of a Claim Name and a
Claim Value.

## Claim Name

The name portion of a claim representation.  A Claim Name is
always a string.

## Claim Value

The value portion of a claim representation.  A Claim Value can be
any JSON value.

## Nested JWT

A JWT in which nested signing and/or encryption are employed.  In
Nested JWTs, a JWT is used as the payload or plaintext value of an
enclosing JWS or JWE structure, respectively.

## Unsecured JWT

A JWT whose claims are not integrity protected or encrypted.

## Collision-Resistant Name

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
