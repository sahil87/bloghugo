---
title: 'JWT: JSON Web Token - Passing on the secret without letting the neighours know'
date: 2016-11-23 16:43:52
tags: [jwt, web]
categories: [guide]
author: Sahil Ahuja
---
Login is still a tough problem! It's been 5 years since I left coding professionally and still parts of this remain unresolved.

<!--more-->
Hello JWT
=========
During my search for a good encrytion system to store user secrets, I came across something very cool - [JWT](https://jwt.io/introduction/) - reminds me of the RSA public/private key encription system - only modified to be much more user friendly for web/mobile development.
 
JWT creates a token that can be decrypted only by person having a secret key using which it was encrypted. As long the website stores JWT in it's cookie, the server can decrypt the cookie every time and trust the decrypted content. 

This allows us to store sensitive information like user id and user permissions in the cookie. This is a stateless authentication mechanism as the user state is never saved in server memory. The server's protected routes will check for a valid JWT in the Authorization header, and if it's present, the user will be allowed to access protected resources. As JWTs are self-contained, all the necessary information is there, reducing the need to query the database multiple times.

Structure of a JWT token
=======================
JSON Web Tokens consist of three parts separated by dots (.), which are: Header, Payload, Signature

**Header**: The header typically consists of two parts: the type of the token, which is JWT, and the hashing algorithm being used, such as HMAC SHA256 or RSA.

**Payload**: Contains the claims. There are three types of claims: reserved, public, and private
1. Reserved claims: Set of predefined claims which are not mandatory but recommended, to provide a set of useful, interoperable claims. Some of them are: iss (issuer), exp (expiration time), sub (subject), aud (audience), and others.
1. Public claims: These can be defined at will by those using JWTs.
1. Private claims: These are the custom claims created to share information between parties that agree on using them.

Example payload:
```
{
 "sub": "1234567890",
 "name": "John Doe",
 "admin": true
}
```
**Signature**: Take the encoded header, encoded payload, a secret, the algorith specified in header and sign that
`HMACSHA256(base64UrlEncode(header) + "." + base64UrlEncode(payload), secret)`

For more details: https://jwt.io/