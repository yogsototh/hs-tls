> This project has two homes.
> It is ok to work in github, still, for a better decentralized web
> please consider contributing (issues, PR, etc...) throught:
>
> https://gitlab.esy.fun/yogsototh/hs-tls

---


haskell TLS
===========

This library provides native Haskell TLS and SSL protocol implementation for server and client.

Description
-----------

This provides a high-level implementation of a sensitive security protocol,
eliminating a common set of security issues through the use of the advanced
type system, high level constructions and common Haskell features.

Features
--------

* tiny codebase (more than 20 times smaller than OpenSSL, and 10 times smaller than gnuTLS)
* client certificates
* permissive license: BSD3
* supported versions: SSL3, TLS1.0, TLS1.1, TLS1.2
* key exchange supported: RSA, DHE-RSA, DHE-DSS
* bulk algorithm supported: any stream or block ciphers
* supported extensions: secure renegociation, next protocol negotiation (draft 2), server name indication

Common Issues
=============

The tools mentioned below are all available from the tls-debug package.

Certificate issues
------------------

It's useful to run the following command, which will connect to the destination and
retrieve the certificate chained used.

    tls-retrievecertificate -d <destination> -p <port> -v -c

As an output it will print every certificate in the chain and will give the issuer and subjects of each.
It creates a chain where issuer of certificate is the subject of the next certificate part of the chain:

    (subject #1, issuer #2) -> (subject #2, issuer #3) -> (subject #3, issuer #3)

A "CA is unknown" error indicates that your system doesn't have a certificate in
the trusted store belonging to any of the node of the chain.

TLS issues
----------

When having unknown issues with TLS, if your protocol is HTTP based it's useful to use tls-simpleclient from the
tls-debug package.

    tls-simpleclient -d -v <www.myserver.com> <port>

This provides useful information for debugging issues related to TLS.
